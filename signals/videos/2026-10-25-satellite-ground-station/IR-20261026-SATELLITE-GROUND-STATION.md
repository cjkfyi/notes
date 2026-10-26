```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

# A BACKYARD L-BAND GROUND STATION
## Link Budget, Polarization Sense, and the Mechanical Errors That Actually Mattered

| Field | Value |
|---|---|
| **Report No.** | IR-20261026-SATELLITE-GROUND-STATION |
| **DTG** | 260713ZOCT26 |
| **Classification** | UNCLASSIFIED // OPEN SOURCE |
| **Originator** | Analyst (independent) |
| **Source** | `transcript.md` (same folder) — ASR transcript, 46:42 runtime, unchaptered |
| **Source path** | `notes/signals/videos/2026-10-25-satellite-ground-station/transcript.md` |
| **Source type** | OSINT — build documentary; first-person, single practitioner, self-declared novice in the subject |
| **Reliability** | **B2** — usually reliable, probably true. See ¶2.2 |
| **Subject** | 8-ft surplus dish, az/el mount, L-band reception of GOES and Meteor; pointing control |
| **Distribution** | Unlimited |
| **Handling** | Analytic exercise. Includes a safety and compliance section (§7). |

**Handling caveat.** `[SOURCE CLAIM]` marks reproduction without endorsement; `[ANALYST ADD]` marks material from outside the source. The report's principal addition is the **link budget the source never computes** (§5), which is presented as a template with computed terms marked.

---

## TABLE OF CONTENTS

- **1. BLUF**
- **2. Source Assessment**
- **3. Framework** — why the dB chain is a different verification method · the receive chain · the design space
- **4. Technical Analysis** — the reflector · the feed · the chain · pointing · the mechanics
- **5. The Missing Link Budget**
- **6. The Mistakes, as Evidence**
- **7. Safety and Compliance**
- **8. Cross-Archive Links**
- **9. Indicators and Warnings**
- **10. Intelligence Gaps and Key Judgments**
- **Appendices A–G**

---

## 1. BLUF — BOTTOM LINE UP FRONT

**1.1** This is the archive's first **build log** rather than an explainer, and it is valuable for a reason the genre usually misses: **the author documents his own failures in enough detail to diagnose them.** Five separate faults are shown, diagnosed on camera, and fixed. That is a better evidentiary record than a polished tutorial, because a tutorial hides the failure modes that a builder will actually encounter. **Confidence: high.**

**1.2 — The single largest omission is the link budget, and computing it changes the story.** The video never adds up the decibels. Doing so shows that the **dish is the entire system**: at 1.694 GHz an 8-ft reflector yields about **30 dBi**, and without it the received signal sits roughly **21 dB below the noise floor** and is undetectable regardless of what electronics are attached. **Every other component is a refinement of a link that the antenna alone makes possible.** **Confidence: high** (the computed terms).

**1.3 — The polarization handling is the most technically sophisticated thing in the video and it is correct.** GOES transmits right-hand circular; the reflection off the dish reverses the sense; therefore the feed must be left-hand circular. The source states this and builds the correct antenna. **This is the kind of detail that silently fails a build, and the author got it right while claiming to know nothing about the subject.** **Confidence: high.**

**1.4 — The mechanical work is where the real engineering happened, and the source misdiagnoses one thing.** The azimuth drive was rebuilt three times: plasma-cut gears with welding warpage, then a scrap flywheel and pinion, then gussets to stop the flywheel flexing. **The lesson is that the drive train, not the electronics, is the hard part** — and the source half-knows this. What he does not note is that the **0.3° of backlash he measures is a property of the gearbox he chose**, not a defect to be tuned out; a worm drive was selected for holding torque and worm drives have backlash by construction. **Confidence: moderate-high.**

**1.5 — One internal inconsistency is worth flagging.** The source says the encoders are geared down for resolution and then, later, that "the encoders are directly on the axis" — which is how he justifies measuring gearbox slop. **Both cannot be true.** The measurement is still valid (the encoder reports axis position either way), but the reasoning as stated is confused. **Confidence: high.**

**1.6 — The safety gap is real and unaddressed: no grounding.** The author says the dish "is begging to get struck" during a thunderstorm and then goes inside. A 2.4-metre metal reflector on a 3-foot concrete pad, connected by Ethernet and power to a building, is a lightning attractor with no bond to earth described anywhere in the build. **This is the most consequential omission in the video and it is not a technicality.** **Confidence: high.**

**1.7 — Why this belongs in `signals/` rather than `eng/`.** The build is mostly fabrication, but the **verification method** is different, and that is what separates the areas. In `eng/` a claim is checked by recomputing a number after the fact. Here the entire system can be **summed as a decibel chain before anything is built**, and that sum predicts whether it will work. **A link budget is a prediction, not a post-mortem** — and the source's failure to write one is exactly why he spent a day pointing at a satellite that had been decommissioned. **Confidence: high.**

---

## 2. SOURCE ASSESSMENT

### 2.1 Provenance

**2.1.1** A 46-minute, 42-second build documentary by `@cranktowncity`, URL `https://www.youtube.com/watch?v=jto2xUEAp0Q`. Local capture: `transcript.md`, same folder. Unchaptered; the transcript is a continuous narration over build footage.

**2.1.2 — Stated competence.** The author is explicit and unusually honest about his position: *"I truly know basically nothing about this hobby."* He separates what he knows — *"I know how to weld stuff. I know how to make motor go burr"* — from what he does not. **This is the reverse of the usual credibility problem in this archive**: instead of over-claiming authority, the source under-claims it and then demonstrates competence in the parts he does claim.

**2.1.3 — Structure**, inferred from content:

| Phase | Content | Approx. span |
|---|---|---|
| 1 | Motivation; the 8-ft dish from Facebook Marketplace | 0:00–1:36 |
| 2 | Scavenging: linear actuator, wheelchair motor | 1:36–2:48 |
| 3 | CAD; the base enclosure | 2:48–5:15 |
| 4 | The shaft — machining for concentricity | 5:15–7:21 |
| 5 | Drive mechanism v1 — plasma-cut gears, warpage | 7:21–11:18 |
| 6 | Assembly; discovery of slop | 11:18–13:18 |
| 7 | Drive mechanism v2 — flywheel and pinion | 13:18–16:38 |
| 8 | Encoders — AS5600, geared offset | 16:38–19:34 |
| 9 | Electronics; first motion; deadband; backlash measured | 19:34–23:08 |
| 10 | Finishing, concrete, install | 23:08–26:23 |
| 11 | Wind stow; the crash; limit switches | 26:23–30:15 |
| 12 | Dish mounted; calibration | 30:15–33:40 |
| 13 | Antenna, LNA, SDR; the five faults | 33:40–39:40 |
| 14 | Raster scan; GOES images; homing | 39:40–42:24 |
| 15 | LEO tracking; Meteor; BladeRF; wrap | 42:24–46:42 |

### 2.2 Reliability grading

| Axis | Grade | Basis |
|---|---|---|
| **Source reliability** | **B — Usually reliable** | First-person, unedited, self-critical; failures shown rather than hidden; but self-declared novice in the subject and several technical statements are loose |
| **Information credibility** | **2 — Probably true** | The build evidently worked — full-disc images are shown. Mechanisms and components are identifiable and correct. Numerical claims are approximate |
| **Composite** | **B2** | Usable as a field record of what actually goes wrong; not usable as a tutorial for the RF design |

