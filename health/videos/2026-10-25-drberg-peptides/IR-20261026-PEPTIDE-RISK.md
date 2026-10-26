```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

> **NOT MEDICAL ADVICE.** This product analyzes the claims in a public video. It is not a
> prescription, a dosing guide, or a substitute for evaluation by a licensed clinician. Several
> compounds discussed here are unapproved, are sold outside licensed supply chains, and carry
> documented injection and contamination risks. Nothing in this document should be used to decide
> whether to take, inject, or administer any substance.

# PEPTIDE CLAIMS AND SUPPLY-CHAIN RISK
## Evidence Grading, Regulatory Status, and Gray-Market Integrity of Six Compound Classes

| Field | Value |
|---|---|
| **Report No.** | IR-20261026-PEPTIDE-RISK |
| **DTG** | 260700ZOCT26 |
| **Classification** | UNCLASSIFIED // OPEN SOURCE |
| **Originator** | Analyst (independent) |
| **Source** | `transcript.md` (same folder) — ASR transcript, 12:33 runtime, 11 chapters |
| **Source path** | `notes/health/videos/2026-10-25-drberg-peptides/transcript.md` |
| **Source type** | OSINT — single-source, open-platform video commentary |
| **Reliability** | **C3** (source) / **B2** (regulatory assertions, where checked against primary) |
| **Subject** | Peptide pharmacology, evidence quality, regulatory status, supply-chain integrity |
| **Distribution** | Unlimited |
| **Handling** | Analytic exercise. "Mil-spec" formatting is a presentation frame; no classified, proprietary, or privileged material is contained. |

**Handling caveat.** This report assesses *a set of claims*, not a patient. Claims are marked `[SOURCE CLAIM]` when reproduced without endorsement, and `[ANALYST ADD]` when supplied from outside the source. Regulatory status is time-sensitive and was checked on 26 OCT 2026; it should be re-verified before any action.

---

## TABLE OF CONTENTS

- **1. BLUF — Bottom Line Up Front**
- **2. Source Assessment**
  - 2.1 Provenance · 2.2 Reliability grading · 2.3 Commercial interest · 2.4 Transcription integrity · 2.5 Verification status
- **3. Analytic Framework**
  - 3.1 What a peptide is, and why the word is not a drug class · 3.2 Half-life as an engineered parameter · 3.3 Pulsatility versus continuous exposure · 3.4 Receptor pharmacology and desensitization · 3.5 Evidence grading scheme · 3.6 Regulatory framework (503A/503B, Category 1/2, RUO)
- **4. Compound-by-Compound Technical Analysis**
  - 4.1 GLP-1 receptor agonists · 4.2 Sermorelin and the GH axis · 4.3 BPC-157 · 4.4 TB-500 · 4.5 GHK-Cu · 4.6 Epitalon · 4.7 Collagen peptides (the control case)
- **5. Supply-Chain Threat Model**
  - 5.1 Structure of the gray market · 5.2 Failure modes · 5.3 What a COA does and does not prove · 5.4 The statistics: traceable and untraceable · 5.5 Synthesis impurity arithmetic
- **6. The Cancer Question**
- **7. Indicators and Warnings (I&W)**
- **8. Decision Framework**
- **9. Intelligence Gaps and Collection Requirements**
- **10. Key Judgments with Confidence**
- **Appendix A** Glossary · **B** Chronology · **C** Claim ledger · **D** Verbatim extracts · **E** Terminology reconciliation · **F** Estimative lexicon · **G** Revision log

---

## 1. BLUF — BOTTOM LINE UP FRONT

**1.1** The source is **substantially more responsible than the genre norm** and **materially wrong on the one claim that carries operational consequences.** It correctly warns that evidence for the popular peptides is largely rodent-derived, correctly flags the single-Russian-group problem in Epitalon research, correctly identifies lean-mass loss as the central complication of GLP-1 therapy, and correctly describes the gray market as hazardous. It then states that the FDA reclassified 14 peptides to a prescribable category in February 2026 — **a claim this report assesses as likely false, and false in the direction that matters.** **Confidence: moderate-high.**

**1.2 — The regulatory finding is the headline.** `[ANALYST ADD]` FDA's live bulk-substance page (checked 26 OCT 2026) lists **BPC-157, TB-500, Epitalon, injectable GHK-Cu, CJC-1295, Semax, MOTS-c, DSIP/emideltide, AOD-9604, dihexa, and LL-37** under **"Bulk drug substances nominated but withdrawn"** — each with a **published significant-safety-risk finding**. They are not in Category 1. The most probable origin of the source's error is a **misreading of the 22 April 2026 restructure** of that page, in which twelve peptides moved out of the active Category 2 table into the withdrawn table. **Withdrawal is not clearance.** It removes a pending nomination; it does not create a lawful compounding pathway. The active Category 2 table itself now contains 14 substances, which is the most likely source of the "14 peptides" figure. **Confidence: moderate-high.**

**1.3 — The single most important technical distinction the source gets right** is that "peptide" names a **molecular format**, not a pharmacological class. GLP-1 receptor agonists and BPC-157 share a backbone chemistry and nothing else: one is an incretin mimetic with an engineered seven-day half-life and a completed Phase III program; the other is a fifteen-residue fragment of a gastric protein with no completed human randomized trial. Treating them as one category — which the market, and to a degree the source's framing, does — is the category error from which most of the confusion follows. **Confidence: high.**

**1.4 — The source's best pedagogical device is also technically correct.** The "dimmer switch versus new lamp" metaphor maps onto a real pharmacological principle: **amplifying endogenous pulsatile signalling** (secretagogues, which preserve the body's own feedback control) versus **imposing continuous exogenous receptor occupancy** (long-acting agonists, which override it). The distinction is not rhetorical. Loss of pulsatility changes downstream physiology, and the source's implicit claim that these are different kinds of intervention is sound. **Confidence: high** (that the distinction is real); **moderate** (that the source's specific compound assignments are correct — sermorelin is genuinely a dimmer; semaglutide is genuinely a lamp).

**1.5 — The source contains one clean factual error in physiology and one in pharmacology.** Growth hormone is secreted in approximately **6–8 pulses per 24 hours, roughly every 3 hours** — not every 90 minutes. The 90-minute figure in the literature refers to **pulse duration**, not inter-pulse interval, which is the likely origin of the conflation. Separately, the claim that BPC-157 "does not trigger cancer" is stated with more certainty than the evidence permits; the correct formulation is that no human carcinogenicity signal has been established, and an angiogenic mechanism supplies a theoretical concern that has not been excluded. **Confidence: high** on the GH figure; **high** that the cancer claim is over-asserted.

**1.6 — The supply-chain section is the most valuable content in the video and the least well sourced.** Its structural warnings are correct and match regulatory guidance: "research use only" labelling combined with published dosing charts, Telegram-mediated transactions, implausibly low prices, and certificates of analysis from labs with no independent existence. Its quantitative claims are uneven. The **30% wrong-sequence** and **arsenic at 10× limit** figures are traceable to a real peer-reviewed study (Janvier et al., *Talanta*, 2018) — but that study examined **ten falsified pharmaceuticals seized on the Belgian market**, not a representative sample of research-peptide vials. The **65% endotoxin failure** figure has **no traceable primary source** that this analysis could locate. **Confidence: moderate-high** on the traceability findings.

**1.7 — The real risk is not the compound, it is the vial.** For every compound in this report except the approved GLP-1 agents, the dominant expected harm is not a pharmacological effect at a stated dose — it is **identity error, endotoxin, elemental contamination, non-sterility, aggregate-driven immunogenicity, and injection injury**, in a product with no lot traceability and no recall pathway. This reframing is the report's central operational conclusion, and the source gestures at it ("the wild, wild west") without making it explicit. **Confidence: high.**

**1.8 — Net assessment.** The source is a **competent risk-aware overview with a correct core taxonomy, a serious regulatory error, one physiological error, and a commercial interest that biases its recommendations toward purchasable interventions.** It should be used for orientation and for its supply-chain warnings; it should not be used as a basis for sourcing or administration decisions. Grade: **C3 overall, with the regulatory assertions independently downgraded to unreliable.**

---

## 2. SOURCE ASSESSMENT

### 2.1 Provenance

**2.1.1** The source is a 12-minute, 33-second video essay published on a public video platform by the channel `@Drberg`, URL `https://www.youtube.com/watch?v=qovnfjVd8cs`. Local capture: `transcript.md`, same folder as this report. Format: single-presenter explanatory monologue with chapter markers, addressed to a general consumer audience.

**2.1.2** Structure, from the transcript's own chapter markers:

| Ch. | Segment | Span |
|---|---|---|
| 1 | Peptides explained | 0:00–0:36 |
| 2 | What are peptides? | 0:37–0:59 |
| 3 | How do peptides work? | 1:00–2:24 |
| 4 | Sermorelin | 2:25–3:01 |
| 5 | GLP-1 peptide side effects | 3:02–3:59 |
| 6 | BPC-157 | 4:00–4:55 |
| 7 | GHK-Cu copper peptide | 5:46–5:59 |
| 8 | Epitalon | 6:00–6:32 |
| 9 | Peptides and cancer | 6:33–7:17 |
| 10 | Are peptides safe? | 7:18–9:51 |
| 11 | Should I use peptides? | 10:14–12:33 |

**2.1.3 — Coverage asymmetry.** The video devotes roughly 3 minutes 30 seconds to GLP-1 side effects and BPC-157, and approximately **14 seconds** to GHK-Cu and **32 seconds** to Epitalon. The allocation is defensible on grounds of popularity, but it means the report's treatment of the less-covered compounds must be built from sources other than the video.

### 2.2 Reliability grading

| Axis | Grade | Rationale |
|---|---|---|
| **Source reliability** | **C — Fairly reliable** | Identifiable presenter with domain-adjacent credentials; content is internally coherent; explicit about evidence limitations in several places; **but** makes at least one material regulatory error and one physiological error, and has a commercial interest. |
| **Information credibility** | **3 — Possibly true** | Mechanism descriptions are largely accurate; evidence characterizations are directionally honest; quantitative supply-chain claims are partly untraceable; regulatory claim is likely false. |
| **Composite** | **C3** | Adequate for orientation and hypothesis generation. **Not** adequate as a basis for sourcing, dosing, or regulatory assumptions. |

