# Diverse Intelligence and the Interface Thesis

**Source** — "Where Does Intelligence Live? | Michael Levin on Evolution, AI, and Platonic Space",
`@632nmPodcast`, 1:28:02. Transcript: `transcript.md`.

An interview with a developmental biologist who runs a substantial experimental lab and is also advancing
a metaphysical thesis. The two must be graded separately: the experiments are strong, the framework is
not, and the source's own tone does not mark the difference.

## Why the split matters

The speaker flags publication status explicitly and repeatedly — "this is unpublished, so grain of salt,"
"in review right now," "we don't have evidence for this yet." That is exemplary practice. It also means
that **the interview's most quotable material is its least established material**, and the flags are
lexical rather than prosodic, so a reader scanning for content will miss them.

| Claim class | Grade | Basis |
|---|---|---|
| **Empirical** — barium adaptation, xenobots, the 2014 computational result, GRN learning | **A2** | Named lab, identifiable methods, specific quantities, explicit flags |
| **Framework** — Platonic space, ingression, minds as non-physical | **C3** | Presented as hypothesis; not testable as stated; no competing hypotheses excluded |

Eight of eleven substantive claims are flagged as unpublished, in review, or hypothesis.

## The empirical core: barium adaptation

Planaria placed in barium — a non-specific potassium-channel blocker — lose their heads within roughly a
day. Left in barium, they regenerate a head within weeks, and **the new head functions in barium**.
Comparing gene expression of a standard head against a barium-adapted head revealed **fewer than a dozen
altered genes** out of roughly 20,000. Attributed to Angela Tung and others in the lab.

Three features make this extraordinary: the perturbation is severe and novel (barium is a toxin, not an
ecological challenge, so there is no selection history for it); the response is functional rather than
defensive (the animal rebuilds a working head that works *in the toxin*); and the response is minimal (a
targeted solution, not a stress response).

The combinatorial argument is correct and is the sharpest formulation in the interview: with 20,000 genes
and a handful to choose, the space of possible responses is vast, "you don't have time to test all the
possibilities," and most combinations would kill the organism. That is a **credit-assignment problem with a
tiny sample budget** — formally the same problem that limits spiking neural networks in this archive.

One caveat the source does not attach: "fewer than a dozen genes altered" is a statement about
transcriptional difference at a sampled time point, not about mechanism. A tissue can solve a problem
without changing transcription — by reweighting gap-junction connectivity, redistributing ions, or
altering post-translational state. So the result may mean the solution was transcriptionally cheap, or
that it **was not transcriptional at all**. The second reading is more consistent with the lab's own
bioelectric framework and is the stronger claim.

## Three ways to pay for competency

Any competent controller arises by design (someone knew how to solve it), selection (many variants, most
eliminated), or learning (contact with the problem). Each is a way of paying in a different currency, and
the corresponding formal homes are control theory, population genetics, and statistical learning theory.

The argument is that xenobots and anthrobots exhibit competencies none of the three would predict. The
premise needs care: **the cells were selected** — for embryonic development, wound healing, tissue
self-assembly. A xenobot is an aggregate of cells doing tissue-level things in an unfamiliar geometry. The
honest claim is not "none of the three applies" but "**the competency does not follow from what the three
would predict.**" That is weaker, more defensible, and what he actually means.

## Free lunches, and the theorem that limits them

The source's distinction between **constraint** and **enablement** is real. A constraint restricts the
accessible state space, which has two opposite effects: fewer states reachable, and higher probability
density on the remaining ones — a shorter search path to any state in the constraint. **A constraint that
removes the irrelevant makes the relevant reachable.** That is the logic of inductive bias, of
canalisation in Waddington's landscape, and of dimensional reduction generally.

His claim that random networks are "already optimized" for learning collides with the **No Free Lunch**
theorems: averaged over all objective functions, every optimiser including random search has identical
expected performance. The claim survives only in restricted form — biological problems are drawn from a
**non-uniform, structured distribution**, and certain topologies are pre-adapted to *that* distribution.
Under that reading the free lunch is real and is paid for by the structure of the problem distribution
rather than by the system.

