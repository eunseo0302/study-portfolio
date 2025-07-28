# 📘 In-Class Problems – Week 1-1 (MIT 6.042J Discrete Mathematics)

## 🔍 Problem 1: Identify the mistake in each bogus proof

---

### (a) Claim:  
```
1/8 > 1/4
```

#### ❌ Bogus proof:
```
3 > 2  
3 log10(1/2) > 2 log10(1/2)  
log10((1/2)^3) > log10((1/2)^2)  
(1/2)^3 > (1/2)^2  
```

#### 🔎 Explanation:
The error lies in step 2.  
Since `log10(1/2)` is **negative**, multiplying both sides by it should **reverse the inequality sign**.  
The reasoning fails due to incorrect handling of inequalities involving negative numbers.

---

### (b) Claim:
```
1¢ = $0.01 = ($0.1)^2 = (10¢)^2 = 100¢ = $1
```

#### ❌ Bogus proof:
This manipulation treats **monetary units as algebraic quantities** that can be squared, which is incorrect.

#### 🔎 Explanation:
You **cannot square a unit** like dollars or cents.  
For example, `(10¢)^2 = 100 (¢)^2`, not `100¢`.  
This is a misuse of dimensional reasoning and leads to a false conclusion.

---

## 🧮 Problem 2: AM ≥ GM Inequality

### Claim:
```
(a + b)/2 ≥ √(ab), for all nonnegative real numbers a and b.
```

#### ❌ Bogus proof:
```
(a + b)/2 ≥ √(ab)  
a + b ≥ 2√(ab)  
a^2 + 2ab + b^2 ≥ 4ab  
a^2 - 2ab + b^2 ≥ 0  
(a - b)^2 ≥ 0  
```

#### 🔎 Explanation:
Although `(a - b)^2 ≥ 0` is **true**, the proof is **invalid** because it works **backwards** from the desired conclusion.  
This is a **circular argument** — assuming the conclusion and deriving a true statement from it does not constitute a valid proof.
(a - b)^2 ≥ 0  
⇒ a^2 - 2ab + b^2 ≥ 0  
⇒ a^2 + b^2 ≥ 2ab  
⇒ (a + b)^2 ≥ 4ab  
⇒ (a + b)/2 ≥ √(ab)
```
