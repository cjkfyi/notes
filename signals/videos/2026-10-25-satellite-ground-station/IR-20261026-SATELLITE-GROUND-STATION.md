# A Backyard L-Band Ground Station

**Source** — "I Built a MASSIVE Satellite Ground Station in My Backyard", `@cranktowncity`, 46:42.
Transcript: `transcript.md`.

A build log rather than an explainer, and valuable for a reason the genre usually misses: the author
documents his own failures in enough detail to diagnose them. Seven independent faults are shown, diagnosed
on camera and fixed. A tutorial would have hidden exactly these.

## What was built

An 8-ft surplus dish — a C-band TVRO reflector from the 1980s–90s — on a fabricated azimuth/elevation mount,
driving a Raspberry Pi that points it, tracks satellites and decodes weather imagery.

Repurposing a 4 GHz dish at 1.7 GHz is sensible: the surface-accuracy requirement scales with wavelength, so
a dish figured for C-band is over-specified at L-band by more than a factor of two. **The reflector is the
one component that gets better with age and lower frequency.**

## The mechanical work

**Elevation** uses the dish's original linear actuator; **azimuth** uses a scavenged wheelchair motor, 24 V
with a worm gear. The shaft was machined for concentricity on the lathe, using two plasma-cut discs tacked
inside a pipe and reamed to the shaft diameter — reaching about 20 thou (0.5 mm) of deviation.

**Drive v1** used plasma-cut gears. Two independent problems: a plasma-cut tooth is not an involute, so
contact is point-like rather than rolling; and welding concentrates heat asymmetrically, so shrinkage warped
the part until the gear "got stuck on the shaft." **Drive v2** substituted a scrap flywheel and pinion —
solving a precision problem by *buying* precision rather than manufacturing it, which is the right decision
when the tolerance is beyond the available process.

The motor then flexed under load. The fix was a tensioner, described by the author as "a trashy tensioning
mechanism" that he "pretended was okay." That is the most honest sentence in the video and also the correct
engineering judgment: the flex is a **compliance problem** — the mount is not stiff enough to hold the pinion
centre distance under tangential load — and a tensioner converts stiffness into preload, at the cost of
adding a wearing part and a source of drift.

A third iteration added gussets to stop the flywheel flexing.

## Pointing

AS5600 magnetic encoders, 12-bit, mounted **offset through a gear reduction** — for resolution and because
there was no good way to mount them on-axis.

```
AS5600 = 4096 counts/rev = 0.0879°/count
Direct on axis:            0.088°
Through a 5:1 reduction:   0.0176°
```

A PID loop with a **deadband** of 0.1° prevents limit cycling. The measured residual is 0.3° of backlash.

**The measurement out-resolved the mechanism by a factor of fifteen**, so the limiting error is mechanical
and improving the encoder would do nothing. The author reaches this conclusion correctly and then does not
act on it: he attributes the 0.3° to "a better gearbox" being needed, when it is a property of the worm drive
he chose. Self-locking worm drives have backlash by construction, because thread clearance is what prevents
binding — **the 0.3° is the price of the property that made the drive suitable.**

Against the antenna's 5.1° beamwidth, 0.3° is 6% of beam, worth approximately **0.004 dB**. The defect he
spent a day eliminating never affected his signal.

One internal inconsistency: he says the encoders are "directly on the axis," which contradicts the gearing.
The measurement is still valid — a geared encoder reports axis position with more resolution — but the stated
reasoning is confused.

## Wind stow, and the crash

Wind sensors on the shop roof feed an ESP32 which sends data over RS-485. Above a threshold the azimuth
turns 90° from the wind and elevation goes to 90°. At elevation 90° the aperture faces the zenith, presenting
the minimum projected area to horizontal wind; azimuthing broadside means the dish turns edge-on rather than
face-on, halving the load. Correct.

On first boot the linear actuator was wired backwards, the controller did not detect an encoder signal, and
**it went to stow** — driving the dish down and destroying an encoder.

That is a **fail-safe inversion**: the controller treated "no encoder signal" as "wind is high, stow now."
The safe response to a lost sensor is to stop, not to move. The general rule the video does not state: **a
protective action must be gated on positive evidence of the hazard, not on absence of evidence of safety.**

The fix — hard stops plus calibration switches — is correct, but the design lesson is the one to record.

**Limit switches on a linear actuator** use a switch and a diode per end. The diode is oriented so current
passes around the open switch in one polarity only, so the switch cuts power in the direction that would
drive further into the stop while permitting motion away from it. Two components, no logic. This is the
strongest single piece of electrical work in the build.

## The RF chain

GOES transmits at **1694.1 MHz** (HRIT) with **right-hand circular polarization**. A reflection reverses the
handedness of circular polarization as seen along the propagation direction — the field component parallel to
the plane of incidence inverts while the perpendicular component does not — so the feed must be **left-hand
circular**. The author states this correctly and it is the most technically sophisticated element in the
build.

The penalty for getting it wrong is not 3 dB. A wrong-sense circular antenna has a cross-polar discrimination
of roughly 20 dB or more; it is nearly blind. **This is a hard-fail parameter, not a tuning parameter**, and
it is the single most likely reason a first-time L-band build receives nothing. He identified it from reading
rather than from failure, which is why it is the one fault that did not cost him a day.

The feed is an axial-mode helix, which requires circumference ≈ 1λ (177 mm at 1.694 GHz), turn spacing ≈ λ/4,
at least 3–4 turns, and a ground plane ≥ 3λ/4. Gain is ~8–10 dBi — twenty decibels less than the dish, which
is the point of the budget below.

