# 📘 In-Class Problems – Week 1-2 (MIT 6.042J Discrete Mathematics)

## 🔍 Problem 3: Boolean Logic in Digital Circuit Design

### 🧠 Overview
Boolean logic is fundamental in digital circuit design, where T (True) corresponds to 1 and F (False) to 0. This problem explores how to express the bit-wise addition of binary numbers — either adding a single bit `b` to a binary number `k`, or summing two binary numbers — using Boolean logic formulas.

---

## (a) Add a Single Bit `b` to a Binary Number `k = aₙ ... a₀`

### ✨ Goal
- Input: `aₙ, ..., a₀` (binary representation of `k`), and `b ∈ {0, 1}`
- Output: `o₀, ..., oₙ₊₁` (bits of `k + b`)
- Internal carry bits: `c₀, ..., cₙ₊₁`

### ✅ Boolean Definitions

```
c₀     := b
For 0 ≤ i ≤ n:
  oᵢ   := aᵢ XOR cᵢ
  cᵢ₊₁ := aᵢ AND cᵢ
oₙ₊₁ := cₙ₊₁
```

- `XOR`: exclusive OR (⊕), true if operands differ
- `AND`: logical conjunction (∧), true only if both operands are true

---

## (b) Add Two Binary Numbers: `A = aₙ ... a₀`, `B = bₙ ... b₀`

### ✨ Goal
- Input: two binary numbers `A` and `B`
- Output: `o₀, ..., oₙ₊₁`
- Internal carry bits: `c₀, ..., cₙ₊₁`

### ✅ Boolean Definitions (Full Adder)

```
c₀     := 0
For 0 ≤ i ≤ n:
  oᵢ   := aᵢ XOR bᵢ XOR cᵢ
  cᵢ₊₁ := (aᵢ AND bᵢ) OR (aᵢ AND cᵢ) OR (bᵢ AND cᵢ)
oₙ₊₁ := cₙ₊₁
```

- `OR`: logical disjunction (∨), true if any operand is true

---

## 📌 Summary

- Part (a) handles adding a single bit `b` to an `n+1`-bit number `k`.
- Part (b) defines a general full-adder for summing two `n+1`-bit binary numbers.
- All operations rely on basic Boolean logic: `XOR`, `AND`, and `OR`, making them implementable in digital logic circuits.

---
