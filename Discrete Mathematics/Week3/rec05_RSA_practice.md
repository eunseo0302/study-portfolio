# Recitation 05: RSA Practice

This is a hands-on RSA encryption/decryption exercise based on the MIT OCW *Mathematics for Computer Science* course (Recitation 05). All computations were carried out manually using modular arithmetic and repeated squaring.

---

## 🔐 RSA Key Generation

**Chosen primes:**

- \( p = 5 \)
- \( q = 13 \)

**Compute:**

- \( n = p \times q = 5 \times 13 = 65 \)
- \( \phi(n) = (p-1)(q-1) = 4 \times 12 = 48 \)

---

**Choose public exponent \( e \):**

- \( e = 11 \), such that \( \gcd(11, 48) = 1 \)

---

**Compute private exponent \( d \):**

We want \( d \equiv e^{-1} \mod 48 \), i.e.,

\[
11d \equiv 1 \mod 48
\]

Using the Extended Euclidean Algorithm:

\[
1 = 3 \cdot 48 - 13 \cdot 11 \Rightarrow d \equiv -13 \equiv 35 \mod 48
\]

✅ So, the private key is \( d = 35 \)

---

## 🧾 Summary of Key Pairs

| Key Type    | Value          |
|-------------|----------------|
| Public Key  | \( (e, n) = (11, 65) \) |
| Private Key | \( (d, n) = (35, 65) \) |

---

## ✉️ Message Encryption

**Original message:**  
\[
m = 4 \quad \text{("You guys are slow!")}
\]

**Encrypt with public key (11, 65):**

\[
m' = 4^{11} \mod 65
\]

Using repeated squaring:

- \( 4^2 = 16 \)
- \( 4^4 = 16^2 = 256 \equiv 61 \mod 65 \)
- \( 4^8 = 61^2 = 3721 \equiv 16 \mod 65 \)

Now compute:

\[
4^{11} = 4^8 \cdot 4^2 \cdot 4 = 16 \cdot 16 \cdot 4 = 1024 \equiv \boxed{49} \mod 65
\]

🔒 **Encrypted message: \( m' = 49 \)**

---

## 🔓 Message Decryption

**Received ciphertext:** \( m' = 49 \)  
**Use private key \( d = 35 \)**

\[
m = 49^{35} \mod 65
\]

Using repeated squaring:

- \( 49^2 = 2401 \equiv 61 \mod 65 \)
- \( 49^4 = 61^2 = 3721 \equiv 16 \mod 65 \)
- \( 49^8 = 16^2 = 256 \equiv 61 \mod 65 \)
- \( 49^{16} = 61^2 = 3721 \equiv 16 \mod 65 \)
- \( 49^{32} = 16^2 = 256 \equiv 61 \mod 65 \)

Now combine powers:

\[
49^{35} = 49^{32} \cdot 49^2 \cdot 49 = 61 \cdot 61 \cdot 49 = 3721 \cdot 49 \equiv 16 \cdot 49 = 784 \equiv \boxed{4} \mod 65
\]

✅ **Decrypted message: \( m = 4 \)**

---

## ✅ Result

| Step       | Value |
|------------|-------|
| Original m | 4 ("You guys are slow!") |
| Encrypted  | 49    |
| Decrypted  | 4     |

---

## 📚 Reference

Based on **Recitation 5** of [MIT 6.042J: Mathematics for Computer Science (Fall 2010)](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2010/)

