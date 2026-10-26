# Wiener's Cybernetics: Doom Scrollers and Doom Resistors

**Source** — "DOOM Scrollers & DOOM Resistors: Wiener's Cybernetics", `@thepast33yrs`, 34:26.
Transcript: `transcript.md`.

A quotation-and-commentary essay reading four passages from Norbert Wiener's *Cybernetics* (1948; 2nd
ed. 1961) and extrapolating them onto algorithmic media. The presenter is informal, self-taught in the
material, and does not claim otherwise; the argument is stronger than its delivery.

## The thesis

Wiener's model of affect is captured by the platform and pointed at engagement rather than fitness. The
presenter calls the result a **cybernetic lock**: a state where the operator's behaviour is held at an
attractor whose goal was set externally and whose attainment yields no benefit to the operator.

The core claim is sound. Its best evidence is a sentence in Wiener that the video does not read.

## The four passages

**I — Associationism.** From Locke to Hume the mind was held to consist of ideas that bundle themselves
"according to the principles of similarity, contiguity, and cause and effect," with contiguity the most
significant: ideas that often occurred together in time or space acquire the power of invoking one
another, so the presence of one produces the whole bundle.

Read technically this is a specification of an associative memory. Nodes are ideas, edges are
association weights, the edge-formation rule is Hebbian co-occurrence (Hume's "often occurred together"
is a weight update stated two centuries before Hebb), and retrieval is pattern completion. Of the three
Humean relations, contiguity is the one most exploitable industrially, for three reasons: it requires
only co-occurrence rather than truth or resemblance; it is the substrate of classical conditioning; and
it is invisible to the subject, who cannot notice that a chime has been paired with a reward ten
thousand times.

**II — The operationalist turn.** Wiener notes that the step from these static ideas to Pavlov's
dynamic point of view is "perfectly clear," because Pavlov reported *visible actions* rather than the
introspective states of the mind. This is a change in the observability class of the system's state
variables, and it matters because observability is the precondition of controllability: a state that
cannot be measured cannot be compared to a reference, and a state that cannot be compared cannot be
regulated. The chain reads equally well as a vulnerability disclosure:

```
observable → measurable → comparable → regulable → exploitable
```

The behaviourist turn is the precondition of the attention economy. The platform's entire sensor
apparatus — dwell time, scroll velocity, rewatch, hesitation, abandonment point — exists because
behaviour is observable.

**III — Contiguity transferred to behaviour.** The association Locke observed introspectively among
ideas becomes, in Pavlov, a union of patterns of behaviour. The difference is that Pavlov's responses
"carry a process to a successful conclusion" or avoid catastrophe — eating, or escaping injury — and
"thus there enters into the conditioned reflex something we may call affective tone."

The definition is functional, not phenomenological: a response has positive affect tone if it
*terminates* a process successfully. Two properties follow. Affect tone is defined by outcome rather
than sensation, and it is a **terminal** signal — its natural dynamics are rise, act, close, decay.

That second property is the whole exploit. The platform deletes the terminal condition: no last page,
no end of list, autoplay removes the decision point, and the reward is scheduled so the next item is
always *possibly* the one that closes the loop. Affect tone rises and never resolves. The signal that
evolved to terminate behaviour is repurposed to perpetuate it.

Negative affect tone has higher gain than positive, which is adaptive — a missed meal is recoverable,
a missed predator is not — so a system optimising engagement converges on threat content not by design
but by yield.

**IV — Affect tone as a self-amplifying scale.** Wiener: affect tone lies on a scale from negative to
positive; an increase "favors all processes in the nervous system that are underway at that time and
gives them a secondary power to increase affective tone even more"; a decrease inhibits all processes
underway and gives them "a secondary ability to decrease affective tone further."

Three commitments in one sentence. Affect tone is **scalar and bipolar**, hence comparable, summable,
optimisable. It is a **global gain control** on ongoing processes — it does not select among processes,
it multiplies them, which is why the signal that would normally redirect you instead makes you better
at what you are already doing. And it is **self-referential**.

## The omitted sentence

