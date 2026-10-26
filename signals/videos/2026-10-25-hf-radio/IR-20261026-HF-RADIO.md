```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

# HF AS A BACKUP COMMS LAYER
## NVIS Geometry, the Bandwidth Trick, and the Two Inverted Claims

| Field | Value |
|---|---|
| **Report No.** | IR-20261026-HF-RADIO |
| **DTG** | 260724ZOCT26 |
| **Classification** | UNCLASSIFIED // OPEN SOURCE |
| **Originator** | Analyst (independent) |
| **Source** | `transcript.md` (same folder) — ASR transcript, 42:06 runtime, 6 chapters |
| **Source path** | `notes/signals/videos/2026-10-25-hf-radio/transcript.md` |
| **Source type** | OSINT — instructional video; same channel as `IR-20261026-ONE-TIME-PADS` |
| **Reliability** | **B2** — usually reliable, probably true. See ¶2.2 |
| **Subject** | HF propagation; NVIS; QRP and weak-signal modes; JS8Call; emergency comms planning |
| **Distribution** | Unlimited |
| **Handling** | Analytic exercise. Includes legal and RF-exposure sections (§7). |

**Handling caveat.** `[SOURCE CLAIM]` marks reproduction without endorsement; `[ANALYST ADD]` marks material from outside the source. The report's principal addition is the **bandwidth arithmetic in §5** — the mechanism behind "weak signal" that the video invokes without quantifying.

---

## TABLE OF CONTENTS

- **1. BLUF**
- **2. Source Assessment**
- **3. Framework** — the geometry · noise-limited versus sensitivity-limited · the bandwidth trade
- **4. Technical Analysis** — the alternatives survey · propagation · NVIS · the antenna · the gear · the settings · JS8Call
- **5. The Missing Number: 17 dB for Free**
- **6. Corrections**
- **7. Legal, Safety, and RF Exposure**
- **8. Cross-Archive Links**
- **9. Indicators and Warnings**
- **10. Intelligence Gaps and Key Judgments**
- **Appendices A–G**

---

## 1. BLUF — BOTTOM LINE UP FRONT

**1.1** This is the **strongest source in the `signals/` area on propagation**, and it contains the best single technical insight of any source in the archive — stated almost in passing: **NVIS is a mode of propagation, not a type of antenna.** That sentence is correct, non-obvious, and it dissolves most of the confusion in the amateur literature. **Confidence: high.**

**1.2 — The video gets the central propagation mechanism backwards, twice, and then contradicts itself.** `[SOURCE CLAIM]` The D layer "absorbs higher frequency, lower wavelength" and "allows the lower frequency, higher wavelength to pass through." **Both clauses are inverted.** The D layer absorbs **low** frequencies (long wavelengths) and is transparent to high ones — which is why 80 m is dead at noon and 20 m works. The source then advises 40 m "because it doesn't get absorbed by the D layer," which is correct and contradicts the inverted explanation given ninety seconds earlier. **Confidence: high.**

**1.3 — The best number in the video is the one it never states: 17 dB.** `[ANALYST ADD]` "Weak signal mode" is not a claim about sensitivity — it is a **bandwidth** claim. JS8Call occupies roughly **50 Hz**; SSB voice occupies ~2,500 Hz. The SNR gain from that narrowing alone is

```
10 · log₁₀(2500 / 50) = 17.0 dB
```

**Seventeen decibels for free, from arithmetic rather than from hardware.** That single number explains why a 10 W attic dipole reaches 400 miles, and it is the mechanism behind every claim in the video's "weak signal modes are where it's at." **Confidence: high.**

**1.4 — HF is noise-limited, not sensitivity-limited, and this inverts the lesson of the previous report.** In `IR-20261026-SATELLITE-GROUND-STATION` the antenna supplied ~100% of the margin and the electronics were refinements. **Here the limiting term is atmospheric noise**, which no amount of antenna gain removes — so the remedies are **more power, a better antenna, or a narrower mode**, and the third is cheapest. **The two reports are a matched pair: one where geometry dominates, one where the noise floor dominates.** **Confidence: high.**

**1.5 — The attic installation works by accident, and the video does not notice.** `[ANALYST ADD]` NVIS requires an antenna below ~1/10 λ. On 40 m that is **4.2 m (13.9 ft)**. An attic dipole sits at roughly 2.5–3 m — **inside the NVIS window by construction**, not by design. The 400-mile contact is therefore better explained by the accidental height than by the "multiple hops" hypothesis the source offers. **Confidence: moderate-high.**

**1.6 — The legal section is the weakest part and it gives advice that contradicts itself.** `[SOURCE CLAIM]` "The FCC doesn't really care. They never find you... They only go after the really bad ones." **This is false**, and the same passage immediately says "get your license, it's not that hard." Unlicensed transmission on amateur allocations is a federal offence with a routine enforcement record; the correct advice is the second sentence, and the first should not be there. Separately, the demonstration appears to transmit with a **fictitious call sign**, which is its own violation. **Confidence: high.**

**1.7 — One safety omission is serious: 100 W into an attic dipole above occupied space.** `[ANALYST ADD]` At 7 MHz the wavelength is 42 m, so every point inside a house is in the **near field**, where simple power-density estimates do not apply and a proper evaluation is required. The video recommends an attic antenna and up to 100 W and never mentions RF exposure. **Confidence: high** that the omission is real; **moderate** on the magnitude without a site-specific calculation.

---

## 2. SOURCE ASSESSMENT

### 2.1 Provenance

**2.1.1** A 42-minute, 6-second instructional video by `@CivilDefenseEngineer`, URL `https://www.youtube.com/watch?v=hePS5MwMcLk`. Local capture: `transcript.md`, same folder. Second video from this channel in the archive (see `IR-20261026-ONE-TIME-PADS`). Format: gear review, propagation explainer, and screen-recorded setup walkthrough.

**2.1.2** Structure:

| Ch. | Segment | Span |
|---|---|---|
| 1 | Intro: the alternatives | 0:00–6:13 |
| 2 | The Gear | 6:14–13:48 |
| 3 | Intro to HF Propagation | 13:49–22:02 |
| 4 | Step-by-step process | 22:03–27:40 |
| 5 | Intro to JS8Call | 27:41–40:00 |
| 6 | Action items | 40:00–42:06 |

**2.1.3 — Stated competence, and it is honest.** `[SOURCE CLAIM]` "I am not an RF engineer. I am a mechanical engineer. So I will be bringing things into lay parliament and dumb person speak as much as possible. This video is not for the ham nerd."

**Assessment: the disclaimer is accurate and it is the right one.** `[ANALYST ADD]` The video's target audience is a non-specialist who needs a working system, and it serves that audience well on **procedure** and badly on **mechanism**. **The failures cluster exactly where a mechanical engineer's intuition would be expected to slip — in the sign conventions of ionospheric absorption.**

### 2.2 Reliability grading

| Axis | Grade | Basis |
|---|---|---|
| **Source reliability** | **B — Usually reliable** | Demonstrates a working end-to-end system; shows his own failures; recommends licensing; admits the security limitations of JS8Call. But the propagation mechanism is inverted twice and the enforcement claim is false |
| **Information credibility** | **2 — Probably true** | Antenna formula, NVIS height criterion, settings, frequencies, and JS8 behaviour all check out. The propagation *explanation* does not |
| **Composite** | **B2** | Reliable as a build guide; unreliable as a physics explanation |

**2.2.1 — What raises the grade.** Four things:
1. **"NVIS is a type of propagation, not a type of antenna."** Correct, non-obvious, and it prevents a category error that the amateur literature propagates constantly.
2. **He reports his failures.** Test-PTT held the transmitter open; propagation was poor and he said so; the heartbeat got no reply and he said so.
3. **He admits the security is illusory.** "It adds a little bit of security by obscurity, but don't count on it." That is the honest framing and it is the same discipline as the previous report's subject, applied against his own recommendation.
4. **He recommends licensing** — the correct advice, even though it is undermined by the sentence before it (§7.2).

**2.2.2 — What lowers it.** The D-layer inversion is not a slip of the tongue; it is stated as the explanatory mechanism, and then contradicted by the practical advice. **A reader who learns the mechanism from this video will choose the wrong band.** That is a consequential error rather than a cosmetic one.

### 2.3 Conflict of interest

**2.3.1** No sponsor read, no affiliate links. Gear is named by model with prices on screen; no purchase links are evident in the transcript. **Clean.**

