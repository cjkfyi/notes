# One-Time Pads and the Properties They Do Not Provide

**Source** — "Low-tech, Unbreakable Encryption — One Time Pads", `@CivilDefenseEngineer`, 28:48.
Transcript: `transcript.md`.

A manual-encryption tutorial. The primitive is taught correctly and is genuinely unbreakable. The
mathematics is sound; the threat model is not, and that gap is the substance.

## The primitive

Encryption has four elements — plaintext, ciphertext, key, algorithm — and the box-and-padlock
demonstration enacts Kerckhoffs's principle: the algorithm is public, the key is the secret.

Classical ciphers fail for instructive reasons. The Caesar cipher has 26 keys and is defeated by
enumeration. Monoalphabetic substitution has **26! ≈ 4.03 × 10²⁶ ≈ 2⁸⁸·⁴** keys and is still broken by
hand in about half an hour, because it **preserves the statistics of the plaintext**: letter frequencies,
digram frequencies, word-length distribution, positions of repeated letters. The ciphertext leaks structure
even though it hides content.

That is precisely what the one-time pad removes, and it is why the pad works: it destroys the statistics
rather than hiding them. **The source demonstrates the failure and the fix without connecting them, and the
connection is the whole theory.**

The construction is modular addition:

```
C_i = (M_i + K_i) mod 10
M_i = (C_i − K_i) mod 10
```

Security depends on the key being **uniform over the same alphabet as the message**, not on the operation.
With `K` uniform over {0..9} and independent of `M`, `P(C = c | M = m) = 1/10` for every `c` — the ciphertext
is uniform regardless of the message. XOR is the binary instance of the same identity; addition mod 10 is
chosen because a human can do it without carrying, at no cost in security.

**Shannon's conditions** (1949) are the formal basis, and the source states them in substance without naming
the theorem. Perfect secrecy is `P(M = m | C = c) = P(M = m)` for all `m, c`: the ciphertext is statistically
independent of the plaintext. It requires key length `H(K) ≥ H(M)`, a uniform key, independence from the
message, and single use.

Perfect secrecy means an eavesdropper cannot do better than guessing. It does **not** mean the message cannot
be modified, cannot be replayed, that its existence is hidden, or that its length is hidden.

The historical point the source omits: **Vernam's 1918 system used a paper tape key looped for reuse** — a
repeating-key cipher, and breakable. Mauborgne's recognition that the key must be as long as the message,
random and never repeated is what made it a one-time pad. The field learned the rule by breaking the looped
version, which is the intuition the video should have given and did not.

## Encoding and its structural weakness

Letters map to two digits (01–26), space to 29, numerals are prefixed with `3`, and codebook entries are
prefixed `00` followed by three digits. The first two groups of every transmission are the sheet number and
the starting line, **in the clear**.

The weakness is that the encoding mixes elements of different lengths and relies on the decoder recognising
which is which from context. The source is explicit that this requires judgement — "you just got to use your
common sense."

For a cipher this is a design flaw, not a style choice. Three consequences: ambiguity (a stream beginning
`00…` could be a codebook entry or a mis-transcription); no error detection; and no self-synchronisation, so
alignment cannot be re-acquired without restarting from a known point.

The fix is standard and costs nothing: **fixed-length code groups**, every element four or five digits with a
leading flag, plaintext padded to a fixed length. The parse becomes unambiguous, an error corrupts one group
rather than the remainder, and the message length is quantised, which incidentally improves traffic-flow
confidentiality.

## Key volume: the governing arithmetic

Two digits per character; 25 digits per row; 12.5 characters per row; **125 characters per 50-row sheet**.

One sheet of fifty rows carries about one sentence. A single page of typed text (~1,800 characters) requires
about fourteen sheets, or one full pad. Twenty messages a day of two hundred characters consumes about three
sheets per day — roughly a thousand sheets per year per pair of correspondents.

**This is why the codebook exists.** At a 4–5× compression ratio the same sheet carries 500–600 characters.
The codebook is not a security improvement; it is a 4–5× reduction in the mass of paper that must be
couriered.

