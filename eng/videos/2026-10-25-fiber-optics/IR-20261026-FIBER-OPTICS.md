# The Engineering of Fiber Optics

**Source** — "The Insane Engineering of Fiber Optics", `@Veritasium`, 34:20. Transcript: `transcript.md`.

A produced documentary on the invention of low-loss optical fiber, carrying primary evidence: the surviving
Corning participants — Keck, Schultz, Maurer — are interviewed, and Keck's lab notebook is read on camera.
The best-made source in this archive, and the only one whose central number is both striking and correct.

## The problem: copper's ceiling

Between 1960 and 1973 US daily calls doubled, from 285 to 576 million. AT&T could not keep up. Calls ran
over copper using frequency-division multiplexing: the voice band is 300–3400 Hz, filtered above 4 kHz, and
conversations are shifted into adjacent 4 kHz slots, separated at the far end by filters and shifted back
down.

The limit is the **skin effect**. The oscillating current generates a magnetic field and eddy currents that
cancel the driving current in the interior and reinforce it near the surface, and they strengthen as the
signal changes faster. So as frequency rises the current is confined to a thinner shell, effective
resistance rises (roughly as √f), and reach falls. Above **65 MHz** the signal died within two kilometres,
making regeneration uneconomic. The constraint was never "copper cannot carry high frequencies" but
"copper cannot carry them far enough to pay for the repeaters."

Shannon–Hartley (1948) explains why this was fatal: `C = B log₂(1 + S/N)`. Capacity grows only
logarithmically with power and linearly with bandwidth, so you cannot buy capacity by shouting louder. You
have to move to a higher frequency. Visible light is in the hundreds of terahertz.

## The two enabling problems

**A source.** A light bulb could not produce enough power. Maiman's ruby laser (1960) supplied a coherent
source at ~10¹⁴ Hz, which "rejuvenated the interest in possible optical communications."

**Loss.** Glass is not as clear as it looks. Signal loss is measured in decibels, `α(dB) = 10 log₁₀(P_in/P_out)`.
The target was 20 dB/km, comparable to copper. The best 1960s fibers measured **1000 dB/km**.

The dB arithmetic is used correctly throughout, and two of the analogies are worth checking. The sand-truck
analogy — 100 kg down to 1 kg over a kilometre is 20 dB — is **exact**, since 20 dB is a factor of 100. The
universe-to-atom analogy for 1000 dB is **true but loose**: 1000 dB is a power ratio of 10¹⁰⁰, and dividing
the observable universe's ~10⁵³ kg by that leaves ~10⁻⁴⁷ kg, about twenty orders of magnitude *less* than a
hydrogen atom.

The headline figure is correct: 1000 dB/km down to 20 dB/km is an improvement of **10⁹⁸** in transmitted
power per kilometre (10⁻¹⁰⁰ versus 10⁻²). Both that and the e-folding comparison are true and measure
different things:

