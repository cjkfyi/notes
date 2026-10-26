# cybernet — video source archive

Notes vault for analyzing video essays on cybernetics, control theory, and their application to
networked systems. One folder per video; the transcript and every report derived from it live
together.

## Layout

```
cybernet/
├── README.md                  this file — conventions + index
├── videos/
│   └── <YYYY-MM-DD>-<slug>/
│       ├── transcript.md      raw ASR capture, unedited
│       ├── IR-<YYYYMMDD>-<SLUG>.md   analytic report(s)
│       └── notes.md           optional scratch / pre-analysis thoughts
└── synthesis/                 cross-video reports, not tied to one source
```

## Naming conventions

| Element | Pattern | Example |
|---|---|---|
| Video folder | `YYYY-MM-DD-<slug>` | `2026-10-25-wiener-cybernetics-doom-scrollers` |
| Transcript | always `transcript.md` | — |
| Report | `IR-<YYYYMMDD>-<SLUG>.md` | `IR-20261026-CYBERNETIC-LOCK.md` |
| Scratch | always `notes.md` | — |

Rules:

- **Date is the processing date, not the upload date.** Upload dates are frequently wrong or
  absent, and the date you care about is when you did the work. Record the upload date inside the
  report if known.
- **Slug is lowercase, hyphenated, 3–6 words.** It must distinguish the video from its neighbours,
  not describe it fully.
- **Multiple reports per video are expected.** Second and later reports take a distinguishing
  suffix: `IR-20261026-CYBERNETIC-LOCK-ADDENDUM.md`. Never overwrite; append and bump the revision
  log.
- **Transcripts are immutable.** ASR output is evidence. Corrections go in the report's
  transcription-integrity table (see §2.3 of the first report), never back into `transcript.md`.

## Report header block

Copy this into every new report. Fields map to the structure used in
`videos/2026-10-25-wiener-cybernetics-doom-scrollers/`.

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
| **Handling** | Analytic exercise; formatting is a presentation frame. |
```

## Workflow for a new video

1. `mkdir -p videos/$(date +%F)-<slug>` and save the transcript as `transcript.md`.
2. Fix the ASR damage first — names, terms of art, numerals. Build the corruption table before
   analysis, or you will propagate errors into the report.
3. Verify quotations against the primary text where possible. Mark each as
   verified / substantively verified / unverified, with a locus (page, chapter).
4. Write the report: BLUF → source assessment → framework → analysis → threat model →
   assessment of the source's claims → gaps → judgments with confidence.
5. Add a row to the index below.

## Index

| Date | Video | Channel | Report | Status |
|---|---|---|---|---|
| 2026-10-25 | [DOOM Scrollers & DOOM Resistors: Wiener's Cybernetics](https://www.youtube.com/watch?v=kTL_sQc9uJc) | `@thepast33yrs` | [`IR-20261026-CYBERNETIC-LOCK`](videos/2026-10-25-wiener-cybernetics-doom-scrollers/IR-20261026-CYBERNETIC-LOCK.md) | Complete, rev 1.2 |
| 2026-10-25 | [Hyper-Subjectivism, "Word Art," & AI Psychosis](https://www.youtube.com/watch?v=NQh5unOfc2w) | `@thepast33yrs` | [`IR-20261026-HYPERSUBJECTIVISM`](videos/2026-10-25-hypersubjectivism-ai-psychosis/IR-20261026-HYPERSUBJECTIVISM.md) | Complete, rev 1.0 |

## Series note

The two `@thepast33yrs` videos form a sequence, and the second cites the first's comments section
directly. Read them in order:

1. **Attention capture** — `CYBERNETIC-LOCK`. Affect tone, infinite scroll, the severed termination
   condition.
2. **Epistemic capture** — `HYPERSUBJECTIVISM`. Word art, unbounded paraphrase, the severed error
   signal.
3. **Institutional capture** — *Inoculating Against Reality*. Referenced by video 2, **not in the
   archive**. This is the missing third term.

## The archive's unifying finding

Across all four reports (including the two in `../health/`), one structure recurs:

> **A feedback loop whose terminating element has been removed.**
>
> | Report | Severed element | Consequence |
> |---|---|---|
> | `CYBERNETIC-LOCK` | Termination condition | Unbounded session |
> | `HYPERSUBJECTIVISM` | Error signal | Unbounded discourse |
> | `PEPTIDE-RISK` | Falsification pathway | Unbounded market |

The diagnostic question this generates — **what would terminate this process, and who removed it?** —
is domain-independent and is the most portable instrument the archive has produced. See
`HYPERSUBJECTIVISM` §7. The prediction that would falsify the pattern is stated at §7.5 and is
untested; until it is tested, hold it as a strong hypothesis rather than a law.

## Open threads

Cross-video items to resolve as the archive grows. These are the gaps flagged in the first report
that more sources may fill.

- **"Berlanthy" / "Berilon"** — unresolved attribution, cited by the first source for the phrase
  "the behavior boys." Probably a contemporary commentator, not a cybernetics figure. See §9.4.
- **"Automa"** — the first source's coinage, traced to an earlier video of his on "the bureaucratic
  automa." No established technical referent. Needs a source that defines it.
- **Wiener, *Cybernetics* ch. I and ch. V** — read in full. The first report assesses four passages,
  one verified to page.
- **Wiener, *The Human Use of Human Beings* (1950)** — repeatedly cited, not yet covered.
- **Counter-variety literature** — what actually works. The first source has no treatment of
  interventions; this is the largest gap between its diagnosis and any prescription.
- ***Inoculating Against Reality*** — the channel's third video, cited by the second, supplies the
  institutional half of the argument. Highest-priority acquisition for the series.
- **The mathematics in `HYPERSUBJECTIVISM`** — the irrep/degeneracy correspondence (¶3.3.4) is
  asserted in outline and should be verified formally. The source invites correction on exactly this
  and it would be worth taking him up on it.
- **AI-associated psychosis literature** — read the BJPsych Open review, the amplification-spiral
  paper, and the 185-report analysis in full rather than from abstracts. The percentages in
  `HYPERSUBJECTIVISM` §5 depend on their coding methodology.
- **Bergson** — currently used as a loose synonym for irreversibility. *Durée* is not that, and the
  label should not be reused until the primary text is read.
