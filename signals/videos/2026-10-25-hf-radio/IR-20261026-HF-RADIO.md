# HF as a Backup Comms Layer

**Source** — "HF Radio: The OP Weapon of Modern Minutemen", `@CivilDefenseEngineer`, 42:06.
Transcript: `transcript.md`.

A preparedness guide to HF radio. The strongest source in this area on propagation, and it contains the best
single technical statement in the archive — stated almost in passing — while getting the central propagation
mechanism backwards twice.

## The alternatives, and why they fail

| Option | Claim | Assessment |
|---|---|---|
| Starlink | Parallel infrastructure; vulnerable to one operator's policy | Correct, and the political point is the substantive one |
| Baofeng VHF/UHF | 2–3 miles handheld | Correct |
| Repeaters | One repeater boosts power and elevation; it is not a mesh | **Correct, and the best correction in the survey** |
| Meshtastic | Every node relays; 1–2 miles; good for a dense crowd, not a dispersed group | Correct |

The repeater misconception — that a repeater network works like a cell network, so that tapping in lets you
reach anyone in a region — is widespread and worth correcting. Range is set by radio horizon,
`d ≈ 4.1(√h₁ + √h₂)` km with height in metres: a handheld at 1.7 m and a repeater at 100 m gives ~46 km; two
handhelds at 1.7 m give ~11 km. **The variable is height, not power.**

The framing error is that HF is presented as a competitor to local comms when it is a different layer. A PACE
plan needs both — HF for the 200-mile link, VHF/Meshtastic for the 2-mile link. The video's conclusion
("don't use this for everything") is right and disagrees with its own framing.

## Propagation

| Layer | Altitude | Day/night | Role |
|---|---|---|---|
| **D** | 60–90 km | Day only | **Absorption** — attenuates HF passing through |
| **E** | 90–150 km | Day; sporadic at night | Weak refraction; occasional Sporadic-E openings |
| **F1** | 150–220 km | Day only | Merges with F2 at night |
| **F2** | 220–500 km | Day and night | **The main refracting layer** for long-haul HF |

Three paths. **Ground wave** hugs the surface, reaching tens of kilometres on 40 m and dying with frequency.
**Skywave** refracts at a shallow takeoff angle and lands hundreds to thousands of kilometres away, in one or
more hops, attenuating heavily with each bounce. **NVIS** refracts at near-vertical incidence and returns
steeply, reaching 0–500 km.

The **skip zone** is the annulus too far for ground wave and too near for low-angle skywave. It is not a
defect of HF; it is the reason NVIS is necessary. The source's explanation of this is correct and clear.

**The inversion.** The source says the D layer "absorbs higher frequency, lower wavelength" and "allows the
lower frequency, higher wavelength to pass through." Both clauses are backwards. Absorption is proportional
to electron density over the square of frequency:

```
A ∝ N_e / f²
```

**Low frequencies are absorbed heavily; high frequencies pass through almost untouched.** This one relation
explains why 80 m and 160 m are daytime-dead and night-viable, why 40 m works day and night with a daytime
penalty, why 20 m is a daytime band, and why the maximum usable frequency rises during the day.

The "sorry, yeah" mid-sentence suggests he caught a slip and corrected in the wrong direction. And the advice
that follows — use 40 m "because it doesn't get absorbed by that D layer" — is correct and contradicts the
explanation given ninety seconds earlier. **The practical advice is right and the mechanism is inverted,
which means the reader can follow the instruction but cannot generalise it to a new band or hour.**

## NVIS

The insight: *"NVIS is a type of propagation, not a type of antenna."* That distinction is between a mode and
a configuration. NVIS is what the ionosphere does with a steep-angle signal; the antenna configuration only
*biases* the takeoff angle. A low horizontal dipole radiates a lobe near the zenith **and** residual low-angle
lobes — which is exactly why a "NVIS antenna" still makes contacts well beyond the nominal radius.

Three consequences: range is probabilistic rather than bounded, since the nominal 200–300 mile figure is a
mode of the distribution; terrain independence is conditional, because NVIS clears mountains *because* the
path is steep while the low-angle component does not; and DF resistance is partial, since a strong low-angle
component is direction-findable even when the NVIS component is not.

**The heights, computed** at 7.078 MHz (λ = 42.4 m):

| Criterion | Metric | Imperial |
|---|---|---|
| NVIS maximum (λ/10) | **4.24 m** | **13.9 ft** |
| Skywave minimum (λ/2) | 21.2 m | 69.5 ft |
| Half-wave dipole (468/f) | 20.1 m | 66.1 ft |

The two criteria differ by a factor of five, which is why the same wire behaves completely differently
depending on where it hangs.