**2.2.1 — What raises the grade, and it is unusual.** The source's value is **failure density**. A polished tutorial shows a working system and implies a linear path. This shows:
- three iterations of the azimuth drive;
- a crash that destroyed an encoder;
- a satellite that no longer exists;
- a connector with no pin;
- a double-powered LNA;
- a feed at the wrong focal distance.

**Six independent faults, each diagnosed from evidence.** For an analyst, that is a richer dataset than a success story, because each fault is a *specific* way the system fails and the diagnosis reveals the underlying model.

**2.2.2 — What lowers it.** Three things:
1. **No link budget, no noise figure, no gain figures.** The RF design is entirely empirical — built, pointed, and adjusted until it worked. That is a legitimate engineering method and it leaves the design unexplained.
2. **The encoder description is internally inconsistent** (¶1.5).
3. **The 0.3° slop is attributed to the wrong cause** — presented as a defect of *this* gearbox rather than as an intrinsic property of worm drives (¶1.4).

### 2.3 Conflict of interest

**2.3.1** No sponsor read in the transcript. A Patreon build-log is referenced; a 3D-printable antenna scaffold is credited to a third party ("AZ Dave") with a link. No affiliate structure is evident.

**2.3.2 — The one structural interest.** The video is a **build narrative**, and build narratives have a known bias toward the *visible* work. The fabrication — welding, machining, painting, concrete — consumes most of the runtime and most of the author's evident effort. The RF design, which is the part that determines whether any of it works, gets four minutes. **This is not dishonesty; it is the natural gravity of a maker channel, and it is the reason the link budget is missing.**

### 2.4 Transcription integrity