**2.3.2 — The relevant interest is ideological, and it is disclosed.** `[ANALYST ADD]` The channel's premise is that surveillance is expanding and that infrastructure may fail or be shut down. That framing predicts a specific bias: **toward emphasising capability and understating constraint**, because a technique described as available is more motivating than one described as marginal. The video resists this better than most — it says propagation was poor, the heartbeat failed, and the mode is not secure. **The one place it does not resist is the enforcement claim (§7.2), which is exactly where the bias would predict a distortion.**

### 2.4 Transcription integrity

| As transcribed | Correct form | Note |
|---|---|---|
| "True SDX" | **(tr)uSDX** | The QRP transceiver |
| "Yau rig" / "YESU" / "Yus" | **Yaesu** | FT-891 |
| "Bow Fang" | **Baofeng** | VHF/UHF handhelds |
| "Mishtastic" | **Meshtastic** | LoRa mesh |
| "envis" / "ENVIS" / "NVIZ" / "Envis" | **NVIS** — near-vertical incidence skywave | Central term |
| "balon" | **balun** | — |
| "Digi Rig" / "Digg" | **DigiRig** | Sound-card interface |
| "JSA call" / "JS8" | **JS8Call** | — |
| "FTA" | **FT8** | — |
| "maiden head grid" | **Maidenhead grid** | Locator system |
| "K factor" | **Kp index** | Geomagnetic activity |
| "pace plan" | **PACE plan** | Primary/Alternate/Contingency/Emergency |
| "waifu catg girls" | *(as spoken)* | — |
| "hurting sheep" | *(as spoken)* | — |
| "lay parliament" | **lay parlance** | — |
| "2 or 3 miles" (Baofeng) | miles | — |

**2.4.1 — "NVIS" is corrupted five different ways** and it is the video's central concept. This is the archive's recurring pattern: the ASR destroys precisely the term that carries the technical content, and the report must restore it before analysis.

### 2.5 Verification status

| Claim | Locus | Status |
|---|---|---|
| Starlink is a parallel system, hard to take down wholesale | 0:32 | **Verified in outline** |
| VHF/UHF handheld range ~2–3 miles | 1:43 | **Verified** for ground-level handhelds |
| A repeater boosts power and provides elevation advantage | 2:43 | **Verified** — and correctly described |
| Internet-linked repeater networks exist (East Coast Reflector) | 2:50 | **Verified** |
| Meshtastic: every node relays; ~1–2 mile range | 3:09 | **Verified** |
| QRP = under 10 W | 6:36 | **Approximately correct** — conventionally ≤5 W CW, ≤10 W SSB (¶6.4) |
| (tr)uSDX: 5 W on USB power, 10 W with battery pack | 6:43 | **Plausible** for that rig |
| SMA is a threaded connector with a nut; BNC is quarter-turn | 7:42 | **Verified** |
| Aluminum is ~60% as conductive as copper; used for HV lines | 8:13 | **Verified** |
| A balun matches antenna to coax | 8:33 | **Imprecise** — a 1:1 balun suppresses common-mode current, it does not change the ratio (¶6.3) |
| Dipole length = 468 / f(MHz) feet | 9:29 | **Verified** (492 × 0.95 end-effect factor) |
| Fan dipole for multiple bands | 9:16 | **Verified** |
| **D layer absorbs higher frequencies** | 15:18 | **INVERTED** — it absorbs low frequencies (§4.2.3) |
| **D layer passes lower frequencies through** | 15:29 | **INVERTED** — it passes high frequencies |
| Ground wave ~30 miles on HF | 14:52 | **Verified** in order of magnitude |
| Skip zone exists between ground-wave and skywave range | 15:55 | **Verified** |
| NVIS: takeoff within ~30° of vertical, reaches the skip zone | 16:25 | **Verified** |
| NVIS ignores terrain; works from a canyon | 16:47 | **Verified** — steep-angle paths clear obstacles |
| Multiple hops attenuate heavily | 17:15 | **Verified** |
| Skywave antenna height ≥ ½ λ; NVIS ≤ ~1/10 λ | 18:06 | **Verified** |
| Ground plane reflects downward energy upward | 18:35 | **Correct in effect**, loosely described |
| **NVIS is a propagation mode, not an antenna type** | 19:00 | **Verified — best insight in the video** |
| NVIS is hard to direction-find; explains numbers stations | 19:33 | **Verified in principle** |
| Solar flux drives the ionosphere; 11-year cycle | 20:21 | **Verified** |
| Geomagnetic storms degrade HF | 20:51 | **Verified** |
| "K factor" | 21:27 | **Kp index** — minor |
| Attic dipole attenuated by shingles, nails, board | 22:32 | **Verified** — metal fasteners detune and absorb |
| 400 miles on 10 W with an attic dipole | 37:50 | **Plausible**; reported −1 and −14 dB SNR |
| Get licensed; test costs ~$20–30, valid 10 years | 23:08 | **Verified** (US amateur licence term is 10 years) |
| **"The FCC doesn't really care, they never find you"** | 23:25 | **FALSE** (§7.2) |
| USB = upper sideband; digital modes use USB on all bands | 25:40 | **Verified**, and a genuinely useful clarification |
| 40 m is the most capable all-round band | 26:25 | **Verified in practice** |
| RTS = request to send, used to key PTT | 33:27 | **Verified** |
| JS8Call requires accurate clock | 28:25 | **Verified** — 15-second T/R periods |
| "Automatic time drift" feature | 28:52 | **Unverified** — the requirement is real; the named feature is not confirmed |
| JS8Call heartbeats map propagation | 35:52 | **Verified** |
| JS8Call relays store-and-forward | 12:19 | **Verified** |
| JS8Call is not encrypted; obscurity only | 11:53 | **Verified and honestly stated** |
| 7.078 MHz is the 40 m JS8 calling frequency | 37:14 | **Verified** |
| S2 Underground runs a net on 7.107 MHz | 37:29 | **Unverified**, and see ¶8.3 |

---

## 3. FRAMEWORK

### 3.1 The geometry

**3.1.1** `[ANALYST ADD]` HF propagation is a geometry problem with a plasma in it. Three paths:

| Path | Mechanism | Range | Constraint |
|---|---|---|---|
| **Ground wave** | Surface-hugging diffraction | ~tens of km on 40 m | Ground conductivity; dies with frequency |
| **Skywave** | Refraction in the ionosphere at a shallow takeoff angle | hundreds to thousands of km | MUF/LUF; one or more hops |
| **NVIS** | Refraction at near-vertical incidence, returning steeply | ~0–500 km | Antenna height; frequency below the critical frequency |

**3.1.2 — Why the skip zone exists.** `[ANALYST ADD]` Ground wave fails beyond a few tens of kilometres; a shallow-angle skywave overshoots and lands hundreds of kilometres away. **The region between them is unreachable** — unless you send the signal nearly straight up, which is exactly what NVIS does. **The skip zone is not a defect of HF; it is the reason NVIS is necessary**, and the video's explanation of this is correct and clear.

**3.1.3 — The heights, computed.** `[ANALYST ADD]` At 7.078 MHz, λ = 42.4 m:

| Criterion | Metric | Imperial |
|---|---|---|
| NVIS maximum (λ/10) | **4.24 m** | **13.9 ft** |
| Skywave minimum (λ/2) | **21.2 m** | **69.5 ft** |
| Half-wave dipole length (468/f) | 20.1 m | **66.1 ft** |

**The two criteria differ by a factor of five**, which is why the same wire works completely differently depending on where you hang it. **This is the single most useful table in the report** and the video gives the rule without the numbers.

### 3.2 Noise-limited versus sensitivity-limited

**3.2.1** `[ANALYST ADD]` The two receiver regimes, and the archive now contains one of each:

| | `SATELLITE-GROUND-STATION` | **This report** |
|---|---|---|
| **Limiting term** | Thermal noise (kTB) | **Atmospheric and man-made noise** |
| **Antenna gain** | ~100% of the margin | Helpful but not dominant |
| **Dominant remedy** | More aperture | **More power, better antenna, narrower mode** |
| **Frequency** | 1.7 GHz (quiet) | 7 MHz (loud) |

**3.2.2 — Why the distinction matters.** `[ANALYST ADD]` At 7 MHz the **external noise** is typically 40–50 dB above thermal noise in a quiet rural location, and higher in a city. That means:

