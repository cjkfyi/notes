# Spiking Networks, Neuromorphic Hardware, and the Credit-Assignment Constraint

**Source** — "Introduction to Spiking Neural Networks, Neuromorphic Computing and Computational
Neuroscience", `@MarkoVelich`, 1:10:18. Transcript: `transcript.md`.

A practitioner's survey of NeuroAI — the intersection of computational neuroscience, machine learning and
neuromorphic hardware. Its most valuable content is the last eight minutes, which explain why the field
has not scaled. Most material on neuromorphic computing is promotional; this is not.

## The three generations

The taxonomy is Maass (1997), *Networks of spiking neurons: the third generation of neural network
models*, used here without attribution.

| Generation | Unit | Computation | Learned by |
|---|---|---|---|
| 1st | Threshold gate (McCulloch–Pitts 1943, Rosenblatt 1958) | Binary output from a weighted sum | Perceptron rule; linearly separable only |
| 2nd | Continuous activation | Universal approximation | Backpropagation |
| 3rd | Spiking neuron | Computation over spike times | No settled method |

Maass's actual theorem is stronger than "it is newer": spiking networks are computationally more powerful
than sigmoid networks **in the temporal domain**, because a single spiking neuron can compute functions on
spike trains that a threshold gate cannot compute with any number of inputs. **Time adds expressive
power** — that is the reason the third generation exists, and without it the taxonomy reads as a
chronology with no claim attached.

The generations are ordered by **adoption in machine learning**, not by invention. Lapicque's
integrate-and-fire model dates to 1907, before the perceptron; it was never a competitive learning
architecture because no training rule made it useful at scale. A technique can be older than its
predecessor and still be its successor if the enabling condition arrives late.

## Neuron models

The ladder trades fidelity against cost:

| Model | Equations | Fidelity | Cost |
|---|---|---|---|
| **LIF** | 1 | No spike shape, no adaptation | Lowest |
| LIF + refractory | 1 + rule | Adds a dead time | Low |
| **AdLIF** | 2 | Spike-frequency adaptation | Low–moderate |
| **ExLIF** | 1 + exponential term | Smooth, realistic spike onset | Low |
| **Izhikevich** | 2 | ~20 firing patterns | Moderate |
| **Hodgkin–Huxley** | 4 | Ion-channel biophysics | High |
| Compartmental | Many | Dendritic morphology, NMDA/calcium spikes | Highest |

LIF is an RC circuit: a leak conductance `G_L`, a leak reversal potential `E_L`, a membrane capacitance
`C_M`, and an applied current `I`. When the applied current overwhelms the leak, membrane potential rises
to threshold and the neuron spikes.

**The LIF ↔ RNN mapping is the most useful pedagogical item in the lecture**: membrane potential is a
hidden state, leak is the decay of a linear RNN or state-space model, and the spike is a binary step
activation. That mapping is why SNN training can reuse RNN tooling — BPTT, truncated BPTT — and therefore
why surrogate-gradient training is the method that works.

**Izhikevich's model is a normal-form reduction**, not a curve fit. It captures the *bifurcation
structure* of the dynamics rather than the quantitative detail, which is why two equations reproduce
twenty firing patterns. That is the same mathematical move as finding a canonical form for an equivalence
class.

## Dendrites: the correction

The source says a dendritic model of one neuron "can approximate the entire convolutional neural network."
The direction is inverted.

Beniaguev, Segev & London (*Neuron*, 2021) trained deep networks to replicate the input–output function of
a biophysical layer-5 cortical pyramidal cell at millisecond resolution:

1. A **temporally convolutional network with 5–8 layers** was required to capture the mapping.
2. It generalised outside its training distribution — evidence it captured the computation, not
   overfitting.
3. **Removing NMDA receptors reduced the requirement to a single-hidden-layer fully connected network**,
   isolating NMDA kinetics as the source of the depth.
4. Dendritic branches behave as spatiotemporal pattern detectors.

**The neuron is not "like a CNN"; it requires one to emulate.** The corrected version is stronger: if the
fundamental unit of biological computation is itself network-shaped, the comparison between brains and
artificial networks is not "fewer layers, more neurons" but "each unit contains a network."

## Encoding and sensors

Rate coding, latency (time-to-first-spike), and delta modulation are the schemes the source lists. Missing:
population coding, rank-order coding. The gap matters because **the choice of encoding determines what the
network can compute**, and there is no settled answer — an indeterminacy the field does not treat as a
problem.

Event cameras (dynamic vision sensors) report per-pixel brightness *changes* asynchronously, with
microsecond temporal resolution, ~120–140 dB dynamic range versus ~60 dB for a frame sensor, and no
motion blur. The deeper point the source treats as an efficiency story: **frame-based vision is a sampling
convention imposed by hardware**, and motion blur, rolling-shutter artifacts and fixed latency are
consequences of the frame rather than of optics.

## Learning rules

Five families, correctly chosen:

**BPTT with surrogate gradients.** Spikes are non-differentiable, so a sigmoid surrogate is substituted
for the spike derivative. The unstated consequence: **the resulting gradient is a biased estimator** — the
forward function has derivative zero almost everywhere, so the update direction is systematically wrong,
and the method works anyway. Why is not fully settled, and it bears on the credit-assignment problem: if a
biased surrogate suffices, the requirement for exact gradients may be weaker than the biological
plausibility critique assumes.

