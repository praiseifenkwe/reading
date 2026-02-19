# Chapter 1: Digital Systems and Binary Numbers

## 1.1 Digital Systems

### What is a Digital System?
A digital system manipulates discrete elements of information represented in binary form (0s and 1s). Unlike analog systems that work with continuous values, digital systems work with distinct, separate values.

**SIMPLE ANALOGY**: Think of a light switch vs a dimmer.
- **Digital (Light Switch)**: Only ON or OFF - no in-between. This is like 1 or 0.
- **Analog (Dimmer)**: Can be at any brightness level - infinite possibilities.

Your computer is digital - it only understands ON (1) and OFF (0). Everything you see on screen is just millions of 1s and 0s!

**WHY THIS MATTERS FOR YOUR TEST**: Digital systems use binary (0 and 1) because:
- Easy to build with electronics (voltage HIGH = 1, voltage LOW = 0)
- Reliable - no confusion about "is this a 1 or 0?"
- Can represent ANY information (numbers, text, images, videos) using just 1s and 0s

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

**SIMPLE STORY**: Imagine you're in a dark room with 4 light bulbs in a row. Each bulb can only be ON or OFF.
- Bulbs: [ON] [OFF] [ON] [ON]
- Binary: 1 0 1 1

This is how computers "see" numbers! Each position has a value based on powers of 2.

### Binary Number System:
- **Base**: 2 (only uses 0 and 1)
- **Digits**: 0 and 1 (called bits - short for "binary digits")
- **Position values**: Powers of 2 (1, 2, 4, 8, 16, 32, ...)

**THINK OF IT LIKE MONEY**: In decimal, positions are 1s, 10s, 100s. In binary, positions are 1s, 2s, 4s, 8s.

### Example:
Binary: 1011₂ (the ₂ means "base 2")

**Step-by-step like counting money**:
```
Position:    8s  4s  2s  1s
Binary:       1   0   1   1
Value:       8 + 0 + 2 + 1 = 11
```

So 1011₂ = 11₁₀ (eleven in decimal)

**TEST TIP**: Always write position values above the binary number to avoid mistakes!

### Important Terms:
- **Bit**: Binary digit (0 or 1)
- **Byte**: 8 bits
- **Nibble**: 4 bits
- **Word**: System-dependent (typically 16, 32, or 64 bits)

---

## 1.3 Number-Base Conversions

### Decimal to Binary Conversion:
**Method 1: Repeated Division by 2**

**SIMPLE ANALOGY**: Think of sharing cookies with a friend. You keep dividing by 2 and see if there's a leftover (remainder).

**Example: Convert 13₁₀ to binary**
```
13 ÷ 2 = 6 remainder 1 (LSB - Least Significant Bit, rightmost)
 6 ÷ 2 = 3 remainder 0
 3 ÷ 2 = 1 remainder 1
 1 ÷ 2 = 0 remainder 1 (MSB - Most Significant Bit, leftmost)
```
**Read remainders from BOTTOM to TOP**: 1101₂

**MEMORY TRICK**: "Divide by 2, write the remainder, repeat until you hit 0, then read UP!"

**TEST TIP**: This method ALWAYS works. Practice it 5 times and you'll never forget!

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

**REAL-WORLD ANALOGY**: Imagine you owe someone $5. Instead of thinking "I need to subtract $5 from my wallet," you think "I need to add -$5 to my wallet." Complements let computers do subtraction by just adding negative numbers!

**WHY COMPUTERS CARE**: Building a subtraction circuit is hard. Building an addition circuit is easy. So we use complements to turn subtraction into addition! Smart, right?

### Types of Complements:

#### 1. Diminished Radix Complement (r-1's complement)
For base r, subtract each digit from (r-1)

**1's Complement (Binary):**
- Flip all bits (0→1, 1→0)
- Example: 1011 → 0100

**SIMPLE RULE**: Change every 0 to 1, and every 1 to 0. That's it!

**9's Complement (Decimal):**
- Subtract each digit from 9
- Example: 546 → 453 (9-5=4, 9-4=5, 9-6=3)

#### 2. Radix Complement (r's complement)
Add 1 to the diminished radix complement

**2's Complement (Binary):** - THIS IS THE MOST IMPORTANT ONE!
- Method 1: Flip all bits and add 1
- Method 2: Copy bits from right until first 1, then flip remaining bits

**STORY TIME**: Think of 2's complement as "the opposite number."
- If you have 5, the opposite is -5
- In binary, 2's complement gives you the negative version!

**Example: 2's complement of 1011**
```
Original:       1011
1's complement: 0100  (flip all bits)
Add 1:        + 0001
              ------
2's complement: 0101
```

**SUPER EASY TRICK** (Method 2):
```
Original: 1011
          ↓
Step 1: Copy from right until you hit the first 1 (including that 1)
        ...1
Step 2: Flip the rest
        0101
```

**TEST TIP**: Method 1 is safer for tests - just flip and add 1!

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

**THE BIG QUESTION**: How do we show negative numbers in binary? We need a system!

#### 1. Sign-Magnitude Representation:
- MSB (leftmost bit) represents sign: 0 = positive, 1 = negative
- Remaining bits represent magnitude

**SIMPLE ANALOGY**: Like writing a + or - sign before a number.
- First bit is the "sign" (0 = +, 1 = -)
- Rest of the bits are the "number"

**Example (4-bit):**
- +5 = 0101 (0 means positive, 101 is 5)
- -5 = 1101 (1 means negative, 101 is 5)

**PROBLEM**: This gives us two zeros! +0 (0000) and -0 (1000). Confusing for computers!