**2.2.1 — What raises the grade.** Three specific behaviours are atypical for the genre and should be credited:

1. **It volunteers the replication failure.** On Epitalon: "the only studies that are out there are from a single Russian research group in 2003 and also 2006. And neither was independently replicated by any outside institution." This is the correct epistemic move and most supplement content does not make it.
2. **It volunteers the species gap.** On BPC-157: "almost all those studies were in rodents."
3. **It volunteers the adverse outcome of the intervention it spends most time on.** The GLP-1 lean-mass passage is not a defence of the drug; it is a warning about it, and it is the passage most likely to reduce a viewer's willingness to purchase.

**2.2.2 — What lowers it.** The regulatory error (¶2.5.1) is not a minor slip; it is the sentence that tells a viewer a prescription is available, which is the difference between a gray-market purchase and a clinical pathway. An error that converts "not legally accessible" into "ask your doctor" is the highest-consequence error the video could have made.

### 2.3 Commercial interest

**2.3.1** The presenter is credentialed as a **chiropractor (DC), not a physician**, and operates a supplement business. `[ANALYST ADD]` Both facts are matters of public record and neither is concealed. The relevance is structural, not personal: it establishes a **direction of bias** that can be tested against the content.

**2.3.2 — The bias is detectable and it is consistent.** At 7:02, mid-video and immediately after the cancer segment, the source inserts a "free download" call to action for a personal daily-routine checklist. In the final segment, the alternatives it recommends are **zinc carnosine, garlic, zinc, vitamin C, glycine, and magnesium glycinate** — all purchasable, several sold by the presenter. The recommended non-purchasable interventions (sprinting, HIIT, sleep, fasting, keeping insulin low) are correct and are mentioned first, which partially mitigates the concern.

**2.3.3 — Assessment.** The commercial interest does **not** invalidate the content, and this report does not treat it as evidence of dishonesty. It does predict the **shape** of the recommendations: interventions that can be bought will be over-represented relative to interventions that cannot, and risk will be framed in a way that preserves the purchase decision. That prediction is confirmed at the margins. It should be weighted accordingly, not discounted entirely. **Confidence: moderate-high.**

### 2.4 Transcription integrity

**2.4.1** The transcript is machine-generated and corrupts proper nouns and terms of art systematically. Corrections required before quotation:

| As transcribed | Correct form | Consequence if uncorrected |
|---|---|---|
| "serorlin" | **sermorelin** | Compound unidentifiable |
| "epalin" | **Epitalon** | Compound unidentifiable |
| "GOP1s" / "GOP1" | **GLP-1s** | — |
| "HPC" / "HLC" | **HPLC** (high-performance liquid chromatography) | The entire COA argument becomes unintelligible |
| "fleas" (in "in fleas, mice and rats") | **flies** (almost certainly *Drosophila*) | Changes the claim from absurd to merely unverified |
| "telomeirs" | **telomeres** | — |
| "co-actor" | **cofactor** | — |
| "TB500" | **TB-500** | — |
| "GHK CU" / "CU copper peptide" | **GHK-Cu** | — |
| "category one" | **Category 1** | Regulatory term of art |
| "200 and 400 microgram" | 200–400 **µg** | Unit integrity matters in a dose discussion |

**2.4.2 — Unresolved names.** The source names three testing laboratories it says "the research community trusts": **Janoshik Analytical**, **Covera Labs**, and **Freedom Diagnostics**. `[ANALYST ADD]` Janoshik Analytical is a known third-party peptide-testing laboratory. The other two could not be verified in this analysis and may be ASR corruptions. **The source itself disclaims verification** ("I'm not telling you that I verify these companies"), which is the correct hedge, but the naming still functions as an endorsement in practice. See ¶9.4.

### 2.5 Verification status