- **A better receiver buys almost nothing.** The signal-to-noise ratio is set by the antenna and the band, not by the radio.
- **The noise floor scales with bandwidth.** Halving the bandwidth halves the noise power — **so bandwidth is a direct SNR lever, and it is free.**
- **The ionosphere is the channel, and it is not stationary.** The same link closes at 02:00 and fails at 14:00.

**The whole video is an implicit argument for §3.2.2, and stating it explicitly is what makes the advice generalise.**

### 3.3 The bandwidth trade

**3.3.1 — The identity.** `[ANALYST ADD]` For a receiver limited by external noise, and for noise that is flat across the band:

```
SNR = P_signal / (N₀ · B)
```

**Narrowing `B` by a factor `k` raises SNR by `10 log₁₀ k` decibels — with no change to transmitter, antenna, or receiver.** This is the entire basis of every "weak signal" mode.

**3.3.2 — The arithmetic for JS8Call.** `[ANALYST ADD]`

| Mode | Occupied bandwidth | Noise in that band (relative) |
|---|---|---|
| SSB voice | ~2,500 Hz | 0 dB reference |
| **JS8Call** | **~50 Hz** | **−17.0 dB** |

**Seventeen decibels, for free.** In power terms that is a factor of fifty — equivalent to raising a 10 W transmitter to 500 W, or to a 17 dB antenna gain, which would be a dish the size of a small building.

**3.3.3 — The cost, which is not free.** `[ANALYST ADD]` The trade is **data rate and latency**:

| Cost | Detail |
|---|---|
| **Throughput** | ~50 Hz carries a few characters per 15-second frame; voice carries continuous speech |
| **Latency** | JS8Call's frames are 15 s; a QSO is minutes, not seconds |
| **Synchronisation** | Both ends need clocks within ~1–2 s (§4.7) |
| **Ergodicity assumption** | Narrowband works because noise is flat across the band; **impulse noise and interference violate this**, which is why a single carrier can wipe out a 50 Hz slot |

**3.3.4 — The generalisation.** `[ANALYST ADD]` This is the same trade as in `IR-20261026-FIBER-OPTICS`, in a different currency: **there is no free lunch, only a cheaper lunch.** In fiber, loss was traded against wavelength; here, SNR is traded against throughput. **The archive now has two instances of the same move — buy the scarce resource with an abundant one — and in both cases the correct answer is to identify which resource is actually scarce.**

---

## 4. TECHNICAL ANALYSIS

### 4.1 The alternatives survey

**4.1.1 — The comparisons, assessed.** `[ANALYST ADD]`

| Option | Source's claim | Assessment |
|---|---|---|
| **Starlink** | Parallel infrastructure; vulnerable to a single operator's policy | **Correct**, and the political point is the substantive one: dependence on a single private switch is a real single point of failure |
| **Baofeng VHF/UHF** | 2–3 miles handheld; repeaters help but do not form a network | **Correct.** Handheld-to-handheld at ground level is genuinely short |
| **Repeaters** | One repeater boosts power and elevation; it is not a mesh | **Correct and the best correction in the survey.** The misconception that repeaters work like cell towers is widespread |
| **Meshtastic** | Every node relays; 1–2 miles; good for a dense crowd, not a dispersed group | **Correct**, and the distinction between *density* and *dispersion* use cases is well drawn |

**4.1.2 — The one comparison he omits.** `[ANALYST ADD]` **HF is not a replacement for local comms; it is a different layer.** A PACE plan (§4.8) needs *both*: HF for the 200-mile link, VHF/Meshtastic for the 2-mile link. The video frames them as competitors and then, correctly, recommends HF only for "key pieces" — **so the framing and the conclusion disagree, and the conclusion is right.**

**4.1.3 — The repeater-range physics worth adding.** `[ANALYST ADD]` VHF/UHF range is set by radio horizon:

```
d ≈ 4.1 · (√h₁ + √h₂)   km,  h in metres
```

A handheld at 1.7 m and a repeater at 100 m gives ~5 + 41 = **46 km**. **Two handhelds at 1.7 m give ~11 km** — which is why the source's "2–3 miles" is right for handheld-to-handheld and pessimistic for repeater access. **The variable is height, not power**, and that is the same lesson as NVIS.

### 4.2 Propagation

**4.2.1 — The layers.** `[SOURCE CLAIM]` D, E, F1, F2.

**Assessment: correct.** `[ANALYST ADD]` The standard structure, with the functional roles the video is reaching for:

| Layer | Altitude | Day/night | Role |
|---|---|---|---|
| **D** | 60–90 km | Day only | **Absorption** — attenuates HF passing through |
| **E** | 90–150 km | Day; sporadic at night | Weak refraction; occasional Sporadic-E openings |
| **F1** | 150–220 km | Day only | Merges with F2 at night |
| **F2** | 220–500 km | Day and night | **The main refracting layer** for long-haul HF |

**4.2.2 — Why the D layer matters more than its size suggests.** `[ANALYST ADD]` The D layer does not refract usefully; it **absorbs**. Absorption is proportional to electron density divided by the square of the frequency:

```
A ∝ N_e / f²
```

**So low frequencies are absorbed heavily and high frequencies pass through almost untouched.** This single relation explains:

- why 80 m and 160 m are daytime-dead and night-time-viable;
- why 40 m works day and night but with a daytime penalty;
- why 20 m is a daytime band and 40 m a night band;
- and why the maximum usable frequency rises during the day.

**4.2.3 — The inversion.** `[SOURCE CLAIM]` "This D layer here absorbs lower frequency — sorry, yeah — higher frequency, lower wavelength — and it allows the lower frequency, higher wavelength to pass through and get refracted by these higher ionosphere levels."

**Assessment: both clauses are backwards.** `[ANALYST ADD]` The correct statement is the exact opposite:

> **The D layer absorbs *low* frequencies (long wavelengths) and is nearly transparent to *high* frequencies (short wavelengths), which pass through to be refracted by the F layer.**

**The source appears to catch himself mid-sentence** — the "sorry, yeah" suggests he noticed a slip and then corrected in the wrong direction. **The result is an explanation that would lead a reader to pick the wrong band.**

**4.2.4 — And the advice that follows contradicts it.** `[SOURCE CLAIM]` 40 m is capable "because it doesn't get absorbed by that D layer."

**Assessment: correct, and inconsistent with ¶4.2.3.** `[ANALYST ADD]` 40 m survives D absorption better than 80 m because 7 MHz is high enough for the `1/f²` penalty to be tolerable. **The practical advice is right and the mechanism given for it is inverted** — which means the reader can follow the instruction but cannot generalise it to a new band or a new time of day. **That is the specific cost of an inverted explanation: it works for the case in front of you and fails everywhere else.**

### 4.3 NVIS

**4.3.1 — The insight.** `[SOURCE CLAIM]` "NVIS is a type of propagation, not a type of antenna. And that means that even though you have it set up in a sort of NVIS configuration, like one-tenth wavelength above the ground, you may still be getting a component of your transmission that is propagating regular skywave."

**Assessment: correct, and this is the best technical statement in the archive.** `[ANALYST ADD]` The distinction is between a **mode** and a **configuration**:

- **NVIS is what the ionosphere does** with a steep-angle signal.
- **The antenna configuration only biases the takeoff angle.** A low horizontal dipole radiates a lobe near the zenith *and* residual low-angle lobes.
- **Therefore a "NVIS antenna" still produces some skywave**, which is exactly why the source makes contacts well beyond the nominal radius.

**4.3.2 — Why this matters operationally.** `[ANALYST ADD]` It means:

| Consequence | Detail |
|---|---|
| **Range is probabilistic, not bounded** | The nominal 200–300 mile figure is a mode of the distribution, not a limit |
| **Terrain independence is conditional** | NVIS clears mountains *because* the path is steep; the low-angle component does not |
| **The DF resistance is partial** | A strong low-angle component is direction-findable even if the NVIS component is not (§4.3.4) |

**4.3.3 — The accidental compliance.** `[ANALYST ADD]` The source's attic dipole sits at roughly 2.5–3 m. The NVIS ceiling on 40 m is **4.24 m**. **So the antenna is inside the NVIS window by construction**, because an attic is simply not tall enough to violate it. The 400-mile contact is therefore better explained by:

1. the low height forcing a high takeoff angle (NVIS), **plus**
2. the residual low-angle lobe that the source himself identifies, **plus**
3. possibly a second hop —

