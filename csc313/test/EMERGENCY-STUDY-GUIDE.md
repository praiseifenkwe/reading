# EMERGENCY STUDY GUIDE - Complete Last Minute Prep
## ALL 4 CHAPTERS - Condensed & Prioritized

---

## 🚨 CRITICAL PATH - DO THESE IN ORDER

**Total Time Needed**: 3-4 hours for everything | 2 hours for essentials only

---

## 📍 PRIORITY 1: CHAPTER 1 ESSENTIALS (30 minutes)

### Number Conversions (10 min) ⭐ EASY POINTS!

#### Decimal to Binary
**Method**: Divide by 2, write remainders bottom-to-top

**Example**: 13₁₀ to binary
```
13 ÷ 2 = 6 remainder 1 (LSB)
 6 ÷ 2 = 3 remainder 0
 3 ÷ 2 = 1 remainder 1
 1 ÷ 2 = 0 remainder 1 (MSB)
Read UP: 1101₂
```

#### Binary to Decimal
**Method**: Multiply each bit by power of 2, sum them

**Example**: 1101₂ to decimal
```
Position: 8s 4s 2s 1s
Binary:    1  1  0  1
Value:    8 +4 +0 +1 = 13₁₀
```

#### Hexadecimal Conversions
**Binary to Hex**: Group 4 bits, convert each group
```
10111010₂
1011 1010
  B    A  = BA₁₆
```

**Hex to Binary**: Each hex digit = 4 bits
```
3F₁₆
3 = 0011
F = 1111
Result: 00111111₂
```

**MEMORIZE**: A=10, B=11, C=12, D=13, E=14, F=15

### 2's Complement (10 min) ⭐⭐⭐ VERY IMPORTANT!

**Method**: Flip all bits, add 1

**Example**: 2's complement of 1011
```
Original:       1011
Flip bits:      0100
Add 1:        + 0001
              ------
Result:         0101
```

**QUICK TRICK**: Copy from right until first 1 (including it), then flip the rest
```
1011 → 0101
   ↑ first 1, copy it and everything right
   flip everything left
```

**Signed Numbers**:
- First bit = sign (0=positive, 1=negative)
- Range for n bits: -2^(n-1) to 2^(n-1)-1
- 4-bit: -8 to +7
- 8-bit: -128 to +127

### Binary Codes (10 min)

#### BCD (Binary Coded Decimal) ⭐ IMPORTANT!
**Rule**: Each decimal digit = 4 bits

**Example**: 395 in BCD
```
Decimal:  3      9      5
BCD:     0011   1001   0101
```

**NOT the same as binary!**
- 395₁₀ in binary: 110001011
- 395₁₀ in BCD: 0011 1001 0101

#### Gray Code ⭐ IMPORTANT FOR K-MAPS!
**Rule**: Only ONE bit changes between consecutive numbers

**Pattern**: 00, 01, 11, 10 (MEMORIZE THIS!)

```
Decimal | Binary | Gray
--------|--------|------
   0    |  00    |  00
   1    |  01    |  01
   2    |  10    |  11  ← Only 1 bit changed
   3    |  11    |  10  ← Only 1 bit changed
```

**Why It Matters**: K-maps use Gray code ordering!

### Basic Logic Operations (5 min)

**AND (·)**: Output 1 only if ALL inputs are 1
```
A B | A·B
----|----
0 0 | 0
0 1 | 0
1 0 | 0
1 1 | 1  ← Only this one!
```

**OR (+)**: Output 1 if ANY input is 1
```
A B | A+B
----|----
0 0 | 0  ← Only this one is 0
0 1 | 1
1 0 | 1
1 1 | 1
```

