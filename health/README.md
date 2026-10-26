# health — video source archive

Notes vault for analyzing health, nutrition, and pharmacology content. Same layout and conventions as
`../cybernet/`, with one addition that matters more here: **evidence grading and a safety notice**.

> **Not medical advice.** Nothing in this directory is a prescription, a dosing guide, or a substitute
> for a licensed clinician. Content here analyzes *claims made in public videos*. Several compounds
> discussed are unapproved and sold outside licensed supply chains.

## Layout

```
health/
├── README.md                  this file — conventions + index
├── videos/
│   └── <YYYY-MM-DD>-<slug>/
│       ├── transcript.md      raw ASR capture, unedited
│       ├── IR-<YYYYMMDD>-<SLUG>.md   analytic report(s)
│       └── notes.md           optional scratch / pre-analysis thoughts
└── synthesis/                 cross-video reports, not tied to one source
```

## Conventions

Inherited from `../cybernet/README.md` — same naming rules, same append-only report rule, same
"transcripts are immutable" rule. Differences specific to this area:

- **Every report carries a safety notice** at the top, above the header table.
- **Claims are graded E1–E5** (multiple RCTs → anecdote). Ten rodent studies do not aggregate into
  human evidence; see ¶3.5 of the peptide report.
- **Regulatory claims are verified against the primary source, never against the video.** This is the
  lesson of the first report: a consumer-health video's regulatory statement can be wrong in the
  direction that changes the reader's next action.
- **No dosing, no protocols, no reconstitution arithmetic** in any report, regardless of what the
  source provides. Report what the source said; do not restate it as usable instruction.

## Report header block

```
| Field | Value |
|---|---|
| **Report No.** | IR-<YYYYMMDD>-<SLUG> |
| **DTG** | <DDHHMMZMONYY> |
| **Classification** | UNCLASSIFIED // OPEN SOURCE |
| **Source** | `transcript.md` (same folder) |
| **Source type** | OSINT — single-source, open-platform video commentary |
| **Reliability** | <A–F><1–6> |
| **Distribution** | Unlimited |
| **Handling** | Analytic exercise; not medical advice. |
```

## Index

