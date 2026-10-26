# signals — video source archive

Notes vault for RF, antennas, software-defined radio, satellite links, radar, and positioning: how
signals are generated, radiated, propagated, and recovered.

Seventh topic area. Same layout and conventions as the other six.

## Why a separate area — and why `signals/` rather than `comms/` or `eng/`

**Not `eng/`.** The first video in this area is 80% fabrication — welding, machining, concrete — and it
would fit `eng/` on subject matter. It is separated on **method**, which is the archive's actual
principle:

> In `eng/` a claim is checked by **recomputing a number after the fact**.
> In `signals/` the whole system is **summed as a decibel chain before anything is built.**

A link budget is a **prediction**, not a post-mortem. That is a different kind of verification, and it
is falsifiable in the cheapest possible way: you can know a design will fail without cutting metal.

**Not `comms/`.** Communications is the largest use but not the category — radar, radio astronomy,
passive sensing, and GPS are all `signals/` and none is communications. The unifying object is the
**signal chain**, not the message.

## Conventions specific to this area

- **Write the link budget.** If a source doesn't, the report does. Mark computed terms as computed,
  unknowns as unknown, and anything inferred from an observation as **back-solved** — a consistency
  check, not a measurement.
- **Check the polarization sense against the geometry.** Circular polarization reverses on reflection.
  A wrong-sense feed is a hard fail (~20 dB cross-polar discrimination), not a 3 dB penalty.
- **Put gains and losses in order along the chain, and check the topology.** The LNA goes at the
  antenna, before cable loss. Any other placement is a design error regardless of the parts.
- **Compare mechanical tolerances to beamwidth.** A 0.3° backlash against a 5° beam is 6% of
  beamwidth and worth ~0.004 dB — irrelevant. Tolerances only mean something relative to the beam.
- **Separate the sensor from the mechanism.** If the encoder out-resolves the gearbox by 15×, no
  amount of electronics work will improve pointing.
- **Safety and compliance are in scope here** (see below). This is the first area with real physical
  hazards.

## Safety and compliance note

This area's sources involve outdoor structures, high voltage, RF, and — potentially — transmission.
Every report carries a safety and compliance section. Standing points:

- **Grounding is both a safety measure and an RF measure.** A floating shield and a USB-powered mast
  amplifier on a long cable is exactly the configuration that produces ground-loop noise. The fix for
  lightning and the fix for interference are often the same fix.
- **Receive-only is generally unlicensed; transmission is not.** Any build that adds a transmitter
  changes the compliance picture entirely — EIRP limits, coordination, interference obligations.
- **A protective action must be gated on positive evidence of the hazard, not on absence of evidence
  of safety.** The most instructive failure in the first report: a wind-stow routine triggered on
  *missing encoder data* and drove the dish into its stop, destroying the encoder.

## Index

