# neuroai — video source archive

Notes vault for brain-inspired computing: spiking networks, neuromorphic hardware, computational
neuroscience, and the machine learning that borrows from them.

Third topic area. Same layout and conventions as `../cybernet/` and `../health/`.

## Why a separate area

`cybernet/` covers control and communication in systems; this covers **how neurons and neuromorphic
hardware compute**. The overlap is real — both care about feedback and credit assignment — but the
evidence standards differ. Cybernetics sources are assessed for conceptual soundness; these are
assessed for **technical accuracy against the literature**, because a wrong neuron model or a wrong
date propagates into implementation.

## Layout

```
neuroai/
├── README.md                  this file — conventions + index
├── videos/
│   └── <YYYY-MM-DD>-<slug>/
│       ├── transcript.md      raw ASR capture, unedited
│       ├── IR-<YYYYMMDD>-<SLUG>.md   analytic report(s)
│       └── notes.md           optional scratch
└── synthesis/                 cross-video reports
```

## Conventions specific to this area

- **Acronyms are the content.** ASR destroys them systematically, and here `ALIF` vs `ExLIF` denote
  different models with different equations. Build the terminology table before analysis, always.
- **Every numerical or historical claim gets a status**: verified / consistent with record /
  imprecise / garbled / error. The distinction between *imprecise* and *garbled* matters — the first
  is a detail wrong, the second is a finding stated as its own inverse.
- **Check the hardware clause on any efficiency claim.** "Spiking networks use less energy" is false
  as stated and true only with an event-driven hardware qualifier. See `IR-20261026-NEUROAI-SNN` §6.
- **Demos are not scaling results.** A robot chasing a ball demonstrates that a method runs; it does
  not demonstrate that it scales. Keep the two separate in every assessment.

## Index

| Date | Video | Channel | Report | Status |
|---|---|---|---|---|
| 2026-10-25 | [Introduction to Spiking Neural Networks, Neuromorphic Computing and Computational Neuroscience](https://www.youtube.com/watch?v=F633rfo7JC0) | `@MarkoVelich` | [`IR-20261026-NEUROAI-SNN`](videos/2026-10-25-spiking-neural-networks/IR-20261026-NEUROAI-SNN.md) | Complete, rev 1.0 |

## Open threads

- **The scaling ceiling needs a citation.** "No local learning rule scales past ImageNet" is the
  governing constraint of the whole field and is asserted, not sourced. Highest-value gap.
- **Surrogate gradients are biased and work anyway.** Why is unresolved, and it bears directly on how
  strong the biological-plausibility objection really is. Two literatures — surrogate gradients and
  local learning — are asking the same question from opposite ends and under-citing each other.
- **Hardware status is a moving target.** Loihi 2, Hala Point, SpiNNaker 2, Akida, and the
  analog/mixed-signal efforts. Track **training** hardware separately from **inference** hardware;
  the training side is the actual bottleneck.
- **The adjacent-market prediction.** The report argues adoption will track a high-volume adjacent
  application (always-on sensing) rather than scientific maturity, by analogy with GPUs and gaming.
  Testable against historical adoption curves.
- **NIR** — the intermediate representation is probably more consequential than any single chip,
  because it decouples model development from hardware choice. Mentioned in one sentence by the
  source; worth its own assessment.
