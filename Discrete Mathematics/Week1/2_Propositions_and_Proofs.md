📘 In-Class Problems – Week 1-2 (MIT 6.042J Discrete Mathematics)

🔍 Problem 3: Boolean Logic in Digital Circuit Design

🧠 Overview

Boolean logic is fundamental in digital circuit design, where T (True) corresponds to 1 and F (False) to 0. This problem explores how to express the bit-wise addition of binary numbers—either adding a single bit  to a binary number , or summing two binary numbers—using Boolean logic formulas.

✨ Goal

Input:  (binary representation of ), and 

Output:  (bits of )

Internal carry bits: 

✅ Boolean Definitions

c_0     ::= b
For 0 <= i <= n:
  o_i   ::= a_i ⊕ c_i
  c_{i+1} ::= a_i ∧ c_i
o_{n+1} ::= c_{n+1}

⊕: XOR (mod 2 sum)

∧: AND (carry generation)

✨ Goal

Input: two binary numbers A and B

Output: 

Internal carry bits: 

✅ Boolean Definitions (Full Adder)

c_0     ::= 0
For 0 <= i <= n:
  o_i   ::= a_i ⊕ b_i ⊕ c_i
  c_{i+1} ::= (a_i ∧ b_i) ∨ (a_i ∧ c_i) ∨ (b_i ∧ c_i)
o_{n+1} ::= c_{n+1}

∨: OR (carry merging condition)

⊕: XOR (bit-wise sum output)

📌 Summary

Part (a) handles the case of adding a single bit , while part (b) generalizes to the full addition of two binary numbers.

All expressions rely only on XOR, AND, and OR, making them suitable for implementation in logic circuits.

This document summarizes the Week 1-2 in-class discussion of binary addition via Boolean expressions.
