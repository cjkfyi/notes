# eng — video source archive

Notes vault for engineering, instrumentation, materials, and manufacturing: how things are made,
measured, and pushed to their limits.

Sixth topic area. Same layout and conventions as the other five.

## Why a separate area — and why `eng/` rather than `sci/`

`sci/` would be redundant: every other area is science. What is distinct here is **how things are
made and measured**, and that changes the evidence standard in a specific way:

> **In this area the numbers are the argument.** A claim is checked by recomputing it — the dB, the
> ratio, the draw ratio, the date — not by assessing the author's interpretation.

So the core artefact of a report here is a **verification table**, and the characteristic finding is
either "the striking number is correct" or "the striking number is correct but the reason is missing."

The second is the more useful of the two. A documentary can report that modern fiber loses 0.2 dB/km
and never say that this is the *minimum of a curve* where Rayleigh scattering crosses infrared
absorption — and the number is then impressive but inert. **Reporting a result is not explaining it.**

## Conventions specific to this area

- **Recompute everything.** If a source says "10⁹⁸," check it (it is right). If it says "20 dB is
  100 kg down to 1 kg," check it (also right). Arithmetic errors in this genre are rare; unexamined
  numbers are common.
- **Distinguish intrinsic from extrinsic limits.** This is the master distinction of the area. Kao's
  achievement was establishing that fiber's loss was extrinsic — contamination, not silica. A term
  you can engineer away is a different kind of problem from one you cannot, and conflating them is
  what makes a problem look impossible.
- **Ask for the *reason* behind each headline figure**, not just the figure. Note the omission when
  it is consequential.
- **Watch for load-bearing details disguised as colour.** "A glass rod" where the experiment required
  quartz is the same failure mode as a misnamed neuron model in `neuroai/`: cosmetic on the surface,
  essential underneath.
- **Reproduced demonstrations outrank asserted ones.** If the presenter builds it, it counts for more.

## Index

| Date | Video | Channel | Report | Status |
|---|---|---|---|---|
| 2026-10-25 | [The Insane Engineering of Fiber Optics](https://www.youtube.com/watch?v=NiCgcUTL9_Q) | `@Veritasium` | [`IR-20261026-FIBER-OPTICS`](videos/2026-10-25-fiber-optics/IR-20261026-FIBER-OPTICS.md) | Complete, rev 1.0 |

## The template this report extracted

The film follows a structure worth naming, because it recurs across engineering history and predicts
what a good account will contain:

```
BOTTLENECK → ENABLER → MATERIAL INSIGHT → MANUFACTURING SOLUTION → SYSTEM
```

Fiber optics: copper's Shannon limit → the laser → the loss is extrinsic → doped preform → TAT-8.

**The allocation of difficulty is the diagnostic.** Here the enabler takes four minutes, the insight
twelve, and the manufacturing solution eight — and that matches where the work actually was. A film
that spends its time on the enabler is a film about physics, not engineering.

## Open threads

- **The 1550 nm minimum** is the single most important omission in the first report: 0.2 dB/km is not
  a property of silica but the crossing point of two opposing loss curves, and that fact explains the
  entire architecture of the modern system (erbium amplifiers, the C-band, WDM). Needs a primary
  reference.
- **The water peak at 1383 nm** — the OH absorption band that split the low-loss spectrum and forced
  low-water-peak fiber. The film presents impurity control as a solved 1970 problem; it recurred for
  thirty years.
- **Dispersion** — attenuation is only half of what limits a link. The film never explains why the
  core is 8 µm inside a 125 µm cladding, and modal dispersion is the answer.
- **Fiber strength is a Weibull problem**, not a materials one. The film's "stronger than steel" and
  "weak to sharp turns" appear contradictory without the flaw mechanism.
- **The amplifier sequel** — the film explicitly invites it, and the EDFA is the second half of the
  story. The archive does not have it.