**The accidental compliance.** The author's attic dipole sits at roughly 2.5–3 m — inside the NVIS window by
construction, because an attic is not tall enough to violate it. The 400-mile contact is therefore better
explained by the low height forcing a high takeoff angle, plus the residual low-angle lobe he himself
identifies, plus possibly a second hop — in that order. He offers the second and third and misses the first,
which is the one his geometry guarantees.

**Direction finding.** A ground-based DF array resolves a bearing from the horizontal phase or amplitude
gradient across its elements. A signal arriving at 70–90° elevation presents almost no horizontal gradient,
so the bearing is poorly determined. The station is locatable in principle but not by a simple baseline. This
is correct, and it connects directly to the previous report in this area, where the same author announced he
was acquiring a Doppler RDF unit. **The two videos are a matched pair on the same problem from both sides**,
and neither states the synthesis: the counter to DF is a steep takeoff angle, low power and short
transmissions; the counter to that is a multi-site DF network that resolves elevation as well as bearing.

## Space weather

Solar flux energises the ionosphere and follows an 11-year cycle; the field is currently near maximum, which
is why aurora appeared as far south as Alabama. Increased flux boosts the ionosphere but also brings flare
activity and geomagnetic storms, during which the ionosphere is too unstable for skywave — the source's
"reflective pool versus stormy sea" analogy, though the mechanism is refraction rather than reflection.

The practical advice — use a published band-conditions service rather than learning the indices — is sound.
"K factor" should be the **Kp index**. And the honest caveat is right: band predictions are often wrong in
both directions.

## The antenna

The formula `468/f(MHz)` gives length in feet for a half-wave dipole; the constant is `492 × 0.95`, where 0.95
accounts for end effect and velocity factor. At 7.078 MHz that is 66.1 ft.

The balun explanation is imprecise. A **1:1 balun does not change the impedance ratio.** It forces the
transition from a balanced antenna to unbalanced coax, suppressing **common-mode current** on the shield,
which otherwise causes pattern distortion, unpredictable SWR, a "hot" feedline that radiates, and receiver
noise pickup from the shack. A 4:1 balun *would* transform impedance. **The advice is right, the stated
reason is wrong, and the correct reason is a safety reason** — a radiating feedline indoors is an
RF-exposure problem.

The "better is the enemy of good enough" principle is sound engineering judgment with a boundary: a dipole cut
for 7.078 MHz fed with a 2:1 mismatch loses about 0.5 dB, invisible on the air, so chasing the last
half-decibel is irrational. But chasing a resonant antenna at all is rational, because a 10:1 mismatch can
destroy a QRP final stage. **The boundary is the point at which inefficiency becomes equipment damage.**

Attic penalties — asphalt shingles, roofing nails, particle board — are correctly identified, and the nails
are the significant one: metal fasteners within a fraction of a wavelength detune the antenna, absorb energy
as lossy parasitic elements, and can arc at high power if contact is intermittent.

## Gear

The list is a QRP transceiver, coax and connectors, antenna wire, balun, DigiRig and cable, and a "beater
computer." Three omissions matter:

- **No SWR meter.** A QRP final is cheap and unprotected; a badly mismatched antenna can destroy it in
  seconds. A $20 meter or a nanoVNA is the difference between a working station and a dead radio, and costs
  less than the coax. **This is the omission with the highest expected cost.**
- **No antenna tuner** — needed only for non-resonant wire, so defensible.
- **No RF-exposure assessment** — see below.

## Settings

The USB/LSB clarification is genuinely useful and proportionate to the failure rate. The convention is LSB
for voice below 10 MHz and USB above (a historical artefact, not physics), but **digital modes use USB on
every band**, because the software defines the audio passband relative to the suppressed carrier and expects
a consistent inversion. Getting this wrong produces a signal that decodes as garbage.

The 3–4 kHz filter is correct for the audio passband and is not a contradiction of the narrowband argument:
the **RF** signal is ~50 Hz, while the audio passband must contain the sub-band you are monitoring.

**RTS keying** — request-to-send as a PTT line over RS-232 — is used when CAT control is unavailable or
unwanted, which is the case for a (tr)uSDX with limited CAT support. Choosing RTS over CAT is right for this
rig; the source does not explain why, so a reader with a different radio may copy the wrong choice.

## JS8Call, and the number it never gives

JS8Call inherits FT8's **15-second T/R period** structure, so symbols must land within the slot; a clock error
beyond ~1–2 s causes partial decodes, which is why the waterfall shows dots. The standard remedy is a
time-synchronisation service; whether a specific "automatic time drift" control exists could not be confirmed.

Heartbeats advertise presence and are relayed, effectively building a crowdsourced propagation map — and
incidentally a location-disclosure mechanism, since heartbeats carry the sender's grid square. A six-character
Maidenhead locator is roughly a 6 × 4 km cell; four characters is ~150 × 100 km. That is a deliberate
coarse-graining, which is the right design, but it is a trade rather than a mere convenience.

