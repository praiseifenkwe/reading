# 🎯 PRACTICE PROBLEMS - Test Your Knowledge!

## Instructions:
1. Try each problem WITHOUT looking at the answer
2. Time yourself (should take 2-3 minutes per problem)
3. Check your answer
4. If wrong, understand WHY before moving on

---

## SECTION 1: Number Conversions (CRITICAL!)

### Problem 1.1: Decimal to Binary
Convert 157₁₀ to binary

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
157 ÷ 2 = 78 R 1  ← LSB
 78 ÷ 2 = 39 R 0
 39 ÷ 2 = 19 R 1
 19 ÷ 2 = 9  R 1
  9 ÷ 2 = 4  R 1
  4 ÷ 2 = 2  R 0
  2 ÷ 2 = 1  R 0
  1 ÷ 2 = 0  R 1  ← MSB
```
**Read bottom to top**: 10011101₂

**CHECK**: 128+16+8+4+1 = 157 ✓
</details>

### Problem 1.2: Binary to Hexadecimal
Convert 11010110₂ to hexadecimal

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Group into 4s from right: 1101 0110
- 1101 = D
- 0110 = 6

**ANSWER**: D6₁₆

**QUICK CHECK**: D=13, 6=6 → 13×16 + 6 = 214₁₀
Binary: 128+64+16+4+2 = 214₁₀ ✓
</details>

### Problem 1.3: Hexadecimal to Binary
Convert 3F₁₆ to binary

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
- 3 = 0011
- F = 1111

**ANSWER**: 00111111₂ (or 111111₂)
</details>

### Problem 1.4: Octal to Binary
Convert 157₈ to binary

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Each octal digit = 3 binary bits
- 1 = 001
- 5 = 101
- 7 = 111

**ANSWER**: 001101111₂ (or 1101111₂)
</details>

### Problem 1.5: Binary to Decimal
Convert 10110101₂ to decimal

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Position values: 128 64 32 16 8 4 2 1
Binary:           1  0  1  1  0 1 0 1

= 128 + 32 + 16 + 4 + 1
= **181₁₀**
</details>

---

## SECTION 2: 2's Complement (VERY IMPORTANT!)

### Problem 2.1: Find 2's Complement
Find the 2's complement of 01011010

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Step 1: Flip all bits
01011010 → 10100101

Step 2: Add 1
10100101 + 1 = **10100110**

**ANSWER**: 10100110
</details>

### Problem 2.2: Range Question
What is the range of 7-bit 2's complement numbers?

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Formula: -2^(n-1) to 2^(n-1) - 1

For n=7:
- Negative: -2^6 = -64
- Positive: 2^6 - 1 = 63

**ANSWER**: -64 to +63
</details>

### Problem 2.3: Subtraction Using 2's Complement
Perform 01101 - 00110 using 2's complement (5-bit)

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
A = 01101 (13)
B = 00110 (6)
Find A - B:

Step 1: Find 2's complement of B
00110 → flip → 11001 → add 1 → 11010

Step 2: Add A + (2's comp of B)
  01101
+ 11010
-------
1 00111

Step 3: Discard carry (result is positive)
**ANSWER**: 00111 = 7₁₀

**CHECK**: 13 - 6 = 7 ✓
</details>

### Problem 2.4: Negative Number Representation
What decimal number does 11010110 represent in 8-bit 2's complement?

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
First bit is 1 → negative number

Step 1: Find 2's complement to get magnitude
11010110 → flip → 00101001 → add 1 → 00101010

Step 2: Convert to decimal
00101010 = 32 + 8 + 2 = 42

Step 3: Apply negative sign
**ANSWER**: -42₁₀
</details>

---

## SECTION 3: K-Maps (MOST TESTED!)

### Problem 3.1: 3-Variable K-Map
Simplify F(A,B,C) = Σ(0,2,4,6)

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
      BC
     00 01 11 10
A 0 │1 │0 │0 │1 │
  1 │1 │0 │0 │1 │
```

