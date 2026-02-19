# Chapter 2: Boolean Algebra and Logic Gates

## 2.1 Introduction

Boolean algebra is the mathematical foundation for digital logic design. It provides:
- A systematic way to analyze and design logic circuits
- Methods to simplify complex logic expressions
- Rules for manipulating binary variables

Named after George Boole (1854), who developed algebraic system for logic.

---

## 2.2 Basic Definitions

### Binary Variable:
- Can take only two values: 0 or 1
- Also called: True/False, High/Low, On/Off
- Examples: A, B, C, X, Y, Z

### Boolean Function:
- Relationship between binary variables
- Expressed using logic operations
- Example: F(A,B,C) = A·B + C

### Literal:
- A variable in its normal or complemented form
- Examples: A, A', B, B'

### Product Term:
- Single literal or logical product (AND) of literals
- Examples: A, A·B, A·B'·C

### Sum Term:
- Single literal or logical sum (OR) of literals
- Examples: A, A+B, A+B'+C

---

## 2.3 Axiomatic Definition of Boolean Algebra

### Huntington Postulates:

#### 1. Closure:
- **Closure with respect to AND**: If A and B are in set, then A·B is in set
- **Closure with respect to OR**: If A and B are in set, then A+B is in set

#### 2. Identity Elements:
- **Identity for OR**: A + 0 = A
- **Identity for AND**: A · 1 = A

#### 3. Commutative Laws:
- **OR**: A + B = B + A
- **AND**: A · B = B · A

#### 4. Distributive Laws:
- **AND over OR**: A · (B + C) = (A · B) + (A · C)
- **OR over AND**: A + (B · C) = (A + B) · (A + C)

#### 5. Complement:
- For every element A, there exists A' such that:
  - A + A' = 1
  - A · A' = 0

#### 6. Distinct Elements:
- At least two distinct elements: 0 and 1
- 0 ≠ 1

### Duality Principle:
Every Boolean expression remains valid if:
- AND (·) and OR (+) are interchanged
- 0 and 1 are interchanged

**Example:**
- Original: A + 0 = A
- Dual: A · 1 = A

---

## 2.4 Basic Theorems and Properties of Boolean Algebra

### Single-Variable Theorems:

1. **A + 0 = A** (Identity for OR)
2. **A · 1 = A** (Identity for AND)
3. **A + 1 = 1** (Null element for OR)
4. **A · 0 = 0** (Null element for AND)
5. **A + A = A** (Idempotent for OR)
6. **A · A = A** (Idempotent for AND)
7. **A + A' = 1** (Complement for OR)
8. **A · A' = 0** (Complement for AND)
9. **(A')' = A** (Double complement/Involution)

### Two-Variable Theorems:

10. **A + B = B + A** (Commutative - OR)
11. **A · B = B · A** (Commutative - AND)
12. **A + (B + C) = (A + B) + C** (Associative - OR)
13. **A · (B · C) = (A · B) · C** (Associative - AND)
14. **A · (B + C) = A·B + A·C** (Distributive - AND over OR)
15. **A + (B · C) = (A + B) · (A + C)** (Distributive - OR over AND)

### Absorption Theorems:

16. **A + A·B = A**
    - Proof: A + A·B = A·1 + A·B = A·(1 + B) = A·1 = A

17. **A · (A + B) = A**
    - Proof: A·(A + B) = A·A + A·B = A + A·B = A

18. **A + A'·B = A + B**
    - Proof: A + A'·B = (A + A')·(A + B) = 1·(A + B) = A + B