**in that order of likelihood.** The source offers (3) and (2) and misses (1), which is the one his own geometry guarantees.

**4.3.4 — The direction-finding point, which is the strongest operational claim in the video.** `[SOURCE CLAIM]` NVIS is hard to direction-find because the signal is weak and comes from the sky; this is why numbers stations survived so long.

**Assessment: correct in principle, and it connects directly to the previous report.** `[ANALYST ADD]` A ground-based DF array resolves a bearing from the **horizontal** phase/amplitude gradient across its elements. A signal arriving at 70–90° elevation presents almost no horizontal gradient, so the bearing is poorly determined. **The station is locatable in principle but not by a simple baseline.**

**4.3.5 — And the archive now holds both halves.** `[ANALYST ADD]` In `IR-20261026-ONE-TIME-PADS` the same author announced he was acquiring a **Doppler RDF unit**. Here he explains why NVIS defeats one. **The two videos, taken together, are a matched pair on the same problem from both sides** — and neither states the synthesis: *the counter to DF is a steep takeoff angle, low power, and short transmissions; the counter to that is a multi-site DF network, which resolves elevation as well as bearing.*

### 4.4 The antenna

**4.4.1 — The formula.** `[SOURCE CLAIM]` Length in feet = 468 / frequency in MHz.

**Assessment: correct.** `[ANALYST ADD]` The constant is `492 × 0.95`, where 492 is the free-space half-wave length in feet at 1 MHz and 0.95 accounts for the end effect and the velocity factor of the wire. At 7.078 MHz:

```
468 / 7.078 = 66.1 ft  (20.1 m)
```

**4.4.2 — The balun claim.** `[SOURCE CLAIM]` A balun "helps match the impedance of the antenna to the coax cable... they have to match in order to get the most efficient setup."

**Assessment: imprecise.** `[ANALYST ADD]` A **1:1 balun does not change the impedance ratio.** What it does is force the transition from a balanced antenna to an unbalanced coax, suppressing **common-mode current** on the shield. Common-mode current causes:

- pattern distortion and unpredictable SWR;
- **"hot" coax** — the feedline radiates, which is both an efficiency loss and an RF-exposure problem indoors;
- receiver noise pickup from the shack.

**A 4:1 balun *would* transform impedance**, and which one is correct depends on the antenna. **The practical advice ("use a balun") is right; the stated reason is the wrong one**, and the wrong reason matters here because the right one is a *safety* reason (§7.3).

**4.4.3 — The "good enough" principle.** `[SOURCE CLAIM]` "A lot of this stuff the ham nerds will chase maximum efficiency, but in my opinion, better is the enemy of good enough."

**Assessment: sound engineering judgment, correctly applied.** `[ANALYST ADD]` The relevant calculation: a dipole cut for 7.078 MHz fed with a 2:1 SWR mismatch loses about **0.5 dB** — invisible on the air. **Chasing the last half-decibel is irrational; chasing a resonant antenna at all is rational because a 10:1 mismatch can damage a QRP final stage.** So the aphorism is right *and* it has a boundary, and the boundary is the point at which inefficiency becomes equipment damage.

**4.4.4 — The attic penalties, correctly identified.** `[SOURCE CLAIM]` Attenuation from asphalt shingles, roofing nails, and particle board.

**Assessment: correct, and the nails are the significant one.** `[ANALYST ADD]` Metal fasteners within a fraction of a wavelength of the wire:
- **detune** the antenna (shifting resonance, raising SWR);
- **absorb** energy in nearby conductors, which are effectively lossy parasitic elements;
- and can create **arcing** at high power if contact is intermittent.

**The source's 10–80 W through an attic dipole is therefore operating an antenna in a lossy, detuned, and potentially arcing environment — which is exactly the configuration in which an SWR meter matters, and it is absent from the gear list (¶6.5).**

### 4.5 The gear

**4.5.1 — The list, assessed.** `[ANALYST ADD]`

| Item | Present | Comment |
|---|---|---|
| QRP transceiver | Yes | (tr)uSDX-class; 5 W USB, 10 W with pack |
| Coax + connectors | Yes | SMA / BNC correctly distinguished |
| Antenna wire | Yes | Aluminum fence wire is a legitimate cheap choice |
| Balun | Yes | Reason imprecise (§4.4.2) |
| DigiRig + cable | Yes | Sound-card interface |
| Computer | Yes | "Beater computer" is the right instinct |
| **SWR meter** | **No** | **Significant omission** (§4.4.4) |
| **Antenna tuner** | **No** | Needed only for non-resonant wire |
| **RF exposure assessment** | **No** | **Significant omission** (§7.3) |

**4.5.2 — The missing SWR meter is the most consequential gear omission.** `[ANALYST ADD]` A QRP rig's final transistors are cheap and unprotected; **a badly mismatched antenna can destroy them in seconds.** A $20 SWR meter or a nanoVNA is the difference between a working station and a dead radio, and it costs less than the coax.

### 4.6 The settings

**4.6.1 — The USB/LSB clarification.** `[SOURCE CLAIM]` "You want USB. This is not referring to universal serial bus. This is referring to upper sideband... Usually if you're on 40 m and you're talking on voice, you want LSB. But for digital modes, at least for JS8Call, it uses upper sideband modulation."

**Assessment: correct and genuinely useful.** `[ANALYST ADD]` The convention is:
- **Below 10 MHz: LSB for voice; above 10 MHz: USB for voice** (a historical artefact, not physics);
- **Digital modes use USB on every band**, because the software defines the audio passband relative to the suppressed carrier and expects a consistent inversion.

**Getting this wrong produces a signal that is decoded as garbage and sounds like noise** — and it is one of the most common setup failures. **The video's emphasis is proportionate to the failure rate.**

**4.6.2 — The filter bandwidth.** `[SOURCE CLAIM]` Full, at least 3 kHz.

**Assessment: correct for the audio passband, with a note.** `[ANALYST ADD]` The **RF** signal is ~50 Hz; the **audio** passband must be wide enough to contain the sub-band you are monitoring (multiple JS8 signals across ~3 kHz). **So the wide filter is for situational awareness, not for the signal** — a point worth stating because it looks like a contradiction of §5.

**4.6.3 — RTS keying.** `[SOURCE CLAIM]` RTS = request to send, used to toggle PTT over RS-232.

**Assessment: correct.** `[ANALYST ADD]` RTS is a modem control line repurposed as a PTT key. It is used when **CAT control is unavailable or unwanted** — which is exactly the case for a (tr)uSDX, which has limited CAT support. **Choosing RTS over CAT is the right call for this rig and the source does not explain why**, which means a reader with a different radio may copy the wrong choice.

### 4.7 JS8Call

**4.7.1 — The clock requirement.** `[SOURCE CLAIM]` JS8Call's frames must align with the horizontal lines on the waterfall, so every station needs an accurate clock.

**Assessment: correct and important.** `[ANALYST ADD]` JS8Call inherits FT8's **15-second T/R period** structure; symbols must land within the slot. A clock error of more than ~1–2 s causes decode failure or partial decodes. **This is why the waterfall shows dots** — the software decoded a fragment and could not recover the frame.

**4.7.2 — The named feature.** `[SOURCE CLAIM]` "Automatic time drift" adjusts the decode offset.

**Assessment: the requirement is real; the named feature is unverified.** `[ANALYST ADD]` The standard remedy is a time-synchronisation service (NTP, or GPS where no internet exists), and JS8Call does expose a **DT** (delta-time) readout that lets an operator see and correct the offset. **Whether a specific auto-correction control exists under that name could not be confirmed**, and the report flags it rather than repeating it.

**4.7.3 — The security statement, which is the honest one.** `[SOURCE CLAIM]` "It's not encrypted, but it's encoded into its own digital protocol... anybody who's listening who is decoding on JS8 will be able to read your messages in the clear, but it adds a little bit of security by obscurity, but don't count on it."

**Assessment: correct, and it is the right way to say it.** `[ANALYST ADD]` Two distinct facts, correctly separated:
- **Encoding ≠ encryption.** JS8's protocol is public; the software is free; **decoding is the default behaviour of every listener.**
- **Obscurity has a bounded value.** It raises the cost of casual interception and does nothing against a motivated listener.

**This is the same distinction the previous report's subject turns on, applied correctly and against the author's own recommendation.** It is the most creditable passage in the video.

**4.7.4 — The relay function.** `[SOURCE CLAIM]` Station 2 can relay between stations 1 and 3.