| Claim | Locus | Status |
|---|---|---|
| Peptides are short amino acid chains; proteins are long | 0:42 | **Verified** (conventional; boundary ~50 residues) |
| Steroids derive from cholesterol; peptides do not | 1:45 | **Verified** |
| Collagen powder is peptide | 1:50 | **Verified** (hydrolysed collagen, ~2–5 kDa) |
| GH is secreted in pulses | 2:30 | **Verified** |
| GH pulses occur "every 90 minutes" | 2:34 | **FALSE** — ~6–8 pulses/day, ~every 3 h; 90 min is pulse *duration* |
| Native GLP-1 has a very short half-life | 3:13 | **Verified** (~1.5–2 min; DPP-4 cleavage) |
| GLP-1 agents engineered to act for seven days | 3:16 | **Verified for semaglutide** (~165 h); not for the class |
| Lean mass is a substantial fraction of GLP-1 weight loss | 3:41 | **Verified** (commonly ~20–40%) |
| Weight regain after cessation | 3:48 | **Verified** (~two-thirds within 1 year, STEP-1 extension) |
| Regain is fat but not muscle | 3:50 | **Partially supported**, stated with excess certainty |
| BPC-157 rodent evidence on angiogenesis/healing | 4:21 | **Verified** (directionally; "50% more blood vessels" is one study's figure) |
| BPC-157 human evidence limited to small series | 5:00 | **Verified** — no completed RCTs located |
| GHK-Cu acts topically on collagen synthesis | 5:46 | **Verified** (mechanism); evidence quality modest |
| Epitalon targets telomeres via telomerase | 6:00 | **Unverified mechanism**; single-group data only |
| Epitalon studies 2003 and 2006, never replicated | 6:22 | **Consistent with the record**; the source's characterization is fair |
| BPC-157 "does not trigger cancer" | 6:40 | **Over-asserted** — no human signal, but not established as absent |
| 80–90% of raw peptide material originates overseas/China | 7:20 | **Directionally plausible, unsourced** |
| 30% contained wrong amino acid sequence | 7:37 | **Traceable** to Janvier et al. 2018 — different population (¶5.4.2) |
| 65% failed bacterial endotoxin limits | 7:48 | **No traceable primary source located** |
| Arsenic at 10× safety limits | 8:01 | **Traceable** to Janvier et al. 2018 (inorganic As, 10× ICH limit) |
| HPLC does not test heavy metals, endotoxins, sterility | 8:17 | **Verified** — correct and important |
| **FDA reclassified 14 peptides to Category 1, Feb 2026** | **9:56** | **ASSESSED LIKELY FALSE** — see ¶2.5.1 |
| "A doctor can give you a prescription for this specific peptide" (BPC-157) | 10:09 | **ASSESSED LIKELY FALSE** — see ¶2.5.1 |

**2.5.1 — MATERIAL FINDING: the regulatory claim.** This is the report's most consequential correction, so the evidence chain is set out in full.

*What the source says* (9:56–10:11): "In February of 2026, the FDA reclassified 14 peptides back to category one where you can have a prescription and get these. So, as of right now, a doctor can give you a prescription for this specific peptide" — the "this" being BPC-157.

*What the primary record shows.* FDA's live page, "Certain Bulk Drug Substances for Use in Compounding that May Present Significant Safety Risks," contains two tables: an active **Category 2** table (substances for which FDA has identified significant safety risks and which **cannot be compounded**) and a separate table headed **"Bulk drug substances nominated but withdrawn."** BPC-157 appears in the **second** table, not Category 1. The entry reads, in part:

> "Compounded drugs containing BPC-157 may pose risk for immunogenicity for certain routes of administration and may have complexities with regard to peptide-related impurities and active pharmaceutical ingredient (API) characterization. FDA has identified no, or only limited, safety-related information for the proposed routes of administration. Therefore, the agency lacks sufficient information to know whether the drug would cause harm when administered to humans."

The same table carries equivalent findings for TB-500, Epitalon, injectable GHK-Cu, CJC-1295, Semax, MOTS-c, DSIP/emideltide, AOD-9604, dihexa acetate, and cathelicidin LL-37. `[ANALYST ADD]`

*What actually happened in 2026.* On **22 April 2026**, FDA restructured that page into an active Category 2 table and a new "nominated but withdrawn" table. **Twelve peptides moved from the first to the second** — because the **nominators withdrew the nominations**, not because FDA cleared them. FDA continued to publish a safety-risk finding for all twelve on the same page. **Leaving Category 2 by withdrawal moves a substance further from a lawful pathway, not closer**, because it removes the pending nomination rather than establishing eligibility.

*Probable error mechanism.* Two conflations, both natural:

1. **The number 14.** The active Category 2 table now holds 14 substances. A reader comparing the pre- and post-restructure page could read "14" as the count of things that changed rather than the count of things that remain.
2. **"Moved out of Category 2."** Twelve peptides did leave Category 2. They left into a *worse* status, not a better one. The direction of the move was inverted.

A further confound: a widely circulated March 2026 claim attributed an announcement on **27 February 2026** to the HHS Secretary, stating that roughly 14 peptides would move from Category 2 back to Category 1. At least one site that published that story has since **retracted it**, stating on re-review that the announcement could not be verified against any primary source, that the cited press release does not resolve, and that the claim circulates almost entirely on low-quality commercial peptide sites.

*Assessment.* **The source's regulatory claim is likely false** — not merely imprecise. The operational conclusion it supports ("ask your doctor for a prescription") is unsupported for BPC-157 and the other withdrawn compounds. **Confidence: moderate-high.** Residual uncertainty is genuine: FDA pages change, the underlying policy area is in active flux, and a February 2026 action that left no trace on the current page cannot be excluded with certainty. **Verification path** is specified at ¶9.1 and should be executed before any decision that depends on this finding.

*Why this matters more than the other errors.* Every other error in the video degrades the quality of a judgment. This one changes a **category of action**. A viewer who believes a lawful prescription pathway exists will approach a clinician; a viewer who believes it does not will approach a gray-market vendor. The error therefore has a direct causal path to the harm the video spends its second half warning about — an irony worth noting, and the strongest argument for treating regulatory claims in consumer health content as requiring primary-source verification.

---

## 3. ANALYTIC FRAMEWORK

### 3.1 What a peptide is, and why the word is not a drug class

**3.1.1 — Chemical definition.** A peptide is a chain of amino acids linked by amide bonds. The peptide/protein boundary is **conventional, not natural**: roughly 50 residues, or ~10 kDa. Below it, the molecule is a peptide; above it, a protein. The convention exists because short chains behave differently — they are synthesizable, orally survivable in some cases, and cheap to manufacture — not because there is a sharp physical transition.

**3.1.2 — Sub-classifications that matter.**

| Class | Length | Examples | Relevance |
|---|---|---|---|
| Di/tripeptide | 2–3 | GHK-Cu, carnosine | Absorbed intact; oral bioavailability plausible |
| Oligopeptide | 4–20 | BPC-157 (15), Epitalon (4), TB-500 (~7) | The gray-market core; synthesis cheap, QC hard |
| Polypeptide | 21–50 | GLP-1 (30), semaglutide (31), sermorelin (29) | Recombinant or complex synthesis; regulated as drugs |
| Protein hydrolysate | variable | Collagen "peptides" | Food ingredient, 2–5 kDa average; not a signalling molecule |

**3.1.3 — The category error.** "Peptide" describes **how a molecule is built**, not **what it does**. Two peptides can differ in receptor, tissue, potency, half-life, route, evidence base, and regulatory status by more than two small-molecule drugs in unrelated classes differ. The market exploits this: a consumer who has heard that "peptides work" has been given a statement with no pharmacological content, and the inference to "this peptide will work for me" is unsupported by the premise.

**3.1.4 — The source's "bricks versus blueprint" metaphor.** `[SOURCE CLAIM]` Amino acids are "the raw material or the bricks"; signalling peptides are "a blueprint" that tells the body what to do. **Assessment: correct and well chosen.** It cleanly separates two things the market conflates:

- **Structural peptides** — collagen hydrolysate, the "bricks." Supplying them is supplying raw material; the body decides what to build. Risk is low because the mechanism is nutritional.
- **Signalling peptides** — GLP-1, BPC-157, sermorelin, the "blueprint." Supplying them is issuing an instruction. Risk is higher because the mechanism is regulatory, and instructions can be wrong, mistimed, or addressed to the wrong tissue.

This distinction predicts the risk gradient observed in practice: collagen peptides are sold as food and are largely benign; signalling peptides are sold as "research chemicals" precisely because they cannot be sold as drugs.

### 3.2 Half-life as an engineered parameter

**3.2.1** For peptides, **half-life is the primary engineering problem**, because the body is built to destroy them. Proteases are ubiquitous, the kidney filters small chains efficiently, and the gut is a proteolytic reactor. A native signalling peptide is therefore usually short-lived by design — the signal is meant to be transient.

**3.2.2 — Native GLP-1.** GLP-1(7-36)amide, 30 residues, secreted by intestinal L-cells after nutrient ingestion. Plasma half-life **1.5–2 minutes**, cleaved by **DPP-4** at the Ala8 position and by neutral endopeptidase. This is why native GLP-1 cannot be a drug and why the incretin field was, for years, a pharmacology problem rather than an endocrine one.

**3.2.3 — The engineering solutions**, and what each buys:

| Agent | Modification | Half-life | Consequence |
|---|---|---|---|
| Exenatide | Gila monster homolog (Exendin-4), DPP-4 resistant | ~2.4 h | Twice-daily injection |
| Liraglutide | C16 fatty acid + γGlu spacer → albumin binding | ~13 h | Once daily |
| **Semaglutide** | Aib8 substitution + C18 diacid → tight albumin binding | **~165 h (~7 days)** | **Once weekly** — the source's "seven straight days" |
| Dulaglutide | Fc fusion (IgG4) | ~5 days | Once weekly |
| Tirzepatide | GIP/GLP-1 dual agonist + acylation | ~5 days | Once weekly |

**3.2.4** The source's "seven straight days" is therefore **correct for semaglutide and incorrect as a class statement** — exenatide is ~2.4 hours. The imprecision is minor in effect but reveals the general habit of describing a class from its most salient member.

**3.2.5 — Why this is the crux of the "dimmer versus lamp" distinction.** A half-life of seven days is not a convenience feature bolted onto a working drug. It is a **change in the shape of the signal**: from a postprandial spike lasting minutes to a square wave lasting a week. Everything in ¶3.3 follows from that.

### 3.3 Pulsatility versus continuous exposure

**3.3.1 — The endocrine principle.** Many hormonal axes are **pulsatile by design**, and the downstream response depends on pulse frequency and amplitude, not merely on mean concentration. Continuous exposure is not a smoothed version of pulsatile exposure; it is a different signal, often producing different gene expression and different receptor regulation.

**3.3.2 — The GH axis, corrected.** `[ANALYST ADD]` Growth hormone is released from anterior pituitary somatotrophs in **approximately 6–8 discrete pulses per 24 hours, roughly every 3 hours**, with the largest pulse at sleep onset, associated with the first phase of slow-wave sleep. In men, sleep-associated pulses contribute on the order of **70% of daily GH output**. Between pulses, GH is near-undetectable. Secretion is set by the balance of hypothalamic **GHRH** (stimulatory) and **somatostatin** (inhibitory), modulated by ghrelin, gonadal steroids, nutrition, and sleep.

**3.3.3 — The source's error, and its likely origin.** "Every 90 minutes you have this pulse of growth hormone" (2:34). The literature's 90-minute figure is the **duration of a secretory episode**, not the interval between them. The inter-pulse interval is closer to 128–180 minutes. The conflation is easy, and its effect is to make the system sound roughly twice as active as it is. It does not change the qualitative argument — pulsing is real, and it declines with age — but it is the kind of error that a viewer with a background in the area will notice and that should reduce confidence in the video's finer-grained physiological claims.

**3.3.4 — Somatopause.** GH secretion falls with age — on the order of a **two- to three-fold decline between the ages of 30 and 40**, with continued decline thereafter, alongside a reduction in slow-wave sleep. This is the factual basis for the anti-aging market, and it is real. What does not follow is that restoring youthful GH levels restores youthful outcomes; see ¶4.2.6.

**3.3.5 — Why pulsatility matters pharmacologically.** Two consequences:

1. **Feedback integrity.** A secretagogue acts on the pituitary's own GHRH receptor, so it **amplifies a pulse that somatostatin and IGF-1 feedback can still shut off**. The body retains control. Continuous exogenous agonist or continuous GH removes that control point.
2. **Downstream differentiation.** Continuous versus pulsatile GH produces measurably different hepatic responses — pulsatile GH preferentially drives IGF-1 and longitudinal growth, while continuous exposure shifts hepatic gene expression toward a different pattern. `[ANALYST ADD]` This is well established in rodent models and is the mechanistic justification for the "dimmer versus lamp" intuition.

**3.3.6 — Assessment of the metaphor.** `[SOURCE CLAIM]` "A dimmer switch type peptide or getting the entire new lamp type peptides." **Assessment: sound, and better than most of the video's other framings.** It correctly identifies that the relevant variable is *whether the intervention modulates an existing control loop or replaces it*. That is a cybernetic distinction as much as a pharmacological one, and it predicts the risk gradient: a dimmer can only turn a light up to its rated output and can be turned down; a lamp runs until the circuit is broken.

### 3.4 Receptor pharmacology and desensitization

**3.4.1** Continuous agonist exposure typically produces **tachyphylaxis** through receptor phosphorylation, β-arrestin recruitment, internalization, and downregulation. This is why the source's phrase "the signal never shuts off" (3:27) is not a complete description of what happens — a receptor that never shuts off tends to stop listening.

**3.4.2 — Biased agonism, and why semaglutide is not naive.** `[ANALYST ADD]` Semaglutide was selected partly for **cAMP-biased signalling with reduced β-arrestin recruitment** relative to native GLP-1, which limits receptor desensitization and internalization. The engineering is therefore not only about half-life; it is also about sustaining responsiveness across a seven-day window. **The source misses this**, and the omission matters because it is the strongest available counter to a naive "constant signal must cause desensitization" objection. The correct statement is: continuous occupancy *would* normally desensitize, and the drug was engineered specifically to resist that.

**3.4.3 — Why this cuts against the gray market.** For BPC-157, Epitalon, TB-500, and GHK-Cu, no equivalent engineering exists because no development program exists. There is no characterized receptor for several of them, no established potency assay, and therefore **no way for a vendor or a buyer to know whether a given vial contains a molecule with the intended activity at the intended concentration.** "99% pure" is a statement about a chromatogram, not about pharmacology.

### 3.5 Evidence grading scheme

**3.5.1** Claims in this report are graded on a five-level scheme, adapted for the fact that most of the underlying literature is preclinical:

| Level | Definition | Evidential weight |
|---|---|---|
| **E1** | Multiple randomized controlled trials, or meta-analysis, in humans; clinically meaningful endpoints | High |
| **E2** | At least one adequately powered RCT, or consistent smaller RCTs | Moderate |
| **E3** | Uncontrolled human studies, case series, or small trials with surrogate endpoints | Low |
| **E4** | Animal or in-vitro data only, mechanistically plausible | Very low for human efficacy |
| **E5** | Anecdote, tradition, or mechanism-based conjecture | Negligible |

**3.5.2** Two rules govern application. First, **E4 does not aggregate into E2** — ten rodent studies of the same compound remain E4 for human efficacy, because the translational failure rate is high and non-random. Second, **absence of evidence is not evidence of absence, but it is also not a licence to assume safety.** A compound with no human safety data has an *unknown* risk profile, and unknown is not the same as low.

### 3.6 Regulatory framework

**3.6.1 — Why this matters to a consumer.** The legal status of a peptide determines whether the vial in front of you was made under any quality system at all. This is the single largest determinant of the expected harm, larger than the choice of compound.

**3.6.2 — The pathways.**

| Pathway | What it is | Quality implication |
|---|---|---|
| **FDA-approved drug** | NDA/BLA holder, GMP manufacturing, approved indications | Highest assurance; recall and pharmacovigilance exist |
| **503A compounding** | State-licensed pharmacy, patient-specific prescription from a prescriber | Moderate; bulk substance must be monograph-compliant, an approved-drug component, or on the 503A bulks list |
| **503B outsourcing facility** | Registered outsourcing facility, larger scale | Moderate-high; subject to CGMP and FDA inspection |
| **"Research use only" (RUO)** | Not a legal pathway for human use. A labelling convention for laboratory reagents | **None.** No quality system, no sterility assurance, no lot traceability, no recall |

**3.6.3 — The Category system.** FDA's interim 503A policy sorted nominated bulk substances into categories. **Category 1**: nominated with sufficient supporting information; FDA generally does not intend to take enforcement action against a compounder using it, provided other conditions are met. **Category 2**: FDA has identified significant safety risks; these cannot be compounded. Critically — and this is what the source's error turns on — **Category 1 does not mean approved, and it does not mean lawful to sell to consumers.** It is an enforcement-discretion posture toward *compounders*.

**3.6.4 — The 2025 policy change.** `[ANALYST ADD]` The revised interim policy published in the *Federal Register* on **7 January 2025** **ended the categorization** of bulk drug substances into Categories 1, 2, or 3 for substances nominated on or after the publication date. Pre-existing Category 1 entries may continue within the policy's scope. The category system is therefore being phased out for new nominations — a fact that makes any claim of the form "compound X was reclassified to Category 1" doubly suspect, since the mechanism is being retired.

**3.6.5 — The RUO fiction.** A vendor selling "BPC-157, for research use only, not for human consumption" while also publishing **dosing charts and reconstitution guides** is not selling a laboratory reagent. It is selling a drug while using a label to avoid the obligations of selling a drug. This is the structural core of the gray market, and the source identifies it correctly (8:33) as a red flag. `[ANALYST ADD]` The legal logic is straightforward: the RUO label is a disclaimer of intended use; conduct demonstrating intended human use defeats the disclaimer.

---

## 4. COMPOUND-BY-COMPOUND TECHNICAL ANALYSIS

### 4.1 GLP-1 receptor agonists

**4.1.1 — Mechanism.** GLP-1 is an incretin: it amplifies glucose-dependent insulin secretion, suppresses glucagon, slows gastric emptying, and acts on hypothalamic and hindbrain circuits to reduce appetite. The receptor is a class B GPCR. The appetite effect is central as well as peripheral — this is why the drugs produce weight loss beyond what gastric slowing alone would explain.

**4.1.2 — Evidence level: E1.** Large cardiovascular and renal outcome trials in type 2 diabetes, plus dedicated obesity trials, constitute one of the strongest evidence bases in this entire report. This is the only compound class discussed here with completed Phase III programs and mortality-relevant endpoints.

**4.1.3 — The source's central warning, assessed.** `[SOURCE CLAIM]` "A good portion of that weight loss is muscle, gain the weight back, but not the muscle. They gain the fat back. So they're in a worse situation than when they started because your metabolic machine that helps you lose the weight is muscle."

**Assessment: the concern is correct and important; the certainty is too high.** Three components:

| Component | Status |
|---|---|
| A substantial fraction of weight lost is lean mass | **Supported.** Commonly reported in the range of roughly 20–40% of total weight lost, depending on population, rate of loss, and protein intake. |
| Weight is regained after cessation | **Supported.** In the STEP-1 extension, participants regained roughly two-thirds of lost weight within a year of stopping. |
| The regain is fat, not muscle | **Partially supported, overstated.** Some body-composition data show regain skewed toward fat, but this is not uniformly demonstrated across studies, and it is strongly modified by whether the patient resistance-trains and maintains protein intake during and after treatment. |
| "Worse situation than when they started" | **Not established.** Plausible as a risk in a sedentary, low-protein patient; not a general finding. |

**4.1.4 — The correct framing.** The lean-mass issue is real, is the main reason clinical guidance now pairs these agents with **resistance training and adequate protein**, and is a legitimate reason for caution. It is not a reason to conclude the drugs are net harmful — the cardiovascular outcome data argue strongly otherwise in the indicated population. The source's framing converts a **manageable complication** into a **reason for avoidance**, which is the predictable direction of bias for a channel whose business model is nutritional supplementation. **Confidence: moderate-high** in this reading.

**4.1.5 — What the source omits.** `[ANALYST ADD]` Not mentioned, and all material: gallstone and pancreatitis signals; delayed gastric emptying with aspiration risk under anaesthesia; the rodent thyroid C-cell tumour finding underlying the boxed warning; sarcopenia risk in older patients; the 2025 concern over **compounded** semaglutide dosing errors, where unapproved compounded product was associated with adverse events including dosing mistakes. That last omission is notable because it is squarely within the video's own supply-chain thesis and would have strengthened it.

**4.1.6 — Distinction worth preserving.** Prescribed, approved semaglutide and gray-market "research" semaglutide are different products with different risk profiles. The video discusses them as one thing. The regulatory and quality analysis in §5 applies only to the second.

### 4.2 Sermorelin and the GH axis

**4.2.1 — Identity.** Sermorelin is **GHRH(1-29)amide** — the first 29 residues of growth-hormone-releasing hormone, which retains full receptor activity. It is a GHRH receptor agonist on pituitary somatotrophs.

**4.2.2 — Pharmacokinetics.** Half-life on the order of **10–20 minutes**. This is the pharmacological basis of the "dimmer" claim: a short-acting secretagogue administered in a pulse produces a pulse, and the pituitary's own somatostatin and IGF-1 feedback remain operative.

**4.2.3 — The source's description, assessed.** `[SOURCE CLAIM]` "This peptide turns the dimmer switch up... it's not growth hormone. It's more like it's telling growth hormone to work more. It's sending a signal to the pituitary, which already makes growth hormone, and just turning up the dimmer switch."

**Assessment: mechanistically correct.** This is an accurate description of a GHRH-receptor agonist, and it is the clearest passage in the video. The distinction between "supplying the hormone" and "amplifying the endogenous signal" is the right distinction, and the source draws it cleanly.

**4.2.4 — What the source does not say.** `[ANALYST ADD]` Sermorelin's regulatory history is more complicated than "a peptide." It was approved as a **diagnostic** agent (Geref) for evaluating pituitary function, not for anti-aging or weight loss, and that product was discontinued. Its use for body composition or "optimization" is **off-label at best**. Its presence in compounded preparations depends on bulk-substance status that this analysis did not verify (¶9.3).

**4.2.5 — The substitution logic.** The source's implicit argument is that if you want more GH, you should raise your own rather than inject the hormone. **This is defensible.** Exogenous GH in adults carries a well-documented adverse profile — fluid retention, arthralgia, carpal tunnel syndrome, insulin resistance, and acromegalic changes with sustained exposure — and the 1990 Rudman study that launched the anti-aging GH market reported increased lean mass and decreased fat **alongside** a high rate of these effects, in a small sample, over a short period. `[ANALYST ADD]` No mortality or functional benefit has been established in healthy older adults.

**4.2.6 — The "natural" alternatives, assessed.** `[SOURCE CLAIM]` Sprinting and HIIT are "at the top of the list" for raising GH; sleep preserves it; fasting and low insulin raise it.

**Assessment: directionally correct, magnitude overstated.** Exercise, sleep, and energy restriction do raise GH — this is well established. But the effect is **transient and physiological**, not cumulative in the way a pharmacological intervention is, and the framing invites an invalid inference: that a bout of sprinting is a dose-equivalent substitute for a secretagogue. It is not. The honest version is that these interventions are worth doing **for their own sake** — cardiovascular fitness, insulin sensitivity, sleep quality, body composition — and that GH elevation is a marker of having done them, not the mechanism of benefit.

### 4.3 BPC-157

**4.3.1 — Identity.** "Body Protection Compound," a **15-residue** peptide (GEPPPGKPADDAGLV) derived from a protein found in human gastric juice. Notable for acid stability, which is why an oral form is used in some preparations.

**4.3.2 — Proposed mechanism.** `[ANALYST ADD]` Animal literature describes promotion of angiogenesis (VEGF receptor and eNOS pathways), upregulation of growth factor signalling, and accelerated healing in tendon, ligament, muscle, and GI mucosa models. There is **no established human receptor or signalling pathway** — which is precisely why it cannot be characterized the way a developed drug can, and why FDA's safety finding cites "complexities with regard to peptide-related impurities and API characterization."

**4.3.3 — Evidence level: E3 at best, effectively E4 for the claims made.** The source's own summary is accurate: "the research on rats is amazing... but almost all those studies were in rodents."

**4.3.4 — The human data the source cites, assessed.** `[SOURCE CLAIM]` Study 1: 12 people with knee pain, 200–400 µg intra-articular weekly for 4–8 weeks, 7 of 12 improved, benefit lasting 6 months. Study 2: 16 people, BPC-157 plus TB-500, 14 of 16 with significant pain reduction at 6–12 months.

**Assessment: these are case series, and they cannot support the inference drawn.** Specific problems:

| Problem | Consequence |
|---|---|
| No control arm | Regression to the mean and natural recovery are unaddressed; knee pain fluctuates |
| No blinding | Expectation effects unmeasured |
| Small n (12, 16) | Confidence intervals on a 7/12 response rate span nearly the whole plausible range |
| Unvalidated endpoints | "Significant improvement" is not a defined outcome measure |
| Intra-articular administration by a physician | Not reproducible by a consumer; the source does say this, correctly |
| Co-administration with TB-500 in study 2 | Cannot attribute effect to either agent |
| No safety monitoring reported | The thing most needed is the thing least measured |

**4.3.5 — The cancer claim.** `[SOURCE CLAIM]` "BPC-157 does not trigger cancer, but if you have an active cancer, probably not a good idea to take it because it's going to increase more blood flow to a tumor potentially."

**Assessment: the conclusion is defensible; the premise is over-asserted, and the two are in tension.** The statement "does not trigger cancer" is a **negative safety claim** — the hardest kind to support, requiring either mechanistic exclusion or large-scale surveillance, neither of which exists. The video then immediately supplies the mechanistic reason to doubt it (angiogenesis, which tumours exploit). The logically consistent formulation is: *no human carcinogenicity signal has been established; the angiogenic mechanism supplies a theoretical concern that cannot presently be excluded; therefore avoid in active or recent cancer.* That is what the source means, and it is close to what it says — but "does not trigger cancer" is the sentence a viewer will remember, and it is the one that is not supported.

**4.3.6 — Regulatory status.** Per ¶2.5.1: listed by FDA under **"nominated but withdrawn"** with a **published significant-safety-risk finding** covering immunogenicity risk and API characterization difficulty. **Not Category 1. Not prescribable on the basis claimed.**

### 4.4 TB-500

**4.4.1 — Identity.** A synthetic fragment of **thymosin β4**, corresponding to its actin-binding region. Frequently co-sold with BPC-157, as in the source's study 2.

**4.4.2 — Mechanism.** `[ANALYST ADD]` Thymosin β4 sequesters G-actin and promotes actin polymerization; the fragment is associated in animal models with cell migration, wound healing, and reduced inflammation. **Evidence level: E4.** No human RCTs located.

**4.4.3 — Source coverage.** The source mentions TB-500 only as a co-administered agent in the 16-person series. It does not characterize it. Given that TB-500 appears in FDA's withdrawn table with its own safety finding, the omission is a coverage gap rather than an error.

**4.4.4 — Regulatory status.** `[ANALYST ADD]` Listed under "nominated but withdrawn" with a published safety-risk finding. Not a lawful consumer product.

### 4.5 GHK-Cu

**4.5.1 — Identity.** Glycyl-L-histidyl-L-lysine complexed with copper(II) — a **tripeptide**. Naturally occurring in plasma and saliva; declines with age.

**4.5.2 — Mechanism.** `[ANALYST ADD]` Proposed roles in collagen synthesis, wound healing, antioxidant defence, and copper transport. In-vitro and animal evidence for fibroblast stimulation and collagen deposition is reasonably consistent. Human evidence is limited to small trials, mostly cosmetic, with surrogate endpoints (skin elasticity, wrinkle depth).

**4.5.3 — Source claim.** `[SOURCE CLAIM]` "This specific peptide helps with collagen synthesis and tissue remodeling using it topically on their face, not through injections. And the results are pretty significant topically."

**Assessment: the mechanism claim is fair; "pretty significant" is unsupported without a quantified effect size and a comparator.** Cosmetic endpoints are highly susceptible to expectation effects, and the trials are small. Evidence level: **E2–E3** for modest cosmetic effect; **E5** for any claim beyond that.

**4.5.4 — A distinction the source gets right by accident.** FDA's safety finding for GHK-Cu applies to **injectable routes of administration** — the entry is explicitly headed "GHK-Cu (for injectable routes of administration)" and cites aggregation and immunogenicity risk. **Topical use is a materially different risk profile**: the skin barrier, the absence of systemic exposure, and the absence of needle-borne contamination. The source recommends topical use, and on this narrow point the recommendation is the lower-risk one. This is worth stating explicitly because it is the one place where the video's advice and the risk analysis converge.

### 4.6 Epitalon

**4.6.1 — Identity.** A **tetrapeptide**, Ala-Glu-Asp-Gly (AEDG), developed by the Khavinson group at the St Petersburg Institute of Bioregulation and Gerontology.

**4.6.2 — Claimed mechanism.** Telomerase activation, with downstream effects on telomere length and replicative lifespan. Also described in the Russian literature as a pineal regulator.

**4.6.3 — The source's characterization, assessed.** `[SOURCE CLAIM]` "In flies, mice and rats, it does extend the lifespan. Now in humans, the only studies that are out there are from a single Russian research group in 2003 and also 2006. And neither was independently replicated by any outside institution."

**Assessment: this is the most epistemically careful passage in the video, and it is essentially correct.** The elements that make it correct:

- It distinguishes the **animal** result from the **human** claim.
- It identifies the **single-group** problem, which is the dominant threat to validity in this literature — a research programme developed by one group, published largely in its own journal, with no independent replication.
- It does not assert that the human claim is false; it asserts that the support is inadequate. That is the right posture.

**4.6.4 — What is missing.** `[ANALYST ADD]` The telomerase claim is the load-bearing one and it is the least secure. Telomerase activation is not a neutral intervention: telomerase is expressed in most cancers, and constitutive activation is one of the hallmarks of oncogenesis. A compound claimed to induce telomerase in humans without independent replication, without dose-response characterization, and without long-term cancer surveillance is not a longevity intervention; it is an **unquantified oncogenic hypothesis being sold as a supplement.** The source does not make this point, and it is the most important thing that can be said about Epitalon.

**4.6.5 — Regulatory status.** `[ANALYST ADD]` FDA lists epitalon under "nominated but withdrawn" with a safety finding citing immunogenicity risk from aggregation and peptide-related impurities, and stating that **no safety-related information was identified for the proposed route of administration.** That last clause is unusually blunt: it means FDA found nothing to evaluate, not that it found nothing concerning.

### 4.7 Collagen peptides (the control case)

**4.7.1 — Identity.** Hydrolysed collagen — gelatin broken down enzymatically into fragments averaging **2–5 kDa**. Not a signalling peptide. It is a **protein hydrolysate sold as food**, and the "peptide" in the name denotes molecular size, not mechanism.

**4.7.2 — Why it belongs in this report.** It is the source's own example of the "bricks" category, and it functions as the **control case** that makes the taxonomy testable. If the bricks/blueprint distinction is real, the bricks should be low-risk and modestly effective, and the blueprints should be higher-risk and less well evidenced. That is exactly the observed pattern.

**4.7.3 — Evidence level: E2–E3.** Small RCTs support modest improvements in skin hydration and elasticity, and modest reductions in joint pain in some populations. Effects are small, heterogeneity is high, and publication bias is likely given industry funding. **But the risk profile is that of a food ingredient**, which is the decisive difference.

**4.7.4** This is the case that demonstrates why the report's framing matters. A consumer asking "do peptides work?" is asking an unanswerable question. A consumer asking "what is the evidence and risk for this specific molecule, at this specific route, from this specific supply chain?" is asking an answerable one. The source's taxonomy supports the second question and does not quite ask it.

---

## 5. SUPPLY-CHAIN THREAT MODEL

### 5.1 Structure of the gray market

**5.1.1 — The chain.** `[ANALYST ADD]` A typical gray-market peptide reaches a consumer through five links, none of which is regulated as a drug supply chain:

```
Bulk API synthesis (largely China)
   │   protected amino acids, SPPS, cleavage, crude purification
   ▼
Bulk distributor / repackager
   │   aliquots into vials; labelling; sometimes lyophilisation
   ▼
"Research chemical" vendor (web store, often offshore)
   │   RUO labelling; COA (often vendor-supplied, sometimes fabricated)
   ▼
Payment / logistics (card processors, crypto, Telegram, reshippers)
   │
   ▼
Consumer (reconstitutes with bacteriostatic water, self-injects)
```

**5.1.2 — Where quality can be lost.** At every link. There is no point in this chain at which a regulator verifies identity, potency, sterility, or endotoxin content. The COA — when one exists — is typically generated by the **vendor**, not by an independent party, and is frequently a single HPLC run on a single vial from a single lot.

**5.1.3 — Why the consumer cannot close the gap.** Verifying a peptide requires equipment the consumer does not have: LC-MS/MS for identity, HPLC for purity, LAL assay for endotoxin, culture for sterility, ICP-MS for elemental impurities. The consumer's available signals are all **proxies** — price, labelling, vendor reputation, COA presence — and every one of them is cheap to fake. This is a market with **severe asymmetric information**, which is the textbook condition for a lemons market: quality is unobservable, so price competition drives quality down.

### 5.2 Failure modes

**5.2.1** Ordered by expected harm:

| # | Failure | Mechanism | Detection | Consequence |
|---|---|---|---|---|
| **F-1** | **Non-sterility** | No terminal sterilisation; no aseptic fill | Requires culture; not on a COA | Abscess, cellulitis, sepsis, endocarditis |
| **F-2** | **Endotoxin** | Gram-negative LPS from synthesis/purification; survives 0.22 µm filtration | LAL assay only | Fever, rigors, hypotension, shock |
| **F-3** | **Identity error** | Wrong sequence, wrong peptide, wrong concentration | LC-MS/MS + quantitative assay | No effect, or unintended pharmacological effect |
| **F-4** | **Immunogenicity** | Aggregates, impurities, non-human sequences; SC and nasal routes amplify | Not detectable by the consumer | Anti-drug antibodies; possible neutralisation of the endogenous peptide |
| **F-5** | **Elemental contamination** | Catalysts, reagents, water quality; arsenic, lead | ICP-MS only | Cumulative toxicity; arsenic in its more toxic inorganic form |
| **F-6** | **Injection injury** | Technique, site, contamination, intravascular injection | Clinical | Infection, nerve or vessel injury, granuloma |
| **F-7** | **Residual solvents / synthesis byproducts** | Incomplete purification | GC / specialised assays | Variable; some are mutagenic |
| **F-8** | **Dose error** | Reconstitution arithmetic, unit confusion (mg vs µg), "peptide calculator" apps | Clinical | Overdose; the compounded-semaglutide experience is the precedent |

**5.2.2 — The aggregation point deserves emphasis.** `[ANALYST ADD]` FDA's advisory-committee briefing on BPC-157 notes that peptides have an inherent tendency to aggregate, that aggregates are a risk factor for immunogenicity, and that **subcutaneous and nasal routes increase immunogenicity relative to oral or rectal**. It further notes that an immune response can produce **neutralising antibodies against the endogenous counterpart** of the peptide — meaning the harm is not limited to the injected molecule. No studies formally investigating BPC-157 immunogenicity were identified. This is a mechanism by which a "harmless" peptide can produce durable harm, and it is invisible to every consumer-facing quality signal.

### 5.3 What a COA does and does not prove

**5.3.1** The source's argument here is correct and is the most technically useful part of the video: a COA showing 99% purity does not mean the product is safe, because **purity is one question and safety is several.**

**5.3.2 — The test-to-question mapping.**

| Question | Required test | Does HPLC answer it? |
|---|---|---|
| Is the main peak the intended molecule? | LC-MS/MS, amino acid analysis, sequencing | **No** — HPLC separates by hydrophobicity; a wrong-sequence peptide of similar hydrophobicity co-elutes |
| How much of the material is the intended species? | HPLC-UV (% area) | **Yes**, for chromatographically visible material |
| Are there bacterial endotoxins? | LAL / rFC assay | **No** — LPS has no chromophore at peptide wavelengths |
| Is it sterile? | Culture / sterility testing | **No** — a bacterial cell contributes no UV peak |
| Are there heavy metals? | ICP-MS | **No** |
| Are there residual solvents? | GC | **No** |
| Is the counterion and water content correct? | Karl Fischer, ion chromatography | **No** — so "% purity" can be "% of a smaller mass than labelled" |
| Is it the stated concentration? | Quantitative assay | **No** — purity ≠ content |

**5.3.3 — The structural point.** A chromatogram answers **one** question — what proportion of the UV-visible material is the intended species — and it is routinely filed as evidence about five. The source states this well ("a vial could score like 99% pure but be loaded with arsenic"), and the observation is worth preserving because it is the single most useful thing a consumer can learn from the video.

**5.3.4 — The sterility-filter fallacy.** `[ANALYST ADD]` A 0.22 µm filter removes bacteria but **not endotoxin**, because LPS is a molecule of roughly 10–20 kDa, orders of magnitude smaller than the pore. "Filtered" is therefore not "endotoxin-free," and this is a common and dangerous conflation.

### 5.4 The statistics: traceable and untraceable

**5.4.1 — The source's numbers.** `[SOURCE CLAIM]` "80 to 90% of all raw peptide materials originate overseas, usually from China... 30% contained the wrong amino acid sequence... 65% failed bacterial endotoxin limits... Some batches contain arsenic at 10 times the safety limits."

**5.4.2 — Traceability assessment.** `[ANALYST ADD]` This analysis traced two of the four figures and could not trace two.

| Figure | Status | Detail |
|---|---|---|
| 80–90% of raw material from overseas/China | **Plausible, unsourced** | China is the dominant global supplier of peptide APIs and protected amino acids. The direction is almost certainly right; the specific range is not attributed. |
| 30% wrong amino acid sequence | **Traceable — different population** | Janvier et al., *Talanta* (2018): systematic screening of the **ten most frequently seized falsified polypeptide drugs on the Belgian market**, from three suspected illegal internet pharmacies. Found ~30% with incorrect sequences, purity 5–75%. |
| Arsenic at 10× safety limit | **Traceable — same study** | Same study: elemental impurities including arsenic and lead; arsenic concentrations up to ten times the ICH limit for parenteral drugs, and **speciation showed all of it in the more toxic inorganic form.** |
| 65% failed endotoxin limits | **No traceable primary source located** | Attributed in secondary commercial sources to a 2020 *Drug Testing and Analysis* paper. This analysis could not confirm that attribution, and at least one review explicitly states it could find no reliable primary source for the figure. Treat as **unverified.** |

**5.4.3 — The generalisation problem.** Even the traceable figures do not establish a base rate for research-peptide vials. Janvier et al. analysed **seized counterfeit pharmaceuticals** — a population selected precisely because it was already suspected of being falsified, and consisting of finished drug products rather than RUO vials. Extrapolating "30% of gray-market peptides have the wrong sequence" from that sample is an **inference, not a measurement.** It may well be approximately right. It has not been shown to be right.

**5.4.4 — Why the distinction matters analytically.** A claim with a real citation attached to a different population is more dangerous than an unsourced claim, because the citation supplies unearned authority. The correct formulation is: *systematic screening of falsified peptide products has found sequence errors, sub-95% purity, and elemental contamination at multiples of safety limits; the same supply chain serves the RUO market; a comparable failure rate in RUO vials is plausible but unmeasured.*

### 5.5 Synthesis impurity arithmetic

**5.5.1** `[ANALYST ADD]` The reason peptide purity is hard is arithmetic. Solid-phase peptide synthesis (SPPS) adds one residue per cycle at a per-cycle coupling efficiency below 100%. For a chain of length *n*:

```
yield of full-length product ≈ (efficiency)^n
```

**5.5.2** For a 15-mer such as BPC-157:

| Per-cycle efficiency | Full-length yield |
|---|---|
| 0.999 | 98.5% |
| 0.99 | **86.0%** |
| 0.98 | 73.9% |
| 0.95 | 46.3% |

**5.5.3 — Implications.** At a routine 99% coupling efficiency, a 15-residue peptide is **~86% full-length before purification** — meaning ~14% is truncated or deletion sequences, many of which are **isobaric or near-isobaric with the target and therefore hard to separate and invisible to a purity percentage that merely integrates the main peak.** A 30-residue GLP-1 analogue is worse. This is why real pharmaceutical peptide manufacture requires orthogonal purification, rigorous characterization, and impurity profiling, and why an RUO vial with a single HPLC trace is not evidence of a well-characterized product.

**5.5.4 — The deeper point.** Impurities are not inert. `[ANALYST ADD]` Work on crude versus purified peptide preparations has shown that biological activity present in a crude (low-purity) preparation can **disappear** when the same peptide is purified — meaning some observed "effects" in the literature, and by extension in user reports, may be attributable to contaminants rather than to the peptide. This cuts both ways: it undermines claims of efficacy and it supplies an additional mechanism of harm.

---

## 6. THE CANCER QUESTION

**6.1** The source addresses two distinct questions and runs them together: (a) do peptides cause cancer, and (b) can someone with cancer take peptides. They require different answers.

**6.2 — Question (a): causation.** No human carcinogenicity signal has been established for any compound discussed here, with the partial exception of the GH/IGF-1 axis, where the epidemiological picture is more developed (¶6.4). But absence of a signal in a population that is not being systematically monitored is weak evidence. There is no registry, no post-market surveillance, and no long-term follow-up for gray-market peptide users. **The correct statement is "not established," not "no."**

**6.3 — Question (b): use in existing cancer.** The source's answer — avoid — is defensible on mechanism:

| Compound class | Mechanistic concern in active malignancy |
|---|---|
| Angiogenic (BPC-157) | Tumour growth depends on neovascularisation; promoting angiogenesis is the wrong direction |
| GH/IGF-1 raising (sermorelin, and other secretagogues) | IGF-1 is mitogenic and anti-apoptotic; the axis is implicated in several tumour types |
| Telomerase-activating (Epitalon) | Telomerase is expressed in most cancers; constitutive activation is a canonical oncogenic step |
| GLP-1 agonists | Not directly oncogenic in humans; the rodent thyroid C-cell finding has not translated, but the boxed warning exists |

**6.4 — The GH/IGF-1 axis, expanded.** `[ANALYST ADD]` The association between circulating IGF-1 and risk of prostate, breast, and colorectal cancer is reasonably consistent in epidemiology, though effect sizes are modest and causality is not established. Acromegaly — endogenous GH excess — is associated with increased colorectal neoplasia, which is the closest thing to a natural experiment. This is the strongest available argument that **raising GH pharmacologically is not a neutral act**, and it applies to secretagogues as well as to exogenous hormone, since both raise the same downstream mediator.

**6.5 — Assessment.** The source's practical conclusion (avoid in active cancer) is **sound**. Its framing ("BPC-157 does not trigger cancer") is **over-asserted** and is the sentence most likely to be misremembered. **Confidence: high.**

---

## 7. INDICATORS AND WARNINGS (I&W)

**7.1** Red flags for a consumer evaluating a peptide product or vendor. Ordered by discriminating power — the first four are near-decisive.

| ID | Indicator | Why it matters | Weight |
|---|---|---|---|
| **W-1** | "For research use only / not for human consumption" **plus** published dosing charts or reconstitution guides | Intended human use contradicts the label; the RUO disclaimer is defeated by the vendor's own conduct | **Decisive** |
| **W-2** | Transaction conducted over Telegram, DM, or a platform that prohibits the sale | Removes payment recourse, chargeback, and any audit trail | **Decisive** |
| **W-3** | Price far below the market for the same compound | Peptide synthesis has a real cost floor; below it, either the quantity or the identity is wrong | **Near-decisive** |
| **W-4** | COA from a lab with no independent website, phone number, or physical address | The certificate is unverifiable, hence not evidence | **Near-decisive** |
| **W-5** | COA shows HPLC purity only — no LC-MS identity, no LAL endotoxin, no sterility | Purity answers one question of five (¶5.3) | High |
| **W-6** | No lot number, no expiry, no batch traceability on the vial | No recall pathway; no way to link an adverse event to a batch | High |
| **W-7** | Vendor claims FDA approval, or cites a "2026 reclassification" | Regulatory status is checkable and frequently misstated (¶2.5.1) | High |
| **W-8** | No prescription, no clinician review of labs or history | Removes the only gatekeeper in the chain | High |
| **W-9** | Claims of a single compound addressing unrelated conditions (fatigue, joints, cognition, longevity) | Pan-indication claims are a signature of marketing rather than pharmacology | Moderate |
| **W-10** | Testimonials in place of data; no effect sizes; no comparators | Standard supplement-marketing pattern | Moderate |
| **W-11** | "Pharmaceutical grade" used as a quality claim | Not a regulated term; carries no defined meaning | Moderate |
| **W-12** | Product requires self-reconstitution with bacteriostatic water | Introduces a contamination and arithmetic-error vector controlled by the user | Moderate |

**7.2 — The compound-specific warning.** For **Epitalon**, the telomerase-activation claim is itself the warning, independent of supply chain: it is an unquantified oncogenic hypothesis with no independent replication and no long-term surveillance. For **BPC-157**, the specific warning is angiogenic promotion in anyone with active or recent malignancy. For **sermorelin and other GH secretagogues**, it is the IGF-1 axis.

**7.3 — The meta-indicator.** The strongest single predictor of harm is not the molecule; it is **whether the product entered through a licensed supply chain.** A prescription for an approved drug dispensed by a licensed pharmacy and a vial of "BPC-157, RUO" from an offshore web store differ by orders of magnitude in expected harm, and they differ in nothing about the molecule's name.

---

## 8. DECISION FRAMEWORK

**8.1 — Scope and limits.** This section describes how a careful analyst would structure the decision. It is **not** a recommendation to use any substance, and it is **not** medical advice. It deliberately contains no doses, no protocols, and no reconstitution arithmetic.

**8.2 — The governing principle.** The evidence and risk analysis supports one clear ordering: **interventions should be ranked by evidence quality and supply-chain integrity jointly, not by plausibility of mechanism.** A well-characterized molecule from an unverifiable vial is a higher-risk proposition than a modestly effective molecule from a licensed pharmacy, because the variance in product quality dominates the variance in pharmacology.

**8.3 — Structure of the decision.**

| Tier | Content | Rationale |
|---|---|---|
| **Tier 0 — Foundation** | Sleep, resistance training, protein sufficiency, alcohol moderation, management of any diagnosed condition | Highest evidence, lowest risk, addresses root causes the source itself identifies |
| **Tier 1 — Clinician-gated, approved** | Any FDA-approved agent, prescribed, dispensed through a licensed pharmacy, with monitoring | Evidence base exists; quality assured; adverse events reportable |
| **Tier 2 — Clinician-gated, compounded** | Compounded preparations only where a lawful 503A/503B pathway exists and the bulk substance status has been verified | Intermediate; requires active verification of both prescriber and pharmacy |
| **Tier 3 — Not advised** | Self-sourced injectables from RUO-labelled vendors | Dominant risk is product quality and injection injury, not pharmacology |

**8.4 — Verification steps for any Tier 2 decision.**

1. **Confirm regulatory status on FDA's live page**, not on a vendor page, a forum, or a video. The Category tables change; see ¶9.1.
2. **Confirm the pharmacy's status** — 503A licensed in your state, or 503B registered. Ask for the registration.
3. **Read the COA and check what was actually tested** against the mapping in ¶5.3.2. If it shows only HPLC purity, the COA is not evidence of safety.
4. **Verify the testing lab independently** — an address, a phone number, a website that predates the product.
5. **Ask what the monitoring plan is.** Any intervention that raises GH, IGF-1, or suppresses appetite has measurable parameters; a prescriber with no monitoring plan is not providing care.
6. **Establish the stop criteria in advance** — what finding would end the trial. This is the same pre-commitment logic that applies to any intervention whose effects are hard to evaluate from inside.

**8.5 — The root-cause question, which the source gets right.** `[SOURCE CLAIM]` "Why are you even wanting to take these peptides in the first place? What problem are you trying to solve and what is at the root cause of that problem?"

**Assessment: this is the best question in the video and it is asked too late.** It appears at 10:14, after ten minutes of compound-by-compound detail. Asked first, it would have reframed everything that followed: a tendon that will not heal, a body composition goal, and a desire to slow ageing are three different problems with three different evidence bases, and only one of them plausibly involves a peptide.

**8.6 — Adverse-event protocol.** If a reaction occurs after any injection: seek emergency care, **bring the vial and the packaging**, and report the event. `[ANALYST ADD]` In the United States, an adverse event can be reported to FDA MedWatch. The vial is the only evidence that will allow anyone to determine what was administered, which is precisely why lot traceability (W-6) matters prospectively.

---

## 9. INTELLIGENCE GAPS AND COLLECTION REQUIREMENTS

**9.1 — Regulatory status (priority: critical).** The ¶2.5.1 finding is time-sensitive and was established from FDA's live page plus a secondary correction article. **Requirement:** re-check the FDA bulk-substance page, the *Federal Register* notices from 2025–2026, and HHS press releases for any February 2026 action. **This is the one gap that must be closed before any decision depends on it.**

**9.2 — The 65% endotoxin figure (priority: high).** No primary source located. **Requirement:** obtain the alleged 2020 *Drug Testing and Analysis* paper, or establish that the figure has no primary source and should be dropped from the claim set entirely.

**9.3 — Sermorelin's bulk-substance status (priority: moderate).** Not verified in this analysis. Sermorelin's history — approved as a diagnostic, later discontinued — makes its compounding status non-obvious. **Requirement:** check the 503A bulks list and Category tables directly.

**9.4 — The three named testing laboratories (priority: moderate).** Janoshik Analytical is known; **Covera Labs** and **Freedom Diagnostics** could not be verified and may be transcription artifacts. **Requirement:** confirm names and existence; if the names are wrong, the source's most actionable recommendation is unusable as stated.

**9.5 — BPC-157 human literature (priority: moderate).** The two series the source cites (n=12; n=16 with TB-500) were not located in this analysis. **Requirement:** identify the publications, their journals, their funding, and whether they were peer reviewed. The quality of these two studies determines whether BPC-157's human evidence is "E3, weak" or "E5, effectively anecdotal."

**9.6 — Janvier et al. full text (priority: moderate).** The 30% and arsenic figures are cited here from secondary descriptions plus the abstract. **Requirement:** read the full paper to confirm the sample, the assay methods, and the denominators.

**9.7 — GLP-1 body composition (priority: low).** The "regain is fat not muscle" claim needs a specific trial-level source. **Requirement:** locate body-composition substudy data on regain, with attention to whether resistance training and protein intake were controlled.

**9.8 — Epitalon replication (priority: low).** The claim that no outside institution has replicated the Khavinson group's work is asserted by the source and is consistent with this analysis's impression, but has not been systematically verified. **Requirement:** a citation search for AEDG/Epitalon outside the originating group.

---

## 10. KEY JUDGMENTS WITH CONFIDENCE

| ID | Judgment | Confidence |
|---|---|---|
| **KJ-1** | The source's regulatory claim — that 14 peptides were reclassified to Category 1 in February 2026, making BPC-157 prescribable — is **likely false**. FDA lists BPC-157 under "nominated but withdrawn" with a live safety-risk finding. | **Moderate-high** |
| **KJ-2** | The probable error mechanism is an inversion of the 22 April 2026 page restructure: twelve peptides left Category 2 by **nomination withdrawal**, which is a move *away* from a lawful pathway, not toward one. | **Moderate** |
| **KJ-3** | "Peptide" is a molecular format, not a drug class; conflating GLP-1 receptor agonists with BPC-157 is the category error underlying most consumer confusion. The source gets this right. | **High** |
| **KJ-4** | The dimmer/lamp distinction is pharmacologically real: amplifying endogenous pulsatile signalling preserves feedback control; imposing continuous exogenous occupancy overrides it. | **High** |
| **KJ-5** | The source's GH pulse frequency is wrong (90 min vs. ~3 h / 6–8 pulses daily); the 90-minute figure is pulse *duration*. | **High** |
| **KJ-6** | The dominant expected harm for every non-approved compound here is **product quality and injection injury**, not pharmacological effect. Supply chain dominates pharmacology. | **High** |
| **KJ-7** | The supply-chain statistics are **partially traceable**: 30% sequence error and 10× arsenic trace to Janvier et al. 2018, but that study examined seized counterfeit pharmaceuticals, not RUO vials; the 65% endotoxin figure has no located primary source. | **Moderate-high** |
| **KJ-8** | A COA showing HPLC purity is evidence about one question and is routinely presented as evidence about five; it says nothing about identity, endotoxin, sterility, or elemental contamination. The source states this correctly. | **High** |
| **KJ-9** | The Epitalon telomerase claim is the most hazardous in the video: an unreplicated oncogenic hypothesis presented as a longevity intervention, with no long-term surveillance. The source's replication caveat is good but stops short of the implication. | **Moderate-high** |
| **KJ-10** | The GLP-1 lean-mass warning is legitimate and important; the "worse off than when they started" conclusion is not established, and the framing reflects a commercial bias toward purchasable alternatives. | **Moderate-high** |
| **KJ-11** | The source is more epistemically careful than the genre norm on evidence limitations, and materially unreliable on regulatory status. It should be used for orientation and supply-chain warnings, not for sourcing or access decisions. | **High** |

---

## APPENDIX A — GLOSSARY

| Term | Definition |
|---|---|
| **503A / 503B** | Sections of the FD&C Act governing traditional compounding pharmacies (503A) and outsourcing facilities (503B). |
| **Aggregation** | Peptides associating into multi-chain species; a risk factor for immunogenicity and loss of potency. |
| **Biased agonism** | Preferential activation of one signalling pathway over another at the same receptor; semaglutide is cAMP-biased with reduced β-arrestin recruitment. |
| **Category 1 / 2** | FDA interim-policy categories for nominated bulk substances: 1 = may be eligible, enforcement discretion generally applies; 2 = significant safety risks identified, may not be compounded. |
| **COA** | Certificate of Analysis — a document reporting test results for a lot; its value depends entirely on who performed which tests. |
| **DPP-4** | Dipeptidyl peptidase-4; cleaves native GLP-1 at Ala8, giving it a ~2-minute half-life. |
| **Endotoxin** | Lipopolysaccharide from gram-negative bacteria; pyrogenic; not removed by 0.22 µm filtration; detected by LAL assay. |
| **GHRH** | Growth-hormone-releasing hormone; hypothalamic stimulator of pituitary GH release. Sermorelin is GHRH(1-29). |
| **HPLC** | High-performance liquid chromatography; separates by hydrophobicity; gives % area purity but not identity. |
| **ICP-MS** | Inductively coupled plasma mass spectrometry; the method for elemental impurities such as arsenic and lead. |
| **IGF-1** | Insulin-like growth factor 1; principal downstream mediator of GH; mitogenic and anti-apoptotic. |
| **LAL** | Limulus amoebocyte lysate assay; the standard bacterial endotoxin test. |
| **LC-MS/MS** | Liquid chromatography tandem mass spectrometry; the method for confirming molecular identity. |
| **RUO** | "Research use only" — a labelling convention for laboratory reagents; **not** a legal pathway for human use. |
| **Somatopause** | Age-related decline in GH secretion; roughly two- to three-fold between ages 30 and 40. |
| **Somatostatin** | Hypothalamic inhibitor of GH release; the counterweight to GHRH. |
| **SPPS** | Solid-phase peptide synthesis; stepwise chain assembly with sub-quantitative per-cycle yield. |
| **Tachyphylaxis** | Rapid loss of response to a drug on repeated or continuous administration. |

---

## APPENDIX B — CHRONOLOGY

| Year | Event | Relevance |
|---|---|---|
| 1953 | Du Vigneaud synthesizes oxytocin | First peptide synthesis; establishes the field |
| 1963 | Merrifield develops SPPS | Makes peptide manufacture routine — and impurity-prone |
| 1983 | Native GLP-1 sequence characterized | Starts the incretin field |
| 1990 | Rudman et al., GH in elderly men | Launches the anti-aging GH market; benefits with substantial adverse effects |
| 1993 | BPC-157 first described (gastric juice protein derivative) | Origin of the most-sold gray-market peptide |
| 1997 | Sermorelin approved as a diagnostic (Geref) | Approved for pituitary testing, not anti-aging; later discontinued |
| 2003 / 2006 | Khavinson group Epitalon studies | The entire human evidence base; never independently replicated |
| 2005 | Exenatide approved | First GLP-1 receptor agonist |
| 2010 | Liraglutide approved | Fatty-acid acylation extends half-life to ~13 h |
| 2017 | Semaglutide approved | ~165 h half-life; once weekly |
| 2018 | **Janvier et al., *Talanta*** | Seized falsified peptides: 30% wrong sequence, purity 5–75%, arsenic up to 10× limit |
| 2021 | STEP-1 published | Semaglutide obesity trial; establishes the modern class |
| 2022 | STEP-1 extension | ~Two-thirds of lost weight regained within a year of stopping |
| Sep 2023 | FDA moves BPC-157 and others to Category 2 | Significant-safety-risk finding |
| Jan 2025 | Revised 503A interim policy (*Federal Register*) | Ends Category 1/2/3 assignment for new nominations |
| Feb 2026 | **Claimed** peptide reclassification to Category 1 | **Unverified; likely a misreading** |
| 22 Apr 2026 | FDA restructures the Category 2 page | Twelve peptides move to "nominated but withdrawn"; safety findings remain |
| 2026 | Tirzepatide and successors in wide use | Dual/triple agonism; longer half-lives |

---

## APPENDIX C — CLAIM LEDGER

| # | Claim | Type | Evidentiary status | Assessment |
|---|---|---|---|---|
| C-1 | A peptide is a short amino acid chain | Definitional | Verified | Sound |
| C-2 | Peptides are "messages"; amino acids are "bricks" | Framing | — | Sound and useful |
| C-3 | Steroids derive from cholesterol, peptides do not | Factual | Verified | Sound |
| C-4 | GH is released in pulses | Factual | Verified | Sound |
| C-5 | GH pulses occur every 90 minutes | Factual | **False** | ~6–8/day, ~every 3 h |
| C-6 | Sermorelin amplifies endogenous GH rather than replacing it | Mechanistic | Verified | Sound; best passage in the video |
| C-7 | Native GLP-1 has a very short half-life | Factual | Verified | Sound (~1.5–2 min) |
| C-8 | GLP-1 agents act for seven days | Factual | **True for semaglutide only** | Class-level statement is false |
| C-9 | A substantial fraction of GLP-1 weight loss is lean mass | Factual | Verified | Sound; ~20–40% |
| C-10 | Regain is fat, not muscle | Factual | Partially supported | Overstated |
| C-11 | GLP-1 users end up "worse than when they started" | Inferential | Not established | Plausible risk, not a general finding |
| C-12 | BPC-157 heals tendon/ligament in animals | Factual | Verified | Sound; E4 for humans |
| C-13 | Human BPC-157 evidence is limited to small series | Factual | Verified | Sound |
| C-14 | BPC-157 does not trigger cancer | Safety | **Over-asserted** | Not established; angiogenic concern |
| C-15 | GHK-Cu supports collagen synthesis topically | Mechanistic | Verified (mechanism) | Effect size unquantified |
| C-16 | Epitalon extends lifespan in animals | Factual | Consistent with record | Single group |
| C-17 | Epitalon human data: 2003, 2006, never replicated | Factual | Consistent | Sound; best epistemic passage |
| C-18 | Epitalon activates telomerase | Mechanistic | Unverified | Load-bearing and unsecured |
| C-19 | 80–90% of raw peptide material is foreign | Factual | Plausible, unsourced | Direction right, figure unattributed |
| C-20 | 30% wrong sequence | Statistic | Traceable, different population | Not a base rate for RUO vials |
| C-21 | 65% endotoxin failure | Statistic | **No source located** | Unverified |
| C-22 | Arsenic at 10× limit | Statistic | Traceable, same study | Sound as to that study |
| C-23 | HPLC does not test metals, endotoxins, sterility | Technical | Verified | **Correct and important** |
| C-24 | 99% pure can still be contaminated | Technical | Verified | Sound |
| C-25 | RUO label + dosing charts = red flag | Regulatory | Verified | Sound; decisive indicator |
| C-26 | **FDA reclassified 14 peptides to Category 1 (Feb 2026)** | Regulatory | **Likely false** | See ¶2.5.1 |
| C-27 | **A doctor can prescribe BPC-157 now** | Regulatory | **Likely false** | See ¶2.5.1 |
| C-28 | Exercise, sleep, fasting raise GH | Factual | Verified | Sound; magnitude overstated |
| C-29 | Zinc, vitamin C, glycine, magnesium support healing | Nutritional | Plausible | Correct but commercially aligned |
| C-30 | Ask what problem you are solving at the root | Prescriptive | — | **Best question in the video** |

---

## APPENDIX D — VERBATIM EXTRACTS (timestamped, lightly corrected)

**D-1** [0:39] "A peptide is made from amino acids. A peptide is a very short chain. Versus, like, if you were to eat a steak — a piece of protein — that's a very long chain. They're short chains that are basically messages that will give a signal to tell the body to do a certain thing. So look at them like a blueprint."

**D-2** [2:18] "Just look at peptides from two different viewpoints. You have a dimmer-switch-type peptide, or getting-the-entire-new-lamp-type peptides."

**D-3** [2:30] "Your pituitary gland makes growth hormone on a pulse. So every 90 minutes you have this pulse of growth hormone, and it mainly happens through the night." *(Pulse interval is ~3 h; 90 min is pulse duration.)*

**D-4** [3:16] "GLP-1s are engineered to be active in the bloodstream for seven straight days. That's installing a new lamp in the system that's turned on 24/7 for a week. The signal never shuts off."

**D-5** [3:41] "With people taking the GLP-1s, they lose a lot of weight. A good portion of that weight loss is muscle. [They] gain the weight back, but not the muscle. They gain the fat back. So they're in a worse situation than when they started, because your metabolic machine that helps you lose the weight is muscle."

**D-6** [4:21] "The research on rats is amazing. I mean, there's like 50% more blood vessels in the damaged area. Healing is accelerated across muscle, tendon, ligament areas. But almost all those studies were in rodents."

**D-7** [6:22] "In flies, mice and rats, it does extend the lifespan. Now in humans, the only studies that are out there are from a single Russian research group in 2003 and also 2006. And neither was independently replicated by any outside institution."

**D-8** [6:40] "BPC-157 does not trigger cancer, but if you have an active cancer, probably not a good idea to take it, because it's going to increase more blood flow to a tumor, potentially."

**D-9** [7:37] "30% contained the wrong amino acid sequence. So you would be injecting a completely different chemical than what was on the label. 65% failed bacterial endotoxin limits."

**D-10** [8:17] "HPLC does not check for heavy metals. It does not check for bacterial toxins. It does not verify if the product is sterile or standardized. A vial could score like 99% pure but be loaded with arsenic."

**D-11** [8:33] "If it says 'for research use only, not for human consumption,' but the seller includes dosing charts and mixing guides — or the transaction happens over Telegram, or you find the price is super cheap — suspect there could be a problem."

**D-12** [9:56] "In February of 2026, the FDA reclassified 14 peptides back to category one, where you can have a prescription and get these. So, as of right now, a doctor can give you a prescription for this specific peptide." *(Assessed likely false; see ¶2.5.1.)*

**D-13** [10:14] "Let's talk about the elephant in the room. Why are you even wanting to take these peptides in the first place? What problem are you trying to solve, and what is at the root cause of that problem?"

**D-14** [9:42] "As you can see, peptides are the wild, wild west. They come with the package."

---

## APPENDIX E — TERMINOLOGY RECONCILIATION

| Source usage | Correct / preferred | Note |
|---|---|---|
| "serorlin" | **sermorelin** | GHRH(1-29)amide |
| "epalin" | **Epitalon** | AEDG tetrapeptide |
| "GOP1" | **GLP-1** | — |
| "HPC" / "HLC" | **HPLC** | The whole COA argument depends on this |
| "every 90 minutes" (GH) | **~every 3 hours, 6–8 pulses/day** | 90 min = pulse duration |
| "category one" | **Category 1** | Enforcement-discretion category, not approval |
| "peptides are the wild, wild west" | **lemons market** | Asymmetric information; quality unobservable |
| "new lamp" | **continuous exogenous agonism** | Overrides endogenous feedback |
| "dimmer switch" | **secretagogue / pulse amplification** | Preserves endogenous feedback |
| "the research community trusts" (labs) | **unverified endorsement** | Source disclaims verification; the disclaimer does not travel with the claim |
| "bricks" | **structural / nutritional peptides** | Collagen hydrolysate |
| "blueprint" | **signalling peptides** | The regulated, higher-risk class |

---

## APPENDIX F — ESTIMATIVE LEXICON

**Confidence:**

| Term | Meaning |
|---|---|
| **High** | Verified primary source, or well-established consensus with direct application |
| **Moderate** | Credible but single-stream, or sound reasoning with an inferential gap |
| **Low** | Fragmented or contested basis; provisional |

**Likelihood:**

| Term | Range |
|---|---|
| Almost no chance | 01–05% |
| Very unlikely | 05–20% |
| Unlikely | 20–40% |
| Roughly even | 40–60% |
| Likely | 55–85% |
| Very likely | 80–95% |
| Almost certain | 95–99% |

**Evidence levels:** E1 (multiple RCTs) · E2 (at least one adequate RCT) · E3 (uncontrolled human data) · E4 (animal/in-vitro only) · E5 (anecdote/conjecture). See ¶3.5.

---

## APPENDIX G — REVISION LOG

| Rev | Date | Change |
|---|---|---|
| 1.0 | 2026-10-26 | Initial issue. Source: `transcript.md` (ASR, 12:33). Regulatory status verified against FDA bulk-substance page on 26 OCT 2026. |
| 1.1 | 2026-10-26 | Superseded numbering: this report was issued as 1.0 before the archive held a second health source. No content change. |
| 1.2 | 2026-10-26 | **Cross-reference.** `IR-20261026-LOOKSMAXXING` ¶6.2 records two corrections to this report: (a) ¶1.7's framing ("the risk is the vial, not the compound") is incomplete — product-quality risk and mechanistic risk are separate classes, and better manufacturing addresses only the first; (b) the Epitalon telomerase hazard is one instance of a general hazard class, now confirmed across three compounds. Body text retained unaltered per append-only convention; read the later report alongside ¶1.7 and ¶4.6.4. |

**Known deficiencies in this revision:**

1. Regulatory finding is time-sensitive and rests on a live FDA page plus one secondary correction (¶9.1). **Highest priority.**
2. The 65% endotoxin figure is untraced (¶9.2).
3. Sermorelin's bulk-substance status not verified (¶9.3).
4. Two of three named testing labs unverified; possible ASR artifacts (¶9.4).
5. The two BPC-157 human series were not located (¶9.5).
6. Janvier et al. read from abstract and secondary description, not full text (¶9.6).

---

```
UNCLASSIFIED // OPEN SOURCE // ANALYTIC EXERCISE
```

*End of report. This document is analysis of a public video's claims and is not medical advice.*
