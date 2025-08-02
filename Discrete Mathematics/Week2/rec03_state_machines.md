# Recitation 3 – State Machines & Invariants

## 📘 Overview

This summary covers three classic problems from Recitation 3 of MIT 6.042J (Fall 2010):

1. [Problem 1: Breaking a Chocolate Bar](#-problem-1-breaking-a-chocolate-bar)
2. [Problem 2: The Temple of Forever – Can You Escape?](#-problem-2-the-temple-of-forever--can-you-escape)
3. [Problem 3: Maximum Number of Reachable Unique States](#-problem-3-maximum-number-of-reachable-unique-states)

---

## 🍫 Problem 1: Breaking a Chocolate Bar

### 🧩 Problem

You are given an \( m \times n \) chocolate bar.  
You may break one piece at a time (either vertically or horizontally).  
Your goal is to end up with \( m \cdot n \) individual 1×1 squares.

### ✅ Claim

No matter how you break it, you always need **exactly \( mn - 1 \)** breaks.

### 🧠 Proof Sketch (Strong Induction)

Let \( P(k) \): A bar of size \( k \) needs \( k - 1 \) breaks to split into 1×1 squares.

- **Base case**: \( P(1) \) is true → no break needed.
- **Inductive step**:
  - Assume \( P(s) \) is true for all \( s \leq k \).
  - For size \( k+1 \), split into two parts: \( p \), \( q \), with \( p + q = k+1 \).
  - Use hypothesis: \( P(p) = p - 1 \), \( P(q) = q - 1 \)
  - Total breaks: \( 1 + (p - 1) + (q - 1) = p + q - 1 = k \)

✅ Therefore, \( P(k+1) \) holds and the claim follows by strong induction.

---

## 🧘 Problem 2: The Temple of Forever – Can You Escape?

### 🧩 Setup

Each monk starts with:
- 15 red beads
- 12 green beads

At each Gong of Time, the monk must do **one** of:

1. **Exchange**: If \( r \geq 3 \), exchange 3 red beads for 2 green beads  
   \[
   (r, g) \rightarrow (r - 3, g + 2)
   \]

2. **Swap**: Replace red ↔ green counts  
   \[
   (r, g) \rightarrow (g, r)
   \]

### 🎯 Escape Condition

A monk may leave the temple **only if** their bowl has **exactly (5, 5)**.

### 🔒 Invariant (Mod 5 Argument)

Let us define an invariant:
- After any sequence of steps, \( r - g \equiv 2 \text{ or } 3 \pmod{5} \)

This holds because:
- Exchange reduces \( r - g \) by 5
- Swap changes \( r - g \) to \( -(r - g) \)
- Both preserve the mod 5 class of 2 or 3

Initial state: \( r - g = 15 - 12 = 3 \Rightarrow 5 \cdot 0 + 3 \)

The target state (5, 5) has \( r - g = 0 \), which is not congruent to 2 or 3 mod 5.

### ✅ Conclusion

**No monk can ever reach (5, 5). Escape is impossible.**

---

## 🔢 Problem 3: Maximum Number of Reachable Unique States

### 🧩 Question

Starting from (15, 12), how many **distinct** (r, g) states can a monk possibly visit by applying any sequence of **Exchange** and **Swap** operations?

### 🧠 Key Observations

- Each **Exchange** reduces total bead count \( r + g \) by 1  
  - Start: \( r + g = 27 \)
  - Must stop when \( r + g = 2 \) (since \( r < 3 \) → no more exchange possible)
  - ⇒ **Maximum of 25 exchanges**

- Each **Swap** just flips the pair  
  - A swap done twice brings you back:  
    \( (a, b) \rightarrow (b, a) \rightarrow (a, b) \)
  - So **each pair of swaps contributes at most 1 new state**

- If you perform a swap between each exchange (including first and last), you can have **up to 26** useful swaps.

### ✅ Conclusion

- \( 26 \) unique states from exchanges (initial + 25)
- \( 26 \) more from well-placed swaps
- **Maximum number of distinct reachable states:**
  \[
  26 + 26 = \boxed{52}
  \]

---

## ✅ Summary Table

| Problem                        | Key Result                         | Main Idea            |
|-------------------------------|------------------------------------|----------------------|
| Chocolate Bar                 | Breaks needed = \( mn - 1 \)        | Strong Induction     |
| Temple of Forever (Escape)    | (5, 5) is unreachable               | Invariant (mod 5)    |
| Max Reachable States          | At most 52 unique states reachable | State tracing + logic |

---

📘 Source: [MIT OCW 6.042J Recitation 3 Solutions (Fall 2010)](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2010/53de72598d04039f51069ac2e1ac812e_MIT6_042JF10_rec03_sol.pdf)
