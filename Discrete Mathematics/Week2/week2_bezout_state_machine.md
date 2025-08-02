# 📘 Week 2 – State Machines, Invariants, and Bézout’s Identity

This week’s focus is on applying **state machine models**, using **invariants** to reason about possible outcomes, and connecting them to number theory through **linear combinations** and the **greatest common divisor (GCD)**.

---

## 🏗️ 1. State Machines

A **state machine** is a model of computation defined by:

- A finite set of **states**
- A set of **inputs** and **transition rules**
- A **start state**
- Optional: accepting/final states

At each step, the machine transitions from one state to another according to input and rules.

### 🔹 Example: Jug Problem

You have a 3-gallon and 5-gallon jug.  
You can fill, empty, or pour water between them.  
Each state is represented as a pair `(x, y)` where:
- `x`: amount in 3-gallon jug
- `y`: amount in 5-gallon jug

The question is: **Can you reach a state where one jug has exactly 4 gallons?**

---

## 🧷 2. Invariants

An **invariant** is a condition that remains true throughout all transitions of a state machine.

### ✅ Example Invariant in the Jug Problem:

Let `m = gcd(3, 5) = 1`. Then, **any state (x, y)** reachable from (0, 0) satisfies:

\[
x + y \equiv 0 \pmod{1} \Rightarrow \text{(i.e., all integers)}.
\]

But if instead the jugs were 3 and 6 gallons, then `gcd(3, 6) = 3`.  
So **only multiples of 3** can be reached:
- No way to get 4 gallons → **Invariant proves impossibility**

---

## 🧠 3. Linear Combinations

A **linear combination** of integers `a` and `b` is any number of the form:

\[
sa + tb \quad \text{where } s, t \in \mathbb{Z}
\]

### 🔹 Example:
Let `a = 3`, `b = 5`. Then:

\[
3·3 + 5·(-1) = 4 \Rightarrow 4 \text{ is a linear combination of 3 and 5}
\]

---

## 📏 4. GCD and Linear Combinations

> Key idea: **All linear combinations of `a` and `b` are multiples of `gcd(a, b)`**

So if:
- `gcd(a, b) = d`
- Then every `sa + tb` is a multiple of `d`

This is why **gcd divides all linear combinations** of `a` and `b`.

---

## 📐 5. Bézout’s Identity

### 🎯 Statement:

> For any integers `a` and `b`, there exist integers `s` and `t` such that:

\[
\gcd(a, b) = sa + tb
\]

---

## 🧮 6. Proof using Strong Induction

### 📌 Base Case: `b = 0`

\[
\gcd(a, 0) = a = 1·a + 0·b
\]

✅ Identity holds.

---

### 🔁 Inductive Step:

Assume:
\[
\gcd(b, a \bmod b) = sb + t(a \bmod b)
\]

But:
\[
a \bmod b = a - q·b
\Rightarrow
\gcd(a, b) = s·b + t·(a - qb)
= t·a + (s - t·q)·b
\]

So:
\[
\gcd(a, b) = s'·a + t'·b
\quad \text{where } s' = t, \, t' = s - t·q
\]

✅ Holds for all `a, b` by induction.

---

## ✅ Final Takeaways

| Concept | Summary |
|--------|---------|
| State Machine | System with states and transitions |
| Invariant | Property that remains true through all transitions |
| Linear Combination | Any number of the form `sa + tb` |
| GCD | The greatest number that divides both a and b |
| Bézout’s Identity | `gcd(a, b) = sa + tb` for some integers `s, t` |

---

## ✨ Bonus: Extended Euclidean Algorithm (Optional)

To compute `gcd(a, b)` and the coefficients `s, t`, use the extended Euclidean algorithm:

```python
def extended_gcd(a, b):
    if b == 0:
        return (a, 1, 0)
    g, s1, t1 = extended_gcd(b, a % b)
    return (g, t1, s1 - (a // b) * t1)