**Assessment: correct.** `[ANALYST ADD]` JS8Call supports store-and-forward relaying and directed queries through intermediate stations. **This is genuinely a network capability without infrastructure**, and it is the strongest functional argument for the mode. **It also has a security consequence the video does not mention: every relay operator can read the message.** A relayed message is not a confidential message.

**4.7.5 — The heartbeat.** `[SOURCE CLAIM]` Heartbeats advertise presence and are relayed, building a picture of who can hear whom.

**Assessment: correct.** `[ANALYST ADD]` The heartbeat network is effectively a **crowdsourced propagation map** — and, incidentally, **a location-disclosure mechanism**, since heartbeats carry the sender's grid square (§4.7.6).

**4.7.6 — The Maidenhead grid, and what it discloses.** `[SOURCE CLAIM]` Grid locator rather than GPS coordinates; needed for heartbeats.

**Assessment: correct, and the privacy implication deserves stating.** `[ANALYST ADD]` A **6-character Maidenhead locator** is roughly a 6 × 4 km cell; **4 characters** is ~150 × 100 km. So the grid is a deliberate **coarse-grained** location disclosure — enough for propagation mapping, not enough for street-level targeting. **That is a reasonable trade and it is the correct design**, but it is a trade, and the video presents it as merely a convenience.

### 4.8 The PACE plan

**4.8.1** `[SOURCE CLAIM]` Primary, Alternate, Contingency, Emergency.

**Assessment: correct concept, muddled delivery.** `[ANALYST ADD]` The standard structure:

| Tier | Meaning | Example |
|---|---|---|
| **Primary** | The method you use by default | Cell / internet |
| **Alternate** | A different method, same capability | HF |
| **Contingency** | A method that works when the first two fail | VHF simplex, Meshtastic |
| **Emergency** | Last resort, possibly degraded | Courier, face-to-face |

**The video says HF "will fit somewhere into the A and C category"** — which is true but imprecise. **HF is the Alternate for the strategic link and the Contingency for the local one**, and stating it that way would make the layering explicit.

---

## 5. THE MISSING NUMBER: 17 dB FOR FREE

**5.1 — Why this is the report's central addition.** `[ANALYST ADD]` The video says "weak signal modes are where it's at" and demonstrates a 400-mile contact on 10 W. **It never says why the mode works**, and the reason is one line of arithmetic that generalises to every narrowband system the reader will ever encounter.

**5.2 — The identity.**

```
SNR = P_signal / (N₀ · B)

Narrowing B by factor k  ⟹  SNR improves by 10·log₁₀(k) dB
```

**5.3 — The numbers.**

| Quantity | Value |
|---|---|
| SSB voice occupied bandwidth | ~2,500 Hz |
| JS8Call occupied bandwidth | ~50 Hz |
| **Bandwidth ratio** | **50:1** |
| **SNR gain** | **17.0 dB** |
| Equivalent power increase (from 10 W) | **~500 W** |
| Equivalent antenna gain | **17 dB** — larger than the satellite dish in `IR-20261026-SATELLITE-GROUND-STATION` would need |

**5.4 — What 17 dB buys, in the source's own measurements.** `[ANALYST ADD]` He reports hearing the other station at **−14 dB** and being heard at **−1 dB**, both quoted in JS8Call's 2,500 Hz reference bandwidth.

```
−14 dB in 2,500 Hz  ⟺  +3 dB in 50 Hz
−1 dB in 2,500 Hz   ⟺  +16 dB in 50 Hz
```

**Both contacts are comfortably above the noise once the bandwidth is accounted for.** The "weak signal" is weak only in the wideband sense; **in the bandwidth the decoder actually uses, the signal is strong.** That reframing is the whole point and it is absent from the video.

**5.5 — The link budget, for comparison with the satellite case.** `[ANALYST ADD]`

| Term | Value | Working |
|---|---|---|
| Transmit power | **+40.0 dBm** | 10 W |
| Transmit dipole gain | +2.15 dBi | Half-wave |
| **Free-space path loss, 644 km at 7.078 MHz** | **−105.6 dB** | `20log(644) + 20log(7.078) + 32.45` |
| Receive dipole gain | +2.15 dBi | — |
| **Received power (free space, no ionospheric loss)** | **−61.3 dBm** | |
| Thermal noise, 2,500 Hz | −140.0 dBm | `−174 + 10log(2500)` |
| Thermal noise, 50 Hz | −157.0 dBm | |
| **Actual HF noise floor (atmospheric)** | **≈ −95 to −105 dBm** | External noise dominates by 40–50 dB |

**5.6 — What the budget shows, and it is the inverse of the satellite report.** `[ANALYST ADD]`

| | Satellite (1.7 GHz) | **HF (7 MHz)** |
|---|---|---|
| Dominant loss | Free space, 188 dB | Free space, 106 dB — **82 dB less** |
| Dominant noise | Thermal | **Atmospheric — 40–50 dB above thermal** |
| Antenna's share of margin | **~100%** | Minor |
| Effective remedy | Aperture | **Bandwidth, then power** |

**The path loss is 82 dB lower than the satellite case, and the noise floor is 40–50 dB higher. The two effects nearly cancel** — which is why a 10 W attic dipole reaches 400 miles while an 8-ft dish is needed for a geostationary satellite. **That comparison is the most useful thing the archive can say about HF versus microwave, and neither source says it.**

---

## 6. CORRECTIONS

### 6.1 The D-layer sign inversion

See ¶4.2.3. **The D layer absorbs low frequencies and passes high ones.** Stated twice, inverted twice, then contradicted by correct practical advice.

### 6.2 "The FCC doesn't care" is false

See §7.2. The claim is factually wrong and legally risky.

### 6.3 The balun's function

See ¶4.4.2. A 1:1 balun suppresses common-mode current; it does not transform impedance. **The stated reason is wrong and the correct reason is a safety reason.**

### 6.4 QRP is ≤5 W CW, ≤10 W SSB

**6.4.1** `[SOURCE CLAIM]` "QRP... is a ham brevity code for an HF rig that is low power, under 10 watts."

**6.4.2 — The correction.** `[ANALYST ADD]` The convention is **≤5 W for CW and digital, ≤10 W for SSB** — the distinction exists because SSB is peak-envelope power and CW is average. **The source's single "under 10 W" is approximately right for the mode he is using (digital) and wrong for CW.**

**6.4.3 — Why it matters at all.** `[ANALYST ADD]` Because QRP is a *category* in contests, awards, and equipment claims, and a rig that does 10 W PEP on SSB but 5 W on CW is compliant with both definitions only if the distinction is understood. **Minor, but it is the kind of definition that gets copied.**

### 6.5 The missing SWR meter

See ¶4.5.2. **This is the omission with the highest expected cost** — a mismatched antenna can destroy a QRP final stage, and the instrument that prevents it costs less than the coax.

### 6.6 "K factor" is the Kp index

**6.6.1** `[SOURCE CLAIM]` "You don't need to learn all this jargon like K factor and all that."

**6.6.2 — The correction.** `[ANALYST ADD]` The geomagnetic activity index is **Kp** (planetary K-index, 0–9), derived from magnetometer stations. There is no "K factor" in this context. **Minor, and the underlying advice — use a published band-conditions service rather than learning the indices — is sound.**

### 6.7 The "30° cone" for NVIS

**6.7.1** `[SOURCE CLAIM]` NVIS takeoff is "within like a 30° cone of vertical."

**6.7.2 — The precision.** `[ANALYST ADD]` A 30° cone about the zenith corresponds to **elevation angles of 60–90°**, which is the standard NVIS window. **The statement is correct as a cone and easy to misread as an elevation figure.** Worth restating as "60–90° elevation."

---

## 7. LEGAL, SAFETY, AND RF EXPOSURE

**7.1 — Why this section is present.** `[ANALYST ADD]` The `signals/` area carries a standing safety and compliance note. This source addresses the legal question directly and gets it wrong, and it omits the physical hazard entirely.

### 7.2 The enforcement claim

**7.2.1 — The claim.** `[SOURCE CLAIM]` "The good thing about getting the license is that it gets all the sad hams off your tail, because honestly, the FCC doesn't really care. They never find you. They never go after you if you're just doodling away on HF transmitting. They only go after the really bad ones."

**Assessment: false, and it is the most consequential error in the video.**