| Loss | Transmission per km | 1/e length |
|---|---|---|
| **1000 dB/km** (1960s) | 10⁻¹⁰⁰ | **8.7 m** |
| **20 dB/km** (Kao's target) | 10⁻² = 1% | **434 m** |
| **0.2 dB/km** (modern) | 95.5% | **43.4 km** |

A 1960s fiber lost 63% of its light in under nine metres; modern fiber loses 63% in forty-three kilometres
— a factor of about 5,000 in attenuation length. The dB scale compresses that into the headline number,
which is why the headline sounds absurd.

## Total internal reflection

Light travels slower in some materials than others. When a wave meets a boundary at an angle, one end of the
crest crosses first and changes speed, dragging the beam and refracting it away from the boundary. How much
depends on the angle and on the two indices of refraction — Snell's law.

Moving from a higher index to a lower one, the refracted beam approaches the boundary as the angle
increases, until it runs along it: the **critical angle**, `θ_c = arcsin(n₂/n₁)`. Beyond it, total internal
reflection.

The demonstration is well chosen. Propylene glycol (n = 1.43) against air gives θ_c = 44.4°; water (1.33)
gives 48.8°. The glycol traps light through sharper bends, which is the same trade-off the industry makes:
the bigger the index difference, the more powerful the effect.

The step most popular accounts miss is that reflection against air fails the moment anything touches the
glass. Hence **two glasses**: a high-index core and a low-index cladding. The cladding's function is not
protection — it is to preserve the index step at every point along the length, including wherever the fiber
is touched, coated or bent. The figure of merit is the numerical aperture, `NA = √(n_core² − n_clad²)`. For
a typical single-mode fiber the index difference is only ~0.003–0.005, giving NA ≈ 0.10–0.14, which is why
the glass must be extraordinarily pure.

## Kao's question

The intellectual pivot: *"Why is glass so lossy, and can we remove those factors, or are they intrinsic to
the material?"* If intrinsic, fiber is dead; if not, it has a chance.

That is a decomposition of a measured quantity into its causes:

```
α_total(λ) = α_Rayleigh(λ) + α_IR(λ) + α_OH(λ) + α_impurity + α_scatter(defects) + α_bend
```

Three terms are intrinsic — Rayleigh, infrared, and the ultraviolet edge — and they set a floor. Kao's
contribution was establishing that the floor was low enough.

**Scattering.** Glass is amorphous; the basic unit is a silica tetrahedron, and in the melt the structure is
disordered, locking in as it cools. Fast quenching locks at a higher temperature, giving dense and sparse
regions that re-radiate light. Rayleigh scattering follows `α_R ∝ 1/λ⁴`, which is why the sky is blue and —
critically — why longer wavelengths lose less. Slow cooling lets the tetrahedra settle and reduces
scattering.

Kao's inference: from Maurer's measurements across glass types and cooling rates, a structure locked at
1000 °C would give about 1 dB/km. He expected scattering to rise with fictive temperature and found it
lower than expected — so scattering could not explain 1000 dB/km, and **absorption had to**. That
elimination argument is what licensed the engineering programme: Rayleigh scattering is a floor that cannot
be removed, absorption is a contamination that can.

**Absorption.** Electrons sit at discrete levels; packed into a solid those smear into bands. Light is
absorbed if the photon has at least the band-gap energy. Silicon's gap is 1.12 eV and visible light is
1.63–3.26 eV, so silicon absorbs it — hence opaque. In silica the silicon is bonded to oxygen, which draws
the shared electrons, widening the gap to ~9 eV, so visible light passes.

But most glass is not pure silica. Raw materials carry trace metals, and **iron** is the worst: iron ions
absorb violet, blue and infrared, with green surviving best. That is why a thick pane's edge looks green. If
a few centimetres produce a visible colour shift, a kilometre produces nothing at all.

Removing the metal ions was estimated to bring loss to ~20 dB/km. The 1966 paper concluded that "the
crucial material problem appears to be one which is difficult but not impossible."

## The measurement problem

Measuring attenuation normally requires hundreds of metres to kilometres; Kao had samples under 30 cm. He
and his colleagues therefore built a new instrument over three years. The first result read as zero loss,
which was impossible; the real answer was within their ±4 dB/km error bar; after months of refinement he
reported <5 dB/km in 1969.

Three lessons, none stated: measurement capability was the bottleneck (the physics was settled in 1966, the
proof took three more years of instrument development); a result inside the error bar is not a result; and
the first job of an instrument is to be able to fail. Until the error bar was ±4 dB/km no measurement could
distinguish 5 from 50.

Reporting "<5 dB/km" with ±4 is a **bound**, not a strong measurement. What made it decisive was not
precision but implication: any number below 20 means the target is reachable, so a bound of 5 settles the
question even with a wide bar. The right measurement was the one that answered the decision.

## Corning: three problems

**Material.** Fused silica has the lowest index of any glass (1.46), so it cannot be the core — nothing has
a lower index to clad it. Maurer's move was to make fused silica the **cladding** and raise the core's index
by doping. Every other lab was trying to purify a core; Maurer inverted the structure so the pure material
could be the part that did not need to be pure.

**Dopant.** Titanium works structurally — Ti shares electrons with four oxygens in the same tetrahedral
geometry — but it broke down at drawing temperature and absorbed too much light, requiring a second heat
treatment. Germanium also substitutes for silicon and raises the index without breaking down, so the heat
treatment could be skipped.

The deeper reason the source omits: germanium is **isovalent** with silicon, so substitution requires no
charge-compensation defects; and Ti⁴⁺ has low-lying empty d-orbitals giving ligand-to-metal charge-transfer
absorption in the visible and near-UV. That is why titanium-doped fiber was coloured and lossy — not merely
because it degraded in heat. No amount of process improvement would have saved titanium.

**Geometry.** The preform carries the final cross-section and is drawn to fiber, exactly like patterned hard
candy. Glass resting on a surface picks up stress and impurities; suspending it lets gravity do the work and
the surface tension hold it together. The draw is **scale-invariant**: conservation of volume gives a draw
ratio of `(D/d)²`. For a 100 mm preform drawn to 125 µm, `(100/0.125)² = 640,000` — **one metre of preform
becomes 640 kilometres of fiber.** That is the entire economic logic: a single batch of ultra-pure glass,
made slowly and expensively, becomes an enormous length of product made quickly and cheaply.

The soot problem: Schultz and Keck started from the cladding and worked in, spreading doped soot down the
inside of a pure silica tube. It collected at one end regardless of spray pattern. A technician fetched a
vacuum cleaner and drew a stream down the tube; it coated evenly, and the vacuum did not survive. That is
the most honest moment in the film: the critical variable was found by accident and then rationalised.

## The result

22 July 1970: 17 dB/km on a 29 m sample, notebook reading "Whoopie" and "must remeasure". 21 August:
16.9 dB/km on 210 m. "QED, quod erat demonstrandum… there was no eureka." The choice to end the discovery
arc on "no eureka" is the most disciplined editorial decision in the film: the discovery was a number
crossing a threshold, not a moment of insight.

Germanium doping then gave 4 dB/km with good strength. AT&T trialled fiber under Chicago in 1977; a Japanese
team reached 0.2 dB/km in 1979; TAT-8 crossed the Atlantic in 1988 at 280 Mbit/s carrying 40,000 calls,
ten times the previous copper cable.

## The omissions that matter

**The 1550 nm window.** The film says 0.2 dB/km is "the standard up to today" and never says at what
wavelength. 0.2 dB/km is not a property of silica; it is the **minimum of a curve**:

```
α(λ) = A·λ⁻⁴          (Rayleigh scattering — falls with wavelength)
     + B·exp(−c/λ)    (infrared multiphonon absorption — rises with wavelength)
```

The two terms move in opposite directions and their sum has a minimum at ~1550 nm with α ≈ 0.18–0.20 dB/km.
That means the industry's flagship number is not an achievement in the usual sense but **a physical floor**,
approached asymptotically by better manufacturing and not beatable by it. Every improvement from 20 to 0.2
was removing extrinsic contributions; the remaining 0.2 is irreducible.

It also explains the architecture of the modern system. Because the minimum is at 1550 nm, everything is
built there: erbium-doped fiber amplifiers operate at 1530–1565 nm, engineered to match the fiber's minimum
rather than the reverse; wavelength-division multiplexing stacks channels across the low-loss window; and the
C-band is the workhorse because it is both the minimum and where erbium happens to amplify. **The film teases
amplifiers at the end without saying their wavelength was set by the fiber's loss curve.**

**The water peak.** The hydroxyl ion has an absorption overtone at **1383 nm**, with a tail across the
low-loss region. In early fiber it was tens of dB/km and split the usable spectrum in two. The bands are
named O, E, S, C, L, U, and the **E-band was unusable for years** because of this peak; the industry
developed "low-water-peak" fiber, driving OH below ~0.5 ppb, specifically to open it.

This is the same lesson as iron recurring thirty years later. The film tells the impurity story once, as a
historical episode ending in 1970; in fact impurity control was a continuous engineering constraint, and
presenting it as solved makes the achievement look more finished than it is.

**Dispersion.** Attenuation is only half of what limits a link; the other half is pulse spreading. **Modal
dispersion** (different modes take different path lengths) is eliminated by single-mode design;
**chromatic dispersion** (different wavelengths travel at different speeds) scales with length and spectral
width; **polarization mode dispersion** is the practical limit on old installed fiber.

The film presents the core as "7.2% of the diameter" with no explanation of why it is that small. The answer
is that a small core admits only one mode, which eliminates modal dispersion. **A viewer finishes able to
explain the loss figure and unable to explain the dimensions.**

**Strength.** Fiber is stronger than steel in tension and breaks easily in a sharp bend. Both true, and the
explanation is absent. Pristine silica has a theoretical tensile strength of 10–14 GPa; practical fiber is
rated at 1–2 GPa; the gap is entirely surface flaws, because fracture initiates at the largest flaw. Three
features make strength a statistical problem rather than a materials one: flaw population is random, so
strength follows a **Weibull distribution** and fiber is specified by a **proof test** (every metre strained
to a fixed stress, failures discarded); **slow crack growth** under sustained stress and moisture means
fiber weakens over decades, which is why installed cable has a design life rather than a design strength; and
**bending converts tension into surface stress**, which is why a knot breaks fiber and a straight pull does
not.

The film's two strength claims appear contradictory without this, and a single sentence would have taught the
most transferable idea in it: **the strength of a brittle material is a property of its worst defect, not of
its bulk.**

## Two things it gets right that most accounts miss

**The tower is the annealing schedule.** The diameter is set within a few metres; the seven storeys exist
because the fiber must cool below coating temperature slowly enough to avoid frozen-in stress, and the only
way to cool slowly in a continuous process is to give it distance. **The building is the annealing
schedule.**

**The process taxonomy**, shown but not named: OVD (outside vapour deposition, Corning — soot on a mandrel),
VAD (vapour axial deposition, Japan — soot on a growing boule), MCVD (modified chemical vapour deposition,
Bell Labs — layers inside a tube, then collapsed), and PCVD (plasma-activated MCVD — what the film shows at
Prysmian). Naming it would have connected the modern factory back to Corning's 1970 work, since MCVD is the
direct descendant of the inside-deposition approach Schultz and Keck invented.

## Corrections

- **The 1887 crossbow experiment used fused quartz, not glass.** It is Charles Vernon Boys's, and quartz was
  chosen because it can be drawn to sub-micron diameters with high tensile strength — exactly what a torsion
  fiber requires. The film's "glass rod" removes the reason the experiment worked.
- **AlexNet is 2012**, not 2011 — not in this transcript.
- The **universe-to-atom analogy** is loose by ~20 orders of magnitude (above).
- **Corning's 1930s flame-hydrolysis originator** is unnamed; commonly attributed to Hyde.

## Verification

The dB arithmetic, the 10⁹⁸ figure and the draw ratio were recomputed. The 1550 nm minimum and water peak
are stated from standard fiber-optics knowledge rather than a primary reference and should be confirmed.
Boys (1887) was not read. Kao's 1969 publication was not consulted.