The security statement is honest and correct: *"It's not encrypted, but it's encoded into its own digital
protocol… anybody who's listening who is decoding on JS8 will be able to read your messages in the clear…
it adds a little bit of security by obscurity, but don't count on it."* Encoding is not encryption; the
protocol is public, the software is free, and decoding is the default behaviour of every listener.

Relaying is genuinely a network capability without infrastructure — and it has a consequence the video does
not mention: **every relay operator can read the message.** A relayed message is not a confidential message.

**The missing number: 17 dB.** "Weak signal mode" is not a claim about sensitivity; it is a claim about
bandwidth.

```
SNR = P_signal / (N₀ · B)
Narrowing B by factor k raises SNR by 10 log₁₀(k) dB
```

| Mode | Occupied bandwidth | Noise in that band |
|---|---|---|
| SSB voice | ~2,500 Hz | 0 dB reference |
| **JS8Call** | **~50 Hz** | **−17.0 dB** |

Seventeen decibels for free — equivalent to raising a 10 W transmitter to ~500 W, or to a 17 dB antenna. The
costs are throughput, latency, synchronisation, and the assumption that noise is flat across the band, which
impulse noise and interference violate.

In the source's own measurements, −14 dB and −1 dB are quoted in JS8Call's 2,500 Hz reference, which means
**+3 dB and +16 dB in the 50 Hz the decoder actually uses**. Both contacts are comfortably above the noise.
The signal was never weak; it was only weak in a bandwidth nothing was using.

## The link budget, and the regime

| Term | Value |
|---|---|
| Transmit power | **+40.0 dBm** (10 W) |
| Dipoles, transmit and receive | +2.15 dBi each |
| **FSPL**, 644 km at 7.078 MHz | **−105.6 dB** |
| **Received power** (free space, no ionospheric loss) | **−61.3 dBm** |
| Thermal noise, 2,500 Hz | −140.0 dBm |
| Thermal noise, 50 Hz | −157.0 dBm |
| **Actual HF noise floor (atmospheric)** | **≈ −95 to −105 dBm** |

HF is **noise-limited, not sensitivity-limited**. External noise is 40–50 dB above thermal in a quiet rural
location and higher in a city, so a better receiver buys almost nothing; the SNR is set by antenna and band.
But noise power scales with bandwidth, so bandwidth is a direct and free lever.

Compared with the geostationary link in the adjacent report: path loss is **82 dB lower** and the noise floor
is **40–50 dB higher**, and the two effects nearly cancel. That is why a 10 W wire antenna and an 8-ft dish
reach comparable distances in different bands, and it is the most useful comparison this area has produced.

## Corrections

- **The D-layer mechanism is inverted twice** (above).
- **"The FCC doesn't really care. They never find you."** False, and contradicted three sentences later by
  "get your license." Unlicensed transmission on amateur allocations is a federal offence, the Enforcement
  Bureau maintains a routine published record of notices and consent decrees including for HF operation, and
  detection is driven by complaints and DF rather than by patrols. The practical risk is tail risk — most are
  not caught; the ones who are, are caught expensively. The likely reason for the framing is audience
  sympathy, which is exactly the direction of bias the format predicts.
- **The fictitious call sign.** The JS8Call configuration is shown as "CDEA1," with the explanation that the
  author is licensed but does not want to publish his real call sign. The privacy motive is legitimate; the
  method is not — transmissions must identify the station with its assigned call sign. The compliant solution
  is a PO box on the licence and a grid square rather than coordinates in software.
- **QRP is ≤5 W CW and ≤10 W SSB**, not "under 10 watts," because SSB is peak-envelope power.
- **"K factor"** → Kp index.
- **The 30° cone** for NVIS corresponds to 60–90° elevation; the statement is correct and easy to misread.

## Safety

100 W into an attic dipole with people below is a genuine hazard evaluation the video does not perform. At
7 MHz the wavelength is 42 m, so the near-field boundary for a 20 m dipole is tens of metres — **every point
inside the house is in the near field**, where `P/(4πr²)` does not apply and field strength must be measured
or modelled.

US amateur stations must evaluate compliance with RF exposure limits; the general-population limits apply to
anyone who is not the licensee, i.e. family members in the house; and antennas inside a dwelling are among the
configurations that require evaluation rather than assumption. Mitigations are cheap: reduce power when people
are present (10 dB from 100 W to 10 W), locate the antenna away from occupied rooms, operate with a duty
cycle, use an outdoor wire, or measure rather than assume.

The video recommends the specific configuration — attic antenna, up to 100 W, occupied space below — that most
requires an evaluation, and does not mention exposure at all.

## Verification

The FCC enforcement record is asserted rather than cited and should be sourced. JS8Call's timing controls are
unverified. The NVIS critical-frequency relation — above which NVIS fails — is absent, so the report says
NVIS works but not when it stops. The JS8Call occupied bandwidth is approximate, and the 17 dB figure scales
directly with it.
