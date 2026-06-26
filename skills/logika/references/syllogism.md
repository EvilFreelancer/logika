# Syllogism: Deductive Inference

## 1. Structure

A syllogism is a deductive inference with **two premises** and **one conclusion**, containing exactly **three terms**.

- **Major term (P)**: predicate of the conclusion.
- **Minor term (S)**: subject of the conclusion.
- **Middle term (M)**: appears in both premises but not in the conclusion. It links S and P.

- **Major premise**: contains P and M.
- **Minor premise**: contains S and M.
- **Conclusion**: contains S and P.

## 2. Axiom of the Syllogism (Dictum de omni et de nullo)

- What is affirmed of a whole class is affirmed of everything contained in it.
- What is denied of a whole class is denied of everything contained in it.

## 3. Eight Rules of the Syllogism

1. **Exactly three terms**. If a term is used in two senses (equivocation), there are four terms — *quaternio terminorum*.
2. **Exactly three judgments** (2 premises + 1 conclusion).
3. **Middle term must be distributed at least once**.
4. **A term not distributed in the premises cannot be distributed in the conclusion** (illicit major / illicit minor).
5. **Two negative premises yield no conclusion**.
6. **One negative premise requires a negative conclusion** (and conversely, a negative conclusion requires one negative premise).
7. **Two particular premises yield no conclusion**.
8. **One particular premise requires a particular conclusion**.

## 4. Figures of the Syllogism

Position of the middle term determines the figure:

| Figure | Major Premise | Minor Premise | Character / Use |
|--------|---------------|---------------|-----------------|
| **1**  | M is P        | S is M        | Subsumption: applying general laws to particular cases. |
| **2**  | P is M        | S is M        | Refutation: rejecting false subsumptions. One premise must be negative. |
| **3**  | M is P        | M is S        | Proving exceptions to general rules. Conclusion must be particular. |
| **4**  | P is M        | M is S        | Artificial; rarely used in practice. |

## 5. Valid Modes (19 Correct Moods)

| Figure | Modes | Mnemonic Verse |
|--------|-------|----------------|
| 1 | Barbara, Celarent, Darii, Ferio | *Barbara, Celarent, Darii, Ferioque prioris* |
| 2 | Cesare, Camestres, Festino, Baroko | *Cesare, Camestres, Festino, Baroko, sekundae* |
| 3 | Darapti, Disamis, Datisi, Felapton, Bokardo, Ferison | *Tertia Darapti, Disamis, Datisi, Felapton, Bokardo, Ferison habet* |
| 4 | Bramantip, Camenes, Dimaris, Fesapo, Fresison | *Quarta insuper addit Bramantip, Camenes, Dimaris, Fesapo, Fresison* |

**How to read the mnemonic names:**
- The vowels indicate the mood (A, E, I, O).
- **s** = the preceding premise undergoes simple conversion.
- **p** = the preceding premise undergoes conversion by limitation (per accidens).
- **m** = premises must be transposed (metathesis).
- **B, C, D, F** = the first-figure mode to which the reduction leads.
- **k** = the mode is proved by *reductio ad absurdum* (Baroko, Bokardo).

### Examples of Modes

**Barbara (1st fig., AAA)**
- All M are P. All S are M. ∴ All S are P.
- Ex: All predators eat meat. Tigers are predators. ∴ Tigers eat meat.

**Celarent (1st fig., EAE)**
- No M are P. All S are M. ∴ No S are P.
- Ex: No insect has more than 3 pairs of legs. Bees are insects. ∴ Bees do not have more than 3 pairs of legs.

**Cesare (2nd fig., EAE)**
- No P are M. All S are M. ∴ No S are P.
- Ex: No just person is envious. All ambitious people are envious. ∴ No ambitious person is just.

**Baroko (2nd fig., AOO)** — proved by *reductio ad absurdum*.
- All P are M. Some S are not M. ∴ Some S are not P.
- Ex: All truly moral actions spring from correct motives. Some benevolent actions do not spring from such motives. ∴ Some benevolent actions are not truly moral.

## 6. Reduction of Figures to Figure 1

Other figures can be reduced to Figure 1 to demonstrate their validity.

- **Cesare → Celarent**: simple conversion of the major premise (E).
- **Darapti → Darii**: conversion by limitation of the minor premise (A→I).
- **Bramantip → Barbara**: transpose premises (m), then convert conclusion by limitation (p).
- **Baroko / Bokardo**: proved by *reductio ad absurdum* using Barbara.

## 7. Conditional & Disjunctive Syllogisms

### Conditional (Hypothetical)

**Modus ponens** (constructive):
- If A then B. A. ∴ B.

**Modus tollens** (destructive):
- If A then B. Not B. ∴ Not A.

**Invalid forms** (fallacies):
- Affirming the consequent: If A then B. B. ∴ A. ❌
- Denying the antecedent: If A then B. Not A. ∴ Not B. ❌

### Disjunctive

**Modus ponendo-tollens**:
- A is either B, C, or D. A is B. ∴ A is neither C nor D.

**Modus tollendo-ponens**:
- A is either B, C, or D. A is neither B nor C. ∴ A is D.

Used in geometry as **proof by exclusion** (indirect proof).

## 8. Abbreviated and Complex Syllogisms

- **Enthymeme**: syllogism with one part omitted.
  - 1st kind: missing major premise.
  - 2nd kind: missing minor premise.
  - 3rd kind: missing conclusion (implied).
- **Epicheirema**: syllogism where both premises are themselves enthymemes (conclusions with middle terms).
- **Polysyllogism (sorites)**:
  - Chain of syllogisms where the conclusion of one is a premise of the next.
  - **Progressive**: from more general to less general.
  - **Regressive**: from less general to more general.
- **Sorites (Aristotelian)**: chain where minor premises are omitted.
- **Sorites (Goclenian)**: chain where major premises are omitted.

## Few-Shot Examples

**Example 1: Check validity**
> "All French are Europeans. All Parisians are Europeans. Therefore all Parisians are French."
- Middle = Europeans. Figure 2 (P-M, S-M).
- M is undistributed in both premises (predicate of A in both).
- Violates Rule 3. Invalid.

**Example 2: Detect equivocation**
> "An onion is a weapon of savages. This plant is an onion. Therefore this plant is a weapon."
- "Onion" means different things in the two premises (vegetable vs. bow). Quaternio terminorum. Invalid.

**Example 3: Reduce Cesare to Celarent**
> Cesare: No P are M. All S are M. ∴ No S are P.
- Convert major: No M are P. All S are M. ∴ No S are P. → Celarent (Figure 1).

**Example 4: Reconstruct an enthymeme**
> "Stinginess deserves blame, for it is a vice."
- Missing major: "All vices deserve blame."
- Full syllogism: All vices deserve blame. Stinginess is a vice. ∴ Stinginess deserves blame.