The distinction matters for the framework: if the free lunch comes from the problem distribution, it is a
fact about the world and is investigable. If it comes from mathematics itself, it is the metaphysical
claim. **The same evidence supports the first and does not establish the second.**

The strongest sub-claim here is the "four nodes" point: the simplest network doing Pavlovian conditioning
is four nodes. That decouples the phenomenon from scale — **learning is a small topological motif**, not a
property of complexity. The same structural insight as the Izhikevich normal form in the spiking-network
report.

## The ratchet

Small gene-regulatory networks modelled as coupled ODEs show habituation, sensitisation, Pavlovian
conditioning, and counting to small numbers. As they learn, their **causal emergence** rises; higher
causal emergence makes them better learners; and forcing them to forget **does not undo the gain** (in
review). That is a positive feedback loop pointing upward in agency, in contrast to entropy.

Causal emergence is Hoel's framework, built on effective information: the mutual information between
interventions and outputs under a maximum-entropy input distribution. The claim that a coarse-grained
model can have higher Φ than its substrate is contested, and three problems attach: the maximum-entropy
intervention distribution is a modelling choice; coarse-graining selection is not unique; and the thesis
is actively disputed in the philosophy of science literature.

The salvageable version may be stronger and less contested: **learning increases the functional
integration of a system, and increased integration improves subsequent learning.** That is testable with
standard tools and would be a significant result. The finding may well be right; the metric is doing more
work than it can bear.

The ratchet supplies the archive's most important conceptual import: the distinguishing feature of a
healthy loop is not the sign of its feedback but whether it **retains** anything. A ratchet has a pawl.

## Development as a control loop

Every homeostatic loop needs a set point, a comparison, and an error-minimisation procedure. The lab can
see the set point: the bioelectric prepattern is visible with voltage-sensitive dyes and genetically
encoded voltage reporters, and **changing the pattern changes what the cells build** — which is the
evidence that it is the reference. The evidence is causal rather than correlational, which is the correct
method.

The comparison and the minimisation are unknown. The proposal: **stress molecules are shared and leaky**,
so a cell in the wrong place raises stress in its neighbours; their own stress rises without them knowing
whose it is; the system's "temperature" (plasticity) rises; movement becomes possible; the error is
corrected; the temperature falls.

Why this is a good hypothesis: it requires no new machinery for cooperation (no cell needs to care about
another; each minimises its own stress); it converts a local problem into a distributed one without a
broadcast channel; and it has a natural annealing schedule. **It is a mechanism for credit assignment
without a controller** — and it exploits the *non-attribution* of the stress signal rather than correcting
it. That is genuinely novel as a design principle and is testable: block the signal's diffusion and
development should stall in the way the hypothesis predicts.

The weakness is that "stress" is unnamed. Reactive oxygen species, calcium waves, cytokines and mechanical
strain have different diffusion lengths, timescales and downstream effects. For the hypothesis to be
mechanistic the identity matters.

**The developmental ratchet** is the most scientifically productive idea in the interview and is stated in
ninety seconds: the bioelectric prepattern keeps evolving, the organism implements the current pattern,
stress falls, the pattern moves on, stress rises, it implements the next. Development is a **tracking
problem**, not a program. Three consequences follow that the source does not draw: it explains robustness
without a program (a tracking controller corrects for perturbation by construction); it explains why
development can be re-entered (re-establishing an earlier reference re-runs the trajectory, which is what
regeneration is); and it predicts that development should be perturbable by shifting the reference.

The tail-graft experiment is the cleanest demonstration: a newt tail grafted to the flank remodels into a
limb, and the cells at the tail tip are locally fine — no damage, no problem — yet they become fingers. No
local account explains why a healthy cell in a healthy tail tip should build a finger.

## Top-down transduction