Group all four 1s vertically (they're all in columns 00 and 10)
- BC changes (00 and 10)
- A changes (0 and 1)
- Only C' stays constant!

**ANSWER**: F = C'
</details>

### Problem 3.2: 4-Variable K-Map
Simplify F(A,B,C,D) = Σ(0,1,2,5,8,9,10)

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
       CD
      00 01 11 10
AB 00│1 │1 │0 │1 │
   01│0 │1 │0 │0 │
   11│0 │0 │0 │0 │
   10│1 │1 │0 │1 │
```

Groups:
1. m₀,m₁,m₈,m₉ (left column, wraps top-bottom) → B'·C'
2. m₀,m₂,m₈,m₁₀ (corners!) → B'·D'
3. m₁,m₅ → A'·C'·D

Wait, let me regroup optimally:
1. m₀,m₁,m₈,m₉ → B'·C'
2. m₀,m₂,m₈,m₁₀ → B'·D'

**ANSWER**: F = B'·C' + B'·D' = B'·(C' + D')
</details>

### Problem 3.3: K-Map with Don't-Cares
Simplify F(A,B,C,D) = Σ(1,3,5,7,9), d(6,12,13)

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
       CD
      00 01 11 10
AB 00│0 │1 │1 │0 │
   01│0 │1 │1 │X │
   11│X │X │0 │0 │
   10│0 │1 │0 │0 │
```

Groups (using X's strategically):
1. m₁,m₃,m₅,m₇ (right side, column 01 and 11) → C·D
2. m₉ alone or with X's

Actually, better grouping:
1. m₁,m₃,m₅,m₇,m₁₃ (include X at 13) → C·D
2. m₉ needs coverage → A·B'·C'·D

**ANSWER**: F = C·D + A·B'·C'·D
</details>

### Problem 3.4: POS from K-Map
Find POS form for F(A,B,C) = Σ(1,3,5,7)

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
      BC
     00 01 11 10
A 0 │0 │1 │1 │0 │
  1 │0 │1 │1 │0 │
```

For POS, group the 0s:
0s are at: m₀, m₂, m₄, m₆

Group: All four 0s (columns 00 and 10)
F' = C'
F = (F')' = (C')' = C

**ANSWER**: F = C (or in POS form: F = C)

Actually for proper POS: F = Π(0,2,4,6)
</details>

---

## SECTION 4: Boolean Algebra

### Problem 4.1: DeMorgan's Theorem
Simplify: (A + B·C)'

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Apply DeMorgan's:
(A + B·C)' = A' · (B·C)'

Apply DeMorgan's again:
= A' · (B' + C')

**ANSWER**: A'·(B' + C') or A'·B' + A'·C'
</details>

### Problem 4.2: Simplification
Simplify: A·B + A·B' + A'·B

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
A·B + A·B' + A'·B
= A·(B + B') + A'·B    [Factor A]
= A·1 + A'·B           [B + B' = 1]
= A + A'·B             [A·1 = A]
= A + B                [Absorption: A + A'·B = A + B]

**ANSWER**: A + B
</details>

### Problem 4.3: Prove Identity
Prove: A + A'·B = A + B

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Method 1 (Algebraic):
A + A'·B
= A·1 + A'·B           [A = A·1]
= A·(1 + B) + A'·B     [Distributive]
= A·1 + A·B + A'·B     [1 + B = 1]
= A + B·(A + A')       [Factor B]
= A + B·1              [A + A' = 1]
= A + B                [B·1 = B]

Method 2 (Truth Table):
```
A B | A' | A'·B | A+A'·B | A+B
----|----|----- |--------|----
0 0 | 1  | 0    | 0      | 0  ✓
0 1 | 1  | 1    | 1      | 1  ✓
1 0 | 0  | 0    | 1      | 1  ✓
1 1 | 0  | 0    | 1      | 1  ✓
```
Both columns match! **PROVEN**
</details>

### Problem 4.4: Find Complement
Find F' if F = A·B + C'·D

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
F' = (A·B + C'·D)'

Apply DeMorgan's:
= (A·B)' · (C'·D)'

Apply DeMorgan's to each term:
= (A' + B') · (C + D')

**ANSWER**: F' = (A' + B')·(C + D')
</details>

---

## SECTION 5: Combinational Circuits

### Problem 5.1: Full Adder
What are the outputs of a full adder when A=1, B=1, Cin=0?

**YOUR ANSWER**: Sum = ___, Cout = ___

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Sum = A ⊕ B ⊕ Cin = 1 ⊕ 1 ⊕ 0 = 0 ⊕ 0 = 0
Cout = A·B + A·Cin + B·Cin = 1·1 + 1·0 + 1·0 = 1 + 0 + 0 = 1

**ANSWER**: Sum = 0, Cout = 1

**MEANING**: 1 + 1 + 0 = 10 in binary (2 in decimal)
</details>

### Problem 5.2: BCD Addition
Add 9 + 8 in BCD

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
```
  1001 (9)
+ 1000 (8)
------
1 0001 (carry generated!)
```

Carry = 1, so add correction:
```
  0001
+ 0110 (add 6)
------
  0111
```

**ANSWER**: Carry = 1, Result = 0111
**MEANING**: 17 in BCD = 0001 0111
</details>

### Problem 5.3: Decoder
A 3-to-8 decoder has inputs A=1, B=0, C=1. Which output is active?

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Input = 101₂ = 5₁₀

**ANSWER**: Output D₅ is active (all others are 0)
</details>

### Problem 5.4: Multiplexer Function
Implement F(A,B,C) = Σ(1,2,6,7) using an 8-to-1 MUX

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Connect A,B,C to select lines S₂,S₁,S₀

Data inputs:
- I₀ = 0 (F=0 when ABC=000)
- I₁ = 1 (F=1 when ABC=001) ✓
- I₂ = 1 (F=1 when ABC=010) ✓
- I₃ = 0 (F=0 when ABC=011)
- I₄ = 0 (F=0 when ABC=100)
- I₅ = 0 (F=0 when ABC=101)
- I₆ = 1 (F=1 when ABC=110) ✓
- I₇ = 1 (F=1 when ABC=111) ✓

**ANSWER**: 
- Connect A→S₂, B→S₁, C→S₀
- I₁=I₂=I₆=I₇=1, all others=0
</details>

---

## SECTION 6: XOR and Special Functions

### Problem 6.1: XOR Properties
Simplify: A ⊕ A ⊕ B

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
A ⊕ A ⊕ B
= 0 ⊕ B      [A ⊕ A = 0]
= B          [0 ⊕ B = B]

**ANSWER**: B
</details>

### Problem 6.2: Parity Generator
Design a 3-bit even parity generator for inputs A, B, C

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Even parity bit P makes total number of 1s even.

P = A ⊕ B ⊕ C

**ANSWER**: P = A ⊕ B ⊕ C

**EXAMPLE**: 
- Input: 101 (two 1s - even) → P = 0
- Input: 111 (three 1s - odd) → P = 1
</details>

---

## SECTION 7: Gray Code

### Problem 7.1: Binary to Gray
Convert 1011₂ to Gray code

**YOUR ANSWER**: _______________

<details>
<summary>Click for Solution</summary>

**SOLUTION**:
Copy MSB, then XOR each bit with previous:
```
Binary: 1 0 1 1
        ↓
Gray:   1 (copy MSB)
        1 XOR 0 = 1
        0 XOR 1 = 1
        1 XOR 1 = 0
```

**ANSWER**: 1110
</details>

---

## 🎯 SCORING GUIDE

**Count your correct answers:**

- **18-20 correct**: You're ready for 100%! 🔥
- **15-17 correct**: You'll get 85-95%. Review mistakes!
- **12-14 correct**: You'll get 75-85%. Study weak areas!
- **9-11 correct**: You'll get 65-75%. Need more practice!
- **Below 9**: Study more tonight! Focus on basics!

---

## 📝 WHAT TO DO NEXT

1. **If you got <15 correct**: Do these problems again tomorrow morning
2. **If you got 15-17 correct**: Review the ones you missed
3. **If you got 18+ correct**: You're ready! Just review formulas

**REMEMBER**: Speed matters! Practice until you can do each problem in 2-3 minutes!

Good luck! 🚀