**7.2.2 — The correction.** `[ANALYST ADD]` Unlicensed transmission on amateur allocations is a **federal offence** in the United States, and the FCC's Enforcement Bureau maintains a **routine public record** of notices of unlicensed operation, notices of apparent liability, and consent decrees — including for HF operation and including for interference complaints. The relevant facts:

| Fact | Detail |
|---|---|
| **It is an offence** | Unlicensed operation is prohibited; penalties include monetary forfeitures and equipment seizure |
| **Enforcement is real** | Actions are published routinely; the bureau responds to complaints |
| **Detection is not the barrier** | Complaints, DF, and monitoring drive cases — not the FCC's own patrols |
| **The practical risk is tail risk** | Most unlicensed operators are not caught; **the ones who are caught are caught expensively** |

**7.2.3 — And the video contradicts itself.** `[SOURCE CLAIM]` Three sentences later: "the best thing to do is get the license... So, get your license. It's not that hard."

**Assessment: the second sentence is the correct advice and the first should not be there.** `[ANALYST ADD]` The likely reason for the framing is **audience sympathy** — the channel's readership is sceptical of federal authority, and "they don't care" is reassuring. **That is precisely the direction of bias predicted in ¶2.3.2, and it is the one place the video yields to it.**

### 7.3 The fictitious call sign

**7.3.1** `[SOURCE CLAIM]` The JS8Call configuration is shown with the call sign "CDEA1," described as bogus, with the explanation that the author is licensed but does not want to publish his real call sign.

**Assessment: the privacy motive is legitimate; the method is not.** `[ANALYST ADD]`

| Consideration | Detail |
|---|---|
| **Station identification** | Transmissions must identify the station with its **assigned** call sign. A fictitious identifier does not satisfy this |
| **The demo** | The transcript does not make clear whether the heartbeat transmission occurred with the bogus identifier configured. **If it did, it was an improperly identified transmission** |
| **The stated practice** | He says he uses his real call sign "in actual operation," which is the correct practice |
| **The privacy concern is real** | A US call sign resolves to a name and address in the public database. **The legitimate remedies are a PO box on the licence and a vanity call, not a false identifier** |

**7.3.2 — The correct framing.** `[ANALYST ADD]` **The problem the author is trying to solve is real and the solution he chose is a violation.** The compliant solution — a PO box address on the licence application, and a grid square rather than coordinates in software — achieves the same privacy without a false identifier.

### 7.4 RF exposure

**7.4.1 — The omission.** `[SOURCE CLAIM]` An attic dipole, 10–80 W, sometimes 100 W, with the operator at a desk below.

**Assessment: this is a genuine hazard evaluation that the video does not perform, and the geometry is the worst case for a naive estimate.**

**7.4.2 — Why the usual shortcut fails here.** `[ANALYST ADD]` At 7 MHz the wavelength is **42 m**. The near-field/far-field boundary is at roughly `2D²/λ` for an antenna of dimension `D`, and for a 20 m dipole that is already tens of metres — **so every point inside the house is in the near field**, where the simple `P/(4πr²)` power-density formula does not apply and field strength must be measured or modelled.

**7.4.3 — The applicable rules.** `[ANALYST ADD]`

| Requirement | Detail |
|---|---|
| **Routine evaluation** | US amateur stations must evaluate compliance with RF exposure limits; the FCC provides a specific procedure and exemptions |
| **Uncontrolled environment** | The general-population limits apply to anyone who is not the licensee — i.e. **family members in the house** |
| **The attic case is not exempt** | Antennas inside a dwelling are among the configurations that require evaluation rather than assumption |

**7.4.4 — The mitigations, which are cheap.** `[ANALYST ADD]`

| Measure | Effect |
|---|---|
| **Reduce power when people are present** | Power density scales linearly; 10 W instead of 100 W is 10 dB |
| **Locate the antenna away from occupied rooms** | Distance is the strongest lever in the near field |
| **Operate with a duty cycle** | Exposure limits are averaged over time |
| **Use the low-angle component outdoors** | An outdoor wire removes the problem entirely |
| **Measure, do not assume** | A calibrated field-strength meter settles it |

**7.4.5 — The finding.** `[ANALYST ADD]` **The video recommends the specific configuration — attic antenna, up to 100 W, occupied space below — that most requires an exposure evaluation, and does not mention exposure at all.** That is the most serious omission in the source and it is not a technicality.

### 7.5 Antenna and structural hazards

**7.5.1** `[ANALYST ADD]` Present but minor in this source: work at height, wire under tension, and the arcing risk from an attic antenna in contact with metal fasteners at high power. **The last is the one worth naming** — an intermittent contact in an attic is a fire risk, and it is another argument for the SWR meter.

---

## 8. CROSS-ARCHIVE LINKS

### 8.1 The matched pair: geometry versus noise

See §5.6. **The archive now holds two reports that are the same calculation with different dominant terms**, and comparing them is more instructive than either alone:

| | Satellite | **HF** |
|---|---|---|
| Path loss | 188 dB | 106 dB |
| Noise | Thermal | **Atmospheric, +40–50 dB** |
| Antenna's share of margin | ~100% | Minor |
| Remedy | Aperture | **Bandwidth** |

**The two effects nearly cancel, which is why a 10 W wire antenna and an 8-ft dish reach comparable distances in different bands.** That is a fact about the ionosphere being a mirror and the atmosphere being a noise source, and it is the most useful single comparison the `signals/` area has produced.

### 8.2 The matched pair: the DF problem from both sides

**8.2.1** `[ANALYST ADD]` `IR-20261026-ONE-TIME-PADS` closes with the author announcing a **Doppler RDF unit**. This video explains why **NVIS defeats direction finding.**

| Report | Position |
|---|---|
| `ONE-TIME-PADS` | The message is unbreakable → attack the transmitter instead |
| **This report** | **NVIS makes the transmitter hard to locate** |

**Neither states the synthesis, so the report does:** *the counter to DF is a steep takeoff angle, low power, and short transmissions; the counter to that is a multi-site DF network that resolves elevation as well as bearing.* **The archive now contains both halves of a problem that neither source treats as one problem.**

### 8.3 The operational-security contradiction

**8.3.1** `[SOURCE CLAIM]` "When running your own net with your chums, you may want to find another frequency to avoid unwanted attention. For instance, those of you who follow S2 Underground will know that he runs his ghost net on 7.107 MHz."

**Assessment: the advice and the example contradict each other.** `[ANALYST ADD]`

| Element | Status |
|---|---|
| **The advice** | Correct — move off the calling frequency to avoid crowding and attention |
| **The example** | **Publishes the frequency of a network described as evading attention** |
| **The effect** | Anyone who wants to listen now knows where to listen; anyone who wants to jam now knows where to jam |

**This is the same failure as `IR-20261026-SATELLITE-GROUND-STATION`'s clear-text header, in a different medium: the operational security is defeated by the announcement, not by the adversary.** **Confidence: high.**

### 8.4 The archive's severed-term pattern, in a link

**8.4.1** `[ANALYST ADD]` An HF link has the standard loop:

```
   transmit ──► ionosphere ──► receive ──► decode ──► act?
       ▲                                                │
       └──────────── adjust / retransmit ───────────────┘
```

**The corrective term is the operator's ability to tell whether the link worked.** In this system it exists and it is good: **the waterfall shows the signal, the SNR readout quantifies it, and the heartbeat network maps who can hear whom.** That is a genuinely well-instrumented loop.

| Report | Corrective term | State |
|---|---|---|
| `ONE-TIME-PADS` | Receiver's accept? decision | **Severed — nothing to decide with** |
| **This report** | Operator's link-quality feedback | **Intact and instrumented** |

**8.4.2 — The contrast is the finding.** `[ANALYST ADD]` **The same author, on adjacent subjects, builds one system with no feedback and one with excellent feedback.** The difference is not the author's competence — it is that **a radio link is physical and observable, while a ciphertext is not.** The informational systems in this archive keep losing their corrective terms; the physical ones keep theirs. **That is a sharper version of the archive's central finding: the term is lost where the system cannot observe itself.**

---

## 9. INDICATORS AND WARNINGS

### 9.1 Assessing an HF preparedness guide