**STDP.** Pre-before-post strengthens, post-before-pre weakens; unsupervised. A robot learning that a
visual cue predicts contact demonstrates three things at once — a predictive association from temporal
precedence, an anticipatory rather than reactive behaviour, and a single synapse doing the work.

**e-prop.** Per-synapse eligibility traces updated online give **O(1) memory per synapse independent of
sequence length**, which is what makes on-device learning possible. BPTT requires storing activations for
every timestep.

**ANN→SNN conversion.** Train normally, record per-layer maxima, map ReLU to LIF, normalise. It preserves
the function approximately but not the dynamics, so it forfeits exactly the temporal computation that
motivated spiking. **Conversion is a deployment optimisation, not a research direction.**

## Credit assignment: the governing constraint

Backpropagation solves credit assignment exactly, by propagating an error through the transpose of the
forward Jacobian. Three separate objections to its biological plausibility, which the source merges:

| Objection | Content |
|---|---|
| **Global error supervision** | Requires a scalar loss computed centrally and broadcast backwards |
| **Weight transport** | The backward pass uses the transpose of the forward weights; each synapse would need to know the strength of a different synapse elsewhere. This is Grossberg's problem and has no known biological solution |
| **Update locking** | The forward pass must complete before any weight can update |

Weight transport is the deepest — it is a statement about information a synapse cannot have. Global
supervision is the most cited but the easiest to approximate, since a neuromodulatory reward signal is a
plausible stand-in. Update locking is the most practically important, because it forces BPTT's memory cost.

A method that solves global supervision but not weight transport (feedback alignment) is not a solution to
the biological problem; it demonstrates that exact gradients may not be necessary. That distinction is the
field's actual frontier and the source does not draw it.

Three families of response: exact-gradient approximations (feedback alignment, forward-forward), energy-
based local methods (predictive coding, equilibrium propagation), and eligibility-trace methods (e-prop,
reward-modulated STDP). **No method in any family has been shown to train a deep network at modern
scale.** The gap is roughly the difference between MNIST/CIFAR-class results and frontier models.

## The energy claim is conditional

The single most important sentence in the lecture: *"SNNs by itself are not energy efficient unless paired
with neuromorphic hardware."*

| Statement | Status |
|---|---|
| "Spiking networks use less energy" | **False as stated** |
| "Spiking networks use less energy on neuromorphic hardware" | True for suitable workloads |
| "Spiking networks use more energy than ANNs on GPUs" | True, typically |
| "The gain requires event-driven hardware that can skip work" | True, and this is the mechanism |

A GPU is a dense SIMD machine: it executes the same operation on many elements regardless of whether they
carry a spike, so sparse events do not reduce work — they add the cost of testing for events and iterating
over timesteps. The efficiency gain requires hardware that can skip work, digital (Loihi's asynchronous
mesh) or analog/mixed-signal.

The general form of the fallacy: **an efficiency claim is a claim about a (model, hardware, workload)
triple, and stating only the model is incomplete.** The same structure appears in "quantization makes
models cheaper" (only if the hardware has fast low-precision paths), "sparsity accelerates inference" (only
if the accelerator skips zeros), and "MoE models are cheaper to run" (only if routing overhead amortises).

## The hardware–software deadlock

```
   no installed base  ──►  no tooling investment
          ▲                        │
          │                        ▼
   no developer demand  ◄──  poor developer experience
```

Deep learning escaped the analogous deadlock because **gaming had already funded matrix-multiply
hardware** for real-time 3D rendering. Deep learning then inherited a mature platform at zero development
cost. Neuromorphic computing has no such adjacent mass market; its natural customers — robotics, always-on
sensing, edge inference — are fragmented, low-volume and price-sensitive, which is the opposite of what
funds a fab.

The principle: **a compute paradigm becomes viable when an adjacent mass market has already paid for its
hardware.** The prediction is that adoption will track a high-volume adjacent application (always-on
sensing at microwatt budgets) rather than scientific maturity.

**NIR** (Neuromorphic Intermediate Representation) is the structural precondition for escaping the
deadlock: an intermediate representation reduces an N×M integration problem to N+M, as LLVM, ONNX and
MLIR did for their fields. **If NIR succeeds it will matter more than any individual chip**, because it
decouples model development from hardware choice. The source mentions it in one sentence.

## Corrections

- **ALIF is Adaptive LIF, not "exponentially leaky integrate and fire."** ALIF adds a slow adaptation
  current raising the threshold after each spike; **ExLIF** adds an exponential term producing smooth
  spike onset. The source attributes ExLIF's behaviour to ALIF and then describes ALIF's actual behaviour
  as a separate model. This is the one error with an implementation consequence.
- **AlexNet won ILSVRC in 2012**, not 2011. The error is probably anchored to the presenter's own entry
  into the field, which is why it survives.
- **The dendritic claim is inverted** (above).
- **Maass is unattributed** for the three-generation taxonomy.
- The **perceptron** dates to 1958; 1943 is McCulloch–Pitts.

## Verification

The dendritic correction was checked against the primary paper. The scaling ceiling — no local rule past
ImageNet — is consistent with the record but is asserted rather than cited, and is the field's governing
constraint, so it should be sourced. The surrogate-gradient bias is stated from inference rather than
confirmed. Loihi 2 shipped in 2021 and Hala Point (2024) scaled it to ~1.15 billion neurons across 1,152
chips, so the lecture's hardware timeline is stale while its substantive point — that training hardware is
scarce — remains correct.