Abstract goals reach down to ion fluxes: to execute a financial or social goal you must get out of bed,
which requires sodium and potassium to cross muscle membranes. The point is that downward causation is not
exotic — it is what you are doing right now.

The limit: the counter-argument is standard and strong. Your abstract goals **are** implemented in your
nervous system, so the "downward" causation is causation by a higher-level *part* of the same physical
system. The argument shows that top-down description is useful; it does not show that top-down causation is
irreducible.

## The methodological argument

The strongest epistemics in the interview: the commitment that "nothing in biology knows anything and
nothing has goals" is an **axiom, not a result**. Early modern science needed actionable explanations
rather than appeals to divine will, and the available options were "dumb matter" or "smart agents."
Choosing dumb matter was the productive move; the error was forgetting it was a choice.

The cybernetics point is verified and correct: Rosenblueth, Wiener & Bigelow, "Behavior, Purpose and
Teleology" (*Philosophy of Science*, 1943) supplies a **graded** notion of purpose — purpose as negative
feedback toward a goal, definable for a thermostat and a mammal without either being mysterious. That
ladder was available in 1943 and biology did not climb it.

The methodological claim is not that cells *are* agents; it is that **agency is a modelling choice that
should be tested rather than excluded by fiat.** Build both models, compare predictions, let the data
decide. That requires no metaphysics, and it is what the lab's perturbation experiments actually implement.

On observation versus intervention the point is correct and is the standard causal-inference point:
observational data cannot distinguish "the system always does X" from "the system is trying to do X and X
is what it achieves." The distinguishing test is a barrier. A hardwired system fails; a goal-directed
system compensates, shows delayed gratification, takes a detour.

The Heider–Simmel study is real and the inference is right, but it cuts both ways and the source does not
address it. The 1944 stimuli are a large triangle, a small triangle and a disc moving inside a rectangle,
and the standard finding is that subjects spontaneously attribute intentions, emotions and social
relationships to them. The usual interpretation is that **humans are hyper-active agency detectors.** If
that is true, a biologist claiming agency in cells is making a claim in the direction of a known bias and
should be held to a *higher* standard. The implicit reply — that he is relying on perturbation, which the
Heider–Simmel subjects could not do — is adequate and unstated.

## The framework

**Platonic space.** Mathematical truths are discovered rather than invented, are not derivable from
physics, and form a structured investigable space. The hypothesis: that space contains not only static
mathematical truths but **high-agency patterns — kinds of minds** — and physical systems are interfaces
for them.

Separating the steps:

| Step | Claim | Status |
|---|---|---|
| 1 | Mathematical truths are not derivable from physics | **Defensible** — mathematical realism |
| 2 | They are discovered rather than invented | **Contested but respectable** |
| 3 | Mathematics forms a structured space | **Defensible** |
| 4 | **That space also contains minds** | **Not supported — the leap** |
| 5 | Physical systems are interfaces for those patterns | **Not supported** |
| 6 | The space is bidirectional, stateful, writeable | **Explicitly acknowledged as unevidenced** |

Step 4 is the thesis and it is an analogy extended by assertion: because mathematical structures constrain
physical ones, and because minds are structured, minds must be structures in the same space. The inference
is invalid — "A constrains B" and "B has structure" do not entail "B is a member of A."

The fatal objection is that **the framework predicts nothing the phenomena do not already contain.** Every
observation of a competency is consistent with "it is an interface for a pattern," because for any
competency there is by construction a pattern for it.

The one place it does predict is the strongest form of the argument and should be the headline:

> **Novel interfaces produce competencies that were not designed, selected, or trained for.**

That is a genuine prediction, and it differs from the mechanistic alternative, which predicts capabilities
bounded by the parts' capabilities. The evidence is a series of surprises: xenobots self-replicating
kinematically (not selected for), anthrobots healing neural wounds, a turtle becoming cat-like on a
skateboard, unnoticed competencies in an 80-year-old sorting algorithm, LLMs doing things their training
did not target.