19. **A · (A' + B) = A·B**
    - Proof: A·(A' + B) = A·A' + A·B = 0 + A·B = A·B

### DeMorgan's Theorems (Very Important!):

20. **(A + B)' = A' · B'**
    - The complement of OR is AND of complements

21. **(A · B)' = A' + B'**
    - The complement of AND is OR of complements

**Extended DeMorgan's:**
- (A + B + C)' = A'·B'·C'
- (A·B·C)' = A' + B' + C'

### Consensus Theorem:

22. **A·B + A'·C + B·C = A·B + A'·C**
    - The term B·C is redundant

23. **(A + B)·(A' + C)·(B + C) = (A + B)·(A' + C)**
    - Dual of consensus theorem

---

## 2.5 Boolean Functions

### Definition:
A Boolean function is an expression formed with:
- Binary variables
- Logic operations (AND, OR, NOT)
- Parentheses
- Equal sign

### Representation Methods:

#### 1. Algebraic Expression:
F(A,B,C) = A·B + A'·C

#### 2. Truth Table:
Lists all possible input combinations and corresponding outputs

**Example: F = A·B + A'·C**
```
A | B | C | F
--|---|---|---
0 | 0 | 0 | 0
0 | 0 | 1 | 1
0 | 1 | 0 | 0
0 | 1 | 1 | 1
1 | 0 | 0 | 0
1 | 0 | 1 | 0
1 | 1 | 0 | 1
1 | 1 | 1 | 1
```

#### 3. Logic Diagram:
Graphical representation using logic gates

### Function Manipulation:

**Simplification Example:**
```
F = A·B·C + A·B·C' + A'·B·C
  = A·B·(C + C') + A'·B·C
  = A·B·1 + A'·B·C
  = A·B + A'·B·C
  = B·(A + A'·C)
  = B·(A + C)
```

### Complement of a Function:
Apply DeMorgan's theorem repeatedly

**Example: F = A·B + C'·D**
```
F' = (A·B + C'·D)'
   = (A·B)' · (C'·D)'    [DeMorgan's]
   = (A' + B') · (C + D')  [DeMorgan's again]
```

---

## 2.6 Canonical and Standard Forms

### Minterms and Maxterms:

#### Minterm:
- Product (AND) term with ALL variables present
- Each variable appears exactly once (normal or complemented)
- Produces output 1 for exactly ONE input combination
- Denoted as m₀, m₁, m₂, ...

**Example (3 variables):**
```
Row | A B C | Minterm | Designation
----|-------|---------|------------
0   | 0 0 0 | A'·B'·C'| m₀
1   | 0 0 1 | A'·B'·C | m₁
2   | 0 1 0 | A'·B·C' | m₂
3   | 0 1 1 | A'·B·C  | m₃
4   | 1 0 0 | A·B'·C' | m₄
5   | 1 0 1 | A·B'·C  | m₅
6   | 1 1 0 | A·B·C'  | m₆
7   | 1 1 1 | A·B·C   | m₇
```

#### Maxterm:
- Sum (OR) term with ALL variables present
- Each variable appears exactly once (normal or complemented)
- Produces output 0 for exactly ONE input combination
- Denoted as M₀, M₁, M₂, ...

**Example (3 variables):**
```
Row | A B C | Maxterm     | Designation
----|-------|-------------|------------
0   | 0 0 0 | A+B+C       | M₀
1   | 0 0 1 | A+B+C'      | M₁
2   | 0 1 0 | A+B'+C      | M₂
3   | 0 1 1 | A+B'+C'     | M₃
4   | 1 0 0 | A'+B+C      | M₄
5   | 1 0 1 | A'+B+C'     | M₅
6   | 1 1 0 | A'+B'+C     | M₆
7   | 1 1 1 | A'+B'+C'    | M₇
```

**Important Relationship:**
- mᵢ = Mᵢ' (minterm is complement of corresponding maxterm)
- Example: m₃ = A'·B·C and M₃ = A+B'+C' = (A'·B·C)'

### Canonical Forms:

#### 1. Sum of Minterms (SOM) - Canonical SOP:
- OR of minterms where function = 1
- Also called: Canonical Sum-of-Products

**Example:**
```
Truth Table:
A B C | F
------|---
0 0 0 | 0
0 0 1 | 1  ← m₁
0 1 0 | 0
0 1 1 | 1  ← m₃
1 0 0 | 0
1 0 1 | 0
1 1 0 | 1  ← m₆
1 1 1 | 1  ← m₇

F = m₁ + m₃ + m₆ + m₇
F = A'·B'·C + A'·B·C + A·B·C' + A·B·C
F = Σ(1,3,6,7)  [Compact notation]
```

#### 2. Product of Maxterms (POM) - Canonical POS:
- AND of maxterms where function = 0
- Also called: Canonical Product-of-Sums

**Example (same function):**
```
F = M₀ · M₂ · M₄ · M₅
F = (A+B+C)·(A+B'+C)·(A'+B+C)·(A'+B+C')
F = Π(0,2,4,5)  [Compact notation]
```

**Important:** Σ(1,3,6,7) = Π(0,2,4,5) represent the same function!

### Standard Forms:

#### 1. Sum-of-Products (SOP):
- OR of product terms
- Not all variables need to be present in each term
- More commonly used

**Example:**
F = A·B + B·C' + A'·B·C

#### 2. Product-of-Sums (POS):
- AND of sum terms
- Not all variables need to be present in each term

**Example:**
F = (A+B)·(B'+C)·(A+C')

### Conversion Between Forms:

**SOP to POS:**
1. Find F' in SOP form
2. Apply DeMorgan's to get F in POS form

**Example:**
```
F = A·B + C
F' = (A·B + C)'
   = (A·B)' · C'
   = (A' + B') · C'
F = ((A' + B') · C')'
  = (A' + B')' + C
  = A·B + C  [back to original]
```

### Two-Level Implementation:
- SOP: AND gates feeding into OR gate
- POS: OR gates feeding into AND gate
- Canonical forms may not be minimal

---

## 2.7 Other Logic Operations

### Complete Set of Operations:
A set of operations is complete if any Boolean function can be expressed using only those operations.

### Universal Gates:

#### 1. NAND Gate (Universal):
Can implement AND, OR, and NOT using only NAND gates

**NOT using NAND:**
- A' = (A·A)' = A NAND A

**AND using NAND:**
- A·B = ((A·B)')'  = (A NAND B) NAND (A NAND B)

**OR using NAND:**
- A+B = (A'·B')' = (A NAND A) NAND (B NAND B)

#### 2. NOR Gate (Universal):
Can implement AND, OR, and NOT using only NOR gates

**NOT using NOR:**
- A' = (A+A)' = A NOR A

**OR using NOR:**
- A+B = ((A+B)')' = (A NOR B) NOR (A NOR B)

**AND using NOR:**
- A·B = (A'+B')' = (A NOR A) NOR (B NOR B)

### XOR and XNOR Operations:

#### XOR (Exclusive-OR):
- Symbol: A ⊕ B
- Output is 1 when inputs are DIFFERENT
- Properties:
  - A ⊕ 0 = A
  - A ⊕ 1 = A'
  - A ⊕ A = 0
  - A ⊕ A' = 1
  - A ⊕ B = B ⊕ A (Commutative)
  - (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C) (Associative)

**Truth Table:**
```
A | B | A⊕B
--|---|----
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0
```

**Expressions:**
- A ⊕ B = A·B' + A'·B (SOP form)
- A ⊕ B = (A+B)·(A'+B') (POS form)

#### XNOR (Exclusive-NOR):
- Symbol: A ⊙ B or (A⊕B)'
- Output is 1 when inputs are SAME
- Also called: Equivalence function

**Truth Table:**
```
A | B | A⊙B
--|---|----
0 | 0 | 1
0 | 1 | 0
1 | 0 | 0
1 | 1 | 1
```

**Expression:**
- A ⊙ B = A·B + A'·B'

### Applications:

**XOR Applications:**
- Parity generation/checking
- Arithmetic (half adder, full adder)
- Comparators
- Controlled inverter (A ⊕ 1 = A')

**Odd Function:**
- XOR of n variables = 1 when odd number of inputs are 1
- Example: A ⊕ B ⊕ C = 1 for odd number of 1s

---

## 2.8 Digital Logic Gates

### Basic Gate Symbols:

#### 1. AND Gate:
```
    A ──┐
        │ )──── A·B
    B ──┘
```
- Output HIGH only when ALL inputs are HIGH

#### 2. OR Gate:
```
    A ──┐
        │)──── A+B
    B ──┘
```
- Output HIGH when ANY input is HIGH

#### 3. NOT Gate (Inverter):
```
    A ──▷○──── A'
```
- Output is opposite of input

#### 4. NAND Gate:
```
    A ──┐
        │ )○──── (A·B)'
    B ──┘
```
- Output LOW only when ALL inputs are HIGH

#### 5. NOR Gate:
```
    A ──┐
        │)○──── (A+B)'
    B ──┘
```
- Output HIGH only when ALL inputs are LOW

#### 6. XOR Gate:
```
    A ──┐
        │)──── A⊕B
    B ──┘
```
- Output HIGH when inputs are DIFFERENT

#### 7. XNOR Gate:
```
    A ──┐
        │)○──── (A⊕B)'
    B ──┘
```
- Output HIGH when inputs are SAME

### Gate Characteristics:

#### Propagation Delay:
- Time for output to respond to input change
- Typically nanoseconds (ns)
- Limits maximum operating speed

#### Fan-in:
- Number of inputs a gate can accept
- Typical: 2-8 inputs

#### Fan-out:
- Number of gate inputs that can be driven by one output
- Depends on current driving capability

#### Power Dissipation:
- Power consumed by the gate
- Important for battery-powered devices

### Multiple-Input Gates:

**3-Input AND:**
- F = A·B·C
- Output = 1 only when A=1, B=1, C=1

**4-Input OR:**
- F = A+B+C+D
- Output = 1 when any input = 1

### Gate-Level Design:
- Complex functions built from basic gates
- Minimize number of gates and levels
- Consider propagation delay

---

## 2.9 Integrated Circuits

### What are Integrated Circuits (ICs)?
- Electronic circuits fabricated on a single semiconductor chip (usually silicon)
- Contains transistors, resistors, capacitors, and interconnections
- Compact, reliable, and cost-effective

### Levels of Integration:

1. **SSI (Small-Scale Integration)**:
   - Less than 10 gates
   - Examples: Individual gates, flip-flops

2. **MSI (Medium-Scale Integration)**:
   - 10 to 100 gates
   - Examples: Decoders, multiplexers, registers, counters

3. **LSI (Large-Scale Integration)**:
   - 100 to 10,000 gates
   - Examples: Small processors, memory chips

4. **VLSI (Very Large-Scale Integration)**:
   - More than 10,000 gates
   - Examples: Microprocessors, large memory chips

5. **ULSI (Ultra Large-Scale Integration)**:
   - Millions of gates
   - Examples: Modern CPUs, GPUs

### IC Families:

#### 1. TTL (Transistor-Transistor Logic):
- Uses bipolar junction transistors
- Fast switching speed
- Higher power consumption
- Standard: 7400 series
- Example: 7404 (hex inverter), 7408 (quad 2-input AND)

#### 2. CMOS (Complementary Metal-Oxide-Semiconductor):
- Uses MOSFETs (both n-type and p-type)
- Very low power consumption
- High noise immunity
- Standard: 4000 series, 74HC series
- Most common in modern designs

#### 3. ECL (Emitter-Coupled Logic):
- Fastest logic family
- High power consumption
- Used in high-speed applications

### IC Packaging:

**Common Package Types:**
- **DIP (Dual In-line Package)**: Two rows of pins
- **SOIC (Small Outline IC)**: Surface mount
- **QFP (Quad Flat Package)**: Pins on all four sides
- **BGA (Ball Grid Array)**: Balls underneath chip

### Digital Logic Levels:

**TTL Levels:**
- Logic 0: 0V to 0.8V
- Logic 1: 2V to 5V
- Undefined: 0.8V to 2V

**CMOS Levels:**
- Logic 0: 0V to 30% of VDD
- Logic 1: 70% of VDD to VDD
- Better noise margins than TTL

### Programmable Logic Devices:

#### 1. PLD (Programmable Logic Device):
- User-programmable
- Can implement custom logic functions

#### 2. FPGA (Field-Programmable Gate Array):
- Contains array of logic blocks
- Highly flexible
- Can be reprogrammed
- Used for prototyping and custom designs

#### 3. CPLD (Complex Programmable Logic Device):
- Multiple PLDs on single chip
- Non-volatile (retains programming)

#### 4. ASIC (Application-Specific IC):
- Custom-designed for specific application
- High performance, low cost in volume
- Cannot be reprogrammed

### Design Considerations:

1. **Power Consumption**: Important for battery-powered devices
2. **Speed**: Propagation delay affects maximum frequency
3. **Cost**: Per-unit cost depends on volume
4. **Reliability**: MTBF (Mean Time Between Failures)
5. **Size**: Physical dimensions and pin count
6. **Noise Immunity**: Resistance to electrical interference

---

## Chapter 2 Summary - Key Concepts:

1. **Boolean Algebra Postulates**: Identity, Commutative, Distributive, Complement

2. **Important Theorems**:
   - DeMorgan's: (A+B)' = A'·B', (A·B)' = A'+B'
   - Absorption: A + A·B = A
   - Consensus: A·B + A'·C + B·C = A·B + A'·C

3. **Canonical Forms**:
   - Sum of Minterms: Σ(...)
   - Product of Maxterms: Π(...)

4. **Standard Forms**:
   - SOP: OR of AND terms
   - POS: AND of OR terms

5. **Universal Gates**: NAND and NOR can implement any function

6. **XOR Properties**:
   - A ⊕ 0 = A
   - A ⊕ 1 = A'
   - A ⊕ A = 0
   - A ⊕ B = A·B' + A'·B

7. **Logic Gates**: AND, OR, NOT, NAND, NOR, XOR, XNOR

8. **IC Families**: TTL (fast, high power), CMOS (low power)

---

## Practice Problems:

1. Simplify: F = A·B + A·B' + A'·B
2. Prove: A + A'·B = A + B
3. Find complement of: F = A·B + C'·D
4. Express F(A,B,C) = Σ(0,2,5,7) in:
   - Canonical SOP
   - Canonical POS
5. Implement F = A+B using only NAND gates
6. Find truth table for: F = A⊕B⊕C
7. Convert to POS: F = A·B + B·C