| As transcribed | Correct form | Note |
|---|---|---|
| "Lband" | **L-band** | 1–2 GHz |
| "cat" ("after doing the cat") | **CAD** | — |
| "posting ground" | **post hole** / setting a post | — |
| "scrapard" | **scrapyard** | — |
| "trilly drilly" | *(presenter's idiom)* | — |
| "I squared C" | **I²C** | — |
| "PWM signal from the pie" | **from the Pi** | — |
| "pit loop" / "pit loop" | **PID loop** | Central to §4.4 |
| "deadband to 01" | **0.1°** | — |
| "spurgeear" / "spurgeear" | **spur gear** | — |
| "vain attempt" | **vain attempt** | Correct as spoken |
| "AS5600" | **AS5600** | Correct — 12-bit magnetic encoder |
| "SAT dump" / "sat dump" | **SatDump** | — |
| "Celeste Track" | **CelesTrak** | — |
| "Skyfield by Brandon Roads" | **Skyfield**, by **Brandon Rhodes** | — |
| "TLE's" | **TLEs** — two-line elements | — |
| "Sawbird" | **Sawbird** (Nooelec LNA) | — |
| "RTL SDR" | **RTL-SDR** | — |
| "Blade RF" | **BladeRF** | — |
| "bias T" | **bias tee** | §6.3 |
| "1694.1 MGHertz" | **1694.1 MHz** | — |
| "goes" / "GO 16" / "GO 19" | **GOES-16 / GOES-19** | §6.4 |
| "MedOpsc" / "Medtop" | **Meteor-M** | Russian weather satellite series |
| "mea" / "messalike" / "messalike" | **M-shaped** (spectral peak) | — |
| "RS485" | **RS-485** | — |
| "Aperture Science" | *(Portal reference)* | — |
| "doobly-doo" | *(description box)* | — |

**2.4.1 — The "PID" corruption is the one that matters.** "Pit loop" appears twice and is the control law for the whole mount. A reader unfamiliar with control terminology would not recover it. **This is the archive's recurring lesson**: ASR destroys exactly the terms that carry the technical content, and the report must restore them before analysis.

### 2.5 Verification status

| Claim | Locus | Status |
|---|---|---|
| L-band ≈ 1–2 GHz | 0:47 | **Verified** (0.3–3 GHz by convention) |
| Linear actuator draws 7 A | 2:00 | **Plausible** for a heavy satellite actuator |
| Wheelchair motor: 24 V, worm gear | 2:30 | **Verified** — standard |
| Bearing preload via two pillow blocks | 4:50 | **Correct practice** |
| Shaft concentricity within ~20 thou | 6:50 | **Plausible**; 0.5 mm |
| Plasma-cut gears mesh acceptably | 13:39 | **True, with limits** — see ¶4.5.1 |
| AS5600 is a magnetic angular encoder | 18:01 | **Verified**; 12-bit |
| Gearing an encoder increases resolution | 17:37 | **Correct** |
| PID with deadband prevents oscillation | 21:55 | **Correct** |
| 0.1° deadband achieved | 22:02 | **Plausible** |
| 0.3° of backlash measured | 22:34 | **Plausible**; cause misattributed (¶4.5.4) |
| Wind stow: az 90° from wind, el 90° | 26:42 | **Correct** — minimum projected area |
| Linear actuator limit wiring: switch + diode per end | 27:31 | **Verified** — standard diode-OR endstop |
| GOES downlink 1.694 GHz, RHCP | 32:25 | **Verified** — HRIT at 1694.1 MHz |
| Reflection reverses polarization sense → LHCP feed | 32:32 | **Verified and correct** (¶4.2.2) |
| Helical circumference ≈ λ for axial mode | 32:39 | **Verified** |
| Sawbird LNA tuned to the band, low noise | 33:53 | **Verified** |
| RTL-SDR + SatDump decode pipeline | 34:13 | **Verified** |
| GOES-16 replaced by GOES-19 in 2025 | 37:11 | **Consistent with the record** |
| 1 dB received = background noise | 37:36 | **Correct interpretation** |
| Missing pin in female SMA | 38:01 | **Verified** — a real failure mode |
| Bias tee + USB power = double powering, noise | 38:14 | **Correct diagnosis** |
| Feed must sit at the focal point | 38:50 | **Verified** — the actual fix |
| ~1% BER acceptable; 0.0001 ideal | 39:12 | **Correct** |
| 8.5–9 dB SNR on GOES | 40:27 | **Plausible** — consistent with §5 |
| 10×10° raster search, iteratively narrowed | 39:47 | **Correct method** |
| TLEs from CelesTrak via Skyfield | 42:49 | **Verified** |
| Meteor-M needs higher bandwidth → BladeRF | 43:50 | **Verified in outline** |
| Arctic Weather Satellite has only a microwave radiometer | 44:37 | **Verified** |

---

## 3. FRAMEWORK

### 3.1 Why a dB chain is a different kind of verification

**3.1.1** `[ANALYST ADD]` In `eng/` the method is to recompute a number after the fact — check the draw ratio, check the attenuation. In RF the method is different in kind:

```
P_rx(dBm) = P_tx(dBm) + G_tx(dBi) − FSPL(dB) + G_rx(dBi) − L_cable(dB)
```

**Every term is additive in decibels, so the entire system can be summed on one line before anything is built.** The result is not a post-mortem; it is a **prediction**. And because the prediction is a single number, it is falsifiable in the cheapest possible way — you can know a design will fail without cutting a single piece of metal.

**3.1.2 — Why that makes this a separate area.** The distinguishing question in `signals/` is not "is this number right?" but **"does the budget close?"** A link that closes by 3 dB works; one that closes by −3 dB does not, and no amount of good fabrication changes that. **The source never asks, and the consequence is visible in the video**: he spends a day pointing at a decommissioned satellite and then wiggles the dish hoping for a signal, which is what you do when you have no model of how much signal to expect.

### 3.2 The receive chain, and what each element is for

`[ANALYST ADD]` The system is five elements, and each one addresses a different term in the budget:

| Element | Function | Term addressed |
|---|---|---|
| **Reflector** (8 ft) | Collects and concentrates | `G_rx` ≈ +30 dBi — **the dominant gain** |
| **Feed** (helical) | Transduces the wave to a guided mode, with the correct polarization | Polarization match; feed gain ~8–10 dBi |
| **LNA** (Sawbird) | Amplifies before cable loss, adding minimal noise | Sets system noise temperature |
| **Cable** | Transport | Loss — must come *after* the LNA |
| **SDR** (RTL-SDR) | Digitises | Sets dynamic range and sample rate |
| **Decoder** (SatDump) | Demodulates and decodes | BER |

**3.2.1 — The ordering is not arbitrary and the source gets it right.** `[ANALYST ADD]` The LNA is mounted **at the antenna**, not at the receiver, because any loss before the first amplifier adds directly to the noise figure. **Moving the LNA 10 m down a lossy cable would cost more than the LNA gains.** This is the single most important topological rule in receive systems, and the video places the LNA correctly without explaining why.

### 3.3 The design space the builder chose

**3.3.1** `[ANALYST ADD]` There are two ways to receive weather imagery, and they differ by an order of magnitude in difficulty:

| Path | Frequency | Antenna | Product | Difficulty |
|---|---|---|---|---|
| **NOAA APT** | 137 MHz | Simple V-dipole, ~50 cm | Low-resolution strip, ~4 km/pixel | **Trivial** — a €30 SDR and wire |
| **GOES HRIT** | 1694 MHz | **8-ft dish, az/el mount, tracking** | Full-disc, 1 km/pixel, every 10 min | **Hard** — this project |

**3.3.2 — The choice is the interesting part.** `[SOURCE CLAIM]` The author goes straight to L-band geostationary without attempting the easy path.

**Assessment: this is the correct engineering read of the video, and it is not stated.** `[ANALYST ADD]` The reason to accept the difficulty is **the product**: APT gives a narrow strip at low resolution from a satellite passing overhead twice a day; GOES gives a **full disc, continuously, at 1 km resolution**. The 8-ft dish is not a way of receiving weather data; it is a way of receiving *a particular kind* of weather data. **The mount exists because geostationary reception needs no tracking — and he built tracking anyway, for the LEO satellites.** That is the actual design logic and the video only implies it.

---

## 4. TECHNICAL ANALYSIS

### 4.1 The reflector

**4.1.1 — What the dish is.** `[SOURCE CLAIM]` An 8-ft dish from Facebook Marketplace, with a mounting ring and a linear actuator, previously used for something else.

**Assessment: it is a surplus C-band TVRO dish.** `[ANALYST ADD]` 8–10 ft prime-focus dishes were mass-produced for satellite television in the 1980s–90s at 3.7–4.2 GHz. Repurposing one for 1.7 GHz is entirely sensible: the **surface accuracy requirement scales with wavelength**, so a dish figured for 4 GHz is over-specified at 1.7 GHz by more than a factor of two. **The reflector is the one component that gets better with age and lower frequency.**

**4.1.2 — The consequence the video discovers empirically.** `[SOURCE CLAIM]` "I built this assuming the whole thing was radially concentric, but obviously not" — and later, the feed had to be extended because "the focal point was a lot closer to the ground plane" than expected.

**Assessment: this is the wavelength-dependence of the *feed*, not of the reflector.** `[ANALYST ADD]` The reflector's focal length is fixed geometry. But the **phase centre of the feed** is not at its physical aperture — it depends on the feed's design and its operating wavelength. A helical antenna's phase centre sits well behind its ground plane, so a helix designed for 1.7 GHz placed where a C-band feedhorn sat will be out of focus. **Moving it forward was the correct fix and it was found by experiment rather than calculation.**

**4.1.3 — The geometry worth having.** `[ANALYST ADD]` For a prime-focus paraboloid:

```
f = D² / (16c)          (focal length from diameter and depth)
f/D ≈ 0.3–0.4          (typical for TVRO dishes)
```

and the half-power beamwidth:

```
θ ≈ 70° · λ / D
```

At 1.694 GHz (λ = 0.177 m) and D = 2.438 m:

```
θ ≈ 70 × 0.177 / 2.438 ≈ 5.1°
```

**That number matters for everything downstream** (¶4.4.4): a 5° beam means the 0.3° pointing accuracy is about 6% of the beamwidth, and the 10° raster is two beamwidths across — a sensible search pattern by luck or by feel.

### 4.2 The feed, and the polarization inversion

**4.2.1 — The claim.** `[SOURCE CLAIM]` "The signal emitted from GOES is approximately 1.694 GHz with a right-hand circular polarization. The polarization is actually reversed after bouncing off of the dish. So we need a left-hand polarized helical antenna with a circumference that roughly matches the wavelength."

**Assessment: correct in every part, and this is the most technically impressive passage in the video.**

**4.2.2 — Why the inversion happens.** `[ANALYST ADD]` A reflection reverses the handedness of circular polarization **as seen along the direction of propagation**. The mechanism is that the electric field component parallel to the plane of incidence is inverted while the perpendicular component is not, which flips the rotation sense when the wave reverses direction. **Consequence: a RHCP wave reflecting off a metal surface becomes LHCP**, and a feed cut for RHCP would be cross-polarized.

**4.2.3 — And the penalty for getting it wrong is not 3 dB.** `[ANALYST ADD]` For circular polarization, an antenna of the wrong sense has a **cross-polar discrimination of roughly 20 dB or more** — it is nearly blind, not merely degraded. **So this is a hard-fail parameter, not a tuning parameter**, and it is the single most likely reason a first-time L-band build receives nothing. **The author identified it from reading rather than from failure, which is why it is the one fault in the video that did not cost him a day.**

**4.2.4 — The helix geometry, checked.** `[SOURCE CLAIM]` Circumference ≈ wavelength, built on a 3D-printed scaffold.

**Assessment: correct for axial-mode operation.** `[ANALYST ADD]` Axial-mode (end-fire) helical antennas require:

| Parameter | Requirement | At 1.694 GHz |
|---|---|---|
| Circumference | ≈ 1λ | **177 mm** |
| Turn spacing | ≈ λ/4 | ~44 mm |
| Turns | ≥ 3–4 for good axial ratio | — |
| Ground plane | ≥ 3λ/4 diameter | ≥ 133 mm |
| Gain | ~8–10 dBi for a small helix | — |

**The helix adds ~9 dBi, which is 20 dB less than the dish.** That asymmetry is the point of §5: **the feed's gain is almost irrelevant next to the reflector's.**

### 4.3 The receive chain, and the fault that produced the noise

**4.3.1 — The stack.** `[SOURCE CLAIM]` Sawbird LNA (band-tuned, low noise) → RTL-SDR → Raspberry Pi running SatDump.

**Assessment: correct and standard.** `[ANALYST ADD]` The Sawbird is a filtered LNA with a noise figure around 0.8 dB and a band-pass response that rejects out-of-band interference — important at 1.7 GHz, where mobile base stations and GPS are nearby.

**4.3.2 — The double-powering fault.** `[SOURCE CLAIM]` The LNA was being powered both through the bias tee (over the coax) and through the USB connection; the resulting spikes were noise from the USB power supply.

**Assessment: correct diagnosis, and the mechanism is worth stating precisely.** `[ANALYST ADD]` A bias tee injects DC onto the coax centre conductor to power a mast-mounted amplifier. If the device is *also* powered by USB, two supplies are paralleled through the LNA's internal rail — which produces:
- **Ground loops** between the USB ground and the coax shield, coupling switching noise from the computer into the RF path;
- **Supply contention**, which can raise the noise floor or damage the regulator.

**The signature in the spectrum — a comb of narrow spikes — is the signature of a switching supply, not of the signal.** Recognising "these spikes are my power supply" from the shape of the plot is a real skill, and the author acquired it in one session.

**4.3.3 — The missing pin.** `[SOURCE CLAIM]` A female SMA connector with no centre pin; a normal male has a pin, "and here we have a female connector with no freaking pin."

**Assessment: this is a real and common failure mode.** `[ANALYST ADD]` SMA has a sexless-looking female that *should* contain a receptacle contact; some cheap adapters are supplied without one, or the pin is pushed back. The result is an open circuit that looks like a connected cable. **It cost a full diagnostic cycle because nothing about the assembly looks wrong.**

### 4.4 Pointing: encoders, PID, deadband, backlash

**4.4.1 — The encoder arrangement.** `[SOURCE CLAIM]` AS5600 magnetic encoders, mounted **offset with a gear reduction** for two reasons: more resolution, and no good way to mount them on-axis.

**Assessment: correct on both counts, and the second reason is the honest one.** `[ANALYST ADD]` The resolution arithmetic:

```
AS5600 = 12 bit = 4096 counts/rev = 0.0879°/count
Direct on axis:            0.088°
Through a 5:1 reduction:   0.0176°
```

**4.4.2 — The measurement out-resolved the mechanism, which is the useful finding.** `[SOURCE CLAIM]` A 0.1° deadband was achievable, and the residual error is 0.3° of backlash.

**Assessment: this is the correct conclusion and it is worth making explicit.** `[ANALYST ADD]` The encoder is accurate to ~0.02°; the gearbox has 0.3° of play. **So the limiting error is mechanical by a factor of fifteen.** Improving the encoder would do nothing; only a different drive would help. **The source reaches this conclusion correctly and then does not act on it.**

**4.4.3 — The internal inconsistency.** `[SOURCE CLAIM]` "Since the encoders are directly on the axis, we can actually measure the gearbox slop."

**Assessment: this contradicts ¶4.4.1.** `[ANALYST ADD]` The encoders were geared down, not direct. The measurement is still valid — a geared encoder reports axis position with more resolution — but the stated justification is wrong, and a reader trying to reproduce the measurement would be confused about what "directly on the axis" means.

**4.4.4 — Backlash and the beamwidth.** `[ANALYST ADD]` The 0.3° backlash should be assessed against the 5.1° beamwidth (¶4.1.3):

```
0.3° / 5.1° ≈ 6% of beamwidth
```

**A 6% pointing error costs well under 0.1 dB** — a Gaussian beam at 6% of its half-power radius loses approximately `10·log₁₀(exp(−2.77·(0.06)²))` ≈ 0.004 dB. **The backlash is therefore irrelevant for pointing and matters only for repeatability.** That is a genuinely useful conclusion the video does not draw: **the defect he spent a day eliminating was never affecting his signal.**

### 4.5 The mechanics

**4.5.1 — Drive v1: plasma-cut gears.** `[SOURCE CLAIM]` "The plasma cutter is only so accurate, and we can get gears that mesh pretty good on it. But we had some issues — another of which was the warpage from welding all over it."

**Assessment: correct, and the physics is worth naming.** `[ANALYST ADD]` Two independent problems:
1. **Profile error** — a plasma-cut tooth is not an involute, so the contact is point-like rather than rolling, which produces wear and uneven torque;
2. **Distortion** — welding a gear concentrates heat asymmetrically, and the resulting shrinkage warps the part. **The measured consequence was that the gear "got stuck on the shaft."**

**The fix — a scrap flywheel and pinion — is the right one, because it substitutes a machined involute pair for a hand-cut approximation.** That is a case of solving a precision problem by *buying precision* rather than manufacturing it, which is the correct decision when the tolerance is beyond the available process.

**4.5.2 — The tensioning mechanism.** `[SOURCE CLAIM]` The motor "flexes out" under load; the author throws "a trashy tensioning mechanism" at it and "pretended that everything was okay," noting the subplot "is going to rear its ugly head again."

**Assessment: this is the most honest sentence in the video, and it is also the correct engineering judgment.** `[ANALYST ADD]` The flex is a **compliance problem**: the motor mount is not stiff enough to hold the pinion centre distance under tangential load. A tensioner converts a stiffness problem into a preload problem — which works, at the cost of adding a wearing part and a source of drift. **The author knows it is a patch, says so, and is right that it will recur.**

**4.5.3 — The limit switches, and the elegant part.** `[SOURCE CLAIM]` "To put limits on a linear actuator, we can wire it like this with a limit switch and a diode on each end. When it's powered, it will extend until it hits the limit switch, stopping the flow of power. When we reverse the polarity to retract it, the power can then flow through the diode."

**Assessment: correct, and this is a genuinely clever circuit.** `[ANALYST ADD]` The arrangement is a **diode-OR endstop**:

```
        ┌──── switch_A ────►|────┐
  + ────┤                          ├──── motor
        └──── switch_B ────◄|──────┘
```

The diode is oriented so that current can pass *around* the open switch in one polarity only. **Consequence: the switch cuts power in the direction that would drive further into the stop, while permitting motion away from it.** That is exactly the behaviour required, achieved with two components and no logic. **The author derived it from a diagram and implemented it correctly, which is the strongest single piece of electrical work in the build.**

**4.5.4 — The crash, and what it teaches.** `[SOURCE CLAIM]` The linear actuator was wired backwards; on first boot the wind-stow logic triggered before the encoder was read; the dish drove down and destroyed an encoder.

**Assessment: this is a textbook **fail-safe versus fail-operational** error.** `[ANALYST ADD]` The controller treated "no encoder signal" as "wind is high, stow now." **The safe response to a lost sensor is to stop, not to move.** The author's fix — hard stops plus calibration switches — is correct, but the *design* lesson is the one to record: **a stow routine that can be triggered by sensor loss is a routine that will eventually destroy the machine.** That is a general principle and the video does not state it.

**4.5.5 — The worm gear, and the misattribution.** `[SOURCE CLAIM]` "That is entirely gearbox slop. So to fix that, we're going to need a better gearbox."

**Assessment: the diagnosis is right and the framing is wrong.** `[ANALYST ADD]` A **worm drive was chosen for its holding torque** — it is self-locking, which is why the dish does not back-drive when the motor is unpowered. **But self-locking worm drives have backlash by construction**, because the thread clearance is what prevents binding. **The 0.3° is the price of the property that made the drive suitable.** A "better gearbox" means either a lower-backlash (and more expensive) worm, or a different topology with a brake. **The author treats a design trade-off as a defect**, and that is the one place where the video's engineering reasoning slips.

---

## 5. THE MISSING LINK BUDGET

**5.1 — Why this is the report's central addition.** `[ANALYST ADD]` The video never computes one. Everything is empirical: point, look, wiggle. **A single line of arithmetic would have told him, before he built anything, what signal to expect and therefore whether a given failure was a fault or a design limit.**

**5.2 — The budget, with computed terms marked.**

```
P_rx  =  EIRP_sat  −  FSPL  +  G_rx  −  L_cable  +  G_feed
```

**Computed terms** `[ANALYST ADD]`:

| Term | Value | Working |
|---|---|---|
| **FSPL** at 1694.1 MHz over 35,786 km | **−188.1 dB** | `20log₁₀(35786) + 20log₁₀(1694.1) + 32.45 = 91.07 + 64.58 + 32.45` |
| **G_rx** for 8 ft (2.438 m) at λ = 0.177 m, η = 0.55 | **+30.1 dBi** | `η(πD/λ)² = 0.55 × (43.3)² = 1031` |
| **θ_3dB** | **5.1°** | `70λ/D` |
| **kTB** in 1 MHz at 290 K | **−114 dBm** | `−174 + 60` |
| **Noise floor** with LNA NF ≈ 0.8 dB | **≈ −113.2 dBm** | |

**Unknown terms**, and the report does not invent them:

| Term | Status |
|---|---|
| `EIRP_sat` | Not published in the video; GOES HRIT broadcast power is not something this analysis could verify |
| `L_cable` | Length not stated; at 1.7 GHz, RG-class coax is ~0.3–0.5 dB/m, LMR-400 ~0.2 dB/m |
| `G_feed` | ~8–10 dBi for the helix, from its geometry |

**5.3 — Solving backwards for consistency.** `[ANALYST ADD]` The source reports **8.5–9 dB SNR** with **<1% BER** on GOES. Using the noise floor above:

```
P_rx  =  −113.2 dBm + 9 dB  =  −104.2 dBm
EIRP  =  P_rx + FSPL − G_rx  =  −104.2 + 188.1 − 30.1  =  +53.8 dBW
```

**An implied satellite EIRP of roughly 54 dBW.** That is a plausible figure for a dedicated wide-area broadcast downlink, and it is the right order of magnitude for a service designed to be received by modest ground stations across a hemisphere.

**5.3.1 — What this check establishes, and what it does not.** `[ANALYST ADD]` It establishes that **the reported SNR is internally consistent with an 8-ft dish and a 0.8 dB LNA at this range** — the numbers hang together. It does **not** establish the satellite's actual EIRP, which is back-solved from the observation rather than measured. **It is a consistency check, not a measurement**, and the report labels it as such.

**5.4 — The conclusion that changes the story.**

**5.4.1** `[ANALYST ADD]` Now remove the dish. A 0 dBi antenna at the same range receives:

```
P_rx  =  −104.2 − 30.1  =  −134.3 dBm
```

against a **noise floor of −113.2 dBm**. That is **21 dB below the noise** — not weak, but **undetectable**, in any bandwidth wide enough to carry the data.

**5.4.2 — The system is the dish.** Every other component refines a link that the reflector alone makes possible:

| Component | Contribution | Share of the working margin |
|---|---|---|
| **8-ft reflector** | **+30.1 dB** | **~100%** |
| LNA (NF 0.8 vs. 10 dB) | ~+9 dB of SNR | A refinement |
| Helix feed | +8–10 dBi | Small |
| Short low-loss cable | ~1–2 dB | Housekeeping |

**5.4.3 — Why this matters practically.** `[ANALYST ADD]` It predicts the *failure modes*: if the link is marginal, the fixes that work are **more aperture, a lower-noise LNA, or a shorter cable** — in that order. The fixes that do not work are a better decoder, a faster SDR, or a more accurate mount. **The author spent his hardest day on pointing accuracy (0.3°, worth 0.004 dB) and his easiest on the dish (worth 30 dB).** The budget says which of those was worth the effort, and it is not the one that consumed the video.

---

## 6. THE MISTAKES, AS EVIDENCE

**6.1 — Why this section exists.** `[ANALYST ADD]` A build log's value is its fault record. Six independent faults were found and fixed; each one is a *specific* failure mode with a diagnostic signature. **That is more useful than a success story, and it is why the source is worth grading carefully despite its technical looseness.**

| # | Fault | Diagnostic signature | Root cause | Class |
|---|---|---|---|---|
| **F-1** | Plasma-cut gear warped, seized on shaft | Mechanical binding after welding | Weld distortion + non-involute profile | Manufacturing |
| **F-2** | Motor flexes under load | Visible deflection | Insufficient mount stiffness | Structural |
| **F-3** | Dish crashed, encoder destroyed | Uncommanded motion on boot | **Lost sensor → stow routine triggered** | **Control logic** |
| **F-4** | Pointed at a decommissioned satellite | No signal; 1 dB = noise | **Stale operational knowledge** | **Procedural** |
| **F-5** | Female SMA with no pin | Open circuit that looks connected | Cheap adapter | Connector |
| **F-6** | Comb of spectral spikes | Narrowband spikes across the band | **Double-powered LNA; USB supply noise** | **Power/grounding** |
| **F-7** | Weak, distorted signal at correct pointing | Low SNR after all else fixed | **Feed not at focus** | **Optical** |

**6.2 — The distribution is the finding.** `[ANALYST ADD]` Of seven faults, **two are in the RF/optical chain** (F-6, F-7), **two in control logic and procedure** (F-3, F-4), and **three in fabrication** (F-1, F-2, F-5). **The fabrication faults were the slowest to find and the least consequential; the RF faults were the fastest to find once the right instrument was pointed at them.**

**6.3 — F-4 deserves special attention because it is not a technical fault at all.** `[ANALYST ADD]` The satellite had been replaced a year earlier. **The information existed, was freely available, and was not checked.** This is the archive's most common failure across every area — a claim repeated from memory rather than verified against the current source — and here it cost a full diagnostic cycle in a domain where the author was already out of his depth.

**6.4 — And F-3 is the one with a general lesson.** `[ANALYST ADD]` The stow routine was designed to protect the dish from wind and instead destroyed a component, because the trigger condition ("no encoder data") was satisfied by a wiring error rather than by wind. **The general rule: a protective action must be gated on positive evidence of the hazard, not on absence of evidence of safety.** That is a principle the source does not state and would recognise immediately.

---

## 7. SAFETY AND COMPLIANCE

**7.1 — Why this section is present.** `[ANALYST ADD]` This is the archive's first source with meaningful physical hazards, and the `signals/` area carries a standing note about them. The author is careful about most things and silent about one important one.

### 7.2 Lightning

**7.2.1 — The gap.** `[SOURCE CLAIM]` During the storm: "It's lightning and that thing's begging to get struck."

**Assessment: correct observation, no mitigation described.** `[ANALYST ADD]` A 2.4 m metal reflector on an outdoor pad, connected by Ethernet and mains power to a building, is a **lightning attractor with a direct conductive path indoors**. The relevant measures are standard and absent from the build:

| Measure | Purpose |
|---|---|
| **Bond the dish and mount to a grounding electrode** | Equalise potential; prevent the dish floating above earth |
| **Ground the coax shield at the entry point** (bulkhead arrestor) | Divert surge before it reaches the LNA and the Pi |
| **Ground the Ethernet at entry** (PoE arrestor or fibre) | Prevent surge on the data path |
| **Single-point bonding** to the building's electrode system | Avoid ground loops, which are also an RF-noise source |

**7.2.2 — Why it is not merely a safety point.** `[ANALYST ADD]` **Grounding is also an RF measure.** A floating shield and a USB-powered LNA on a long cable is precisely the configuration that produced fault F-6. **The same fix that protects the equipment from lightning also removes the ground loop that put spikes in the spectrum.** The author found the noise empirically; he did not connect it to the missing bond.

### 7.3 Structural and mechanical

**7.3.1** `[ANALYST ADD]` The pad was increased from 8 inches to **3 feet** — correct instinct, and the right call. Relevant loads:

| Load | Note |
|---|---|
| **Wind** | Dominant. At 30 mph on a 4.6 m² aperture, roughly 300 N; at storm speeds, several times that. The stow position is the correct mitigation |
| **Overturning moment** | A 3-ft pad resists it; the base plate and rebar tie the mount to the mass |
| **Ice** | Not addressed; adds mass and changes the aerodynamic profile |

**7.3.2 — The stow logic is correct.** `[SOURCE CLAIM]` Azimuth 90° from the wind, elevation 90°.

**Assessment: correct.** `[ANALYST ADD]` At elevation 90° the aperture faces the zenith, presenting **the minimum projected area to horizontal wind** — the dish's edge, not its face. Azimuthing broadside is the standard furling position for the same reason. **The 90° azimuth offset means the dish turns edge-on rather than face-on, which halves the load.**

### 7.4 RF exposure and licensing

**7.4.1** `[ANALYST ADD]` This build is **receive-only**, so RF exposure is not a concern and no licence is required in most jurisdictions to *receive*. The relevant note for the area:

| Activity | Status |
|---|---|
| Passive reception | Generally unrestricted |
| Reception of unencrypted weather broadcasts | Unrestricted |
| **Transmission** | **Licensed** — amateur (e.g. FCC Part 97), or experimental |
| **Decoding encrypted services** | Regulated; not applicable here |

**7.4.2 — The one forward-looking risk.** `[ANALYST ADD]` The author wants to try **radio astronomy** and swappable antennas. Radio astronomy is passive and unlicensed, but **any future transmit capability changes the compliance picture entirely** — EIRP limits, coordination, and interference obligations all apply. **A build that is compliant as a receiver is not automatically compliant once a transmitter is attached**, and the video's forward plans do not mention it.

### 7.5 Fabrication hazards

**7.5.1** `[ANALYST ADD]` Present throughout and handled reasonably: welding fume and UV, plasma cutting, grinding, work at height on the shop roof to mount the anemometer, and the physical handling of a dish large enough to injure. **No specific failures are shown**, and the report records the categories rather than dwelling on them.

---

## 8. CROSS-ARCHIVE LINKS

### 8.1 The dB chain is the same instrument as the fiber attenuation budget

**8.1.1** `[ANALYST ADD]` `IR-20261026-FIBER-OPTICS` established the master distinction of `eng/`: **is this limit intrinsic or extrinsic?** This report supplies the complementary instrument for `signals/`: **does the budget close?**

| Report | Instrument | Question it answers |
|---|---|---|
| `FIBER-OPTICS` | Attenuation decomposition (dB/km per mechanism) | Which loss terms can be engineered away? |
| **This report** | **Link budget (dB summed across the system)** | **Will this work before I build it?** |

**Both are additions in decibels, and both convert a qualitative question into a single number.** That is why they belong to adjacent areas rather than one: the fiber budget is a *post-hoc* decomposition of a measured loss; the link budget is an *a priori* prediction of a designed link.

### 8.2 The archive's control-loop pattern, at the level of a single machine

**8.2.1** `[ANALYST ADD]` The vault's cross-cutting finding is the **severed corrective term**. This build contains a compact, literal instance of it:

```
     encoder ──► comparator ──► PID ──► motor ──► dish
        ▲                                          │
        └────────────── feedback ──────────────────┘
```

**Every element of that loop was severed at least once in the video:**

| Severed element | Instance | Consequence |
|---|---|---|
| **Sensor** | Encoder destroyed in the crash | Uncontrolled motion |
| **Error signal** | Encoder not read at boot | Stow routine fired on missing data |
| **Actuator authority** | Limit switches absent | Crash |
| **Reference** | Wrong satellite (decommissioned) | Pointing at nothing |
| **Feedback path** | Encoder housing leaked in rain → erratic in wet weather | Drift |

**8.2.2 — The refinement this supplies.** `[ANALYST ADD]` In the vault's earlier reports, a severed term produces *unbounded* behaviour (endless scrolling, endless discourse). Here the consequence is **bounded and violent** — the machine crashes into its hard stop. **The difference is that a physical system has a mechanical limit.** That is worth noting: **the unbounded pathologies in this archive are all informational, and the bounded ones are all physical.** The archive has not previously had a case where the failure mode was a machine destroying itself.

### 8.3 The archive's meta-finding, benign instance

**8.3.1** `[ANALYST ADD]` The vault records that sources derive a general conclusion from a single case and present it as a consequence. **This source does the opposite** — it presents no general conclusion at all, shows the failures, and lets the viewer draw their own. **That is rarer than the other failure mode and worth naming as the good case.**

---

## 9. INDICATORS AND WARNINGS

### 9.1 Assessing an RF build log

| ID | Indicator | Test |
|---|---|---|
| **S-1** | Is there a link budget? | **Failed here.** Without one, every failure is ambiguous |
| **S-2** | Is the LNA at the antenna, not at the receiver? | **Passed** — placed correctly |
| **S-3** | Is the polarization sense correct for the geometry? | **Passed** — RHCP → LHCP after reflection, and stated explicitly |
| **S-4** | Is the feed at the focal point, and was it verified? | **Passed empirically**, by moving it and observing |
| **S-5** | Are noise figure and gain quoted? | **Failed** — all empirical |
| **S-6** | Is there a raster or peak-search routine? | **Passed** — 10° raster, iteratively narrowed |
| **S-7** | Is the protective logic gated on positive evidence? | **Failed** — F-3 |
| **S-8** | Are there hard stops independent of software? | **Passed after the crash** |
| **S-9** | Is the antenna bonded to earth? | **Failed** — no grounding described (§7.2) |
| **S-10** | Are TLEs fresh, and is the target still operational? | **Failed** — F-4 |
| **S-11** | Is BER or SNR reported with bandwidth? | **Partial** — SNR given, bandwidth not |
| **S-12** | Is the mechanical backlash assessed against beamwidth? | **Failed** — 0.3° treated as significant; it is 6% of beamwidth |

### 9.2 The meta-indicator

**9.2.1** The archive's standing test — *does the source state what would change its mind?* — adapts here to: **does the source know what number it is trying to achieve?** The author knows he wants a "beautiful M-shaped peak centred on 1694.1 MHz" and a BER near 0.0001. **He has the right acceptance criteria and no model of the expected value**, which is why every intermediate result is ambiguous to him and clear to the viewer only in retrospect.

---

## 10. INTELLIGENCE GAPS AND KEY JUDGMENTS

### 10.1 Gaps

**10.1.1 — GOES HRIT link parameters (priority: high).** §5 back-solves an EIRP of ~54 dBW. **Requirement:** the published GOES-R HRIT/GRB downlink budget — EIRP, modulation, occupied bandwidth, FEC — to replace the back-solve with a measurement.

**10.1.2 — The dish's f/D (priority: moderate).** ¶4.1.3 gives the formula and a typical range; the actual value for this surplus dish is unknown. **Requirement:** measure D and depth, compute f, compare with the feed position the author arrived at empirically.

**10.1.3 — Cable type and length (priority: moderate).** `L_cable` is unquantified in the report. **Requirement:** the actual coax and run length, to close the budget properly.

**10.1.4 — AS5600 specification (priority: low).** The 12-bit figure is standard. **Requirement:** confirm resolution and update rate, since the update rate bounds the achievable PID bandwidth.

**10.1.5 — Lightning protection standards (priority: moderate).** §7.2 lists the standard measures without citation. **Requirement:** the applicable code (e.g. NFPA 780 / IEC 62305) and the amateur-radio practice guidance, so the section is actionable rather than advisory.

**10.1.6 — The wind-stow threshold (priority: low).** The 30 mph trigger is stated but not justified. **Requirement:** the dish manufacturer's survival wind rating, if recoverable, and the structural calculation for the mount.

### 10.2 Key judgments

| ID | Judgment | Confidence |
|---|---|---|
| **KJ-1** | The source's value is its fault record: seven independent failures, each diagnosed from a signature. That is a better dataset than a success story. | **High** |
| **KJ-2** | The missing link budget is the principal omission. Computed, it shows the **8-ft dish contributes ~30 dB — essentially the entire working margin.** | **High** |
| **KJ-3** | Without the dish the link is ~21 dB below the noise floor: undetectable regardless of electronics. | **High** |
| **KJ-4** | The reported 8.5–9 dB SNR is internally consistent with a 0.8 dB LNA at this range; the implied satellite EIRP is ~54 dBW, which is plausible. | **Moderate-high** (consistency check, not measurement) |
| **KJ-5** | The polarization inversion (RHCP → LHCP on reflection) is correct and is the most technically sophisticated element in the build. Getting it wrong is a hard fail, not a 3 dB penalty. | **High** |
| **KJ-6** | The 0.3° backlash is 6% of the 5.1° beamwidth and costs ≈0.004 dB. **The defect he spent a day eliminating never affected his signal.** | **High** |
| **KJ-7** | The worm gear's backlash is a *property* of the choice that gave him self-locking holding torque, not a defect. He misdiagnoses a trade-off as a fault. | **Moderate-high** |
| **KJ-8** | The crash was a **fail-safe inversion**: the stow routine triggered on sensor *loss* rather than on positive evidence of wind. General rule: gate protective actions on evidence of hazard. | **High** |
| **KJ-9** | The double-powered LNA (bias tee + USB) produced ground-loop noise that was correctly diagnosed from its spectral signature. | **High** |
| **KJ-10** | No grounding is described for a large outdoor metal reflector with conductive paths indoors. This is the most consequential omission and it is also an RF measure, not only a safety one. | **High** |
| **KJ-11** | The encoder description is internally inconsistent ("geared for resolution" vs. "directly on the axis"). The measurement remains valid; the reasoning does not. | **High** |
| **KJ-12** | This belongs in `signals/` rather than `eng/` because the verification method is **predictive** (sum the decibels before building) rather than **post-hoc** (recompute the number after). | **High** |

---

## APPENDIX A — GLOSSARY

| Term | Definition |
|---|---|
| **AS5600** | 12-bit magnetic angular encoder; 4096 counts per revolution. |
| **Backlash** | Lost motion on reversal, from clearance between meshing parts. |
| **Bias tee** | Circuit that injects DC onto a coax centre conductor to power a mast-mounted amplifier. |
| **Circular polarization (RHCP/LHCP)** | A wave whose E-field rotates; handedness is defined along the propagation direction and **reverses on reflection**. |
| **dBW / dBm** | Power relative to 1 W / 1 mW. |
| **Diode-OR endstop** | Limit circuit in which a diode permits motion away from a stop while the switch cuts motion into it. |
| **EIRP** | Effective isotropic radiated power; transmit power plus antenna gain. |
| **FSPL** | Free-space path loss; `20log d + 20log f + 32.45` (km, MHz). |
| **f/D** | Focal ratio of a paraboloid; `f = D²/(16c)`. |
| **HRIT / GRB** | GOES high-rate information transmission / GOES rebroadcast; L-band downlinks. |
| **Link budget** | The sum of gains and losses in decibels from transmitter to receiver, predicting SNR. |
| **PID** | Proportional–integral–derivative control; here with a deadband to prevent limit cycling. |
| **SMA** | Small coaxial connector; the female normally contains a receptacle contact. |
| **TLE** | Two-line element set; orbital parameters for SGP4 propagation. |
| **TVRO** | Television receive-only; the class of surplus C-band dish used here. |

---

## APPENDIX B — CHRONOLOGY

| Year | Event | Relevance |
|---|---|---|
| 1980s–90s | C-band TVRO dishes mass-produced | The surplus hardware |
| 1946 | First lunar radar echo | The link-budget method's origin |
| 1957 | Sputnik | First amateur-receivable downlink |
| 1970s | GOES series begins | The target service |
| 1996 | Rovelli — *(not relevant; cross-ref only)* | — |
| 2009 | Skyfield lineage; SGP4 standardisation | Tracking |
| 2016 | **GOES-16** launched | The satellite the author initially targeted |
| 2020s | SatDump matures | The decode pipeline |
| 2024 | GOES-19 launched | — |
| **2025** | **GOES-19 replaces GOES-16** | **Fault F-4** |
| 2020s | RTL-SDR and BladeRF widely available | The SDR stack |
| 2024–25 | Arctic Weather Satellite | The LEO target that yielded little |

---

## APPENDIX C — CLAIM LEDGER

| # | Claim | Class | Status | Assessment |
|---|---|---|---|---|
| C-1 | L-band is 1–2 GHz | Definition | Verified | — |
| C-2 | Linear actuator draws 7 A | Measurement | Plausible | — |
| C-3 | Wheelchair motor is 24 V with a worm gear | Fact | Verified | Source of the backlash (¶4.5.5) |
| C-4 | Shaft concentric to ~20 thou | Measurement | Plausible | 0.5 mm |
| C-5 | Plasma-cut gears mesh acceptably | Claim | True with limits | Warpage was the real problem |
| C-6 | Gearing an encoder increases resolution | Engineering | **Correct** | 0.088° → 0.018° |
| C-7 | Encoders are "directly on the axis" | Claim | **Inconsistent** | Contradicts C-6 |
| C-8 | PID with deadband prevents oscillation | Control | Verified | — |
| C-9 | 0.3° backlash, "entirely gearbox" | Measurement | **Correct value, wrong framing** | It is a worm-drive trade-off |
| C-10 | Stow: az 90° from wind, el 90° | Engineering | **Correct** | Minimum projected area |
| C-11 | Diode + switch per actuator end | Circuit | **Verified and elegant** | ¶4.5.3 |
| C-12 | GOES at 1694.1 MHz, RHCP | Fact | Verified | HRIT |
| C-13 | **Reflection reverses polarization → LHCP feed** | Physics | **Verified and correct** | Hard fail if wrong |
| C-14 | Helix circumference ≈ λ | Antenna | Verified | Axial mode |
| C-15 | LNA tuned to band, low noise | Engineering | Verified | — |
| C-16 | GOES-16 replaced by GOES-19 in 2025 | Fact | Consistent with record | F-4 |
| C-17 | 1 dB received is background noise | Interpretation | **Correct** | — |
| C-18 | Female SMA missing its pin | Observation | Verified | Real failure mode |
| C-19 | Double powering caused the spike comb | Diagnosis | **Correct** | Ground loop + supply noise |
| C-20 | Feed was off focus; extending it fixed it | Diagnosis | **Correct** | The actual last fault |
| C-21 | 8.5–9 dB SNR; <1% BER | Measurement | Plausible | Consistent with §5 |
| C-22 | 10×10° raster, iteratively narrowed | Method | Correct | 2× beamwidth |
| C-23 | Meteor-M needs more bandwidth | Fact | Verified in outline | — |
| C-24 | AWS has only a microwave radiometer | Fact | Verified | — |
| C-25 | **Dish provides ~30 dB of the margin** | Computed | **Not in source** | The report's main addition |
| C-26 | **Without the dish: ~21 dB below noise** | Computed | **Not in source** | ¶5.4.1 |
| C-27 | **0.3° backlash ≈ 0.004 dB** | Computed | **Not in source** | ¶4.4.4 |
| C-28 | **No grounding described** | Safety | **Omission** | §7.2 |

---

## APPENDIX D — VERBATIM EXTRACTS

**D-1** [0:21] "When I saw an 8-ft dish on Facebook Marketplace, of course, I got it. Oh god, I got a comedy size satellite dish."

**D-2** [1:01] "I truly know basically nothing about this hobby. I find that the easiest way for me to learn stuff is to just jump all the way in."

**D-3** [1:13] "I know I know how to weld stuff. I know how to make motor go burr. And I know how to put posting ground."

**D-4** [8:26] "The motor flexes out. I'm not really sure what to do about it. I mean, it runs fine. It just gets pushed out, which obviously probably isn't great over time."

**D-5** [8:40] "This was actually a pretty big ongoing problem, but I just went ahead and threw a trashy tensioning mechanism on it and pretended that everything was okay."

**D-6** [13:39] "Just by the nature of plasma cutting, the plasma cutter is only so accurate... another of which was the warpage from welding all over it."

**D-7** [17:37] "Reason one, we get more resolution by gearing it down like this. And reason two, there's no great way to mount them directly centered on each of the shafts."

**D-8** [22:02] "With any PID loop, you want to set a deadband so that it doesn't just wildly oscillate trying to hit the values you want. Well, I set the deadband to 0.1 and it's working."

**D-9** [22:28] "Since the encoders are directly on the axis, we can actually measure the gearbox slop... So we got about 0.3ish degrees of slop. And that is entirely gearbox slop."

**D-10** [26:42] "Once the wind gets past a certain threshold, the azimuth will turn 90° from the wind and the elevation will go up to 90°. So we have the least amount of surface area facing the wind."

**D-11** [27:13] "It didn't detect a signal right away, so it went to go stow for wind safety. And yeah, it kind of came down here and crashed and broke our little freaking encoder here."

**D-12** [27:31] "To put limits on a linear actuator, we can wire it like this with a limit switch and a diode on each end... When we reverse the polarity to retract it, the power can then flow through the diode."

**D-13** [32:25] "The signal emitted from GOES is approximately 1.694 GHz with a right hand circular polarization. Now the polarization is actually reversed after bouncing off of the dish. So we need a left hand polarized helical antenna with a circumference that roughly matches the wavelength."

**D-14** [35:48] "I don't want to stand under there. It's lightning and that thing's begging to get struck."

**D-15** [37:17] "As it turns out, GOES-16 was replaced by GOES-19 in 2025 and is no longer transmitting data. So, this was all in vain."

**D-16** [37:36] "The 1 dB that we are receiving is essentially background noise."

**D-17** [38:01] "Here we have a normal male connector. No pin in the middle. That's expected. And here we have a female connector with no freaking pin in the middle. It's always something dumb, right?"

**D-18** [38:20] "I was powering it through USB and using bias tee. Bias tee is just a setting that allows you to power it through the SMA cable. You only need one of those."

**D-19** [38:50] "Before, the focal point was around a lot closer to the ground plane. Now the focal point is a lot more centered on the helix. And I think that might have been our last problem."

**D-20** [40:27] "The signal is currently around 8.5 to 9 dB with an error rate of less than 1%."

---

## APPENDIX E — TERMINOLOGY RECONCILIATION

| Source usage | Correct / preferred | Note |
|---|---|---|
| "Lband" | **L-band** | 1–2 GHz |
| "pit loop" | **PID loop** | Restore before analysis |
| "deadband to 01" | **0.1°** | — |
| "spurgeear" | **spur gear** | — |
| "cat" | **CAD** | — |
| "encoders are directly on the axis" | **encoders are geared to the axis** | Contradicts ¶17:37 |
| "entirely gearbox slop" | **worm-drive backlash** | A trade-off, not a defect |
| "a better gearbox" | **lower-backlash drive, or a brake** | The self-locking property is why it was chosen |
| "goes" | **GOES** | Geostationary Operational Environmental Satellite |
| "MedOpsc" / "Medtop" | **Meteor-M** | — |
| "bias T" | **bias tee** | — |
| "the focal point" | **the feed's phase centre at the reflector's focus** | Distinction matters (¶4.1.2) |
| "mea" / "messalike" | **M-shaped** | Spectral peak shape |

---

## APPENDIX F — ESTIMATIVE LEXICON

**Confidence:** High (verified against a primary source or standard reference) · Moderate (credible single stream, or sound reasoning with an inferential gap) · Low (fragmented or contested).

**Likelihood:** Almost no chance 01–05% · Very unlikely 05–20% · Unlikely 20–40% · Roughly even 40–60% · Likely 55–85% · Very likely 80–95% · Almost certain 95–99%.

**Technical status:** *Verified* · *Plausible* (consistent, not independently confirmed) · *Computed* (derived in this report) · *Back-solved* (inferred from an observation; a consistency check, not a measurement) · *Omitted* (absent and consequential) · *Error*.

---

## APPENDIX G — REVISION LOG

| Rev | Date | Change |
|---|---|---|
| 1.0 | 2026-10-26 | Initial issue. Source: `transcript.md` (ASR, 46:42). New topic area `signals/` established. Link budget constructed (§5) with computed FSPL, dish gain, and beamwidth; satellite EIRP back-solved and labelled as a consistency check. |

**Known deficiencies:**

1. GOES HRIT link parameters unverified; §5 rests on a back-solve (§10.1.1).
2. Dish f/D unknown; the focus discussion is qualitative (§10.1.2).
3. Cable type and length unquantified (§10.1.3).
4. Lightning-protection measures listed without citation (§10.1.5).
5. Wind-stow threshold not justified structurally (§10.1.6).

---

```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

*End of report.*
