```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

# LEARNING PATHS FOR SDR AND SATELLITE RECEPTION
## The Affordance to Break Things, and a Source That Dates Itself

| Field | Value |
|---|---|
| **Report No.** | IR-20261026-GETTING-STARTED-SDR |
| **DTG** | 260727ZOCT26 |
| **Classification** | UNCLASSIFIED // OPEN SOURCE |
| **Originator** | Analyst (independent) |
| **Source** | `transcript.md` (same folder) — ASR transcript, 27:32 runtime, unchaptered |
| **Source path** | `notes/signals/videos/2026-10-25-getting-started-sdr/transcript.md` |
| **Source type** | OSINT — instructional/meta video; practitioner answering a recurring audience question |
| **Reliability** | **A3** — completely reliable, possibly true. See ¶2.2 for why the second digit is low |
| **Subject** | Entry paths into SDR, amateur satellites, and radio; resources; scavenging; pedagogy |
| **Distribution** | Unlimited |
| **Handling** | Analytic exercise. Includes a safety section (§7) on a hazard the source omits. |

**Handling caveat.** `[SOURCE CLAIM]` marks reproduction without endorsement; `[ANALYST ADD]` marks material from outside the source. **This source contains almost no quantitative claims** — the report's analytic work is therefore about method and about what the source leaves out, not about checking arithmetic.

---

## TABLE OF CONTENTS

- **1. BLUF**
- **2. Source Assessment**
- **3. Framework** — the affordance to break things · the dependency ordering · why this genre self-dates
- **4. Technical Analysis** — the hardware · the satellites · the downlink distinction · the repeater · the resources
- **5. What the Path Omits** — instrumentation · the safety hazard · the search advice
- **6. Corrections**
- **7. Safety**
- **8. Cross-Archive Links** — the citation chain · the missing instrument
- **9. Indicators and Warnings**
- **10. Intelligence Gaps and Key Judgments**
- **Appendices A–G**

---

## 1. BLUF — BOTTOM LINE UP FRONT

**1.1** This is the archive's first **meta-source** — a video about *how to learn* rather than about a subject — and it is the hardest to grade, because its claims are about method rather than fact. Assessed on method it is **excellent**; assessed on specificity it is **thin**; assessed on durability it is **already decaying**. The composite is **A3**: highly trustworthy as testimony, low in verifiable content. **Confidence: high.**

**1.2 — Its central pedagogical claim is correct, non-obvious, and generalises beyond the hobby.** `[SOURCE CLAIM]` Start with "the cheapest, crummiest, most broken thing," because *"you are not afraid to push the boundaries."*

**Formalised** `[ANALYST ADD]`:

```
learning  ∝  exploration
exploration  ∝  tolerated failure
tolerated failure  ∝  1 / (cost of failure − learner's risk threshold)
```

**So cheap equipment is not a budget compromise — it is the pedagogically optimal choice**, because it lowers the cost of failure below the threshold at which exploration stops. That is why simulators exist, why flight training uses them, and why the ground-station builder in `IR-20261026-SATELLITE-GROUND-STATION` bought a **$999 surplus microscope** rather than a working one. **Confidence: high.**

**1.3 — The path is correctly dependency-ordered, and the ordering is the useful part.** Junk you can break → cheap SDR → build your own antenna → easy satellite → licence. **Each step requires only the previous one and nothing else**, which is why the path works for a beginner with no money. Most beginner guides violate this by recommending a transceiver before the learner has ever demodulated anything. **Confidence: high.**

**1.4 — The source recommends two satellites without stating which downlink, and that omission determines the whole equipment budget.** `[SOURCE CLAIM]` Start with "Meteor M2-3 and M2-4."

`[ANALYST ADD]` Meteor-M carries **two** downlinks:

| Downlink | Frequency | Antenna needed | Cost |
|---|---|---|---|
| **LRIT** | **137.9 MHz** | V-dipole, **no tracking** | ~$30 |
| **HRPT** | **1700 MHz** | Dish or good helix **plus rotator** | ~$500+ |

**The beginner path is 137 MHz and the source never says so.** A reader who assumes HRPT will conclude the hobby is broken when a $30 antenna receives nothing. **Confidence: high.**

**1.5 — The path teaches acquisition and never teaches measurement.** `[ANALYST ADD]` There is no SWR meter, no signal source, no way to verify that anything is working. **This is the same omission as in `IR-20261026-FIBER-OPTICS`, where the physics was settled in 1966 and the *proof* took three more years of instrument development.** A learner with no measurement capability cannot distinguish "my antenna is bad" from "the satellite is dead" from "the software is misconfigured" — and all three are common. **Confidence: high.**

**1.6 — The central practice has a lethal hazard the source never mentions.** `[SOURCE CLAIM]` Scavenge broken electronics; take apart VCRs; save everything for parts.

`[ANALYST ADD]` **Scavenged consumer electronics contain stored charge that can kill.** The specific offenders are **CRT televisions and monitors** (the tube and its flyback supply hold hundreds of volts at dangerous current for hours to days) and **microwave ovens** (the high-voltage capacitor). The "save it for parts" ethos leads directly to both. **The video recommends the practice and omits the hazard entirely.** **Confidence: high.**

**1.7 — This is the archive's first explicitly self-dating source, and it says so.** `[SOURCE CLAIM]` "A lot of these satellites are kind of ephemeral... they might not be around by the time you see this video."

**Assessment: correct, and it is the honest thing to say.** `[ANALYST ADD]` But it understates the problem: the decay is not only in the satellites. **The half-life of a beginner guide in this field is roughly two years** — the spacecraft die, the SDR models are superseded, the software breaks, and the surplus dries up. **A tutorial that does not date itself is therefore actively misleading**, and this one dates itself in one sentence and nowhere else. **Confidence: high.**

---

## 2. SOURCE ASSESSMENT

### 2.1 Provenance

**2.1.1** A 27-minute, 32-second video by `@saveitforparts`, URL `https://www.youtube.com/watch?v=hLpP5KEsHbc`. Local capture: `transcript.md`, same folder. Format: direct-to-camera answers to recurring audience questions, with no demonstrations.

**2.1.2 — Position in the archive.** `[ANALYST ADD]` This is the **named inspiration** for `IR-20261026-SATELLITE-GROUND-STATION`: that video opens with *"I've been watching a lot of Save It for Parts on YouTube... one of the things he does a lot of is satellite reception stuff."* **The archive therefore now contains both ends of a citation chain** (§8.1).

**2.1.3 — Structure**, inferred:

| Phase | Content | Approx. span |
|---|---|---|
| 1 | Attitude; expect failure | 0:00–1:40 |
| 2 | Books and websites as resources | 1:40–4:40 |
| 3 | Clubs, maker spaces, universities | 4:40–6:30 |
| 4 | The author's background; off-grid Alaska | 6:30–10:30 |
| 5 | Where to get parts with no money | 10:30–16:10 |
| 6 | The concrete recommendations | 16:10–23:50 |
| 7 | What to study; closing | 23:50–27:32 |

### 2.2 Reliability grading

| Axis | Grade | Basis |
|---|---|---|
| **Source reliability** | **A — Completely reliable** | First-person testimony from a practitioner with a decade of published work; volunteers his own limits ("I am terrible at math," "I don't have professional-level competency"); recommends the free path over the expensive one; no product sold |
| **Information credibility** | **3 — Possibly true** | Not because the source is doubtful, but because **most claims are about method and preference**, which are not truth-apt in the usual sense; and the specific recommendations are time-sensitive |
| **Composite** | **A3** | Trustworthy testimony, low verifiable content, short shelf life |

**2.2.1 — Why the second digit is deliberately low, and it is not a criticism.** `[ANALYST ADD]` The standard scale grades *information credibility*. Most of this video's content — "learn by doing," "join a club," "I grew up off-grid" — is either preference or autobiography. **There is nothing to check and nothing to falsify**, which is a property of the genre rather than a defect of the source. **The correct response is to grade the *method* on soundness rather than the *claims* on accuracy**, which is what §3 does.

**2.2.2 — What raises the grade to A.** Four things:
1. **He recommends the cheap path when the expensive one would be easier to justify.** "I would absolutely not recommend dropping a bunch of money on a new hobby."
2. **He volunteers incompetence.** "I am not good at programming. I am terrible at math... I do not have professional-level competency in most of the things in my degree program."
3. **He dates his own advice.** "They might not be around by the time you see this video."
4. **He names the social cost honestly.** Grumpy older operators who "will freak out if you say the Baofeng word."

### 2.3 Conflict of interest

**2.3.1** No sponsor, no affiliate links, no product. He links his own website, Discord, and prior videos — self-promotion of the ordinary kind, not a commercial interest in any specific purchase.

**2.3.2 — The relevant bias is subtler and worth naming.** `[ANALYST ADD]` The video is **an origin story told by someone whose channel is the origin story.** "How did I learn this" is answered by "here is how I learned this," which is a sample of one. The method generalises (§1.2), but the *specific* resource list is a description of one person's path through one country's surplus economy. **He flags this** — "everyone's situation is a little bit different and what works for me might not necessarily work for you" — which is the correct hedge and it is placed at the top.

### 2.4 Transcription integrity

| As transcribed | Correct form | Note |
|---|---|---|
| "software to find radio" / "software definined" | **software-defined radio (SDR)** | Corrupts repeatedly |
| "rstr.com" / "RTLSTR" | **rtl-sdr.com** | The blog |
| "bow fang" | **Baofeng** | — |
| "hamstats" | **ham sats** | Amateur satellites |
| "Noah and meteor" | **NOAA and Meteor** | — |
| "Meteor M23 and M24" | **Meteor-M №2-3 and №2-4** | §4.2 |
| "ARISS" | **ARISS** | Correct |
| "UF up in Fairbanks" / "UAF" | **UAF** — University of Alaska Fairbanks | — |
| "Axeman Surplus" | **Ax-Man Surplus** | Twin Cities chain |
| "hack a day" | **Hackaday** | — |
| "after CO" | **after COVID** | — |
| "Zenob" | *(not present)* | — |
| "plenarian" | *(not present)* | — |

**2.4.1** The SDR corruption is the one that matters: "software to find radio" is not recoverable by a reader unfamiliar with the term, and it appears at the point where the video names its own subject.

### 2.5 Verification status

| Claim | Locus | Status |
|---|---|---|
| RTL-SDR Blog V3 with antenna kit is a good beginner SDR | 19:15 | **Verified** — the standard recommendation |
| Building your own antennas teaches frequency and wavelength | 19:28 | **Verified** — the best single pedagogical suggestion in the video |
| Meteor-M2-3 and M2-4 are easy to hear | 19:39 | **Verified for LRIT at 137 MHz**; **wrong implication for HRPT** (§4.3) |
| Russian satellites "catch on fire a lot"; US ones get shut down | 19:49 | **Directionally fair**; the characterisation is political, the technical point is that spacecraft fail |
| Ham satellites are easy | 20:22 | **Verified** |
| ISS repeater is easy to hear from most of the world | 20:30 | **Verified** — but the difficulty is Doppler, unmentioned (§4.4) |
| No licence needed to listen | 20:49 | **Verified** in most jurisdictions |
| Technician licence permits transmitting through the ISS | 20:52 | **Verified** — Technician has 2 m/70 cm privileges |
| 6–7 ft C-band dishes are often free for removal | 23:27 | **Verified** — and this is exactly what the ground-station video did |
| 3D printers were unclaimed at universities around 2004 | 5:04 | **Plausible** |
| "AI is polluting the internet with BS answers" | 2:43 | **Verified in substance** (§5.3) |
| "Add `-AI` to a search to filter it out" | 2:48 | **FALSE as a method** (§5.3) |
| Linux revives old computers | 18:50 | **Verified** |
| Dumpster-diving and surplus are viable in the US | 11:19 | **Verified in outline** |

---

## 3. FRAMEWORK

### 3.1 The affordance to break things

**3.1.1 — The claim.** `[SOURCE CLAIM]` "Find some junk to experiment with. Find something that you are not afraid to break or misuse... it can be the cheapest, crummiest, most broken thing. And that will help you learn the most, because you are not afraid to push the boundaries, to go past the things that it says do not do in the manual."

**3.1.2 — Why this is right, and why it is not merely a budget argument.** `[ANALYST ADD]` The mechanism is that **exploration is bounded by the cost of failure**, and the cost of failure is set relative to the learner's risk tolerance rather than in absolute currency:

```
  equipment value ↑   →   perceived cost of damage ↑
                      →   permitted exploration ↓
                      →   learning ↓
```

**A $2,000 radio in the hands of a beginner teaches less than a $30 one**, because the beginner will not open it, will not connect the wrong cable, and will not attempt the thing the manual forbids. **The cheap device is not a compromise; it is the correct instrument**, and the correct instrument is the one whose destruction the learner can afford.

**3.1.3 — Why this generalises, and the archive already contains two more instances.** `[ANALYST ADD]`

| Case | The cheap instrument | What it enabled |
|---|---|---|
| **This source** | A "$30" RTL-SDR from eBay | Trying every mode without fear |
| `IR-20261026-SATELLITE-GROUND-STATION` | A **$999** surplus microscope-grade dish, sold as scrap | Rebuilding the drive three times |
| `IR-20261026-FIBER-OPTICS` | Kao's **sub-30 cm** samples | Inventing an instrument rather than buying one |

**In all three, the enabling property is the same: the object was cheap enough to destroy.** That is the transferable principle, and none of the three sources states it as a principle.

**3.1.4 — The limit of the principle.** `[ANALYST ADD]` It fails where **the cost of failure is not borne by the learner** — mains electricity, mains-powered equipment, RF into a shared antenna, or anything involving a vehicle. **A beginner following this advice into a scavenged microwave oven is applying a principle outside its domain of validity** (§7.2). **The principle is sound and its boundary is physical safety**, which the source does not draw.

### 3.2 The dependency ordering

**3.2.1** `[ANALYST ADD]` The recommended path is a chain in which each step requires only its predecessor:

```
1. Junk you can break        (cost: $0)
2. Cheap SDR + antenna kit   (cost: ~$40)
3. Build your own antenna    (cost: ~$10, teaches wavelength)
4. One easy satellite        (cost: $0, teaches the workflow)
5. Licence                   (cost: ~$30, unlocks transmit)
```

**3.2.2 — Why the ordering is the valuable part.** `[ANALYST ADD]` Most beginner guides invert it — recommending a transceiver before the learner has demodulated anything — which produces a person holding an expensive device they cannot use. **The correct ordering principle is that each step should be *self-verifying*: you know it worked because you heard something.** Steps 1–4 all satisfy this; step 5 does not, which is why it comes last and why it is framed as a social rather than a technical step.

**3.2.3 — Where the ordering is wrong.** `[ANALYST ADD]` **Step 3 is misplaced.** Antenna construction is the one step that *requires* measurement to be instructive — without an SWR meter or a nanoVNA, a learner building a dipole cannot tell whether it worked. **It belongs after instrumentation, not before** (§5.1).

### 3.3 Why this genre self-dates

**3.3.1** `[SOURCE CLAIM]` "These satellites are kind of ephemeral... they might not be around by the time you see this video."

**3.3.2 — The generalisation.** `[ANALYST ADD]` The decay is broader than spacecraft:

| Element | Half-life | Why |
|---|---|---|
| **Spacecraft** | 2–10 years | Failure, deorbit, replacement |
| **SDR models** | ~3 years | Chip availability; clones appear |
| **Software** | ~2 years | Dependencies break; maintainers stop |
| **Surplus supply** | ~5 years | Warehouses empty; auctions move online |
| **Licence question pools** | 4 years | US pools are revised on a fixed cycle |

**So a beginner guide is a perishable good with a shelf life of about two years**, and its *hardware recommendations* decay faster than its *method*.

**3.3.3 — The correct form for the genre.** `[ANALYST ADD]` A guide of this kind should carry **three dates**: when it was recorded, the revision of each software it names, and the epoch of its orbital data. This one carries none, and says "as I film this" once. **That single hedge is the most durable sentence in the video**, because it is the only place where the reader is told that time has passed.

---

## 4. TECHNICAL ANALYSIS

### 4.1 The hardware

**4.1.1 — The recommendation.** `[SOURCE CLAIM]` The RTL-SDR Blog V3 with the antenna kit.

**Assessment: correct, and it is the standard answer for good reasons.** `[ANALYST ADD]` The device's actual specifications, which the video does not state and which determine what a beginner can and cannot do:

| Parameter | Value | Consequence |
|---|---|---|
| ADC | **8-bit** | ~48 dB of dynamic range — **strong signals block weak ones** |
| Sample rate | ~2.4 MSPS usable | ~2.4 MHz of visible spectrum |
| Tuning range | ~24 MHz – 1.7 GHz | **No HF without an upconverter** |
| Transmit | **None** | Receive only |
| TCXO (V3) | ~1 ppm | Adequate for most modes; marginal for some |

**4.1.2 — The two limits that will confuse a beginner.** `[ANALYST ADD]`

1. **No HF.** A learner who reads that HF is where long-distance communication happens will try to tune 7 MHz, hear nothing, and conclude the device is faulty. **The remedy is a direct-sampling modification or an upconverter**, neither of which is mentioned.
2. **8-bit dynamic range.** In an urban environment the FM broadcast band overloads the front end and images appear across the spectrum. **The remedy is a band-stop filter or reduced gain**, and the symptom is universally mistaken for a broken receiver.

**Both are the most common beginner failures and neither is in the source.** **Confidence: high.**

### 4.2 The satellites

**4.2.1 — The recommendation.** `[SOURCE CLAIM]` Meteor-M2-3 and M2-4.

**Assessment: correct as a class, with a caveat the source half-anticipates.** `[ANALYST ADD]`

| Spacecraft | Status as of this report | Note |
|---|---|---|
| **Meteor-M №2-3** | Launched 2019; **degraded** after a 2022 impact | Transmissions intermittent |
| **Meteor-M №2-4** | Launched Feb 2024 | The working example |

**The source's own caveat covers this** — "they might not be around by the time you see this video" — and that is exactly the right hedge. **It is also the reason §3.3 exists.**

### 4.3 The downlink distinction — the omission that sets the budget

**4.3.1** `[ANALYST ADD]` Meteor-M transmits **two** products, and the choice between them is the entire equipment decision:

| Product | Frequency | Bandwidth | Antenna | Tracking | Cost |
|---|---|---|---|---|---|
| **LRIT** | **137.9 MHz** | ~20 kHz | **V-dipole, fixed** | **None** | **~$30** |
| **HRPT** | **1700 MHz** | ~3 MHz | Dish or helix | **Yes — rotator** | **$500+** |

**4.3.2 — Why this is the most useful correction in the report.** `[SOURCE CLAIM]` The source names the satellites and never names the frequency.

**Consequence:** a reader with the recommended $40 kit can receive LRIT **today**, with no rotator and no tracking, from a fixed antenna on a windowsill. A reader who assumes HRPT will spend months concluding that the hobby is broken. **The difference between a working path and an abandoned one is one number the video omits.** **Confidence: high.**

**4.3.3 — And the LRIT product is genuinely enough.** `[ANALYST ADD]` LRIT carries a reduced-resolution image at ~4 km/pixel with a visible and infrared channel. **That is a real weather image of the whole pass**, and it is the correct first success: it is achievable, it is visible, and it teaches the workflow (predict → point → record → decode) that everything else reuses.

### 4.4 The ISS repeater, and the difficulty the source skips

**4.4.1** `[SOURCE CLAIM]` The ISS "has a very powerful repeater, easy to hear from most of the world."

**Assessment: correct, and the difficulty is not signal strength.** `[ANALYST ADD]` The ISS cross-band repeater runs roughly **5 W**, and a handheld with a modest antenna hears it easily on a good pass. **The obstacle is Doppler shift**, which the source does not mention and which is why beginners fail:

| Band | Doppler at 7.4 km/s radial | Practical tuning step |
|---|---|---|
| **2 m uplink** (145.99 MHz) | **~3.6 kHz** | Retune in steps through the pass |
| **70 cm downlink** (437.80 MHz) | **~10.8 kHz** | Retune continuously; FM capture makes it unforgiving |

**A pass lasts about ten minutes and the Doppler curve is steepest at closest approach** — exactly when the signal is strongest and the operator is most excited. **A beginner who does not retune loses the contact in the middle of it and concludes the repeater is broken.** That is the actual failure mode, and one sentence in the video would have prevented it. **Confidence: high.**

### 4.5 The resources

**4.5.1 — Assessed.** `[ANALYST ADD]`

| Resource | Assessment |
|---|---|
| **ARRL study guide** (current edition) | **Correct** for the licence; teaches electronics incidentally |
| **rtl-sdr.com blog** | **Correct** — the canonical beginner archive, and the source of most tutorials |
| **Hackaday** | **Correct** — project aggregation |
| **Ham clubs / maker spaces** | **Correct**, and the reason is social, not technical (§4.5.2) |
| **University surplus and libraries** | **Correct**, and the most under-used item on the list |
| **Dumpsters, kerbside, estate sales** | **Correct for the US**, and heavily jurisdiction-dependent |
| **Linux on old hardware** | **Correct** — an SDR needs a USB port and little else |

**4.5.2 — The club recommendation is the strongest non-technical advice in the video, and for a reason he states almost in passing.** `[SOURCE CLAIM]` Older operators "will be willing to give you stuff or advice, or at least tell you where to find stuff."

**Assessment: correct, and the mechanism is access to tacit knowledge.** `[ANALYST ADD]` A club provides three things no document can:
- **equipment you can borrow** before buying;
- **a working station you can compare against** — the fastest way to diagnose "is it me or is it broken";
- **someone who has made your exact mistake**, which is the only reliable cure for the specific confusion you are in.

**This is the video's implicit argument against self-teaching**, and it is a good one: the method is self-directed, but the *feedback* is social.

### 4.6 The "attentional priming" observation

**4.6.1** `[SOURCE CLAIM]` "Once you get into this hobby, you will start noticing things... it's kind of like once you own a Honda Civic, you start seeing Honda Civics everywhere."

**Assessment: correct, and it is the mechanism that makes scavenging work.** `[ANALYST ADD]` The phenomenon is attentional priming — a perceptual set that raises the salience of a category once it is task-relevant. **The important consequence is economic: the resource was always there and the perception changed.** Free C-band dishes have been sitting in yards for forty years; they become visible only after the learner knows what they are for.

**4.6.2 — And it explains the archive's most concrete overlap.** `[ANALYST ADD]` `IR-20261026-SATELLITE-GROUND-STATION` opens with an 8-ft dish bought on Facebook Marketplace for a low price. **This video is where that idea came from** — "if you can get like a six or seven foot satellite dish, you can do all kinds of silly things with that, and you can often find those for free." See §8.1.

---

## 5. WHAT THE PATH OMITS

### 5.1 Instrumentation

**5.1.1 — The gap.** `[ANALYST ADD]` The recommended path contains **no measuring instrument**. Not an SWR meter, not a signal generator, not a frequency counter, not even a known-good reference signal.

**5.1.2 — Why this is the deepest omission, and the archive has already established the principle.** `[ANALYST ADD]` From `IR-20261026-FIBER-OPTICS` §4.5: **measurement capability was the bottleneck, not the physics.** Kao's result was settled theoretically in 1966 and *proved* in 1969, and the three intervening years were spent building an instrument.

**The beginner's version of the same problem:**

| Symptom | Possible causes | Can the learner distinguish them? |
|---|---|---|
| Nothing received | Antenna bad / satellite dead / software misconfigured / wrong frequency / wrong gain | **No** |
| Weak signal | Antenna bad / too much gain (overload) / wrong polarisation | **No** |
| Distorted decode | Clock drift / wrong mode / interference | **No** |

**Five causes, one symptom, no discriminator.** A $20 SWR meter or a $50 nanoVNA collapses several of these immediately, and **it is the cheapest diagnostic purchase in the hobby.**

**5.1.3 — The correct insertion point.** `[ANALYST ADD]` Instrumentation belongs at **step 3** of the ordering (§3.2.1), *before* building antennas — because building an antenna without a way to measure it teaches only that antennas are frustrating.

### 5.2 The safety hazard

See §7.2. **The most serious omission in the source**, and it follows directly from its central practice.

### 5.3 The search advice

**5.3.1 — The claim.** `[SOURCE CLAIM]` "AI is coming along and polluting the internet with BS answers, but if you can do a search and like do a minus AI at the end, or use some other way to filter out the AI nonsense, you can find a lot of really useful websites."

**Assessment: the problem is real; the remedy does not work.**

**5.3.2 — Why `-AI` fails.** `[ANALYST ADD]` In search syntax, a leading minus excludes results **containing that term**. AI-generated pages do not contain the string "AI" — they contain the technical content, badly. **So the operator excludes the pages that *discuss* AI and leaves the generated ones untouched.** It is worse than useless: it removes exactly the pages that would have warned you.

**5.3.3 — What actually works.** `[ANALYST ADD]`

| Technique | Why it works |
|---|---|
| **Site-restricted search** (`site:rtl-sdr.com`) | Confines results to a source with a known editorial standard |
| **Date-bounded search** | Excludes the post-2023 flood |
| **Link-following from a trusted aggregator** | Hackaday and rtl-sdr.com curate; the curation is the filter |
| **Checking for a build log, a photo of the actual object, and a named author** | Generated pages rarely contain a specific failure the author personally had |
| **Preferring pages that describe something going wrong** | The signature of real experience |

**5.3.4 — The generalisable principle, and it is the archive's own test.** `[ANALYST ADD]` The reliable discriminator is not provenance but **specificity of failure**: a page that reports "mine did not work because the SMA had no pin" is almost certainly human, because a model has no pin to lose. **That is the surplus-content test from `IR-20261026-HYPERSUBJECTIVISM` §3.5 applied to search results** — and it is the only filter in this list that generalises.

---

## 6. CORRECTIONS

### 6.1 `-AI` does not filter AI-generated content

See §5.3. **A folk remedy that excludes the wrong pages.** Minor in consequence, instructive in kind: it is a plausible-sounding operator applied to a problem it does not address.

### 6.2 "Meteor-M2-3 and M2-4 are easy to hear" — at which frequency?

See §4.3. **The omission that determines a $30 versus $500 budget.** Not an error; an incompleteness with a large consequence.

### 6.3 "Very powerful repeater, easy to hear"

See §4.4. **Signal strength is not the difficulty; Doppler is.** A ~5 W repeater is easy to hear and hard to *use* without retuning.

### 6.4 The "ham radio for Dummies" book

**6.4.1** `[SOURCE CLAIM]` "I don't think that one is published anymore and it's probably very out of date."

**6.4.2 — The correction is in his favour.** `[ANALYST ADD]` He is right to steer the reader to a **current** ARRL study guide, because the US amateur question pools are revised on a fixed multi-year cycle and an old guide teaches answers that are now wrong. **His advice is correct and his reason — "out of date" — is the precise one.**

### 6.5 "Russian satellites catch on fire; US satellites get shut down"

**6.5.1** `[SOURCE CLAIM]` "The Russian satellites tend to catch on fire a lot... the US satellites get shut down whenever we decide that science is too wishy-washy."

**6.5.2 — The technical core is sound and the framing is political.** `[ANALYST ADD]` The defensible claim is that **spacecraft fail for institutional as well as engineering reasons** — funding, prioritisation, and decommissioning are real causes of service loss, not only hardware failure. **The partisan framing is unnecessary to the point and reduces its force**; a reader who disagrees politically will discount a technical observation that stands on its own.

---

## 7. SAFETY

**7.1 — Why this section is present.** `[ANALYST ADD]` The `signals/` area carries a standing safety note. This source recommends **disassembling unknown salvaged electronics** as its central practice and does not mention the hazard.

### 7.2 Stored charge in salvaged equipment

**7.2.1 — The hazard.** `[ANALYST ADD]` Consumer electronics contain capacitors that hold dangerous voltage **after** the device is unplugged. The two categories that kill hobbyists:

| Device | Hazard | Detail |
|---|---|---|
| **CRT television or monitor** | The tube itself plus the flyback/anode supply | **Hundreds of volts at lethal current**, retained for hours to days; the tube can implode if struck |
| **Microwave oven** | The high-voltage capacitor and transformer | **Charged to ~2 kV**; the capacitor holds charge with the unit unplugged, and the transformer can be lethal |

**7.2.2 — Why the source's advice leads here.** `[SOURCE CLAIM]` "Everything got saved for parts... you would take pieces and swap them... salvage broken equipment."

**Assessment: the practice is correct and the hazard is unmentioned.** `[ANALYST ADD]` The video names VCRs and old computers — both relatively safe. **But "save it for parts" as a *disposition* does not stop at VCRs**, and the same ethos applied to a kerbside television is lethal. **The boundary is not stated and the reader will not infer it.**

**7.2.3 — The mitigations, which are standard and cheap.** `[ANALYST ADD]`

| Measure | Applies to |
|---|---|
| **Assume every capacitor is charged** | All salvaged equipment |
| **Discharge through a resistor, not a screwdriver** | CRT anode, PSU rails — a screwdriver arc damages the part and can injure |
| **Never work on a CRT or microwave without specific training** | Both — **the correct advice is to not open them** |
| **Work one-handed, unplugged, and never alone** | All mains-derived equipment |
| **Use a residual-current device** | Bench work |

**7.2.4 — The finding.** `[ANALYST ADD]` **The video's central pedagogical principle — cheap equipment you can afford to destroy — is correct and its domain of validity ends at mains voltage.** The principle should be stated with that boundary, and it is not.

### 7.3 Other hazards

**7.3.1** `[ANALYST ADD]` Present and lightly handled:

| Hazard | Source's treatment |
|---|---|
| **Roof work** — taking down dishes | "If you can do it safely" — the only safety caveat in the video |
| **Ladders and antenna masts** | Not addressed |
| **RF exposure** | Not addressed; the path is receive-only until step 5 |
| **Liability** — removing a dish from someone's property | Not addressed; get permission in writing |

**7.3.2 — The roof caveat is the one place the source shows safety awareness**, and it is proportionate to the risk it is attached to. **The omission is that the same instinct was not applied to the salvage practice, which is more dangerous.**

### 7.4 Licensing

**7.4.1** `[ANALYST ADD]` The source's legal guidance is **correct and better than the adjacent video's**: "You don't have to have a licence to listen in, but if you want to start using it as a repeater, then get your ham technician license."

**7.4.2 — The correct framing, and it is worth stating because `IR-20261026-HF-RADIO` gets it wrong.** `[ANALYST ADD]`

| Activity | Status |
|---|---|
| **Receiving** | Generally unrestricted |
| **Decoding** | Generally unrestricted |
| **Transmitting** | **Requires a licence** on amateur allocations |
| **The licence's function** | **Legal permission plus social admission** — not a competence certificate |

**7.4.3 — And the licence's real value is the one the source identifies.** `[SOURCE CLAIM]` Getting the licence "gets all the sad hams off your tail" and "these people can be your allies... being able to talk to them in the clear over the airwaves is a great way to practice."

**Assessment: correct, and it is the honest reason.** `[ANALYST ADD]` The exam is a memorisation gate; **the skill is operational and is learned on the air.** So the licence is best understood as **a ticket to the practice environment**, not as evidence of competence — which is why the source, holding a master's degree he does not use, is unembarrassed about holding a licence he uses for access.

---

## 8. CROSS-ARCHIVE LINKS

### 8.1 The citation chain — the archive's first verified transmission of an idea

**8.1.1** `[ANALYST ADD]` This is the first time the archive can trace an idea from one source to another:

| Step | Source | Content |
|---|---|---|
| **Origin** | **This report** | "You can often find those [6–7 ft dishes] for free... they haven't used it since the 1980s and they want it gone" (23:27) |
| **Transmission** | `IR-20261026-SATELLITE-GROUND-STATION` | *"I've been watching a lot of Save It for Parts... when I saw an 8-ft dish on Facebook Marketplace, of course, I got it"* |
| **Realisation** | Same | The dish is mounted, driven, and receives GOES |

**8.1.2 — Why this matters analytically.** `[ANALYST ADD]` It is a **test case for the archive's own claim that method transfers and specifics do not.** The derived work did *not* follow the beginner path — it skipped straight to an 8-ft dish, a Raspberry Pi, and a rotator, and rebuilt the drive three times. **It followed the *attitude* (scavenge, expect failure, iterate) and discarded the *sequence*.** That is exactly what §3.1 predicts a competent learner should do.

**8.1.3 — And the derived work exceeded the origin on one axis.** `[ANALYST ADD]` The origin recommends LRIT at 137 MHz as a first success. The derivative went to **1.7 GHz geostationary** and needed a link budget it never wrote. **The beginner guide's advice was correct and was not taken**, and the derivative spent a day pointing at a decommissioned satellite as a result. **The chain therefore demonstrates both the value and the cost of skipping the ordering.**

### 8.2 The missing instrument, in three reports

**8.2.1** `[ANALYST ADD]` The archive now has three independent instances of the same finding:

| Report | Measurement absent | Consequence |
|---|---|---|
| `FIBER-OPTICS` | An instrument for sub-30 cm samples | Three years of development before the result was believed |
| `SATELLITE-GROUND-STATION` | A link budget | A day spent on 0.3° of backlash worth 0.004 dB |
| **This report** | **Any instrument at all** | **Five causes, one symptom, no discriminator** |

**The pattern: the missing thing is always the ability to tell whether it worked.** That is the archive's severed-corrective-term finding again, and here it is severed at the level of the *learner* rather than the system.

### 8.3 The archive's pattern, applied to a curriculum

**8.3.1** `[ANALYST ADD]` The recommended path has no corrective term by construction (§5.1). But it does have one thing the other systems lack: **a human in the loop**, in the form of the club. **That is the substitute for instrumentation**, and it is why §4.5.2 argues the club is the strongest non-technical advice in the video.

**8.3.2 — The generalisation.** `[ANALYST ADD]`

> **Where you cannot instrument, you must socialise.** A club, a forum, or a Discord is a borrowed corrective term: someone else can tell you whether the thing you built works, because they have already built it wrong in the same way.

**This is the one place in the archive where a severed feedback path is repaired by a *social* mechanism rather than a technical one**, and it is worth recording as a distinct category.

---

## 9. INDICATORS AND WARNINGS

### 9.1 Assessing a beginner guide

| ID | Indicator | Test |
|---|---|---|
| **G-1** | Does it date itself? | **Partially** — one sentence, one place (§3.3.3) |
| **G-2** | Does it recommend cheap before expensive? | **Passed** — emphatically |
| **G-3** | Does it name the downlink for each satellite? | **Failed** — the $30/$500 omission (§4.3) |
| **G-4** | Does it include a measuring instrument? | **Failed** (§5.1) |
| **G-5** | Does it warn about stored charge in salvage? | **Failed — lethal omission** (§7.2) |
| **G-6** | Is the licence framed as legal/social rather than as competence? | **Passed** (§7.4.3) |
| **G-7** | Are the hardware limits stated? | **Failed** — no HF, 8-bit (§4.1.2) |
| **G-8** | Is the difficulty of the "easy" task named? | **Failed** — Doppler (§4.4) |
| **G-9** | Does it volunteer the author's limits? | **Passed** — repeatedly |
| **G-10** | Does it recommend a social resource? | **Passed** — and it is the strongest advice in it |
| **G-11** | Is the path dependency-ordered? | **Passed**, with step 3 misplaced (§3.2.3) |
| **G-12** | Are jurisdictional caveats given for surplus and dumpsters? | **Partially** — US-specific, flagged as such |

**9.1.1 — Twelve checks, five passes.** The passes cluster in **attitude and ordering**; the failures cluster in **specifics and safety**. That is the characteristic profile of a source whose method is sound and whose transfer of detail is incomplete — **the opposite of `IR-20261026-HF-RADIO`, which had good specifics and an inverted mechanism.**

### 9.2 The meta-indicator

**9.2.1** The archive's standing test — *does the source state what would change its mind?* — adapts here to: **does the source say how the reader will know it worked?** The answer is *yes for the workflow* ("you heard something") and *no for every component of it*. **A path where each step is self-verifying is a good path; this one is self-verifying at the level of the task and blind at the level of the parts**, which is precisely why the club matters.

---

## 10. INTELLIGENCE GAPS AND KEY JUDGMENTS

### 10.1 Gaps

**10.1.1 — RTL-SDR V3 specifications (priority: high).** §4.1.2 states the limits from standard knowledge. **Requirement:** the vendor's datasheet for the exact revision, since the HF capability differs between clones and revisions.

**10.1.2 — Meteor-M downlink parameters (priority: high).** §4.3 gives LRIT at 137.9 MHz and HRPT at 1700 MHz. **Requirement:** confirm the current LRIT centre frequency, modulation, and line rate for the flying spacecraft.

**10.1.3 — ISS repeater frequencies and Doppler (priority: moderate).** §4.4 cites 145.99/437.80. **Requirement:** the current ARISS configuration, which changes between missions.

**10.1.4 — Salvage electrical safety (priority: high).** §7.2 is a safety claim stated from general knowledge. **Requirement:** a citable standard or manufacturer guidance on CRT and microwave capacitor discharge before the section is treated as authoritative. **Highest priority** — it is the report's most consequential addition.

**10.1.5 — Question-pool revision cycle (priority: low).** ¶6.4.2 references a fixed cycle. **Requirement:** the current US amateur pool schedule.

**10.1.6 — The chain's other end (priority: moderate).** §8.1 asserts the influence direction from an explicit citation in the derivative. **Requirement:** nothing further — the citation is in the transcript — but a third source in the chain would test the claim that attitude transfers and sequence does not.

### 10.2 Key judgments

| ID | Judgment | Confidence |
|---|---|---|
| **KJ-1** | The source's central pedagogical principle is correct and generalises: **cheap equipment is the pedagogically optimal instrument because it lowers the cost of failure below the exploration threshold.** | **High** |
| **KJ-2** | The recommended path is correctly dependency-ordered and each early step is self-verifying — which is why it works for a beginner with no money. | **High** |
| **KJ-3** | **The missing downlink frequency is the report's most useful correction**: LRIT at 137 MHz is a $30 path; HRPT at 1.7 GHz is a $500 path. | **High** |
| **KJ-4** | **The path teaches acquisition and never teaches measurement**, so a learner cannot distinguish five common causes of one symptom. | **High** |
| **KJ-5** | **The salvage practice has a lethal hazard the source omits** — CRT and microwave capacitors — and the omission follows from the practice itself. | **High** |
| **KJ-6** | The `-AI` search advice is ineffective: it excludes pages *about* AI and leaves AI-generated pages untouched. | **High** |
| **KJ-7** | The ISS repeater is easy to *hear* and hard to *use*; Doppler (~3.6 kHz at 2 m, ~10.8 kHz at 70 cm) is the actual obstacle. | **High** |
| **KJ-8** | **This is the archive's first explicitly self-dating source**, and the genre's half-life is about two years — hardware recommendations decay faster than method. | **High** |
| **KJ-9** | The archive now contains a **verified citation chain** from this video to the ground-station build, and the derivative took the attitude while discarding the sequence. | **High** |
| **KJ-10** | **Where you cannot instrument, you must socialise** — the club is a borrowed corrective term, and it is the strongest non-technical advice in the video. | **Moderate-high** |
| **KJ-11** | The licence is a ticket to the practice environment, not a competence certificate; the source's framing of it as legal and social is the correct one. | **High** |
| **KJ-12** | The source's limits are honestly stated (no maths, no programming, unused degree), which is what earns it an A on reliability despite a 3 on credibility. | **High** |

---

## APPENDIX A — GLOSSARY

| Term | Definition |
|---|---|
| **ARISS** | Amateur Radio on the International Space Station. |
| **Attentional priming** | Raised perceptual salience for a category once it becomes task-relevant. |
| **Doppler shift** | Frequency change from relative motion; ~10.8 kHz at 437.8 MHz for a LEO pass. |
| **HRPT** | High Resolution Picture Transmission; Meteor-M's 1.7 GHz downlink. |
| **LRIT** | Low Rate Information Transmission; Meteor-M's 137.9 MHz downlink. |
| **nanoVNA** | Low-cost vector network analyser; the cheap instrument for antenna measurement. |
| **RTL-SDR** | Receive-only SDR using the RTL2832U demodulator chip; 8-bit, ~24 MHz–1.7 GHz. |
| **SWR** | Standing wave ratio; the mismatch metric an SWR meter reports. |
| **Tacit knowledge** | Knowledge that transfers by apprenticeship rather than by document. |

---

## APPENDIX B — CHRONOLOGY

| Year | Event | Relevance |
|---|---|---|
| 1970s–80s | C-band TVRO dishes installed | The free-dish supply |
| 2004 | University 3D printers unclaimed | The source's anecdote |
| 2012 | RTL-SDR discovered as a receiver | The hobby's inflection |
| 2019 | Meteor-M №2-3 launched | The recommended spacecraft |
| 2020 | The source begins the channel | His stated starting point |
| 2022 | Meteor-M №2-3 damaged | Why the recommendation dates (§3.3) |
| 2024 | Meteor-M №2-4 launched | The working replacement |
| 2023– | LLM-generated content flood | §5.3 |

---

## APPENDIX C — CLAIM LEDGER

| # | Claim | Class | Status | Assessment |
|---|---|---|---|---|
| C-1 | Start with junk you can afford to break | Pedagogy | **Correct and generalisable** | §3.1 |
| C-2 | Expect and embrace failure | Pedagogy | Correct | — |
| C-3 | Books are less useful than sites and videos now | Preference | Defensible | Time-sensitive |
| C-4 | Get the current ARRL study guide | Recommendation | **Verified** | Pools are revised |
| C-5 | `-AI` filters AI-generated results | Technique | **FALSE** | §5.3 |
| C-6 | Clubs, maker spaces, universities are resources | Recommendation | **Verified** | Tacit knowledge |
| C-7 | Libraries lend tools and cameras | Fact | Verified in outline | — |
| C-8 | US surplus and discard culture supplies parts | Fact | Verified in outline | Jurisdiction-specific |
| C-9 | RTL-SDR Blog V3 + kit is the right first SDR | Recommendation | **Verified** | §4.1 |
| C-10 | **RTL-SDR limits (no HF, 8-bit)** | Fact | **Not in source** | §4.1.2 |
| C-11 | Build your own antennas to learn wavelengths | Pedagogy | **Verified — best suggestion** | Needs instrumentation |
| C-12 | **Meteor-M2-3/M2-4 are easy to hear** | Recommendation | **Incomplete** | Which downlink? §4.3 |
| C-13 | Satellites are ephemeral | Epistemic | **Verified and honest** | §3.3 |
| C-14 | ISS repeater is easy to hear | Fact | Verified | Doppler is the difficulty |
| C-15 | No licence needed to listen | Legal | **Verified** | §7.4 |
| C-16 | Technician licence permits ISS transmit | Legal | Verified | — |
| C-17 | 6–7 ft dishes are often free | Fact | **Verified** | The chain's origin (§8.1) |
| C-18 | Linux revives old computers | Fact | Verified | — |
| C-19 | Salvage broken electronics for parts | Practice | **Correct, hazardous** | §7.2 |
| C-20 | **Stored charge in CRTs and microwaves** | Safety | **Not in source** | §7.2 |
| C-21 | Dumpsters and kerbside are viable | Fact | Verified, jurisdiction-specific | — |
| C-22 | Degree does not determine path | Testimony | Unfalsifiable | Honest |
| C-23 | "I am terrible at math" | Testimony | Unfalsifiable | Credibility marker |
| C-24 | **The genre's half-life is ~2 years** | Analysis | **Not in source** | §3.3 |
| C-25 | **Where you cannot instrument, socialise** | Analysis | **Not in source** | §8.3 |

---

## APPENDIX D — VERBATIM EXTRACTS

**D-1** [0:44] "Attitude is very important... have curiosity, be willing to experiment, don't be afraid of breaking things, expect failure, embrace failure."

**D-2** [2:43] "AI is coming along and polluting the internet with BS answers, but if you can do a search and do a minus AI at the end... you can find a lot of really useful websites."

**D-3** [3:09] "I have gone through the RTL-SDR blog in the past and just looked up different projects... and then I would go to those people's websites or their YouTube videos or their GitHub repositories and figure out how did they do this project."

**D-4** [5:04] "We have this new fangled technology. Nobody knows how to use it. It's just sitting there gathering dust... It's called a 3D printer."

**D-5** [9:41] "I am not good at programming. I am terrible at math. I have a master's in computer science and I basically don't use it."

**D-6** [11:02] "I happen to be very privileged to live in the United States, which is a very disposable culture... So our trash is just full of treasure basically."

**D-7** [16:24] "Find some junk to experiment with. Find something that you are not afraid to break... it can be the cheapest, crummiest, most broken thing. And that will help you learn the most."

**D-8** [19:15] "If you want a good beginner level SDR, I recommend the RTL-SDR Blog V3. Get it with the antenna kit."

**D-9** [19:28] "I would highly recommend building your own antennas, learning how to build antennas, because that's a fantastic way to learn about frequencies, wavelengths."

**D-10** [19:39] "Start with the Russian Meteor system, the M2 series. Meteor M2-3 and M2-4 are pretty easy to hear, at least as I film this."

**D-11** [19:47] "A lot of these satellites are kind of ephemeral... they might not be around by the time you see this video."

**D-12** [20:30] "The International Space Station is a great one to start with. That has a very powerful repeater, easy to hear from most of the world."

**D-13** [20:49] "You don't have to have a license to listen in, but if you want to start using it as a repeater, then get your ham technician license."

**D-14** [21:11] "Once you get into this hobby, you will start noticing things... it's kind of like once you own a Honda Civic, you start seeing Honda Civics everywhere."

**D-15** [23:27] "If you can get like a six or seven foot satellite dish, you can do all kinds of silly things with that. And you can often find those for free... they haven't used it since the 1980s and they want it gone."

**D-16** [16:01] "There can be some older hams who are grumpy and don't like younger people and will freak out if you say the Baofeng word."

**D-17** [26:14] "If I had stuck with computer science 20 years ago, I would probably be making way, way more money than I am now. But you know what? I enjoy this."

---

## APPENDIX E — TERMINOLOGY RECONCILIATION

| Source usage | Correct / preferred | Note |
|---|---|---|
| "software to find radio" | **software-defined radio** | ASR destroys the subject term |
| "rstr.com" | **rtl-sdr.com** | — |
| "bow fang" | **Baofeng** | — |
| "hamstats" | **ham sats** | — |
| "Meteor M23 / M24" | **Meteor-M №2-3 / №2-4** | — |
| "UF / UAF" | **University of Alaska Fairbanks** | — |
| "Axeman Surplus" | **Ax-Man Surplus** | — |
| "minus AI" | **excludes pages containing "AI" — not generated content** | §5.3 |
| "cheapest, crummiest thing" | **the instrument whose destruction the learner can afford** | §3.1.2 |
| "very powerful repeater" | **~5 W; the obstacle is Doppler, not power** | §4.4 |

---

## APPENDIX F — ESTIMATIVE LEXICON

**Confidence:** High (verified against a primary source or standard reference) · Moderate (credible single stream, or sound reasoning with an inferential gap) · Low (fragmented or contested).

**Likelihood:** Almost no chance 01–05% · Very unlikely 05–20% · Unlikely 20–40% · Roughly even 40–60% · Likely 55–85% · Very likely 80–95% · Almost certain 95–99%.

**Technical status:** *Verified* · *Computed* (derived in this report) · *Incomplete* (true as far as it goes; the omission is consequential) · *Omitted* (absent and consequential) · *Error* · *Unfalsifiable* (testimony or preference).

---

## APPENDIX G — REVISION LOG

| Rev | Date | Change |
|---|---|---|
| 1.0 | 2026-10-26 | Initial issue. Source: `transcript.md` (ASR, 27:32). Doppler figures computed; the LRIT/HRPT cost distinction identified (§4.3); the citation chain to `IR-20261026-SATELLITE-GROUND-STATION` verified (§8.1). |

**Known deficiencies:**

1. RTL-SDR revision-specific specifications unverified (§10.1.1).
2. Meteor downlink parameters need confirming against the flying spacecraft (§10.1.2).
3. ARISS frequencies change between missions (§10.1.3).
4. **The salvage-safety section is a safety claim stated from general knowledge and needs a citable standard (§10.1.4). Highest priority.**
5. The genre half-life in §3.3 is the analyst's estimate, not a measured quantity.

---

```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

*End of report.*