**NOT (')**: Flip the bit
```
A | A'
--|---
0 | 1
1 | 0
```

**XOR (⊕)**: Output 1 if inputs are DIFFERENT
```
A B | A⊕B
----|----
0 0 | 0
0 1 | 1  ← Different
1 0 | 1  ← Different
1 1 | 0
```

---

## 📍 PRIORITY 2: CHAPTER 2 ESSENTIALS (40 minutes)

### Boolean Theorems (10 min) ⭐ MEMORIZE KEY ONES!

**Identity Laws**:
- A + 0 = A
- A · 1 = A

**Null Laws**:
- A + 1 = 1
- A · 0 = 0

**Idempotent Laws**:
- A + A = A
- A · A = A

**Complement Laws**:
- A + A' = 1
- A · A' = 0
- (A')' = A (double negative)

**Commutative**:
- A + B = B + A
- A · B = B · A

**Associative**:
- A + (B + C) = (A + B) + C
- A · (B · C) = (A · B) · C

**Distributive**:
- A · (B + C) = A·B + A·C
- A + (B · C) = (A + B) · (A + C)

### DeMorgan's Theorems (10 min) ⭐⭐⭐ SUPER IMPORTANT!

**THE MOST TESTED THEOREM!**

**(A + B)' = A' · B'**
**(A · B)' = A' + B'**

**MEMORY TRICK**: "Break the bar, change the operation, add bars"

**Example 1**: (A + B)'
1. Break the bar: A + B
2. Change + to ·: A · B
3. Add bars: A' · B' ✓

**Example 2**: (A · B · C)'
1. Break the bar: A · B · C
2. Change · to +: A + B + C
3. Add bars: A' + B' + C' ✓

**Example 3**: (A' + B)'
1. Break the bar: A' + B
2. Change + to ·: A' · B
3. Add bars: A'' · B' = A · B' ✓

**Practice**: Simplify (A·B + C)'
```
(A·B + C)'
= (A·B)' · C'     [DeMorgan's]
= (A' + B') · C'  [DeMorgan's again]
```

### Minterms and Maxterms (10 min) ⭐⭐ IMPORTANT!

#### Minterm: "Where F = 1"
**Product term (AND) with ALL variables**

**3-Variable Minterms**:
```
Row | A B C | Minterm | Name
----|-------|---------|-----
 0  | 0 0 0 | A'·B'·C'| m₀
 1  | 0 0 1 | A'·B'·C | m₁
 2  | 0 1 0 | A'·B·C' | m₂
 3  | 0 1 1 | A'·B·C  | m₃
 4  | 1 0 0 | A·B'·C' | m₄
 5  | 1 0 1 | A·B'·C  | m₅
 6  | 1 1 0 | A·B·C'  | m₆
 7  | 1 1 1 | A·B·C   | m₇
```

**PATTERN**: 
- If variable = 0 → use complement (A')
- If variable = 1 → use normal (A)

#### Maxterm: "Where F = 0"
**Sum term (OR) with ALL variables**

**Relationship**: mᵢ = Mᵢ' (complement of each other)

### Canonical Forms (10 min) ⭐⭐ IMPORTANT!

#### Sum of Minterms (SOP)
**Rule**: OR together all minterms where F = 1

**Example**: F(A,B,C) with F=1 at rows 1,3,5,7
```
F = m₁ + m₃ + m₅ + m₇
F = A'·B'·C + A'·B·C + A·B'·C + A·B·C
F = Σ(1,3,5,7)  ← Shorthand notation
```

**THE TRICK**: Just list the row numbers where output = 1!

#### Product of Maxterms (POS)
**Rule**: AND together all maxterms where F = 0

**Example**: Same function, F=0 at rows 0,2,4,6
```
F = M₀ · M₂ · M₄ · M₆
F = Π(0,2,4,6)  ← Shorthand notation
```

**MIND-BLOWING**: Σ(1,3,5,7) = Π(0,2,4,6) are the SAME function!

### XOR Properties (5 min) ⭐ USEFUL!

**Key Properties**:
- A ⊕ 0 = A
- A ⊕ 1 = A'
- A ⊕ A = 0
- A ⊕ A' = 1
- A ⊕ B = A'·B + A·B' (SOP form)

**Parity**: XOR all bits
- Even parity: Even number of 1s
- Odd parity: Odd number of 1s

---

## 📍 PRIORITY 3: K-MAPS (60 minutes) - CANNOT SKIP!

### Why This Matters:
K-maps WILL be on the test. This is the #1 gap you need to fill!

### What to Learn:

#### 1. K-Map Basics (15 min)
**THE GOLDEN RULE**: Gray code order is **00, 01, 11, 10** (NOT 00, 01, 10, 11!)

**3-Variable K-Map Layout:**
```
      BC
     00 01 11 10  ← MEMORIZE THIS ORDER!
A 0 │  │  │  │  │
  1 │  │  │  │  │
```

**4-Variable K-Map Layout:**
```
       CD
      00 01 11 10  ← Gray code on columns
AB 00│  │  │  │  │
   01│  │  │  │  │
   11│  │  │  │  │
   10│  │  │  │  │
    ↑
Gray code on rows too!
```

#### 2. Grouping Rules (10 min) ⭐ MEMORIZE!
1. **Group sizes**: ONLY 1, 2, 4, 8, 16 (powers of 2!)
2. **Shapes**: ONLY rectangles (no L-shapes, no diagonals!)
3. **Wraparound**: Edges connect! Top-bottom, left-right wrap around
4. **Corners**: In 4-variable maps, all 4 corners are adjacent!
5. **Goal**: Make groups as LARGE as possible, use MINIMUM number of groups

#### 3. Reading Groups (5 min)
**THE TRICK**: 
- Variables that DON'T change in group → KEEP them
- Variables that DO change → ELIMINATE them
- If variable is always 0 → use A'
- If variable is always 1 → use A

**Example:**
```
Group covers: A=1 throughout, B changes (0 and 1), C=0 throughout
Result: A·C' (keep A and C', eliminate B)
```

#### 4. PRACTICE K-MAPS (30 min) ⚠️ MUST DO!

**Practice Problem 1 (3-variable):**
F(A,B,C) = Σ(0,2,4,6)
```
      BC
     00 01 11 10
A 0 │1 │0 │0 │1 │
  1 │1 │0 │0 │1 │
```
Group all 4 ones vertically → F = C'

**Practice Problem 2 (3-variable):**
F(A,B,C) = Σ(1,3,5,7)
```
      BC
     00 01 11 10
A 0 │0 │1 │1 │0 │
  1 │0 │1 │1 │0 │
```
Group all 4 ones → F = C

**Practice Problem 3 (4-variable):**
F(A,B,C,D) = Σ(0,2,8,10)
```
       CD
      00 01 11 10
AB 00│1 │0 │0 │1 │
   01│0 │0 │0 │0 │
   11│0 │0 │0 │0 │
   10│1 │0 │0 │1 │
```
Group the 4 corners! → F = B'·D'

**Practice Problem 4 (4-variable):**
F(A,B,C,D) = Σ(0,1,2,5,8,9,10)
```
       CD
      00 01 11 10
AB 00│1 │1 │0 │1 │
   01│0 │1 │0 │0 │
   11│0 │0 │0 │0 │
   10│1 │1 │0 │1 │
```
Groups: 
- m₀,m₁,m₈,m₉ (left column) → C'·D'
- m₀,m₂,m₈,m₁₀ (corners + middle) → B'·D'
- m₁,m₅ → A'·C'·D
F = C'·D' + B'·D' (simplified)

**Practice Problem 5 (with don't-cares):**
F(A,B,C,D) = Σ(1,3,7,11,15), d(0,2,5)
```
       CD
      00 01 11 10
AB 00│X │1 │1 │X │
   01│X │0 │1 │0 │
   11│0 │0 │1 │0 │
   10│0 │0 │0 │0 │
```
Use X's to make bigger groups!
Group: m₁,m₃,m₅,m₇ (include X at m₅) → B·C
Group: m₃,m₇,m₁₁,m₁₅ → C·D
F = B·C + C·D (can simplify to C·(B+D))

**DO MORE PRACTICE**: Look at COMPLETE-TEST-BREAKDOWN.md questions 39-59 for K-map problems!

#### 5. Don't-Care Conditions (5 min)
**THE RULE**: X's can be 0 or 1 - use them to make BIGGER groups!
- Include X in group if it helps → treat as 1
- Ignore X if it doesn't help → treat as 0
- DON'T create groups ONLY for X's

---

## 📍 PRIORITY 4: ADDERS (20 minutes)

### Half Adder (5 min) ⭐ MEMORIZE!
**Adds two 1-bit numbers**

**Equations:**
- **S = A ⊕ B** (Sum is XOR)
- **C = A · B** (Carry is AND)

**Truth Table:**
```
A B | S C
----|----
0 0 | 0 0
0 1 | 1 0
1 0 | 1 0
1 1 | 0 1  ← 1+1=10 in binary
```

**MEMORY TRICK**: 
- Sum = XOR (different inputs give 1)
- Carry = AND (both must be 1)

### Full Adder (15 min) ⭐⭐⭐ SUPER IMPORTANT!
**Adds three bits: A + B + Cin**

**Equations:** (MEMORIZE THESE!)
- **S = A ⊕ B ⊕ Cin** (XOR all three)
- **Cout = A·B + A·Cin + B·Cin** (carry when ANY two are 1)
- **Alternative**: Cout = A·B + (A⊕B)·Cin

**Truth Table:**
```
A B Cin | S Cout
--------|-------
0 0  0  | 0  0
0 0  1  | 1  0
0 1  0  | 1  0
0 1  1  | 0  1
1 0  0  | 1  0
1 0  1  | 0  1
1 1  0  | 0  1
1 1  1  | 1  1
```

**MEMORY TRICK**: 
- Sum = XOR everything
- Carry = at least TWO inputs are 1

**Why This Matters**: Full adders are used in EVERY multi-bit addition!

**Ripple Carry Adder**: Chain full adders together
```
A₃B₃  A₂B₂  A₁B₁  A₀B₀
 │ │   │ │   │ │   │ │
 FA ── FA ── FA ── FA
 │     │     │     │
C₄    S₃    S₂    S₁   S₀
```

---

## 📍 PRIORITY 5: DECODERS (15 minutes)

### What is a Decoder? (5 min)
**Converts n-bit input to 2ⁿ outputs (only ONE output active at a time)**

**Pattern**: n inputs → 2ⁿ outputs
- 2 inputs → 4 outputs
- 3 inputs → 8 outputs
- 4 inputs → 16 outputs

**ANALOGY**: Like a vending machine - you press button 3, only slot 3 opens!

### 2-to-4 Decoder (5 min)
**Inputs**: A₁, A₀
**Outputs**: D₀, D₁, D₂, D₃

**Truth Table:**
```
A₁ A₀ | D₀ D₁ D₂ D₃
------|-------------
0  0  | 1  0  0  0  ← Only D₀ active
0  1  | 0  1  0  0  ← Only D₁ active
1  0  | 0  0  1  0  ← Only D₂ active
1  1  | 0  0  0  1  ← Only D₃ active
```

**Equations** (each output is a minterm!):
- D₀ = A₁'·A₀' (minterm m₀)
- D₁ = A₁'·A₀  (minterm m₁)
- D₂ = A₁·A₀'  (minterm m₂)
- D₃ = A₁·A₀   (minterm m₃)

### 3-to-8 Decoder (5 min)
**Inputs**: A₂, A₁, A₀
**Outputs**: D₀ through D₇

Each output represents a minterm!

### Using Decoders for Boolean Functions (5 min) ⭐ TEST FAVORITE!
**THE TRICK**: Decoder generates ALL minterms, just OR the ones you need!

**Example**: F(A,B,C) = Σ(1,3,5,7)
1. Use 3-to-8 decoder (generates m₀ through m₇)
2. OR together D₁, D₃, D₅, D₇
3. F = D₁ + D₃ + D₅ + D₇

**Why This Works**: Decoder outputs ARE the minterms!

---

## 📍 PRIORITY 6: MULTIPLEXERS (25 minutes)

### What is a Multiplexer? (5 min)
**Selects ONE of many inputs and routes it to output**

**Pattern**: 2ⁿ data inputs + n select lines → 1 output
- 4 inputs need 2 select lines
- 8 inputs need 3 select lines

**ANALOGY**: Like a TV channel selector - pick one channel to display!

### 4-to-1 Multiplexer (5 min)
**Inputs**: I₀, I₁, I₂, I₃ (data), S₁, S₀ (select)
**Output**: Y

**Truth Table:**
```
S₁ S₀ | Y
------|----
0  0  | I₀  ← Select input 0
0  1  | I₁  ← Select input 1
1  0  | I₂  ← Select input 2
1  1  | I₃  ← Select input 3
```

**Equation:**
Y = S₁'·S₀'·I₀ + S₁'·S₀·I₁ + S₁·S₀'·I₂ + S₁·S₀·I₃

### Using MUX for Boolean Functions (15 min) ⭐⭐⭐ VERY IMPORTANT!

#### Method 1: Direct Implementation (Easy!)
**Use 2ⁿ-to-1 MUX for n-variable function**

**SIMPLE STEPS**:
1. Connect variables to select lines
2. Connect function values (0 or 1) to data inputs
3. Done! It's like copying the truth table!

**Example**: F(A,B,C) = Σ(1,3,5,7) using 8-to-1 MUX
```
Connect A,B,C to S₂,S₁,S₀
I₀ = 0 (F=0 when ABC=000)
I₁ = 1 (F=1 when ABC=001)
I₂ = 0 (F=0 when ABC=010)
I₃ = 1 (F=1 when ABC=011)
I₄ = 0 (F=0 when ABC=100)
I₅ = 1 (F=1 when ABC=101)
I₆ = 0 (F=0 when ABC=110)
I₇ = 1 (F=1 when ABC=111)
```

#### Method 2: Reduced Implementation (Tricky but Common!)
**Use 2ⁿ⁻¹-to-1 MUX for n-variable function**

**STEPS**:
1. Connect n-1 variables to select lines
2. Last variable becomes part of data inputs
3. Each input can be: 0, 1, variable, or variable'

**Example**: F(A,B,C) = Σ(1,2,6,7) using 4-to-1 MUX
```
Connect A,B to S₁,S₀ (use 2 variables for select)
C is the remaining variable

Analyze for each AB combination:
AB=00: F=1 when C=1, F=0 when C=0 → I₀ = C
AB=01: F=1 when C=0, F=0 when C=1 → I₁ = C'
AB=10: F=1 when C=0, F=0 when C=1 → I₂ = C'
AB=11: F=1 always (both C=0 and C=1) → I₃ = 1
```

**How to Determine Data Inputs**:
- F=0 for both values of last var → Input = 0
- F=1 for both values → Input = 1
- F follows variable → Input = variable
- F opposite of variable → Input = variable'

---

## 📍 PRIORITY 7: ENCODERS (10 minutes)

### What is an Encoder? (3 min)
**Opposite of decoder: 2ⁿ inputs → n-bit output**

**Example**: 8-to-3 Encoder
- 8 inputs (D₀-D₇)
- 3 outputs (A₂, A₁, A₀)
- Encodes which input is active

### Priority Encoder (7 min) ⭐ IMPORTANT!
**Handles multiple active inputs - highest priority wins!**

**4-to-2 Priority Encoder:**
```
D₃ D₂ D₁ D₀ | A₁ A₀ V
------------|----------
0  0  0  0  | X  X  0  (no input)
0  0  0  1  | 0  0  1  (D₀ active)
0  0  1  X  | 0  1  1  (D₁ has priority)
0  1  X  X  | 1  0  1  (D₂ has priority)
1  X  X  X  | 1  1  1  (D₃ highest priority)
```

**V = Valid output** (0 if no input active)

**THE RULE**: Highest-numbered input has highest priority!

---

## 📍 PRIORITY 8: COMPARATOR (10 minutes)

### What is a Comparator? (3 min)
**Compares two numbers: outputs A>B, A=B, A<B**

### 1-Bit Comparator (3 min)
```
A B | A>B  A=B  A<B
----|---------------
0 0 |  0    1    0
0 1 |  0    0    1
1 0 |  1    0    0
1 1 |  0    1    0
```

**Equations:**
- A>B = A·B'
- A=B = (A⊕B)' (XNOR)
- A<B = A'·B

### 2-Bit Comparator (4 min)
**Logic**: Compare MSBs first, if equal then compare LSBs

**Equations:**
- A>B = A₁·B₁' + (A₁⊙B₁)·A₀·B₀'
- A=B = (A₁⊙B₁)·(A₀⊙B₀)
- A<B = A₁'·B₁ + (A₁⊙B₁)·A₀'·B₀

Where ⊙ is XNOR (equality check)

---

## 🎯 QUICK REFERENCE - MEMORIZE THESE!

### Must-Know Formulas:
1. **2's Complement**: Flip all bits, add 1
2. **DeMorgan's**: (A+B)' = A'·B', (A·B)' = A'+B'
3. **Half Adder**: S = A⊕B, C = A·B
4. **Full Adder**: S = A⊕B⊕Cin, Cout = A·B + A·Cin + B·Cin
5. **K-map Order**: 00, 01, 11, 10 (Gray code!)
6. **Decoder**: n → 2ⁿ (one output active)
7. **MUX**: 2ⁿ → 1 (select one input)
8. **Encoder**: 2ⁿ → n (encode position)

### Must-Know Patterns:
1. **XOR**: A⊕B = A'·B + A·B' (different inputs)
2. **XNOR**: A⊙B = A·B + A'·B' (same inputs)
3. **Minterm**: Product term where F=1
4. **Maxterm**: Sum term where F=0
5. **SOP**: OR of AND terms
6. **POS**: AND of OR terms

---

## 📚 IF YOU HAVE EXTRA TIME - READ THESE NEXT:

### Extra Topic 1: BCD Adder (15 min)
**Location**: Chapter 4, Section 4.6

**The Rule**: When adding BCD digits:
- If sum ≤ 9 and no carry → Valid BCD
- If sum > 9 or carry → Add 6 (0110) to correct

**Example**: 8 + 5 = 13
```
  1000  (8)
+ 0101  (5)
------
  1101  (13 - invalid BCD!)
+ 0110  (add 6)
------
1 0011  (carry=1, digit=3 → represents 13)
```

### Extra Topic 2: Binary Multiplier (15 min)
**Location**: Chapter 4, Section 4.7

**2×2 Multiplier**:
```
      A₁ A₀
    × B₁ B₀
    -------
    A₁B₀ A₀B₀  (partial product)
  A₁B₁ A₀B₁    (partial product)
  -----------
  C₃ C₂ C₁ C₀
```

**Implementation**: AND gates + Half/Full adders

### Extra Topic 3: NAND/NOR Implementation (20 min)
**Location**: Chapter 3, Section 3.6

**NAND-NAND**: Implements SOP directly
**NOR-NOR**: Implements POS directly

**Why**: NAND and NOR are universal gates (can implement any function)

### Extra Topic 4: XOR Functions (10 min)
**Location**: Chapter 3, Section 3.8

**Properties**:
- A ⊕ 0 = A
- A ⊕ 1 = A'
- A ⊕ A = 0
- A ⊕ A' = 1

**Parity**: XOR all bits
- Even parity: Add bit to make even number of 1s
- Odd parity: Add bit to make odd number of 1s

---

## 🎓 FINAL CHECKLIST - Before the Test

### Can You Do These?
- [ ] Convert decimal to binary and back
- [ ] Calculate 2's complement
- [ ] Apply DeMorgan's theorem
- [ ] Simplify Boolean expressions
- [ ] Draw and solve 3-variable K-map
- [ ] Draw and solve 4-variable K-map
- [ ] Use don't-cares in K-map
- [ ] Write half adder equations
- [ ] Write full adder equations
- [ ] Understand decoder operation
- [ ] Understand MUX operation
- [ ] Implement function with decoder
- [ ] Implement function with MUX
- [ ] Understand priority encoder

### Quick Self-Test:
1. What's 2's complement of 1011? (Answer: 0101)
2. What's (A+B)'? (Answer: A'·B')
3. K-map column order? (Answer: 00, 01, 11, 10)
4. Half adder sum? (Answer: A⊕B)
5. Full adder carry? (Answer: A·B + A·Cin + B·Cin)
6. 3-to-8 decoder outputs? (Answer: 8 outputs, one active)
7. 4-to-1 MUX select lines? (Answer: 2 select lines)

---

## ⏰ TIME MANAGEMENT

### Full Coverage: 3-4 Hours
1. **Chapter 1 Essentials** (30 min)
2. **Chapter 2 Essentials** (40 min)
3. **K-Maps** (60 min) - MUST DO!
4. **Adders** (20 min)
5. **Decoders** (15 min)
6. **Multiplexers** (25 min)
7. **Encoders** (10 min)
8. **Comparators** (10 min)
9. **Review COMPLETE-TEST-BREAKDOWN.md** (20 min)

### If You Already Know Chapters 1 & 2: 2-2.5 Hours
Skip Priorities 1-2, start with Priority 3 (K-Maps)

### If You Have Limited Time:
- **2 hours**: Priorities 1, 2, 3, 4, 6 (skip encoders/comparators)
- **1 hour**: Priorities 1 (15 min), 2 (20 min), 3 (25 min)
- **30 min**: Priority 3 K-Maps only (20 min) + quick-reference.md (10 min)

---

## 🚀 YOU'VE GOT THIS!

**Your Complete Study Path**:
- Priorities 1-2: Foundation (Chapters 1 & 2) - 70 min
- Priority 3: K-Maps (Chapter 3) - 60 min  
- Priorities 4-8: Circuits (Chapter 4) - 80 min
- Total: 3-4 hours for complete coverage

**If You Already Know Chapters 1 & 2**:
- Skip to Priority 3 (K-Maps)
- Total time: 2-2.5 hours

**Remember**:
- K-maps are mechanical - just follow the rules!
- Adders are just XOR and AND
- Decoders and MUX are pattern recognition
- Practice makes perfect!

**Good luck! 🎯**
