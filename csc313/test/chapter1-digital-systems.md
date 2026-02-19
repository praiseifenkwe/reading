# Chapter 1: Digital Systems and Binary Numbers

## 1.1 Digital Systems

### What is a Digital System?
A digital system manipulates discrete elements of information represented in binary form (0s and 1s). Unlike analog systems that work with continuous values, digital systems work with distinct, separate values.

### Key Characteristics:
- **Discrete values**: Only specific values are valid (typically 0 and 1)
- **Reliability**: Less susceptible to noise and interference
- **Programmability**: Can be easily modified through software
- **Storage**: Information can be stored without degradation

### Components of Digital Systems:
1. **Hardware**: Physical components (gates, circuits, processors)
2. **Software**: Programs that control the hardware
3. **Input/Output devices**: Interface with the external world

---

## 1.2 Binary Numbers

### Why Binary?
- Electronic circuits have two stable states (ON/OFF, HIGH/LOW)
- Easy to implement with transistors
- Reliable and noise-resistant

### Binary Number System:
- **Base**: 2
- **Digits**: 0 and 1 (called bits)
- **Position values**: Powers of 2 (1, 2, 4, 8, 16, 32, ...)

### Example:
Binary: 1011₂
= (1 × 2³) + (0 × 2²) + (1 × 2¹) + (1 × 2⁰)
= 8 + 0 + 2 + 1
= 11₁₀

### Important Terms:
- **Bit**: Binary digit (0 or 1)
- **Byte**: 8 bits
- **Nibble**: 4 bits
- **Word**: System-dependent (typically 16, 32, or 64 bits)

---

## 1.3 Number-Base Conversions

### Decimal to Binary Conversion:
**Method 1: Repeated Division by 2**
- Divide the number by 2
- Record the remainder (0 or 1)
- Continue dividing the quotient until it becomes 0
- Read remainders from bottom to top

**Example: Convert 13₁₀ to binary**
```
13 ÷ 2 = 6 remainder 1 (LSB)
6 ÷ 2 = 3 remainder 0
3 ÷ 2 = 1 remainder 1
1 ÷ 2 = 0 remainder 1 (MSB)
```
Result: 1101₂

### Binary to Decimal Conversion:
Multiply each bit by its position value (power of 2) and sum.

**Example: 1101₂ to decimal**
= (1 × 2³) + (1 × 2²) + (0 × 2¹) + (1 × 2⁰)
= 8 + 4 + 0 + 1 = 13₁₀

### Decimal Fraction to Binary:
**Method: Repeated Multiplication by 2**
- Multiply fraction by 2
- Record the integer part (0 or 1)
- Keep the fractional part and repeat
- Stop when fraction becomes 0 or desired precision reached

**Example: Convert 0.625₁₀ to binary**
```
0.625 × 2 = 1.25 → 1 (MSB)
0.25 × 2 = 0.5 → 0
0.5 × 2 = 1.0 → 1 (LSB)
```
Result: 0.101₂

---

## 1.4 Octal and Hexadecimal Numbers

### Octal Number System:
- **Base**: 8
- **Digits**: 0, 1, 2, 3, 4, 5, 6, 7
- **Use**: Shorthand for binary (3 bits = 1 octal digit)

### Binary to Octal Conversion:
Group binary digits in sets of 3 (from right to left)

**Example: 101110₂ to octal**
```
101 110
 5   6
```
Result: 56₈

### Hexadecimal Number System:
- **Base**: 16
- **Digits**: 0-9, A-F (A=10, B=11, C=12, D=13, E=14, F=15)
- **Use**: Shorthand for binary (4 bits = 1 hex digit)

### Binary to Hexadecimal Conversion:
Group binary digits in sets of 4 (from right to left)

**Example: 10111010₂ to hex**
```
1011 1010
 B    A
```
Result: BA₁₆

### Quick Reference Table:
| Decimal | Binary | Octal | Hex |
|---------|--------|-------|-----|
| 0       | 0000   | 0     | 0   |
| 1       | 0001   | 1     | 1   |
| 2       | 0010   | 2     | 2   |
| 3       | 0011   | 3     | 3   |
| 4       | 0100   | 4     | 4   |
| 5       | 0101   | 5     | 5   |
| 6       | 0110   | 6     | 6   |
| 7       | 0111   | 7     | 7   |
| 8       | 1000   | 10    | 8   |
| 9       | 1001   | 11    | 9   |
| 10      | 1010   | 12    | A   |
| 11      | 1011   | 13    | B   |
| 12      | 1100   | 14    | C   |
| 13      | 1101   | 15    | D   |
| 14      | 1110   | 16    | E   |
| 15      | 1111   | 17    | F   |

---

## 1.5 Complements of Numbers

### Why Complements?
Complements simplify subtraction operations in digital systems. Instead of subtracting, we can add the complement.

### Types of Complements:

#### 1. Diminished Radix Complement (r-1's complement)
For base r, subtract each digit from (r-1)

**1's Complement (Binary):**
- Flip all bits (0→1, 1→0)
- Example: 1011 → 0100

**9's Complement (Decimal):**
- Subtract each digit from 9
- Example: 546 → 453

#### 2. Radix Complement (r's complement)
Add 1 to the diminished radix complement

**2's Complement (Binary):**
- Method 1: Flip all bits and add 1
- Method 2: Copy bits from right until first 1, then flip remaining bits

**Example: 2's complement of 1011**
```
1's complement: 0100
Add 1:        + 0001
              ------
2's complement: 0101
```

**10's Complement (Decimal):**
- 9's complement + 1
- Example: 546 → 453 + 1 = 454

### Subtraction Using Complements:

**Binary Subtraction (A - B):**
1. Find 2's complement of B
2. Add it to A
3. If carry out exists, result is positive (discard carry)
4. If no carry out, result is negative (take 2's complement of result)

**Example: 1010 - 0011**
```
1010 (10)
+ 1101 (2's complement of 0011)
------
10111
Discard carry → 0111 (7)
```

---

## 1.6 Signed Binary Numbers

### Representation Methods:

#### 1. Sign-Magnitude Representation:
- MSB (leftmost bit) represents sign: 0 = positive, 1 = negative
- Remaining bits represent magnitude
- **Problem**: Two representations of zero (+0 and -0)

**Example (4-bit):**
- +5 = 0101
- -5 = 1101

#### 2. 1's Complement Representation:
- Positive numbers: Normal binary
- Negative numbers: 1's complement of positive
- **Problem**: Two representations of zero

**Example (4-bit):**
- +5 = 0101
- -5 = 1010

#### 3. 2's Complement Representation (Most Common):
- Positive numbers: Normal binary
- Negative numbers: 2's complement of positive
- **Advantage**: Only one zero, easier arithmetic

**Example (4-bit):**
- +5 = 0101
- -5 = 1011

### Range of Signed Numbers:
For n-bit 2's complement:
- Range: -2^(n-1) to +2^(n-1) - 1
- 8-bit: -128 to +127
- 16-bit: -32,768 to +32,767

### Sign Extension:
To increase bit width while preserving value:
- Copy the sign bit to the left

**Example: Extend 1011 (4-bit) to 8-bit**
- Result: 11111011

### Arithmetic Operations in 2's Complement:

**Addition:**
- Add normally
- Ignore carry out from MSB
- Check for overflow (both operands same sign, result different sign)

**Subtraction:**
- Take 2's complement of subtrahend
- Add to minuend

**Overflow Detection:**
- Occurs when: Carry into MSB ≠ Carry out of MSB
- Or: Two positive numbers give negative result
- Or: Two negative numbers give positive result

---

## 1.7 Binary Codes

### What are Binary Codes?
Binary codes represent discrete elements of information using groups of bits.

### 1. Binary Coded Decimal (BCD):
- Represents each decimal digit with 4 bits
- Uses only 0000 to 1001 (0-9)
- 1010 to 1111 are invalid

**Example: 395 in BCD**
```
3    9    5
0011 1001 0101
```

**BCD vs Binary:**
- 395₁₀ in binary: 110001011 (9 bits)
- 395₁₀ in BCD: 001110010101 (12 bits)
- BCD is easier for decimal I/O but less efficient

### 2. Gray Code:
- Only one bit changes between consecutive numbers
- Used in error reduction and position encoding
- Useful in K-maps (Karnaugh maps)

**Conversion Table:**
| Decimal | Binary | Gray |
|---------|--------|------|
| 0       | 0000   | 0000 |
| 1       | 0001   | 0001 |
| 2       | 0010   | 0011 |
| 3       | 0011   | 0010 |
| 4       | 0100   | 0110 |
| 5       | 0101   | 0111 |
| 6       | 0110   | 0101 |
| 7       | 0111   | 0100 |

**Binary to Gray Conversion:**
- Copy MSB
- XOR each bit with the bit to its left

**Example: 1011 (binary) to Gray**
```
1 (copy MSB)
1 XOR 0 = 1
0 XOR 1 = 1
1 XOR 1 = 0
Result: 1110
```

### 3. ASCII Code (American Standard Code for Information Interchange):
- 7-bit code (128 characters)
- Extended ASCII: 8-bit (256 characters)
- Represents letters, numbers, symbols, control characters

**Examples:**
- 'A' = 1000001 (65₁₀)
- 'a' = 1100001 (97₁₀)
- '0' = 0110000 (48₁₀)
- Space = 0100000 (32₁₀)

### 4. Error Detection Codes:

**Parity Bit:**
- Extra bit added to make total number of 1s even (even parity) or odd (odd parity)
- Detects single-bit errors

**Example with even parity:**
- Data: 1011 (three 1s)
- Parity bit: 1 (to make four 1s - even)
- Transmitted: 10111

### 5. Other Codes:
- **Excess-3 Code**: BCD + 3 (self-complementing)
- **2421 Code**: Weighted BCD code
- **Unicode**: Universal character encoding (16 or 32 bits)

---

## 1.8 Binary Storage and Registers

### Storage Elements:

#### 1. Flip-Flops:
- Basic storage element in digital systems
- Stores one bit of information
- Has two stable states (0 or 1)
- Maintains state until changed by input signal

#### 2. Registers:
- Group of flip-flops
- Stores multiple bits (typically 8, 16, 32, or 64 bits)
- Each flip-flop stores one bit

**Types of Registers:**
- **Data Register**: Stores data temporarily
- **Address Register**: Stores memory addresses
- **Instruction Register**: Stores current instruction
- **Program Counter**: Stores address of next instruction

### Register Operations:

**1. Load/Store:**
- Transfer data into or out of register
- Parallel load: All bits loaded simultaneously
- Serial load: Bits loaded one at a time

**2. Shift:**
- Move bits left or right
- Logical shift: Fill with 0s
- Arithmetic shift: Preserve sign bit
- Circular shift (rotate): Bits wrap around

**3. Clear:**
- Set all bits to 0

**4. Increment/Decrement:**
- Add or subtract 1 from register value

### Memory Hierarchy:
1. **Registers**: Fastest, smallest, most expensive
2. **Cache**: Very fast, small
3. **RAM**: Fast, medium size
4. **Hard Drive/SSD**: Slower, large, cheapest per bit

### Register Transfer:
- Notation for describing data movement between registers
- Example: R2 ← R1 (contents of R1 transferred to R2)

---

## 1.9 Binary Logic

### What is Binary Logic?
Binary logic deals with variables that have two discrete values (True/False, 1/0, High/Low) and operations on these variables.

### Basic Logic Operations:

#### 1. AND Operation (·):
- Output is 1 only if ALL inputs are 1
- Symbol: A · B or AB
- Truth Table:
```
A | B | A·B
--|---|----
0 | 0 | 0
0 | 1 | 0
1 | 0 | 0
1 | 1 | 1
```

#### 2. OR Operation (+):
- Output is 1 if ANY input is 1
- Symbol: A + B
- Truth Table:
```
A | B | A+B
--|---|----
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 1
```

#### 3. NOT Operation ('):
- Inverts the input
- Symbol: A' or Ā
- Truth Table:
```
A | A'
--|---
0 | 1
1 | 0
```

### Derived Operations:

#### 4. NAND (NOT-AND):
- Output is 0 only if ALL inputs are 1
- Universal gate (can implement any logic function)
- Symbol: (A·B)'

#### 5. NOR (NOT-OR):
- Output is 1 only if ALL inputs are 0
- Universal gate
- Symbol: (A+B)'

#### 6. XOR (Exclusive-OR):
- Output is 1 if inputs are DIFFERENT
- Symbol: A ⊕ B
- Truth Table:
```
A | B | A⊕B
--|---|----
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0
```

#### 7. XNOR (Exclusive-NOR):
- Output is 1 if inputs are SAME
- Symbol: (A⊕B)' or A⊙B

### Boolean Expressions:
- Algebraic notation for logic functions
- Example: F = A·B + C'
- Can be simplified using Boolean algebra

### Logic Gates:
- Physical implementation of logic operations
- Electronic circuits with one or more inputs and one output
- Building blocks of digital circuits

### Applications:
- Decision making in digital systems
- Arithmetic operations
- Control logic
- Data routing and selection

---

## Chapter 1 Summary - Key Concepts to Remember:

1. **Number Systems**: Binary (base-2), Octal (base-8), Decimal (base-10), Hexadecimal (base-16)

2. **Conversions**: Know how to convert between all number systems

3. **Complements**: 1's complement (flip bits), 2's complement (flip + 1)

4. **Signed Numbers**: 2's complement is most common, range is -2^(n-1) to 2^(n-1)-1

5. **Binary Codes**: BCD (4 bits per decimal digit), Gray code (one bit change), ASCII (character encoding)

6. **Storage**: Flip-flops store bits, registers store multiple bits

7. **Logic Operations**: AND (·), OR (+), NOT ('), NAND, NOR, XOR (⊕)

8. **Important Formulas**:
   - 2's complement: Flip all bits and add 1
   - Range (n-bit 2's complement): -2^(n-1) to 2^(n-1) - 1
   - Binary to Decimal: Sum of (bit × 2^position)

---

## Practice Problems:

1. Convert 156₁₀ to binary, octal, and hexadecimal
2. Find 2's complement of 10110110
3. Perform: 01101 - 01010 using 2's complement
4. Convert 1101₂ to Gray code
5. Encode "Hi" in ASCII
6. What is the range of 12-bit 2's complement numbers?
7. Evaluate: (A·B) + (A'·C) when A=1, B=0, C=1