And it explains the source's own inefficiency: "Subscribe to Civil Defense Engineer" — 34 characters, no
codebook — consumed ~68 digits, about three rows, or 2% of a sheet for a trivial message.

## The codebook's function, corrected

The source says codebooks "obfuscate the message even more." **They do not.**

The OTP already achieves perfect secrecy. Once `H(K) ≥ H(M)` and the key is uniform and single-use, the
ciphertext is independent of the plaintext; there is no residual information for a codebook to hide. A
codebook layered under a correct OTP contributes **exactly zero** additional confidentiality — the bound is
already achieved.

What it does is compress the plaintext, and therefore conserve key.

The cost the source does not mention: a codebook is **static and shared**, and it reduces the entropy of the
plaintext. Under a correct OTP that is harmless, but it creates a second secret with the same distribution
problem as the pad; if a pad is ever compromised the compression makes the recovered plaintext *more*
legible, since code groups resolve to whole phrases rather than letters; and the codebook is long-lived while
the pad is single-use, so its compromise window is much larger.

## What the pad does not provide

COMSEC is five separable properties and the OTP scores one.

| Property | Question | Provided? |
|---|---|---|
| **Confidentiality** | Can it be read? | **Yes — perfectly** |
| **Integrity** | Can it be modified undetected? | **No** |
| **Authentication** | Who sent it? | **No, not by itself** |
| **Traffic-flow confidentiality** | What do timing and volume reveal? | **No** |
| **Forward secrecy** | What does key capture open? | **No** |

**Malleability.** An attacker who knows nothing about the key can modify a ciphertext to control a
predictable change in the plaintext:

```
C' = C + Δ  (mod 10)     ⟹     M' = M + Δ  (mod 10)
```

Because the encoding is structured, a targeted change can be aimed at a specific field — and the message
format includes **quantities**. A single-digit modification to a count changes the report's content while
leaving the message perfectly decryptable, and the recipient has no redundancy to check against.

**Replay.** The source claims encryption prevents spoofing because an attacker without the key "cannot mimic
you." That is true for *forging new content* and false for replay: a recorded ciphertext retransmits
verbatim and decrypts perfectly, because nothing binds it to a time, a sequence number, or a session. The
sender crosses the line out on their own sheet; the receiver has no way to know the message has been heard
before. In a civil-defense context "all clear" or "stand down" can be replayed at any later time.

**Traffic analysis.** The clear-text header exposes three things: the sheet number (how many pads are in
use, whether one pad serves multiple messages, inventory over time); the starting line (a **monotonic counter
of cumulative volume**, so an observer can count messages, measure traffic precisely, detect a change in
behaviour, and correlate senders using pads from the same series); and the group count (message length
exactly, often the most informative feature).

**Forward secrecy.** Capture of a pad opens every message already sent on it and every message that will be
sent on the unused portion, and the recipient cannot know. Modern ratcheting protocols compromise one message
per key; an OTP compromises everything the pad will ever carry. The property that makes it unbreakable — one
key, one use, no evolution — is the property that makes capture total.

**Key distribution** is intrinsic and unsolved: the pad must never transit a channel an adversary can observe.
The OTP does not solve key distribution; it presupposes it. For a scenario premised on infrastructure
failure — when meeting in person is hardest and couriers are unavailable — the system's security assumption
is strongest exactly where its logistics assumption is weakest.

**The composite fix** is a single encrypted header group: a monotonic counter plus a short check value,
perhaps six digits, costing less than one word. It closes both the integrity and replay gaps. **Its absence
is the largest practical weakness in the system, and it is a protocol-design omission rather than a
cryptographic one.**

## DRYAD

A one-time sheet with A–Z down one axis and across the other; "I SET" plus a row letter selects the mapping,
and the letters below are read off. Sheets are used once and destroyed.

This is a **one-time authenticator, not a one-time cipher** — a single fixed substitution per sheet. Its
weakness is that repeated plaintext letters produce repeated ciphertext letters, so it is monoalphabetic
within a sheet and inherits every weakness of substitution. The source presents this as a usability caveat;
it is a security property.

Its security comes from **message brevity**: for a two-word exchange, frequency analysis has no material, and
the one-time sheet means a captured reply cannot be reused. That is why it is short-message only — not a
limitation to be apologised for, but the design. Describing it as "functionally similar to a one-time pad"
blurs the distinction that makes it useful.