The charitable reading is probably what he means: "Platonic space" as a **heuristic for a research
attitude** — there is structure in the space of possible competencies, it is discoverable, and we should
look for it rather than labelling surprises "emergent." That reading requires no metaphysics and is
compatible with everything in the empirical section.

**Ingression** is borrowed from Whitehead. The ordinary-language substitute — "a capability appears" —
carries the same empirical content with none of the commitment.

The ethical turn is the part that does not depend on the metaphysics: if a system has morally relevant
states, creating it for a purpose imposes obligations, regardless of whether those states are physical.
The graded-response framing (we do not stop walking to avoid crushing bacteria, but we think carefully
about larger systems) is the standard structure in animal and AI ethics.

**"Emergence" as a stopper.** The sharpest epistemological observation: "emergent" is used as a terminal
explanation, a label that closes inquiry. The test is right — if you had a story about why this happened
rather than that, it would not be emergent. But the same charge applies to "Platonic space," and he does
not notice: if "emergent" explains any surprise, "it ingressed from Platonic space" does too.

## Apparatus and results

**MAMbot** is a physical robot with effectors in electrical, optical, chemical, vibrational and thermal
modalities; an AI forms hypotheses about what to "say" to frog epithelial cells to produce a xenobot of a
desired shape and behaviour, the cells respond, the robot observes and revises. Three descriptions, and
the third is the strongest: a communication interface; an embodied AI exploring **morphospace** rather
than 3D space; and a **prosthetic** — the skateboard for the xenobots.

The prosthetic framing generalises: a passive interface can unlock a latent competency (the turtle), so an
active intelligent interface should unlock more. **Intervention becomes capability unlocking rather than
capability creation.** The engineering implication is that the search should be over *interfaces*, not over
training procedures.

The 2014 result with Daniel Lobo: roughly 800–1,000 **functional** (not molecular) planarian regeneration
experiments digitised from the literature, then evolutionary computation to answer a question posed over a
century earlier, with predictions confirmed by molecular tools. The significance is not the AI but the
**data curation decision** — a dataset of input–output behaviour of a system treated as an agent, which is
exactly the data type the "semantic medicine" programme requires, and an existence proof that a
behavioural dataset about a tissue is sufficient to recover a mechanism without molecular data.

**"Semantic medicine."** AI-biology is overwhelmingly structural and bottom-up; but the genome is
hardware, and what matters above it is what the cell knows, its priors, its decision-making. The
defensible core: **for many biomedical goals the binding-affinity search space is the wrong search space,
because the failure is in the control layer rather than the component layer.** That is almost certainly
true for regeneration, ageing and some cancers, and is a significant claim about research allocation. The
weakness is that "semantic" is undefined and the psychiatric analogy imports its uncertainty.

## Corrections

- **"pre-western Marxism"** appears in the adjacent video, not here.
- **"plenarian"** → planarian; **"biomectric"** → bioelectric; **"fi"** → Φ; **"Federico Pagosi"** →
  Federico Pigozzi; **"Stu Kaufman"** → Stuart Kauffman; **"Weiner/Rosen Bluth/Bigalow"** → Wiener,
  Rosenblueth, Bigelow; **"Hoffstad's Gerlesherbach"** → Hofstadter, *Gödel, Escher, Bach*; **"Eric
  Bedsik"** → Eric Betzig; **"amplahedron"** → amplituhedron.
- The **"sematic psychiatry"** corruption matters: it reads as a typo for "somatic," which inverts the
  meaning. Somatic medicine treats the body; semantic medicine treats the body's self-model.
- **"Six trillion trillion"** does not appear here; that error belongs to the adjacent video.

## Verification

The barium paper was not located; the combinatorial argument rests on the transcript. The in-review
ratchet result is load-bearing and unverified. Causal emergence's critique is stated in outline rather
than sourced. The NFL reply is the report's own construction. MAMbot's platform identity is unverified.
Part one of the interview is not in the archive.