#### 2. 1's Complement Representation:
- Positive numbers: Normal binary
- Negative numbers: 1's complement of positive
- **Problem**: Two representations of zero

**Example (4-bit):**
- +5 = 0101
- -5 = 1010

#### 3. 2's Complement Representation (Most Common): ⭐ MEMORIZE THIS!
- Positive numbers: Normal binary
- Negative numbers: 2's complement of positive
- **Advantage**: Only one zero, easier arithmetic

**WHY THIS IS THE WINNER**: Every computer uses this! It's the standard.

**Example (4-bit):**
- +5 = 0101 (starts with 0, so positive)
- -5 = 1011 (starts with 1, so negative)

**QUICK CHECK**: If first bit is 0 → positive. If first bit is 1 → negative.

### Range of Signed Numbers:
For n-bit 2's complement:
- Range: -2^(n-1) to +2^(n-1) - 1

**SIMPLE FORMULA EXPLANATION**:
- n-bit means you have n bits total
- First bit is for sign, so you have (n-1) bits for the number
- That's why it's 2^(n-1)

**MEMORIZE THESE FOR TEST**:
- 4-bit: -8 to +7
- 8-bit: -128 to +127
- 16-bit: -32,768 to +32,767

**PATTERN NOTICE**: Negative side has one more number than positive! (-8 to +7, not -7 to +7)

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

### 1. Binary Coded Decimal (BCD): ⭐ IMPORTANT FOR TEST!
- Represents each decimal digit with 4 bits
- Uses only 0000 to 1001 (0-9)
- 1010 to 1111 are invalid

**SIMPLE ANALOGY**: Instead of converting the whole number to binary, convert each digit separately!

**Example: 395 in BCD**
```
Decimal:  3      9      5
BCD:     0011   1001   0101
```

**THE TRICK**: Each decimal digit gets its own 4-bit binary code.
- 3 → 0011
- 9 → 1001
- 5 → 0101

**WHY USE BCD?**: Calculators and digital clocks use BCD because it's easier to display decimal digits!

**BCD vs Binary - THE DIFFERENCE**:
- 395₁₀ in pure binary: 110001011 (9 bits, one number)
- 395₁₀ in BCD: 0011 1001 0101 (12 bits, three separate digits)
- BCD wastes space BUT makes displaying numbers easier

**TEST TIP**: If they say "BCD," treat each decimal digit separately!

### 2. Gray Code: ⭐ YOU'LL SEE THIS IN K-MAPS!
- Only ONE bit changes between consecutive numbers
- Used in error reduction and position encoding
- Useful in K-maps (Karnaugh maps) - Chapter 3!

**WHY GRAY CODE EXISTS**: Imagine a sensor reading position. If multiple bits change at once, you might read wrong values during transition. Gray code prevents this!

**THE MAGIC**: Look at the table - only ONE bit changes each time!

**Conversion Table:**
| Decimal | Binary | Gray | ← Notice!
|---------|--------|------|----------|
| 0       | 0000   | 0000 |
| 1       | 0001   | 0001 | ← 1 bit changed
| 2       | 0010   | 0011 | ← 1 bit changed
| 3       | 0011   | 0010 | ← 1 bit changed
| 4       | 0100   | 0110 | ← 1 bit changed

**REAL-WORLD USE**: Elevator floor sensors, rotary encoders, and K-maps in your test!

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

**SIMPLE EXPLANATION**: Logic is like making decisions with YES/NO questions.
- "Is it raining?" → YES (1) or NO (0)
- "Do I have an umbrella?" → YES (1) or NO (0)
- "Should I go outside?" → Depends on BOTH answers!

This is what computers do - they make decisions using logic!

### Basic Logic Operations:

**THINK OF THESE AS DECISION RULES**:

#### 1. AND Operation (·): "BOTH must be true"
- Output is 1 only if ALL inputs are 1
- Symbol: A · B or AB

**REAL-LIFE ANALOGY**: You can go to the party AND if:
- You finished homework (A=1) AND
- Your parents said yes (B=1)
- BOTH must be true!

**Truth Table:**
```
A | B | A·B | Meaning
--|---|-----|------------------
0 | 0 | 0   | Neither true → NO
0 | 1 | 0   | Only B true → NO
1 | 0 | 0   | Only A true → NO
1 | 1 | 1   | BOTH true → YES!
```

**MEMORY TRICK**: AND is picky - wants EVERYTHING to be 1!

#### 2. OR Operation (+): "AT LEAST ONE must be true"
- Output is 1 if ANY input is 1
- Symbol: A + B

**REAL-LIFE ANALOGY**: You'll be happy if:
- You get ice cream (A=1) OR
- You get cake (B=1)
- Either one (or both!) makes you happy!

**Truth Table:**
```
A | B | A+B | Meaning
--|---|-----|------------------
0 | 0 | 0   | Neither → NO
0 | 1 | 1   | B is true → YES!
1 | 0 | 1   | A is true → YES!
1 | 1 | 1   | Both true → YES!
```

**MEMORY TRICK**: OR is easy to please - just needs ONE thing to be 1!

#### 3. NOT Operation ('): "OPPOSITE"
- Inverts the input (flips it)
- Symbol: A' or Ā

**REAL-LIFE ANALOGY**: "NOT raining" means the opposite of raining!
- If it's raining (1) → NOT raining (0)
- If it's NOT raining (0) → NOT NOT raining = raining (1)

**Truth Table:**
```
A | A' | Meaning
--|----|---------
0 | 1  | Flip 0 to 1
1 | 0  | Flip 1 to 0
```

**MEMORY TRICK**: NOT is the "opposite machine" - flips everything!

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
