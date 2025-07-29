# 📘 MIT 6.042J - Week 1 Assignment (2010)

> Discrete Mathematics for Computer Scientists  
> 🔍 Week 1 Focus: Propositional Logic, Predicate Logic, NAND Logic, and Basic Number Theory

---

## ✅ Problem 1 – Translating English to Predicate Logic

Let:
- `S(x)` = "x has taken 6.042"
- `A(x)` = "x got an A in 6.042"
- `T(x)` = "x is a TA for 6.042"
- `E(x, y)` = "x and y are the same person"

### (a) ∃x. S(x) ∧ A(x)
> There exists someone who has taken 6.042 and gotten an A.

### (b) ∀x. (T(x) ∧ S(x)) → A(x)
> All TAs who took 6.042 got an A.

### (c) ¬∃x. T(x) ∧ ¬A(x)
> There are no TAs who did not get an A.

### (d) ∃x∃y∃z. (x ≠ y ∧ y ≠ z ∧ x ≠ z) ∧ T(x) ∧ ¬S(x) ∧ T(y) ∧ ¬S(y) ∧ T(z) ∧ ¬S(z)
> There are at least three distinct TAs who did not take 6.042.

---

## ✅ Problem 2 – Truth Table Proofs

### (a) Prove:  
¬(P ∨ (Q ∧ R)) ≡ (¬P) ∧ (¬Q ∨ ¬R)  
✅ **True** for all inputs (proved via full truth table)

### (b) Prove or Disprove:  
¬(P ∧ (Q ∨ R)) ≡ ¬P ∨ (¬Q ∧ ¬R)  
❌ **Not equivalent** (counterexample when P=T, Q=T, R=F)

---

## ✅ Problem 3 – Expressing Logic with NAND

### (a) Using `¬` and `↑` (NAND):

| Expression | NAND Form |
|------------|-----------|
| A ∧ B | (A ↑ B) ↑ (A ↑ B) |
| A ∨ B | (A ↑ A) ↑ (B ↑ B) |
| A ⇒ B | (A ↑ (B ↑ B)) |

### (b) Using **only** NAND (no ¬):

- `¬A = A ↑ A`
- So:  
  - A ∧ B = (A ↑ B) ↑ (A ↑ B)  
  - A ∨ B = (A ↑ A) ↑ (B ↑ B)  
  - A ⇒ B = A ↑ (B ↑ B)

### (c) Construct `true` and `false` using only NAND:

- Always **true**: `A ↑ (A ↑ A)`
- Always **false**: `(A ↑ (A ↑ A)) ↑ (A ↑ (A ↑ A))`

---

## ✅ Problem 4 – 12 Coin Puzzle (Find the fake)

**Strategy (max 3 weighings):**
1. Split 12 coins into 3 groups of 4 (A, B, C)
2. Compare A vs B:
   - If balanced → fake is in C
   - If tilted → fake is in lighter group
3. Pick 3 coins from suspect group, compare with 3 known good coins
4. Final weighing: compare 2 remaining suspects

✅ Guaranteed to identify the lighter fake coin in 3 weighings.

---

## ✅ Problem 5 – Contrapositive Proof

### Statement:
If \( r^{1/5} \) is irrational, then \( r \) is irrational.

### Contrapositive:
If \( r \in \mathbb{Q} \), then \( r^{1/5} \in \mathbb{Q} \)

### Proof:
- Let \( r = \frac{a}{b} \)  
- Then \( r^{1/5} = \left(\frac{a}{b}\right)^{1/5} \in \mathbb{Q} \)  
✅ Thus, contrapositive holds → original statement is true.

---

## ✅ Problem 6 – Parity Proof with Squares

### Given:
\( w^2 + x^2 + y^2 = z^2 \), all variables ∈ ℕ⁺

### Prove:
\( z \) is even **iff** \( w, x, y \) are all even

### Key idea:
- Even² ≡ 0 mod 4, Odd² ≡ 1 mod 4
- If w/x/y include:
  - 1 odd → sum ≡ 1 mod 4 → possible
  - 2 odd → sum ≡ 2 mod 4 → ❌ not a square
  - 3 odd → sum ≡ 3 mod 4 → ❌ not a square
  - all even → sum ≡ 0 mod 4 → z² ≡ 0 → z even ✅

✅ Both directions proved.

---