| Date | Video | Channel | Report | Status |
|---|---|---|---|---|
| 2026-10-25 | [Everything You Need to Know About Peptides](https://www.youtube.com/watch?v=qovnfjVd8cs) | `@Drberg` | [`IR-20261026-PEPTIDE-RISK`](videos/2026-10-25-drberg-peptides/IR-20261026-PEPTIDE-RISK.md) | Complete, rev 1.2 |
| 2026-10-25 | [The Science of Looksmaxxing, with Doc Noc](https://www.youtube.com/watch?v=ESvls8ZUg58) | `@StarTalk` / `@dr.noc` | [`IR-20261026-LOOKSMAXXING`](videos/2026-10-25-startalk-looksmaxxing/IR-20261026-LOOKSMAXXING.md) | Complete, rev 1.0 |
| 2026-10-25 | [Dr. Jack Kruse Explains Physics of Consciousness](https://www.youtube.com/watch?v=3lWJkDwp8LE) | `@FitnessWisdomPodcast` | [`IR-20261026-KRUSE-QUANTUM-CONSCIOUSNESS`](videos/2026-10-25-kruse-quantum-consciousness/IR-20261026-KRUSE-QUANTUM-CONSCIOUSNESS.md) | Complete, rev 1.0 |

## The four-layer separation — the convention this area needed

Some sources are not uniformly wrong, and grading them as a whole is as inaccurate as accepting them
whole. Every report in this area now separates claims into four layers:

| Layer | Definition | Test |
|---|---|---|
| **1 — Established** | Correct, textbook, checkable | Verify against a reference |
| **2 — Contested** | A real research programme with a disputed interpretation | Ask whether consensus exists |
| **3 — Unsupported** | An inference that does not follow, or an extraordinary claim without evidence | Ask what would support it |
| **4 — False / harmful** | Contradicted by evidence, or a claim with a harm pathway | Ask whether it is refuted |

**Why this matters more than any single error: it is a credibility-laundering device.** A reader's
natural strategy is to check what can be checked — and layer 1 is checkable and correct. The reader
then concludes the source is reliable and stops. **The accuracy of the checkable part licenses the
uncheckable part.**

Two instances now, and they should be checked for explicitly:

| Report | Layer 1 (correct) | Layer 4 (false) |
|---|---|---|
| `PEPTIDE-RISK` | Accurate pharmacology | The FDA reclassification claim |
| `KRUSE` | Correct thermodynamics, circadian biology | Creatine lethality; named-individual medical claims |

## The other standing check: is the framework falsifiable?

The `KRUSE` report is the archive's clearest case, and the source says it outright: *"What's the break
point? I don't think there is a break point... it's a spectrum."*

A framework with no threshold cannot be tested, and its advice therefore cannot be distinguished into
what works and what does not. Two structural markers to look for:

- **The "spectrum" defence** — individual variation explained by an unmeasured multi-dimensional
  variable absorbs every disconfirming case.
- **Self-citation** — where the authority for the load-bearing claim is the speaker's own unpublished
  framework, and external literature is used only to establish that the mechanism is *conceivable*.

## Source reliability, as issued

| Report | Grade | Basis |
|---|---|---|
| `PEPTIDE-RISK` | **C3** | Identifiable presenter, coherent content, but a material regulatory error and a commercial interest |
| `LOOKSMAXXING` | **A2** | Named domain expert; volunteers limitations of studies including ones favouring its own framing; discloses business model; no product promotion |
| `KRUSE` | **E4** | Framework unfalsifiable by construction ("there is no break point"); credibility laundered across four layers; five sponsors all selling the mechanism |

Grades are per-report, not per-channel. A single channel can produce both.

## Cross-source findings

Where two reports disagree, the later report records the resolution rather than overwriting the earlier one
(see `LOOKSMAXXING` §6). Two corrections to `PEPTIDE-RISK` are on record there and noted in its rev 1.2 entry:

- **The risk locus is two classes, not one.** Product-quality risk (the vial) and mechanistic risk (what a
  correctly-made peptide does biologically) are separable. Better manufacturing fixes only the first.
- **Context-dependent upregulation is a general hazard class**, now confirmed across three compounds:
  telomerase (Epitalon), angiogenesis (BPC-157), and NAD⁺ (nicotinamide).

## Open threads

Carried from the first report's §9. These are the items that more sources may close.

- **FDA bulk-substance status is in flux.** The 503A Category 1/2/3 system is being retired for new
  nominations (Jan 2025 guidance), and the Category 2 page was restructured 22 Apr 2026. Any
  regulatory claim older than a few months should be treated as stale. Re-check the live page.
- **The 65% endotoxin figure** has no located primary source. If a later video repeats it, that is a
  traceable marker of the same circulating claim chain.
- **BPC-157 human data** — the two small series (n=12; n=16 with TB-500) remain unlocated. Whether
  they are peer-reviewed determines whether the human evidence is "weak" or "effectively anecdotal."
- **Testing laboratories** — Janoshik Analytical verified; "Covera Labs" and "Freedom Diagnostics"
  unverified and possibly ASR artifacts. A lab named in a video is an endorsement in practice even
  when the presenter disclaims it.
- **Epitalon / telomerase** — no independent replication located. The oncogenic implication is
  undeveloped in every source seen so far and is the most important thing to say about it.
- **High-risk looksmaxxing practices — no source in the archive covers them.** Bone smashing, DIY
  filler, surgical tourism, and anabolic use are absent from the StarTalk episode, and they carry more
  expected harm than the peptides it does cover. This is the largest gap in the archive.
- **GLP-1 normalisation transfer** — the hypothesis that familiarity with prescribed injections lowers
  the barrier to unregulated ones is novel, plausible, and untested. Any survey data on injection
  acceptance before/after GLP-1 adoption would close it.
- **Numerical corrections outstanding** in `LOOKSMAXXING` ¶9.3: oral semaglutide bioavailability
  (~0.4–1%, not ~2%), the UK Biobank visceral-fat figures (replace with published hazard ratios), and
  low-testosterone prevalence by decade.