| Date | Video | Channel | Report | Status |
|---|---|---|---|---|
| 2026-10-25 | [I Built a MASSIVE Satellite Ground Station in My Backyard](https://www.youtube.com/watch?v=jto2xUEAp0Q) | `@cranktowncity` | [`IR-20261026-SATELLITE-GROUND-STATION`](videos/2026-10-25-satellite-ground-station/IR-20261026-SATELLITE-GROUND-STATION.md) | Complete, rev 1.0 |
| 2026-10-25 | [Low-tech, Unbreakable Encryption — One Time Pads](https://www.youtube.com/watch?v=fppz2qalHKE) | `@CivilDefenseEngineer` | [`IR-20261026-ONE-TIME-PADS`](videos/2026-10-25-one-time-pads/IR-20261026-ONE-TIME-PADS.md) | Complete, rev 1.0 |
| 2026-10-25 | [HF Radio: The OP Weapon of Modern Minutemen](https://www.youtube.com/watch?v=hePS5MwMcLk) | `@CivilDefenseEngineer` | [`IR-20261026-HF-RADIO`](videos/2026-10-25-hf-radio/IR-20261026-HF-RADIO.md) | Complete, rev 1.0 |
| 2026-10-25 | [How To Get Started With Satellites, Radios, And SDR](https://www.youtube.com/watch?v=hLpP5KEsHbc) | `@saveitforparts` | [`IR-20261026-GETTING-STARTED-SDR`](videos/2026-10-25-getting-started-sdr/IR-20261026-GETTING-STARTED-SDR.md) | Complete, rev 1.0 |

## The citation chain — the archive's first traced idea

This is the only case in the vault where an idea can be followed from one source to another:

| Step | Source | Content |
|---|---|---|
| **Origin** | `GETTING-STARTED-SDR` | "Six or seven foot satellite dish… you can often find those for free… they haven't used it since the 1980s and they want it gone" |
| **Transmission** | `SATELLITE-GROUND-STATION` | *"I've been watching a lot of Save It for Parts… when I saw an 8-ft dish on Facebook Marketplace, of course, I got it"* |
| **Realisation** | Same | Dish mounted, driven, receiving GOES |

**The derivative took the attitude and discarded the sequence** — it skipped straight to an 8-ft dish,
a Pi, and a rotator instead of starting with a $30 antenna at 137 MHz. That is exactly what the origin
predicts a competent learner *should* do, and it also cost a day pointing at a decommissioned satellite.

**The transferable rule:** method transfers, specifics do not. A beginner guide is a source of
*disposition*, not of sequence — and the person who follows its ordering literally will be slower than
the one who extracts the disposition and re-derives the path.

## The pedagogical principle worth keeping

The source's central claim, formalised:

```
learning ∝ exploration ∝ tolerated failure ∝ 1 / (cost of failure − risk threshold)
```

**Cheap equipment is not a budget compromise — it is the pedagogically optimal instrument**, because it
holds the cost of failure below the threshold at which exploration stops. A $2,000 radio in a
beginner's hands teaches less than a $30 one, because the beginner will not open it.

**The boundary is physical safety.** The principle is sound and its domain ends at mains voltage —
which is exactly where the source's salvage advice leads without saying so (see §7.2 of the report).

## The two regimes — the area's third instrument

A link is limited either by **thermal noise** or by **external noise**, and which one governs determines
what you should spend money on. The archive now holds one report of each:

| | `SATELLITE-GROUND-STATION` | `HF-RADIO` |
|---|---|---|
| Frequency | 1.7 GHz | 7 MHz |
| Path loss | 188 dB | 106 dB |
| Dominant noise | Thermal | **Atmospheric, 40–50 dB above thermal** |
| Antenna's share of margin | **~100%** | Minor |
| Effective remedy | Aperture | **Bandwidth, then power** |

**The two effects nearly cancel** — 82 dB less path loss, 40–50 dB more noise — which is why a 10 W
wire antenna and an 8-ft dish reach comparable distances in different bands. Get the regime wrong and
you buy the wrong thing: a better receiver does nothing at HF, and a narrower filter does nothing for a
geostationary link.

**Corollary — the 17 dB that "weak signal" means.** JS8Call is ~50 Hz against SSB's ~2,500 Hz:

```
10 · log₁₀(2500 / 50) = 17.0 dB
```

Seventeen decibels from arithmetic, equal to raising 10 W to ~500 W. **"Weak signal mode" is a
bandwidth claim, not a sensitivity claim**, and any source that says the phrase without the number has
not explained it.

## The property matrix — what does this actually protect?

The link budget answers *will this work?* For anything involving a message rather than a waveform, the
first question is *what does this protect?* COMSEC is **five separable properties**, and a technique
usually provides one:

| Property | Question | Typical mechanism |
|---|---|---|
| **Confidentiality** | Can it be read? | Encryption |
| **Integrity** | Can it be modified undetected? | MAC / signature |
| **Authentication** | Who sent it? | Shared secret, signature |
| **Traffic-flow confidentiality** | What do timing and volume reveal? | Padding, schedule discipline |
| **Forward secrecy** | What does key capture open? | Ratcheting; per-message key |

**An OTP scores 1 of 5.** It is perfect at the first and silent on the rest — not a defect of the
primitive, but fatal to a *system* that assumes the others follow. See `IR-20261026-ONE-TIME-PADS` §3.1.

Two things this matrix catches that nothing else does:

- **A monotonic counter in the clear is a side channel.** The OTP video sends the pad line number
  unencrypted; the line number is a running total of traffic volume. Traffic-flow confidentiality
  defeated by the message format, not the cipher.
- **A key that never changes has no forward secrecy.** Capture of a pad opens every message it will
  ever carry. The property that makes the OTP unbreakable — one key, one use, no evolution — is the
  property that makes capture total.

And the same matrix applies to the HF report: JS8Call is unencrypted and relayed through third parties,
so it scores **zero** — the source says so himself, correctly ("obscurity, don't count on it").

## Cross-area note: the same severed term

The vault's cross-cutting finding is **a feedback loop whose corrective term has been removed**. A
COMSEC system has one too, and it is the receiver's *accept?* decision:

```
message → encrypt → transmit → decrypt → accept?
                          ▲                  │
                          └──── reject ──────┘
```

With an OTP and no check value, **the receiver has no basis for that decision** — a garbled message, a
modified message, and a replayed message are all indistinguishable. The loop is open, and that is the
unbounded informational failure the vault keeps finding. The fix is about six digits of header.

**The HF report supplies the contrast.** The same author, on an adjacent subject, builds a link with
excellent feedback — waterfall, SNR readout, heartbeat network mapping who hears whom. **The
difference is not competence; it is observability.** A radio link is physical and visible; a ciphertext
is not. See `IR-20261026-HF-RADIO` §8.4.

## The number that reorders the story

The first report never computes a link budget. Computed:

| Term | Value |
|---|---|
| FSPL at 1694 MHz over 35,786 km | **−188.1 dB** |
| 8-ft dish gain at 1694 MHz | **+30.1 dBi** |
| Beamwidth | **5.1°** |
| Noise floor, 1 MHz, NF 0.8 dB | **−113.2 dBm** |

**The dish is ~100% of the working margin.** Without it the link sits 21 dB *below* the noise floor —
undetectable no matter what electronics are attached. The author spent his hardest day on pointing
accuracy (0.3°, worth 0.004 dB) and his easiest on the dish (worth 30 dB). **The budget says which of
those was worth the effort, and it is not the one that consumed the video.**

And the same kind of arithmetic governs the OTP video, where nobody does it either: **two digits of key
per character, so a 50-row sheet carries ~125 characters — one sentence.** A page of text costs a whole
pad. That is why codebooks exist, and it is the number the video should have given.

## The geometry table worth memorising

At 7.078 MHz (λ = 42.4 m), from the 468/f formula and the λ/10 criterion:

| Criterion | Metric | Imperial |
|---|---|---|
| NVIS maximum (λ/10) | **4.24 m** | **13.9 ft** |
| Skywave minimum (λ/2) | 21.2 m | 69.5 ft |
| Half-wave dipole (468/f) | 20.1 m | 66.1 ft |

**The NVIS and skywave heights differ by a factor of five**, which is why the same wire behaves
completely differently depending on where it hangs — and why an attic dipole is inside the NVIS window
by construction rather than by design.

## Open threads

- **GOES HRIT link parameters** — EIRP, modulation, occupied bandwidth, FEC. The first report
  back-solves ~54 dBW from the observed SNR and labels it a consistency check. A published budget
  would replace the inference.
- **Grounding** — no bond to earth is described anywhere in a build with a 2.4 m reflector, mains
  power, and Ethernet running indoors. Needs a citable standard before the recommendation is
  actionable.
- **Feed phase centre vs. focal point** — the author found the right feed position empirically. The
  dish's f/D is unmeasured, so the correction cannot be verified against theory.
- **The *Signals Handbook for Small Teams*** — the OTP video's primary reference, free online. Whether
  the protocol gaps (no check value, no counter, clear-text header) are inherited from it or invented
  by the presenter determines whether this is one author's omission or a field-wide one. **Highest
  priority in this area.**
- **VENONA** — named but not used. It is the best available case study of why the one-time rule is
  absolute, and the story the OTP video should have told instead of asserting the rule.
- **Radio astronomy** — the ground-station author's stated next step. Passive and unlicensed, but a
  different signal chain (total power, long integration, no demodulation).