## Human factors

The demo contains its own error. Mid-encoding the presenter drops a letter and notices: *"I missed an S,
didn't I?"* Three errors in one twenty-minute demonstration by the person who made the video, comfortable, no
time pressure, no adversary: a dropped letter, a wrong row, and a mis-parsed header.

The encoding is not self-synchronising, so error propagation is severe:

| Error | Effect |
|---|---|
| One digit dropped | Every subsequent group misaligned; the remainder decodes as garbage |
| One digit wrong | One group decodes to a wrong character, if boundaries are intact |
| One group dropped | The rest decodes correctly but is offset |
| A key digit skipped | Same as a dropped digit, and the crossed-out-line discipline hides it |

And the receiver cannot tell which occurred, because there is no check value and no sequence number. A garbled
message is indistinguishable from a tampered one, a replayed one, or a correct one that reads oddly.

```
System security ≤ min( cryptographic strength, operator reliability, procedural discipline )
```

For a hand OTP the first term is infinite and the other two are ordinary human performance, so the system's
security is set entirely by the terms the video treats as an afterthought. That is the real finding, and the
video's own demonstration proves it.

## Legal framing

The source opens with a sketch in which an FCC officer berates a operator for encrypting, then says: "it's a
good thing this is not a ham radio channel. It's a civil defense/militia channel."

That is a rhetorical sidestep, not a legal argument. In the United States, 47 CFR §97.113(a)(4) restricts
transmissions on amateur frequencies whose meaning is obscured for the purpose of concealing it. **The
restriction attaches to the service a signal occupies, not to what a channel is called.** The technique is
lawful to learn and to teach; whether a given *transmission* is lawful depends on the service and licence.

## Operational security, and the irony

The video closes by announcing an intention to acquire a **Doppler radio-direction-finding unit**. Direction
finding does not break the cipher; **it locates the transmitter**, which is the property an OTP cannot
protect. The same channel is teaching confidentiality and, next episode, the tool that defeats the
operational layer around it.

Also unaddressed: **physical security of the pad**. A pad must be stored, transported, inventoried and
destroyed. Standard practice is serialised accountable pads, two-person control for issue, witnessed
destruction, inventory reconciliation, and separate storage of pad and codebook. The cryptographic strength
of the OTP is irrelevant if the pad is photographed. The video spends twenty minutes on the mathematics and
no time on the safe.

## Corrections

- **The substitution key count is 26!, not 2²⁶.** 2²⁶ is 67,108,864 — a factor of ~6 × 10¹⁸ too small. The
  correction strengthens the lesson: a cipher with 2⁸⁸ keys falling to a newspaper puzzle is a more striking
  demonstration than one with 2²⁶.
- **The mod-10 rule is "add ten," not "add a one."** `(1 − 7) mod 10 = 4`. The spoken rule describes writing a
  carried 1 graphically, so the arithmetic is right and the verbal rule is confusing — which matters in a
  procedure executed under stress.
- **Card shuffling is not "random enough for casinos."** A single riffle shuffle is far from uniform; roughly
  **seven** are needed (Bayer & Diaconis 1992), and human shuffling is additionally biased. Dice are the
  better tool because their independence is physical and auditable.
- **Dice**: five d10 give 10⁵ outcomes = **16.6 bits**, exactly enough for one five-digit group with no
  margin. The failure mode is the dice, not the procedure — cheap d10s are pentagonal trapezohedra and
  noticeably unbalanced, and a biased pad is not a pad.
- **"HPC"/"HLC"** → **HPLC**. The COA argument elsewhere in this archive depends on the same distinction.
- **"comse"** → COMSEC, which appears repeatedly and is the actual subject.

## Verification

Shannon (1949) was not read directly; the conditions are stated from standard knowledge. The *Signals
Handbook for Small Teams*, the source's primary reference, was not obtained — so it cannot be determined
whether the protocol gaps (no check value, no counter, clear-text header) are inherited from it or invented
by the presenter, which is the highest-value open question here. The DRYAD framing is asserted without a
doctrine source.