Chain: Sawbird band-tuned LNA at the antenna → RTL-SDR → Raspberry Pi running SatDump. **The LNA is mounted
at the antenna, not at the receiver**, because any loss before the first amplifier adds directly to the noise
figure; moving it ten metres down a lossy cable would cost more than it gains. The video places it correctly
without explaining why.

## The link budget it never computes

| Term | Value | Working |
|---|---|---|
| **FSPL** at 1694.1 MHz over 35,786 km | **−188.1 dB** | `20log(35786) + 20log(1694.1) + 32.45` |
| **G_rx** for 8 ft (2.438 m) at λ = 0.177 m, η = 0.55 | **+30.1 dBi** | `η(πD/λ)² = 0.55 × 43.3²` |
| **Beamwidth** | **5.1°** | `70λ/D` |
| **Noise floor**, 1 MHz, NF 0.8 dB | **≈ −113.2 dBm** | `−174 + 60 + 0.8` |

Solving backwards from the reported **8.5–9 dB SNR**:

```
P_rx  =  −113.2 + 9   =  −104.2 dBm
EIRP  =  −104.2 + 188.1 − 30.1  =  +53.8 dBW
```

An implied satellite EIRP of ~54 dBW, plausible for a dedicated wide-area broadcast downlink. That is a
**consistency check, not a measurement** — the EIRP is back-solved from the observation.

**The conclusion that reorders the story:** remove the dish. A 0 dBi antenna receives −134.3 dBm against a
−113.2 dBm noise floor — **21 dB below the noise**, undetectable in any bandwidth wide enough to carry the
data.

**The system is the dish.** The reflector contributes ~100% of the working margin; the LNA is a refinement;
the helix is small. That predicts the failure modes: if the link is marginal, the fixes that work are more
aperture, a lower-noise LNA, or a shorter cable — in that order. The fixes that do not work are a better
decoder, a faster SDR, or a more accurate mount.

## The fault record

| # | Fault | Signature | Root cause | Class |
|---|---|---|---|---|
| F-1 | Plasma-cut gear warped, seized | Binding after welding | Weld distortion + non-involute profile | Manufacturing |
| F-2 | Motor flexes under load | Visible deflection | Insufficient mount stiffness | Structural |
| F-3 | Dish crashed, encoder destroyed | Uncommanded motion on boot | **Lost sensor → stow triggered** | **Control logic** |
| F-4 | Pointed at a decommissioned satellite | No signal; 1 dB = noise | **Stale operational knowledge** | **Procedural** |
| F-5 | Female SMA with no pin | Open circuit that looks connected | Cheap adapter | Connector |
| F-6 | Comb of spectral spikes | Narrowband spikes across the band | **Double-powered LNA** | **Power/grounding** |
| F-7 | Weak, distorted signal at correct pointing | Low SNR after everything else | **Feed not at focus** | **Optical** |

Of seven, two are RF/optical, two are control logic and procedure, three are fabrication. **The fabrication
faults were the slowest to find and the least consequential; the RF faults were the fastest to find once the
right instrument was pointed at them.**

**F-4 is not a technical fault at all.** GOES-16 had been replaced by GOES-19 in 2025. The information
existed, was freely available, and was not checked. It cost a full diagnostic cycle in a domain where the
author was already out of his depth.

**F-6** deserves precision: a bias tee injects DC onto the coax centre conductor to power a mast amplifier.
Powering the device *also* by USB parallels two supplies through its internal rail, producing ground loops
between USB ground and coax shield, coupling switching noise into the RF path. The signature — a comb of
narrow spikes — is the signature of a switching supply, not of a signal.

**F-7** is the real fix at the end. The reflector's focal length is fixed geometry, but the **phase centre of
the feed** is not at its physical aperture. A helix's phase centre sits well behind its ground plane, so a
helix placed where a C-band feedhorn sat is out of focus. Extending the coupler moved it forward. The author
found this empirically rather than by calculation.

## Why the hard target

There are two ways to receive weather imagery, an order of magnitude apart in difficulty:

| Path | Frequency | Antenna | Product | Difficulty |
|---|---|---|---|---|
| NOAA APT | 137 MHz | V-dipole, ~50 cm | Low-resolution strip, ~4 km/pixel | Trivial |
| **GOES HRIT** | **1694 MHz** | 8-ft dish, az/el, tracking | Full disc, 1 km/pixel, every 10 min | **Hard** |

The reason to accept the difficulty is **the product**. APT gives a narrow strip at low resolution twice a
day; GOES gives a full disc continuously. The 8-ft dish is not a way of receiving weather data; it is a way of
receiving a particular kind of weather data.

## Safety: the omission

During a storm: "It's lightning and that thing's begging to get struck." Correct observation, no mitigation
described.

A 2.4 m metal reflector on an outdoor pad, connected by Ethernet and mains power to a building, is a lightning
attractor with a direct conductive path indoors. The standard measures are absent: bond the dish and mount to
a grounding electrode; ground the coax shield at the entry point with a bulkhead arrestor; ground the Ethernet
at entry; single-point bond to the building's electrode system.

**This is also an RF measure.** A floating shield and a USB-powered mast amplifier on a long cable is exactly
the configuration that produced F-6. The same fix that protects the equipment from lightning removes the
ground loop that put spikes in the spectrum. He found the noise empirically and did not connect it to the
missing bond.

Also unaddressed: ice loading, and the forward plan to add radio astronomy — passive and unlicensed, but any
future transmit capability changes the compliance picture entirely.

## Verification

The link budget terms were computed. GOES HRIT EIRP, modulation, occupied bandwidth and FEC are not
published in the video, so the budget rests on a back-solve. The dish's f/D is unmeasured, so the focus
discussion is qualitative. Lightning-protection measures are listed from standard practice without a
citation.
