---
name: logika
version: 1.0.0
description: >
  Use when the user needs logical analysis, reasoning chains, or critical thinking
  grounded in classical formal logic (concepts, judgments, syllogisms, induction, fallacies).
  Triggers: analyzing arguments, checking validity of inferences, classifying concepts or
  judgments, building syllogisms, identifying logical errors, solving logic textbook problems,
  constructing proofs, or evaluating hypotheses and analogies.
---

# Logika

This skill equips the agent with a classical formal logic framework (based on G. Chelpanov's textbook) to analyze reasoning step by step.

## Response Format

When answering ANY logical task, you MUST respond with a single JSON object containing exactly two fields:
- `reasoning`: your step-by-step logical analysis (plain text, no markdown inside)
- `answer`: the final answer (yes/no for BQA; A/B/C/D for MCQA)

No text before or after the JSON. No markdown code blocks. No explanations outside the JSON.

## Core Workflow

When given any logical task, follow this chain of thought inside the `reasoning` field:

1. **Identify the objects**: Are we dealing with concepts, judgments, inferences, or proofs?
2. **Apply the appropriate formal apparatus**: Use the reference files listed below.
3. **Verify with rules**: Every inference must be checked against the relevant rules (syllogism rules, law of thought, etc.).
4. **State the conclusion clearly**: Indicate whether the reasoning is valid, what fallacy (if any) is present, and what the correct inference should be.

## When to Load References

- **Concepts & definitions** (`references/concepts.md`): When the task involves classifying terms, defining concepts, dividing a genus into species, or checking definition correctness.
- **Judgments & opposition** (`references/judgments.md`): When the task involves classifying judgments by quantity/quality, drawing the logical square, checking distribution, or immediate inferences (conversion, obversion).
- **Syllogism** (`references/syllogism.md`): When the task involves checking a syllogism, finding the figure/mode, reducing figures, or building a deductive proof.
- **Induction & scientific method** (`references/induction.md`): When the task involves inductive reasoning, Mill's methods, analogy, hypothesis, or classifying empirical vs. derivative laws.
- **Logical errors** (`references/errors.md`): When the task requires identifying a fallacy, sophism, paralogism, or logical mistake in an argument.
- **Laws of thought** (`references/laws.md`): When the task involves checking compliance with identity, non-contradiction, excluded middle, or sufficient reason.

## Universal Principles (Always Keep in Mind)

1. **Law of Identity**: A concept must keep the same meaning throughout the reasoning.
2. **Law of Non-Contradiction**: A and not-A cannot both be true in the same respect.
3. **Law of Excluded Middle**: Between A and not-A there is no middle ground.
4. **Law of Sufficient Reason**: Every judgment must have a logical ground.

## Quick-Check: Syllogism Validity

Before loading the full syllogism reference, run this 8-rule checklist:

1. Exactly 3 terms (watch for equivocation / quaternio terminorum).
2. Exactly 3 judgments (2 premises + 1 conclusion).
3. Middle term must be distributed at least once.
4. A term not distributed in the premises cannot be distributed in the conclusion.
5. Two negative premises yield no conclusion.
6. One negative premise forces a negative conclusion (and vice versa).
7. Two particular premises yield no conclusion.
8. One particular premise forces a particular conclusion.

If any rule is violated, the syllogism is invalid. Name the fallacy.

## Few-Shot Patterns

### Pattern A: Classify a judgment and find its relations

**User**: "All metals are elements. Some bodies are metals. Therefore some bodies are elements."
**Agent thinking**:
- Step 1: Identify judgments. Major premise: A (All M are P). Minor premise: I (Some S are M). Conclusion: I (Some S are P).
- Step 2: Check figure. Middle term "metals" is predicate in major, subject in minor → Figure 1.
- Step 3: Check mode against rules. A-I-I in Figure 1 is Darii, a valid mode.
- Step 4: Verify 8 rules quickly. Middle distributed? In A premise predicate is not distributed, but subject M is distributed. Rule 3 satisfied. No rule violated.
**Answer**: `{"reasoning": "Major premise: All M are P (A). Minor: Some S are M (I). Conclusion: Some S are P (I). Middle term 'metals' is predicate in major, subject in minor → Figure 1. A-I-I in Figure 1 is Darii, valid mode. Middle distributed in major premise (subject of A). No rule violated.", "answer": "yes"}`

### Pattern B: Detect a logical error

**User**: "All historians are impartial. Naturalists are not historians. Therefore naturalists are not impartial."
**Agent thinking**:
- Step 1: Form. Major: All M are P (A). Minor: No S are M (E). Conclusion: No S are P (E). Figure 2.
- Step 2: Rule 4 check. Predicate P = "impartial" is not distributed in major premise (predicate of A), but in conclusion it is distributed (predicate of E). This is illicit major (illicit process of the major term).
**Answer**: `{"reasoning": "Major: All M are P (A). Minor: No S are M (E). Conclusion: No S are P (E). Figure 2. Predicate P = 'impartial' is not distributed in major premise (predicate of A), but in conclusion it is distributed (predicate of E). This is illicit major (illicit process of the major term).", "answer": "no"}`

### Pattern C: Immediate inference — conversion

**User**: "Convert: All squares are rectangles."
**Agent thinking**:
- Step 1: A-judgment. Predicate "rectangles" is not distributed in A.
- Step 2: Pure conversion impossible because predicate would become subject of A and thus distributed, which is illicit.
- Step 3: Convert by limitation (per accidens): "Some rectangles are squares" (I-judgment).
**Answer**: `{"reasoning": "A-judgment: All squares are rectangles. Predicate 'rectangles' is not distributed in A. Pure conversion impossible because predicate would become subject and thus distributed, which is illicit. Convert by limitation (per accidens): 'Some rectangles are squares' (I-judgment).", "answer": "Some rectangles are squares."}`

### Pattern D: Identify the opposition relation

**User**: "If 'All planets revolve around the Sun' is true, what about 'Some planets do not revolve around the Sun'?"
**Agent thinking**:
- Step 1: A-judgment vs O-judgment → contradictories.
- Step 2: By definition of contradiction, if A is true, O must be false.
**Answer**: `{"reasoning": "A-judgment vs O-judgment → contradictories. By definition of contradiction, if A is true, O must be false.", "answer": "no"}`

### Pattern E: Induction — Mill's method

**User**: "In three factories using different machines but the same lubricant, the same gear wear occurs. What method applies?"
**Agent thinking**:
- Step 1: Multiple cases with varying circumstances (different machines) but one common factor (same lubricant).
- Step 2: The phenomenon (gear wear) appears in all cases where the common factor is present.
- Step 3: This matches the Method of Agreement.
**Answer**: `{"reasoning": "Multiple cases with varying circumstances (different machines) but one common factor (same lubricant). The phenomenon (gear wear) appears in all cases where the common factor is present. This matches the Method of Agreement.", "answer": "Method of Agreement"}`
