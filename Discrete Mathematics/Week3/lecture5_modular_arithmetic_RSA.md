# 📚 Lecture 5 Summary: Modular Arithmetic & RSA

This summary covers the key concepts from Lecture 5 of MIT 6.042J — focusing on modular arithmetic and the RSA encryption scheme.

---

## 🧮 Modular Arithmetic Basics

### 1. Definition

If integers `a`, `b`, and `n > 0` satisfy:

```
a ≡ b (mod n)
```

then `n` divides `(a - b)`, i.e., `a` and `b` leave the same remainder when divided by `n`.

---

## 🔁 Modular Inverses

### Definition

An integer `a⁻¹` is the **modular inverse** of `a mod n` if:

```
a · a⁻¹ ≡ 1 (mod n)
```

### When does it exist?

Only if `gcd(a, n) = 1`, i.e., `a` and `n` are coprime.

### How to find it?

Use the **Extended Euclidean Algorithm** (a.k.a. Pulverizer) to solve:

```
a · x + n · y = 1
→ x ≡ a⁻¹ mod n
```

---

## 🧠 Euler’s Totient Function \( \varphi(n) \)

### Definition

`φ(n)` counts the number of integers `1 ≤ k < n` such that `gcd(k, n) = 1`.

### Special cases:

- If `n` is prime → `φ(n) = n - 1`
- If `n = p · q` (distinct primes) → `φ(n) = (p-1)(q-1)`

---

## 🔐 RSA Encryption Scheme

### 1. Key Generation

1. Choose two large primes: `p`, `q`
2. Compute `n = p · q`
3. Compute `φ(n) = (p-1)(q-1)`
4. Choose `e` such that `1 < e < φ(n)` and `gcd(e, φ(n)) = 1`
5. Compute `d` such that:

   ```
   e · d ≡ 1 (mod φ(n))
   ```

   → `d` is the **modular inverse of e mod φ(n)**

- **Public key**: `(e, n)`
- **Private key**: `(d, n)`

---

### 2. Encryption

Given message `m` (as integer `0 < m < n`):

```
c = m^e mod n
```

---

### 3. Decryption

Given ciphertext `c`, decrypt using:

```
m = c^d mod n
```

This works because:

```
c = m^e  ⇒  c^d = m^{ed}
→ ed ≡ 1 mod φ(n) ⇒ m^{ed} ≡ m mod n
```

🧠 **Key idea**: `d` is the modular inverse of `e`, so raising to the `d`th power undoes what raising to the `e`th power did.

---

## 🧠 Why is decryption m = c^d valid?

Because:

- `c = m^e`
- `c^d = (m^e)^d = m^{ed}`
- If `ed ≡ 1 (mod φ(n))`, then `m^{ed} ≡ m (mod n)` by **Euler's theorem**

This is the heart of RSA.

---

## ✨ Summary

| Concept | Meaning |
|--------|---------|
| `a ≡ b (mod n)` | a and b have same remainder mod n |
| Modular inverse | `a⁻¹` satisfies `a·a⁻¹ ≡ 1 mod n` |
| Euler’s φ(n) | Number of integers < n coprime to n |
| RSA encryption | `c = m^e mod n` |
| RSA decryption | `m = c^d mod n` (since `ed ≡ 1 mod φ(n)`) |

---

## 🧩 Example

Let `p = 7`, `q = 11`

- `n = 77`
- `φ(n) = 60`
- Choose `e = 17`, then `d = 53` (since `17·53 ≡ 1 mod 60`)
- Encrypt: `m = 9` → `c = 9^17 mod 77 = 4`
- Decrypt: `m = 4^53 mod 77 = 9` ✅

---