| ID | Indicator | Test |
|---|---|---|
| **H-1** | Is the D-layer absorption direction stated correctly? | **Failed** — inverted twice (§4.2.3) |
| **H-2** | Is NVIS described as a mode rather than an antenna? | **Passed — best insight in the video** |
| **H-3** | Are antenna heights given numerically? | **Failed** — the rule is given, the numbers are not (§3.1.3) |
| **H-4** | Is the weak-signal advantage quantified? | **Failed** — 17 dB from bandwidth, unstated (§5) |
| **H-5** | Is an SWR meter recommended? | **Failed** — highest-cost omission (§4.5.2) |
| **H-6** | Is RF exposure addressed for an indoor antenna? | **Failed** (§7.4) |
| **H-7** | Is the enforcement claim accurate? | **Failed — false** (§7.2) |
| **H-8** | Is the mode's security characterised honestly? | **Passed — "obscurity, don't count on it"** |
| **H-9** | Are the operator's own failures shown? | **Passed — test-PTT, poor propagation, no reply** |
| **H-10** | Are standard frequencies given? | **Passed** — 7.078 MHz, correctly |
| **H-11** | Is the clock requirement explained? | **Passed** |
| **H-12** | Is a licence recommended? | **Passed**, though undermined (§7.2.3) |

**9.1.1 — Twelve checks, six passes, and the failures cluster in two places:** the **propagation mechanism** and the **physical safety**. **The procedural content is reliable; the explanatory and safety content is not.** That is the characteristic profile of a practitioner teaching a workflow he has executed but not derived.

### 9.2 The meta-indicator

**9.2.1** The archive's standing test — *does the source state what would change its mind?* — adapts here to: **does the source give the number behind the advice?** The video gives formulas (468/f) and rules (λ/10) but not the derived quantities, so a reader cannot check whether their own installation is compliant. **A rule without a number cannot be applied to a new case**, which is exactly why the D-layer inversion is consequential: it removes the ability to generalise.

---

## 10. INTELLIGENCE GAPS AND KEY JUDGMENTS

### 10.1 Gaps

**10.1.1 — JS8Call's timing controls (priority: high).** ¶4.7.2 flags the "automatic time drift" feature as unverified. **Requirement:** the JS8Call documentation, to confirm whether the named control exists and what it does, since the video's setup instructions depend on it.

**10.1.2 — FCC enforcement record (priority: high).** §7.2 asserts that enforcement is routine and published. **Requirement:** the Enforcement Bureau's published actions for unlicensed HF operation, so the section is citable rather than asserted.

**10.1.3 — RF exposure procedure (priority: high).** §7.4 states the requirement and the mitigations without citation. **Requirement:** the applicable FCC procedure and exemption thresholds, and the amateur RF-exposure rules, so the section is actionable.

**10.1.4 — The S2 Underground net (priority: low).** ¶8.3 treats the 7.107 MHz claim as unverified. **Requirement:** confirm or drop; the operational-security point stands either way.

**10.1.5 — NVIS frequency dependence (priority: moderate).** §4.3 gives the height criterion but not the **critical frequency** above which NVIS fails. **Requirement:** the relation between the critical frequency, the solar flux, and the highest NVIS-usable band, since that is what determines whether NVIS works on a given day.

**10.1.6 — JS8Call bandwidth (priority: moderate).** §5 uses ~50 Hz. **Requirement:** the exact occupied bandwidth, since the 17 dB figure scales directly with it.

### 10.2 Key judgments

| ID | Judgment | Confidence |
|---|---|---|
| **KJ-1** | The best technical statement in the archive is here: **NVIS is a propagation mode, not an antenna type.** | **High** |
| **KJ-2** | **The D-layer explanation is inverted twice**, and then contradicted by correct practical advice — so the reader can follow the instruction but cannot generalise it. | **High** |
| **KJ-3** | **"Weak signal mode" is a bandwidth claim worth 17 dB** — the number the video never gives, and the reason 10 W reaches 400 miles. | **High** |
| **KJ-4** | HF is **noise-limited, not sensitivity-limited**; the remedies are power, antenna, and bandwidth, and bandwidth is cheapest. | **High** |
| **KJ-5** | The attic dipole sits **inside the NVIS height window by construction** (2.5–3 m vs a 4.24 m ceiling), which better explains the 400-mile contact than the source's "multiple hops." | **Moderate-high** |
| **KJ-6** | **The FCC enforcement claim is false** and contradicts the licensing advice three sentences later. | **High** |
| **KJ-7** | The **missing SWR meter** is the gear omission with the highest expected cost — a mismatched antenna can destroy a QRP final. | **High** |
| **KJ-8** | **100 W into an attic dipole above occupied space requires an RF-exposure evaluation** and the video does not mention exposure. | **High** (omission); **Moderate** (magnitude) |
| **KJ-9** | Publishing a "ghost net" frequency defeats the operational security it is meant to have — the same failure as the OTP video's clear-text header. | **High** |
| **KJ-10** | The two `signals/` reports are a **matched pair**: geometry-dominated versus noise-dominated, and the two effects nearly cancel (82 dB less path loss, 40–50 dB more noise). | **High** |
| **KJ-11** | The archive now holds **both halves of the direction-finding problem** — the RDF purchase and the NVIS counter — and neither source treats them as one problem. | **High** |
| **KJ-12** | The severed-corrective-term pattern is **sharper than previously stated**: the term is lost where the system cannot observe itself. A radio link is instrumented; a ciphertext is not. | **Moderate-high** |

---

## APPENDIX A — GLOSSARY

| Term | Definition |
|---|---|
| **D layer** | Daytime absorptive layer at 60–90 km; absorption ∝ N_e/f², so low frequencies suffer most. |
| **F2 layer** | The main refracting layer for long-haul HF; 220–500 km. |
| **Ground wave** | Surface-hugging propagation; tens of km on 40 m. |
| **JS8Call** | Weak-signal keyboard mode derived from FT8; ~50 Hz, 15-second frames, store-and-forward relay. |
| **Kp index** | Planetary geomagnetic activity index, 0–9. |
| **Maidenhead locator** | Grid-square position code; 6 characters ≈ 6 × 4 km. |
| **MUF / LUF** | Maximum / lowest usable frequency for a given path. |
| **NVIS** | Near-vertical incidence skywave; steep-angle refraction filling the skip zone. |
| **PACE plan** | Primary / Alternate / Contingency / Emergency. |
| **QRP** | Low-power operation; conventionally ≤5 W CW, ≤10 W SSB. |
| **Skip zone** | The annulus too far for ground wave and too near for low-angle skywave. |
| **SWR** | Standing wave ratio; a mismatch metric that also predicts final-stage stress. |
| **T/R period** | The 15-second transmit/receive slot structure inherited from FT8. |

---

## APPENDIX B — CHRONOLOGY

| Year | Event | Relevance |
|---|---|---|
| 1901 | Marconi, transatlantic | Skywave demonstrated before it was understood |
| 1920s | Ionospheric sounding | The layers identified |
| 1925 | Breit & Tuve; Appleton | Ionosphere measured directly |
| 1940s–80s | Numbers stations | The NVIS/DF asymmetry exploited |
| 2017 | FT8 released | The weak-signal lineage |
| 2019 | JS8Call | Keyboard messaging on the FT8 physical layer |
| 2024–25 | Solar Cycle 25 maximum | Aurora to Alabama; degraded HF |
| 2020s | Meshtastic, LoRa mesh | The local-layer alternative |
| 2020s | Starlink geopolitics | The single-operator dependency argument |

---

## APPENDIX C — CLAIM LEDGER

