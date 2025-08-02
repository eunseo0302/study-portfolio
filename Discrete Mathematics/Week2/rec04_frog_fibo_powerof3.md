# Recitation 4 – Problem Set Summary

MIT 6.042J – Mathematics for Computer Science  
Topics: Number Theory, Modular Arithmetic, Induction

---

## 🔹 Problem 1: The Pulverizer 🐸

### 🧩 Problem Summary

A frog sits on a circle of `n` pebbles. It jumps clockwise by exactly `k` pebbles.  
The frog’s food (a worm) lies exactly 1 pebble ahead.  
Can the frog reach the worm, and if so, how many jumps are needed?

---

### (a) When can't the frog reach the worm?

The frog visits positions:

```
0, k, 2k, 3k, ..., mod n
```

To reach the worm:
```
k * m ≡ 1 mod n
```

This has a solution **iff** `gcd(k, n) = 1`.  
So if `gcd(k, n) ≠ 1`, the frog can **never** reach the worm.

**Example:**  
If `k = 3`, `n = 6`: the frog will just visit `0, 3, 0, 3, ...`, never reaching 1.

---

### (b) When the frog can reach the worm — use Pulverizer

We want:
```
k * m ≡ 1 mod n
```
This is solved using the **Extended Euclidean Algorithm** (a.k.a. the Pulverizer),  
which finds integers `x`, `y` such that:
```
k * x + n * y = 1
⇒ x ≡ k⁻¹ mod n
```
Then `x` is the number of jumps.

---

### (c) Compute for `n = 50`, `k = 21`

Use Pulverizer:

```
1 = 8 * 50 - 19 * 21
⇒ 21 * (-19) ≡ 1 mod 50
⇒ j = -19 ≡ 31 mod 50
```

✅ **Minimum number of jumps: 31**

But note:

```
21 * 19 ≡ -1 mod 50
⇒ 21 * 931 = 21 * (19 * 49) ≡ 1 mod 50
```

So 931 is **also** a correct answer — but it's 49 cycles of 19 jumps, and inefficient.

---

## 🔹 Problem 2: Fibonacci Coprimality

### 🧩 Statement

Prove by induction that for all `n ≥ 0`, the Fibonacci numbers `Fₙ` and `Fₙ₊₁` are relatively prime:

```
gcd(Fₙ, Fₙ₊₁) = 1
```

Where:
- `F₀ = 0`
- `F₁ = 1`
- `Fₙ = Fₙ₋₁ + Fₙ₋₂` for `n ≥ 2`

---

### ✅ Inductive Proof

Let `P(n): gcd(Fₙ, Fₙ₊₁) = 1`.

**Base case:**  
`F₀ = 0`, `F₁ = 1` → `gcd(0, 1) = 1` ✔

**Inductive step:**  
Assume `gcd(Fₙ, Fₙ₊₁) = 1`.  
We want to prove `gcd(Fₙ₊₁, Fₙ₊₂) = 1`.

Since:
```
Fₙ₊₂ = Fₙ₊₁ + Fₙ
```

Suppose `d` divides both `Fₙ₊₁` and `Fₙ₊₂`. Then it must also divide:
```
Fₙ₊₂ - Fₙ₊₁ = Fₙ
```

⇒ `d` divides both `Fₙ` and `Fₙ₊₁`, contradicting the inductive hypothesis.  
Thus, `gcd(Fₙ₊₁, Fₙ₊₂) = 1`, and `P(n+1)` holds.

✅ By induction, `Fₙ` and `Fₙ₊₁` are relatively prime ∀ n ≥ 0.

---

## 🔹 Problem 3: The Power of 3

### 🧩 Statement

Let `N` be a number with `3ⁿ` identical digits (e.g., 777...777 with `3ⁿ` digits).  
Prove by induction that `3ⁿ` divides `N`.

Example:  
```
3² = 9  
N = 777777777 → 9 digits  
⇒ 9 | N
```

---

### ✅ Key Idea

Recall: A number is divisible by 3 **iff** its digit sum is divisible by 3.  
If `N` is made of `3ⁿ` copies of digit `d`, then:

```
Sum of digits = d * 3ⁿ
⇒ 3ⁿ | sum ⇒ 3ⁿ | N
```

---

### ✅ Inductive Proof

Let `P(n): 3ⁿ divides the number made of 3ⁿ identical digits d`.

**Base case (n = 0):**  
`3⁰ = 1`, and any digit is divisible by 1 ✔

**Inductive step:**  
Assume `P(k)` holds: 3ᵏ divides a number `Nₖ` of `3ᵏ` identical digits.

Then construct `Nₖ₊₁` by repeating `Nₖ` three times → has `3^{k+1}` digits.  
Its digit sum is:
```
3 × (d × 3ᵏ) = d × 3^{k+1}
⇒ divisible by 3^{k+1}
```

✅ Therefore, `P(k+1)` holds.

---

## ✅ Final Notes

These problems combine:
- **Modular arithmetic**
- **Greatest common divisors**
- **Modular inverses**
- **Proof by induction**
- **Digit-sum divisibility tests**

They form the foundation for number theory and computational mathematics.

---
