# Recitation 2: Geometric Sum & Purple-Eyed Logic Puzzle

## 🟣 Problem 1: Geometric Sum

### Problem Statement

Prove the following identity for all real numbers \( r \neq 1 \):

\[
1 + r + r^2 + r^3 + \cdots + r^n = \frac{1 - r^{n+1}}{1 - r}
\]

Prove it using:
1. The Well-Ordering Principle
2. Mathematical Induction

---

### ✅ Proof Using the Well-Ordering Principle

We assume the identity is false and define the set of counterexamples:

\[
C := \left\{ n \in \mathbb{N} \mid 1 + r + r^2 + \cdots + r^n \neq \frac{1 - r^{n+1}}{1 - r} \right\}
\]

By assumption, \( C \) is non-empty. Let \( c \) be the smallest element of \( C \).

- Since the formula is true for \( n = 0 \) (both sides equal 1), we know \( c > 0 \).
- Thus, the identity holds for \( c - 1 \):

\[
1 + r + \cdots + r^{c-1} = \frac{1 - r^c}{1 - r}
\]

Adding \( r^c \) to both sides:

\[
1 + r + \cdots + r^c = \frac{1 - r^c + r^c(1 - r)}{1 - r} = \frac{1 - r^{c+1}}{1 - r}
\]

So the formula also holds for \( c \), contradicting the assumption.

Hence, the formula is valid for all \( n \in \mathbb{N} \). ■

---

## 🟣 Problem 2: The Purple-Eyed Islanders

### Setup

- On an island, there are \( p \geq 1 \) people with **purple eyes**, and \( r \geq 0 \) with **red eyes**.
- Everyone can see others' eye colors, but not their own.
- No one may speak about eye color.
- If someone logically deduces their own eyes are **purple**, they must **leave the island at midnight**.
- All participants are **perfect logicians**.

---

### The Twist

One day, a host publicly announces:

> "I see at least one person with purple eyes."

---

### ❓ What happens next?

**All \( p \) purple-eyed people will leave the island on the \( p^{th} \) night.**

---

### 🧠 Why?

Let’s use inductive reasoning.

#### Case: \( p = 1 \)

- The one purple-eyed person sees no other purple eyes.
- The host’s statement implies at least one exists → must be themself.
- → Leaves on night 1.

#### Case: \( p = 2 \)

- Each sees one purple-eyed person.
- If I don’t have purple eyes, that person is the only one → they’ll leave on night 1.
- But no one leaves on night 1 → I must have purple eyes too.
- → Both leave on night 2.

#### Case: \( p = 3 \)

- Each sees two purple-eyed people.
- If I’m not purple-eyed, the other two would believe \( p = 2 \) and leave on night 2.
- But they don't → I must also be purple-eyed.
- → All leave on night 3.

And so on...

---

### ✅ Formal Inductive Statement

Let \( P(n) \) be the claim:

1. If \( p > n \), then no one leaves on day \( n \).
2. If \( p = n \), all purple-eyed people leave on day \( n \).
3. If \( p < n \), all have already left.

Using mathematical induction, we prove that all \( p \) purple-eyed participants leave on day \( p \).

---

### 🔍 Key Insight

- Participants don’t know the value of \( p \), but use **logical deduction**.
- They **simulate what would happen if they had red eyes**.
- When the expected events do **not** happen (e.g., others don't leave early), they deduce their own identity.
- **Silence is information**.

---

## ✅ Summary

| Question | Answer |
|---------|--------|
| Do participants know how many purple-eyed people there are? | ❌ No |
| How do they figure it out? | Through daily logical reasoning and observing that no one leaves early |
| Why do they all leave together on day \( p \)? | Because only then does each of them gain enough logical evidence |
| Is this reasoning valid? | ✅ Yes, it's a classic inductive puzzle used in logic and computer science |

---