The passage is Wiener [1948] 1961, p. 128. The verified text continues: *"Note that the mechanism of
affective tone is itself a feedback mechanism."*

The presenter reads the passage, correctly identifies the self-amplification, and attributes the
"cybernetic lock" to his own inference. It is not his inference — it is Wiener's claim, stated. The
omission matters twice over: it under-credits the primary text, and it means the source misses that
Wiener had already identified the exact failure mode.

The passage also has a component the video neglects: the **negative branch**. Affect tone that inhibits
all ongoing processes *and* further decreases itself is a downward runaway with the same structure as
the upward one. Doomscrolling is not only a failure to obtain reward; on the negative branch each
unsuccessful search lowers the baseline, which inhibits the capacity to stop, which prolongs the
search. The video describes this vividly ("the toilet flusher of doom") without identifying it as the
mirror-image instability it formally is.

## Why the loop is unstable

With affect tone `A` driving behaviour `B`:

```
dB/dt = α·A(B) − β·B,     with A'(B) > 0
```

Stability requires `α·A'(B) < β` — self-amplification dominated by decay. Wiener's "secondary power to
increase affective tone" is exactly the term `A'(B) > 0`. The platform's contribution is not to create
the feedback but to move the parameters:

| Parameter | Ancestral | Platform | Mechanism |
|---|---|---|---|
| `α` (signal→behaviour gain) | moderate | **high** | Variable-ratio reward, high-surprisal content, personalisation |
| `A'(B)` (self-amplification) | bounded by satiety | **high** | Infinite feed, no terminal state, autoplay |
| `β` (decay/termination) | high | **suppressed** | No pagination, no end of list, no completion signal |

The platform raises the gain and removes the damping, and the system is engineered to run in the
unstable regime. That is a stronger statement than "the loop is hacked," and it follows from Wiener's
text plus a stability analysis.

Because the unstable fixed point has a bounded basin, it is an attractor: information about the
attractor does not move the trajectory out of the basin. Parameter change does.

## Variety: why willpower is the wrong lever

Ashby's Law: `V(E) ≥ V(D) − V(R)`. Only variety absorbs variety. The platform's content space is
effectively unbounded; the operator's repertoire is roughly *scroll, don't scroll, close app*. The
inequality fails by orders of magnitude, so the operator cannot regulate the disturbance by matching it.

Only two moves remain. **Attenuate `V(D)`** — reduce the variety reaching the regulator: notification
blocklists, grayscale, app deletion, DNS filtering, physical separation. **Amplify `V(R)`** — timers,
precommitment, social accountability, substitution.

This is the report's main correction to the source. The source frames the remedy as agency, executive
function overriding primitive drives. That is not wrong, but it is the weakest lever, because it
attempts to satisfy the inequality by effort — which is the resource the loop depletes. The source's own
admission that "you're going to probably fall off the wagon a lot" is the empirical signature of a
failed variety strategy. Structural attenuation is not a workaround; it is the theoretically correct
intervention.

## The control hierarchy, mapped

Beer's Viable System Model describes a platform as five nested functions — System 1 operations (the
feed), 2 coordination (deduplication, diversity constraints), 3 control (engagement optimisation),
3* audit (A/B telemetry, raters), 4 intelligence (trend detection, retraining), 5 policy (corporate
mandate). The relevant point is the **algedonic channel**, which in a healthy organisation carries pain
directly to policy level and must not be filterable.

Two inversions obtain. The operator's distress is not treated as a threat signal — it is the product;
System 5 receives "engagement is up," not "the user is being harmed." And the operator has no algedonic
channel into the platform: complaints are absorbed at System 1 unless aggregated into a metric System 3
already tracks. The operator is regulating a system that cannot hear them, which is why individual
protest is ineffective and why regulatory or collective action is the only channel with requisite
variety against System 5.

## The bifurcation claim, and why it fails

The video predicts a split into doom scrollers and doom resistors. A dynamical-systems bifurcation
requires a named control parameter, a critical value, and an order parameter whose topology changes.
None is supplied. The claim is a heuristic wearing technical clothes.

