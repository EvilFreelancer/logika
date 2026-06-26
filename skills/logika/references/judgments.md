# Judgments: Classification, Opposition, and Distribution

## 1. Basic Structure

Every judgment (proposition) has:
- **Subject (S)**: what is being talked about.
- **Predicate (P)**: what is being said about the subject.
- **Copula**: links S and P ("is" / "is not").

## 2. Classification by Quantity and Quality

| Type | Symbol | Formula | Example |
|------|--------|---------|---------|
| Universal Affirmative | **A** | All S are P | All humans are mortal. |
| Particular Affirmative | **I** | Some S are P | Some metals are precious. |
| Universal Negative | **E** | No S are P | No insect is vertebrate. |
| Particular Negative | **O** | Some S are not P | Some humans are not wise. |

Mnemonic: **A**ffirmo (A, I), **n**ego (E, O) — vowels of the Latin verbs.

## 3. Other Classifications

By **relation between S and P**:
- **Categorical**: unconditional assertion (S is P).
- **Conditional (hypothetical)**: If A is B, then C is D.
  - First part = ground (antecedens); second part = consequence (consequens).
- **Disjunctive**: S is either A, or B, or C.
  - Members must be exhaustive and mutually exclusive.
- **Conditional-disjunctive (dilemma)**: combination of conditional and disjunctive premises.

By **modality**:
- **Problematic**: possible (S is possibly P).
- **Assertoric**: actual (S is P).
- **Apodictic**: necessary (S must be P).

## 4. Distribution of Terms

A term is **distributed** if it is taken in its entire extension.

| Judgment | Subject (S) | Predicate (P) |
|----------|-------------|---------------|
| A (All S are P) | Distributed | **Not distributed** |
| E (No S are P) | Distributed | Distributed |
| I (Some S are P) | Not distributed | Not distributed |
| O (Some S are not P) | Not distributed | **Distributed** |

**Rule of thumb**: In negative judgments the predicate is distributed. In affirmative judgments the predicate is not distributed.

## 5. The Logical Square (Opposition of Judgments)

```
          A -------- E
         / \        / \
        /   \      /   \
       I ----O----
```

Relations:
1. **Contradictories** (A—O, E—I): opposite in both quantity and quality.
   - One must be true, one must be false. They cannot both be true or both false.
   - If A is true → O is false, and vice versa.
   - If E is true → I is false, and vice versa.
2. **Contraries** (A—E): opposite in quality, both universal.
   - Cannot both be true. Can both be false.
   - If A is true → E is false. If E is true → A is false.
   - But if A is false, E is undetermined; if E is false, A is undetermined.
3. **Subalterns** (A—I, E—O): same quality, different quantity.
   - Truth flows downward: if universal is true, particular is true.
   - Falsity flows upward: if particular is false, universal is false.
   - If A is true → I is true. If I is false → A is false.
   - If E is true → O is true. If O is false → E is false.
   - Reverse directions are **not** valid.
4. **Subcontraries** (I—O): opposite in quality, both particular.
   - Can both be true. Cannot both be false.
   - If I is false → O is true. If O is false → I is true.

**Summary Table**

| Given | A | E | I | O |
|-------|---|---|---|---|
| A true | — | E false | I true | O false |
| E true | A false | — | I false | O true |
| I true | A ? | E false | — | O ? |
| O true | A false | E ? | I ? | — |
| A false | — | E ? | I ? | O true |
| E false | A ? | — | I true | O ? |
| I false | A false | E true | — | O true |
| O false | A true | E false | I true | — |

("?" = undetermined)

## 6. Immediate Inferences

### A. Obversion (Prevrashchenie)
Change quality and negate the predicate; quantity stays the same.

| Original | Obverse |
|----------|---------|
| A: All S are P | E: No S are non-P |
| E: No S are P | A: All S are non-P |
| I: Some S are P | O: Some S are not non-P |
| O: Some S are not P | I: Some S are non-P |

### B. Conversion (Obrazovanie)
Swap S and P.

- **A**: Convert by limitation → **I** (because P is undistributed in A).
  - Exception: if S and P are equivalent (same extension), pure conversion to A is possible.
- **E**: Pure conversion → **E**.
- **I**: Pure conversion → **I**.
- **O**: **Not convertible** (would require distributing P in conclusion while it was undistributed in premise).

### C. Contraposition (Protivopostavlenie)
Obvert, then convert.

| Original | Contraposition |
|----------|----------------|
| A: All S are P | E: No non-P are S |
| E: No S are P | I: Some non-P are S |
| O: Some S are not P | I: Some non-P are S |
| I: Not applicable | — |

## Few-Shot Examples

**Example 1: Determine truth values**
> "All birds can fly" is false. What follows?
- A is false → O is true (contradictory). → "Some birds cannot fly" is true.
- A is false → E is undetermined, I is undetermined.

**Example 2: Convert and check validity**
> "No honest witness is bribed."
- E-judgment. Pure conversion: "No bribed person is an honest witness." Valid.

**Example 3: Obvert**
> "Some metals are precious."
- I → O: "Some metals are not non-precious."

**Example 4: Dilemma check**
> "If a pupil loves study, he needs no reward; if he feels aversion, reward is useless. But a pupil either loves study or feels aversion. Therefore reward is either superfluous or useless."
- Analysis: The disjunctive premise is not exhaustive. A pupil may be indifferent (neither love nor aversion). Therefore the dilemma is false.