| # | Claim | Class | Status | Assessment |
|---|---|---|---|---|
| C-1 | VHF/UHF handheld range 2–3 miles | Fact | Verified | Height-limited |
| C-2 | A repeater provides power and elevation, not networking | Fact | **Verified — good correction** | — |
| C-3 | Meshtastic nodes relay; ~1–2 miles | Fact | Verified | Density, not dispersion |
| C-4 | QRP = under 10 W | Definition | Approximately correct | ≤5 W CW, ≤10 W SSB |
| C-5 | (tr)uSDX: 5 W USB, 10 W with pack | Fact | Plausible | — |
| C-6 | Aluminum ~60% as conductive as copper | Fact | Verified | HV-line rationale correct |
| C-7 | **A balun matches antenna impedance to coax** | Engineering | **Imprecise** | 1:1 suppresses common-mode current |
| C-8 | Dipole length = 468/f(MHz) feet | Formula | **Verified** | 66.1 ft on 40 m |
| C-9 | **D layer absorbs higher frequencies** | Physics | **INVERTED** | Absorbs low frequencies |
| C-10 | **D layer passes lower frequencies** | Physics | **INVERTED** | Passes high frequencies |
| C-11 | 40 m survives D absorption | Fact | **Verified** — contradicts C-9/C-10 | ¶4.2.4 |
| C-12 | Skip zone between ground wave and skywave | Physics | Verified | — |
| C-13 | NVIS: 60–90° elevation fills the skip zone | Physics | Verified | — |
| C-14 | NVIS clears terrain | Physics | Verified | Steep path |
| C-15 | Skywave height ≥ λ/2; NVIS ≤ λ/10 | Engineering | **Verified** | 69.5 ft vs 13.9 ft |
| C-16 | Ground plane reflects energy upward | Engineering | Correct in effect | Loosely described |
| C-17 | **NVIS is a propagation mode, not an antenna** | Physics | **Verified — best insight** | ¶4.3.1 |
| C-18 | NVIS is hard to direction-find | Physics | Verified | §8.2 |
| C-19 | Solar flux, 11-year cycle, storms degrade HF | Physics | Verified | — |
| C-20 | "K factor" | Terminology | Minor error | Kp index |
| C-21 | Attic materials attenuate; nails detune | Engineering | **Verified** | Arcing risk unmentioned |
| C-22 | 400 miles on 10 W attic dipole | Measurement | Plausible | −1 / −14 dB reported |
| C-23 | Licence test ~$20–30, valid 10 years | Fact | Verified | US |
| C-24 | **"The FCC doesn't care, they never find you"** | Legal | **FALSE** | §7.2 |
| C-25 | USB = upper sideband; digital uses USB everywhere | Fact | **Verified and useful** | — |
| C-26 | RTS keying instead of CAT | Engineering | Verified | Right for this rig |
| C-27 | JS8Call needs an accurate clock | Fact | Verified | 15 s frames |
| C-28 | "Automatic time drift" control | Software | **Unverified** | ¶4.7.2 |
| C-29 | JS8Call is unencrypted; obscurity only | Security | **Verified and honest** | §4.7.3 |
| C-30 | Relayed messages pass through a third station | Security | Verified | Relay reads the message |
| C-31 | 7.078 MHz is the 40 m JS8 frequency | Fact | Verified | — |
| C-32 | **17 dB from 2,500 Hz → 50 Hz** | Computed | **Not in source** | §5 — the report's main addition |
| C-33 | **Attic height is inside the NVIS window** | Computed | **Not in source** | ¶4.3.3 |
| C-34 | **SWR meter absent from the gear list** | Omission | **Verified** | ¶4.5.2 |
| C-35 | **RF exposure not addressed** | Omission | **Verified** | §7.4 |

---

## APPENDIX D — VERBATIM EXTRACTS

**D-1** [2:29] "I used to think when I first got into amateur radio that repeater networks were like cell networks... But that's not how they work. It's one repeater that boosts your power and your signal by an elevation advantage. So that's all a repeater does for you."

**D-2** [9:09] "It matters how long each leg of the dipole is in order to be resonant... It should just be 468 divided by the frequency that you're using in megahertz. And that will get you the length in feet."

**D-3** [11:53] "It's not encrypted, but it's encoded into its own digital protocol. Anybody who's listening who is decoding on JS8 will be able to read your messages in the clear, but it adds a little bit of security by obscurity — but don't count on it."

**D-4** [15:18] "This D layer here, it absorbs lower frequency — sorry, yeah — higher frequency, lower wavelength — and it allows the lower frequency, higher wavelength to pass through and get refracted by these higher ionosphere levels."

**D-5** [15:55] "There is a skip zone. This is a dead zone where you can't reach anybody in this area, because by ground wave it's too far and by skywave, just based on the trigonometry, you can't bend it down at that acute of an angle."

**D-6** [16:25] "Near vertical incidence skywave. It's a type of skywave propagation where the takeoff angle is basically straight up and then we are refracted back down."

**D-7** [18:06] "For normal skywave, you'll want a height above the ground of at least half of a wavelength. But for NVIS, that should be less than one-tenth wavelength."

**D-8** [19:00] "NVIS is a type of propagation, not a type of antenna. And that means that even though you have it set up in a sort of NVIS configuration... you may still be getting a component of your transmission that is propagating regular skywave."

**D-9** [19:33] "NVIS propagation is very difficult to radio direction find because the signal... it's coming from the sky. It's really hard to get a precise bearing on the transmitter location. That's why spy stations historically were able to get away with using these discrete numbers stations for so long."

**D-10** [23:25] "The FCC doesn't really care. They never find you. They never go after you if you're just doodling away on HF transmitting. They only go after the really bad ones."

**D-11** [24:04] "Honestly, the best thing to do is get the license, because these people can be your allies... So, get your license. It's not that hard."

**D-12** [25:40] "You want USB. This is not referring to universal serial bus. This is referring to upper sideband."

**D-13** [28:25] "They have to be in bursts between the horizontal lines, because that allows the software to decode it accurately. This means that everybody's JS8Call has to be running on an accurate clock."

**D-14** [30:11] "We got him at −21 dB SNR, but he heard whoever this is at minus 09 dB."

**D-15** [37:14] "On 40 m, that's 7.078 MHz. When running your own net with your chums, you may want to find another frequency to avoid unwanted attention. For instance, those of you who follow S2 Underground will know that he runs his ghost net on 7.107 MHz."

**D-16** [37:50] "The contact I made just before this clip appears to be located in Ohio, about 400 miles away from me. Not bad for a 10 watt rig and an attic antenna. He heard me at −1 SNR and I heard him at minus 14. Weak signal modes are where it's at."

**D-17** [38:12] "This also goes to show that NVIS is not a hard and fast thing. My contact... was 400 miles away... That could be either two things. One is that there were multiple bounces off the ionosphere... Or the other option is maybe it wasn't an NVIS propagation."

---

## APPENDIX E — TERMINOLOGY RECONCILIATION

| Source usage | Correct / preferred | Note |
|---|---|---|
| "True SDX" | **(tr)uSDX** | — |
| "Yau rig" / "YESU" | **Yaesu FT-891** | — |
| "Bow Fang" | **Baofeng** | — |
| "Mishtastic" | **Meshtastic** | — |
| "envis" / "NVIZ" | **NVIS** | — |
| "balon" | **balun** | 1:1 suppresses common-mode current |
| "K factor" | **Kp index** | — |
| "the D layer absorbs higher frequency" | **absorbs low frequencies; passes high** | The central inversion |
| "30° cone of vertical" | **60–90° elevation** | Same thing, clearer form |
| "under 10 watts" (QRP) | **≤5 W CW, ≤10 W SSB** | Mode-dependent |
| "weak signal mode" | **narrowband mode — 17 dB from bandwidth** | §5 |
| "ghost net" | **a net whose frequency is published** | §8.3 |
| "automatic time drift" | **unverified feature; DT readout is the standard** | ¶4.7.2 |

---

## APPENDIX F — ESTIMATIVE LEXICON

**Confidence:** High (verified against a primary source or standard reference) · Moderate (credible single stream, or sound reasoning with an inferential gap) · Low (fragmented or contested).

**Likelihood:** Almost no chance 01–05% · Very unlikely 05–20% · Unlikely 20–40% · Roughly even 40–60% · Likely 55–85% · Very likely 80–95% · Almost certain 95–99%.

**Technical status:** *Verified* · *Computed* (derived in this report) · *Imprecise* (right direction, details wrong) · *Inverted* (the mechanism stated as its own opposite) · *Omitted* (absent and consequential) · *Error*.

---

## APPENDIX G — REVISION LOG

| Rev | Date | Change |
|---|---|---|
| 1.0 | 2026-10-26 | Initial issue. Source: `transcript.md` (ASR, 42:06). Bandwidth arithmetic computed (§5); NVIS height window and antenna geometry checked against the 468/f formula (§3.1.3); D-layer inversion recorded (§4.2.3). |

**Known deficiencies:**

1. JS8Call's timing controls unverified (§10.1.1).
2. FCC enforcement record asserted, not cited (§10.1.2).
3. RF-exposure procedure not quoted (§10.1.3). **Highest priority** — §7.4 is a safety claim.
4. NVIS critical-frequency relation absent (§10.1.5); the report says NVIS works but not when it fails.
5. JS8Call occupied bandwidth approximate (§10.1.6); the 17 dB figure scales directly with it.

---

```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

*End of report.*