Worse, it is internally inconsistent: a bifurcation implies loss of accessibility of the original
state, yet the source also insists the operator can leave at any time. Those cannot both hold. The
honest formulation is a **bistable system with asymmetric basin sizes**, where escape remains possible
but costs rise with residence time.

Wiener's own line — "even a doomed race may show a mechanism valid so long as the race lasts" — is
genuinely useful and survives: a **stable attractor need not be viable**. Stability and viability are
orthogonal, and conflating them is the standard error in evaluating such systems. Wiener's use of
"race" is nineteenth-century usage for a population or stock, not the modern sense; any quotation of
the passage out of context should carry that gloss.

## Indicators

Ordered by discriminating power, and weighted toward what can be observed rather than self-reported:

| Indicator | Note |
|---|---|
| **Post-session dysphoria** | The algedonic signal; the most reliable |
| **Failed cessation** | Decision to stop, behaviour continues — ≥2 attempts in 30 days |
| **Cue reactivity** | Checking within seconds of a notification, without intent |
| Pre-sleep and post-waking use | Circadian displacement |
| Session length creep | Requires a log; self-reported time is unreliable |
| Content escalation | Drift toward extremity over months |
| Idle intolerance | Inability to sit without stimulation for five minutes |
| Goal drift | "What did I intend before opening?" — the second-order check |

Time-use self-report is unreliable and should not anchor the assessment.

**The algedonic tripwire.** The aversive affect arising during a capture episode is not a symptom to be
managed; it is the sensor functioning correctly. Its presence indicates the comparator still has a
valid reference. Its *absence* — indifference, boredom, "it's just what I do" — indicates comparator
degradation and is the more advanced pathology. The operational rule is to act on the first occurrence,
not on accumulated evidence, because tolerance degrades the signal.

This inverts the popular framing. Popular discourse treats the bad feeling as the problem; the
cybernetic reading treats it as the instrument, and mood management as the error, because suppressing
the signal removes the only sensor capable of detecting capture.

## Courses of action

Each mapped to the term of the loop it modifies:

| Action | Modifies | Leverage |
|---|---|---|
| **Attenuate the channel** — kill notifications, disable autoplay, remove the app, grayscale, block domains, separate the device physically | `V(D)` | **Highest** |
| **Insert a stop rule** — timer, session budget in *opens* rather than minutes, fixed clock stop | `β` | High |
| **Reassert the comparator** — state intent and duration before opening; log it | `r` | Moderate |
| **Operate the algedonic channel** — first aversive feeling ends the session | sensor | Moderate, best value per effort |
| **Amplify regulator variety** — pre-commit to alternatives with real initiation cost | `V(R)` | Moderate |
| **Add friction** — log out, delete credentials, move the icon | `α` | Moderate |

Sequencing matters more than selection: attenuate the cue channel first, because the other interventions
are hard to sustain while cues are continuous; then termination and reference; then structural change,
informed by the log the earlier phase produced.

The stop rule must be exogenous to the session. Any rule evaluated *inside* the loop is evaluated by a
comparator the loop has already captured. "I'll stop when I get to a good point" is not a stop rule; it
is the loop speaking.

## Corrections

- **"Effective tone"** is *affective* tone. The corruption inverts the meaning: "effective" implies
  efficacy, while the term denotes valence.
- **"Algodonic"** is *algedonic* (Gk. *algos*, pain). The etymology is the concept.
- **"Bread-and-butterfly"** — the transcript renders this "bread and butter fly," destroying the
  allusion. Carroll's insect lives on weak tea with cream; Wiener's point is that a population whose
  affect-tone calibration is mismatched to its environment will not merely suffer, it will fail to
  persist. The allusion is doing real work.
- The **90-minute** claim does not appear here; it belongs to a different video in the archive.

## Verification

The p. 128 passage was checked against a secondary source reproducing the primary text verbatim, and
the omitted feedback sentence confirmed. The other three passages are verified in substance but not
against page images. Wiener's *Cybernetics* ch. I and ch. V have not been read in full.
