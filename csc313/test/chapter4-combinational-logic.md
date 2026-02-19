# Chapter 4: Combinational Logic

## 4.1 Introduction

### What is Combinational Logic?

A combinational circuit is a logic circuit where:
- Outputs depend ONLY on current inputs
- No memory elements (no feedback loops)
- No storage of previous states
- Output changes when input changes (after propagation delay)

### Characteristics:
- **n inputs, m outputs**
- Each output is a Boolean function of inputs
- Can be described by truth table or Boolean equations
- Examples: Adders, multiplexers, decoders, encoders

### Contrast with Sequential Circuits:
- Sequential circuits have memory (flip-flops)
- Outputs depend on inputs AND current state
- Examples: Counters, registers, state machines

---

## 4.2 Combinational Circuits

### Components:
1. **Input variables**: External inputs to circuit
2. **Logic gates**: AND, OR, NOT, NAND, NOR, XOR
3. **Output variables**: Results of logic operations

### Design Hierarchy:
- **Gate level**: Individual logic gates
- **Block level**: Functional blocks (adders, muxes)
- **System level**: Complete systems

### Circuit Representation:

**1. Boolean Equations:**
- F₁ = A·B + C
- F₂ = A'·C + B

**2. Truth Table:**
Lists all input combinations and outputs

**3. Logic Diagram:**
Graphical representation with gates

**4. HDL Description:**
Verilog or VHDL code

---

## 4.3 Analysis Procedure

### Goal:
Given a logic circuit, determine its function (truth table or Boolean equations).

### Analysis Steps:

**Step 1: Label all gate outputs**
- Assign variables to intermediate signals
- Work from inputs toward outputs

**Step 2: Write Boolean equations**
- Express each gate output in terms of inputs
- Substitute to get output equations

**Step 3: Create truth table**
- List all input combinations
- Calculate outputs for each combination

**Step 4: Interpret function**
- Identify what the circuit does
- Simplify if possible

### Example: Analyze this circuit

```
Inputs: A, B, C
Gates:
- T₁ = A·B
- T₂ = T₁ + C
- F = T₂'
```

**Step 1: Label intermediate signals**
- T₁, T₂ already labeled

**Step 2: Boolean equations**
- T₁ = A·B
- T₂ = A·B + C
- F = (A·B + C)'
- F = (A·B)'·C' (DeMorgan's)
- F = (A' + B')·C'

**Step 3: Truth table**
```
A B C | T₁ | T₂ | F
------|----|----|---
0 0 0 | 0  | 0  | 1
0 0 1 | 0  | 1  | 0
0 1 0 | 0  | 0  | 1
0 1 1 | 0  | 1  | 0
1 0 0 | 0  | 0  | 1
1 0 1 | 0  | 1  | 0
1 1 0 | 1  | 1  | 0
1 1 1 | 1  | 1  | 0
```

**Step 4: Interpretation**
- F = 1 only when A=0, B=0, C=0 OR A=0, B=1, C=0 OR A=1, B=0, C=0
- F = C'·(A'·B' + A'·B + A·B') = C'·(A⊕B)'
- Function: Output is 1 when C=0 AND A=B

### Multi-Output Circuits:

When circuit has multiple outputs:
- Analyze each output separately
- Look for shared logic (common subexpressions)
- Can save gates by sharing logic

**Example:**
- F₁ = A·B + C
- F₂ = A·B + D
- Shared term: A·B (compute once, use twice)

---

## 4.4 Design Procedure

### Goal:
Design a combinational circuit from specifications.

### Design Steps:

**Step 1: Problem Specification**
- Understand what circuit should do
- Identify inputs and outputs
- Define behavior clearly

**Step 2: Truth Table**
- List all input combinations
- Determine required output for each

**Step 3: Simplify Boolean Functions**
- Use K-maps or Boolean algebra
- Minimize number of gates/literals
- Consider don't-care conditions

**Step 4: Draw Logic Diagram**
- Implement simplified equations
- Use appropriate gates
- Consider gate availability

**Step 5: Verify Design**
- Check truth table matches specification
- Simulate if possible
- Test critical cases

### Example: Design a circuit that detects if a 3-bit number is greater than 5

**Step 1: Specification**
- Inputs: A, B, C (3-bit binary number, A is MSB)
- Output: F = 1 if ABC > 5, else F = 0

**Step 2: Truth Table**
```
A B C | Decimal | F
------|---------|---
0 0 0 |    0    | 0
0 0 1 |    1    | 0
0 1 0 |    2    | 0
0 1 1 |    3    | 0
1 0 0 |    4    | 0
1 0 1 |    5    | 0
1 1 0 |    6    | 1
1 1 1 |    7    | 1
```

F = Σ(6,7)

**Step 3: Simplify**
```
K-map:
      BC
     00 01 11 10
A 0 │0 │0 │0 │0 │
  1 │0 │0 │1 │1 │
```

Group: m₆, m₇ → A·B
F = A·B

**Step 4: Logic Diagram**
```
A ──┐
    AND── F
B ──┘
```

**Step 5: Verify**
- F = 1 when A=1 AND B=1 (numbers 6 and 7)
- Correct!

### Example 2: BCD to Excess-3 Code Converter

**Step 1: Specification**
- Input: 4-bit BCD (0-9)
- Output: 4-bit Excess-3 code
- Excess-3 = BCD + 3

**Step 2: Truth Table**
```
BCD Input    | Excess-3 Output
A B C D      | W X Y Z
-------------|----------------
0 0 0 0  (0) | 0 0 1 1  (3)
0 0 0 1  (1) | 0 1 0 0  (4)
0 0 1 0  (2) | 0 1 0 1  (5)
0 0 1 1  (3) | 0 1 1 0  (6)
0 1 0 0  (4) | 0 1 1 1  (7)
0 1 0 1  (5) | 1 0 0 0  (8)
0 1 1 0  (6) | 1 0 0 1  (9)
0 1 1 1  (7) | 1 0 1 0  (10)
1 0 0 0  (8) | 1 0 1 1  (11)
1 0 0 1  (9) | 1 1 0 0  (12)
1 0 1 0      | X X X X  (don't care)
1 0 1 1      | X X X X  (don't care)
1 1 0 0      | X X X X  (don't care)
1 1 0 1      | X X X X  (don't care)
1 1 1 0      | X X X X  (don't care)
1 1 1 1      | X X X X  (don't care)
```

**Step 3: Simplify each output**

For W: W = Σ(5,6,7,8,9), d(10-15)
For X: X = Σ(1,2,3,4,9), d(10-15)
For Y: Y = Σ(0,3,4,7,8), d(10-15)
For Z: Z = Σ(0,2,4,6,8), d(10-15)

Using K-maps:
- W = A·B + A·C + B·C·D
- X = B'·C + B'·D + B·C'·D'
- Y = C·D' + C'·D
- Z = D'

**Step 4: Draw circuit with gates**

**Step 5: Verify with test cases**

### Design Considerations:

1. **Cost**: Number of gates, IC packages
2. **Speed**: Propagation delay, number of levels
3. **Power**: Power consumption
4. **Reliability**: Fault tolerance
5. **Testability**: Ease of testing

### Trade-offs:
- Fewer gates vs. faster circuit
- Simple design vs. optimal design
- Development time vs. performance

---

## 4.5 Binary Adder-Subtractor

### Half Adder:

Adds two single bits.

**Inputs**: A, B
**Outputs**: Sum (S), Carry (C)

**Truth Table:**
```
A B | S C
----|----
0 0 | 0 0
0 1 | 1 0
1 0 | 1 0
1 1 | 0 1
```

**Equations:**
- S = A ⊕ B (XOR)
- C = A · B (AND)

**Circuit:**
```
A ──┬──XOR── S
    │
B ──┼──AND── C
    │
```

### Full Adder:

Adds three bits (two inputs + carry-in).

**Inputs**: A, B, Cin
**Outputs**: Sum (S), Cout

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

**Equations:**
- S = A ⊕ B ⊕ Cin
- Cout = A·B + A·Cin + B·Cin
- Cout = A·B + (A⊕B)·Cin (alternative)

**Implementation using Half Adders:**
```
A ──┐
    HA1── S1 ──┐
B ──┘      C1  │
               HA2── S
Cin ───────────┘  C2
                  │
C1 ────OR─────────┴── Cout
C2 ────┘
```

### Binary Ripple Carry Adder:

Adds two n-bit numbers.

**4-Bit Ripple Carry Adder:**
```
A₃B₃  A₂B₂  A₁B₁  A₀B₀
 │ │   │ │   │ │   │ │
 FA ── FA ── FA ── FA
 │     │     │     │  Cin=0
C₄    S₃    S₂    S₁   S₀
```

**Characteristics:**
- Carry propagates from LSB to MSB
- Slow for large n (carry ripple delay)
- Simple design
- Delay = n × (full adder delay)

**Example: Add 1011 + 0011**
```
  1011  (11)
+ 0011  (3)
------
  1110  (14)

Carry: 0111
```

### Carry Lookahead Adder:

Faster alternative to ripple carry.

**Concept:**
- Calculate all carries simultaneously
- No waiting for carry to ripple
- More complex hardware

**Generate and Propagate:**
- Gᵢ = Aᵢ · Bᵢ (carry generate)
- Pᵢ = Aᵢ ⊕ Bᵢ (carry propagate)

**Carry Equations:**
- C₁ = G₀ + P₀·C₀
- C₂ = G₁ + P₁·G₀ + P₁·P₀·C₀
- C₃ = G₂ + P₂·G₁ + P₂·P₁·G₀ + P₂·P₁·P₀·C₀
- And so on...

**Advantages:**
- Much faster for large n
- Constant delay (doesn't depend on n)

**Disadvantages:**
- More complex
- More gates required

### Binary Subtractor:

Performs A - B.

**Method 1: Using 2's Complement**
- A - B = A + (2's complement of B)
- A - B = A + B' + 1

**Half Subtractor:**
**Inputs**: A, B
**Outputs**: Difference (D), Borrow (Br)

```
A B | D Br
----|------
0 0 | 0  0
0 1 | 1  1
1 0 | 1  0
1 1 | 0  0
```

- D = A ⊕ B
- Br = A'·B

**Full Subtractor:**
**Inputs**: A, B, Bin
**Outputs**: Difference (D), Bout

- D = A ⊕ B ⊕ Bin
- Bout = A'·B + A'·Bin + B·Bin

### Adder-Subtractor Circuit:

Combined circuit that can add or subtract.

**Control Signal M:**
- M = 0: Add (A + B)
- M = 1: Subtract (A - B)

**Implementation:**
```
For each bit:
- XOR B with M (gives B when M=0, B' when M=1)
- Feed to full adder with A
- M also connects to C₀ (adds 1 for 2's complement)
```

**4-Bit Adder-Subtractor:**
```
M ──┬── XOR ──┐
    │         FA ── (bit 0)
B₀ ─┘    A₀ ──┘

M ──┬── XOR ──┐
    │         FA ── (bit 1)
B₁ ─┘    A₁ ──┘

... (continue for all bits)

M connects to Cin of first FA
```

**Operation:**
- M=0: Output = A + B
- M=1: Output = A + B' + 1 = A - B

### Overflow Detection:

Overflow occurs when result doesn't fit in available bits.

**For Signed Numbers (2's complement):**
- Overflow when:
  - Adding two positive numbers gives negative result
  - Adding two negative numbers gives positive result
  - Cin to MSB ≠ Cout from MSB

**Overflow Detection Circuit:**
V = Cn ⊕ Cn-1
(XOR of carry into and out of sign bit)

**Example:**
```
  0111  (+7)
+ 0101  (+5)
------
  1100  (-4) ← OVERFLOW!
```

---

## 4.6 Decimal Adder

### BCD Addition:

Adds two BCD digits (0-9).

**Rules:**
1. Add two BCD digits using binary addition
2. If sum ≤ 9 (1001) and no carry: Result is valid BCD
3. If sum > 9 or carry generated: Add 6 (0110) to correct

**Why add 6?**
- BCD uses only 0-9 (10 values)
- Binary uses 0-15 (16 values)
- Difference = 6
- Adding 6 skips invalid codes (1010-1111)

### Examples:

**Example 1: 5 + 3 = 8**
```
  0101  (5)
+ 0011  (3)
------
  1000  (8) ← Valid BCD, no correction needed
```

**Example 2: 8 + 5 = 13**
```
  1000  (8)
+ 0101  (5)
------
  1101  (13 in binary, invalid BCD!)
+ 0110  (add 6 for correction)
------
1 0011  (carry=1, digit=3, represents 13)
```

**Example 3: 9 + 9 = 18**
```
  1001  (9)
+ 1001  (9)
------
1 0010  (carry generated, need correction)
+ 0110  (add 6)
------
1 1000  (carry=1, digit=8, represents 18)
```

### BCD Adder Circuit:

**Components:**
1. 4-bit binary adder (adds two BCD digits)
2. Correction logic (detects when to add 6)
3. Another 4-bit adder (adds 6 when needed)

**Correction Logic:**
Add 6 when:
- Sum > 9, OR
- Carry out = 1

**Detection:**
- C = 1 (carry out), OR
- Z₈·Z₄ = 1 (bit 3 AND bit 2), OR
- Z₈·Z₂ = 1 (bit 3 AND bit 1)

Where Z₈, Z₄, Z₂, Z₁ are the sum bits.

**Correction Signal:**
K = C + Z₈·Z₄ + Z₈·Z₂

**Circuit:**
```
A₃A₂A₁A₀ ──┐
           4-bit Adder ── Z₈Z₄Z₂Z₁ ──┐
B₃B₂B₁B₀ ──┘            C            │
                        │            │
                    Correction ──────┤
                    Logic            │
                        │            │
                        K            │
                        │            │
                    0110 (6) ────────┤
                                     │
                                4-bit Adder ── S₃S₂S₁S₀
                                     │
                                    Cout
```

### Multi-Digit BCD Addition:

For adding multi-digit BCD numbers:
- Chain BCD adders
- Carry propagates from one digit to next
- Each stage adds one BCD digit

**Example: 3-digit BCD adder**
```
Digit 2  Digit 1  Digit 0
  BCD      BCD      BCD
 Adder    Adder    Adder
   │        │        │
  Cout    Cout     Cout
```

---

## 4.7 Binary Multiplier

### 2×2 Bit Multiplier:

Multiplies two 2-bit numbers.

**Inputs**: A₁A₀, B₁B₀
**Output**: C₃C₂C₁C₀ (4-bit product)

**Multiplication Process:**
```
      A₁ A₀
    × B₁ B₀
    -------
    A₁B₀ A₀B₀  (partial product 0)
  A₁B₁ A₀B₁    (partial product 1)
  -----------
  C₃ C₂ C₁ C₀
```

**Implementation:**
- Each partial product bit = AND of two inputs
- Add partial products using half/full adders

**Example: 3 × 2 = 6**
```
      1 1  (3)
    × 1 0  (2)
    -----
      0 0  (3 × 0)
    1 1    (3 × 1, shifted)
    -----
    1 1 0  (6)
```

**Circuit:**
```
A₁B₀ ── AND
A₀B₀ ── AND ── C₀

A₁B₁ ── AND ──┐
              HA ── C₂
A₀B₁ ── AND ──┘  └── to next stage

(Continue with full adders for larger multipliers)
```

### 4×4 Bit Multiplier:

**Inputs**: A₃A₂A₁A₀, B₃B₂B₁B₀
**Output**: P₇P₆P₅P₄P₃P₂P₁P₀ (8-bit product)

**Structure:**
- 16 AND gates (for partial products)
- Array of half adders and full adders
- Organized in rows

**Partial Products:**
```
        A₃ A₂ A₁ A₀
      × B₃ B₂ B₁ B₀
      -------------
        A₃B₀ A₂B₀ A₁B₀ A₀B₀
      A₃B₁ A₂B₁ A₁B₁ A₀B₁
    A₃B₂ A₂B₂ A₁B₂ A₀B₂
  A₃B₃ A₂B₃ A₁B₃ A₀B₃
  ---------------------------
  P₇   P₆   P₅   P₄   P₃ P₂ P₁ P₀
```

**Characteristics:**
- n×n multiplier produces 2n-bit result
- Requires n² AND gates
- Requires approximately n²-n adders
- Combinational circuit (no clock needed)

### Array Multiplier:

Systematic arrangement of adders.

**Advantages:**
- Regular structure
- Easy to design and layout
- Scalable

**Disadvantages:**
- Slow for large numbers
- Many gates required

### Faster Multiplication Methods:

1. **Booth's Algorithm**: Reduces number of additions
2. **Wallace Tree**: Parallel reduction of partial products
3. **Carry-Save Adders**: Faster partial product addition

---

## 4.8 Magnitude Comparator

### Function:
Compares two binary numbers and determines:
- A > B
- A = B
- A < B

### 1-Bit Comparator:

**Inputs**: A, B
**Outputs**: A>B, A=B, A<B

**Truth Table:**
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
- A=B = A'·B' + A·B = (A⊕B)'
- A<B = A'·B

### 2-Bit Comparator:

**Inputs**: A₁A₀, B₁B₀
**Outputs**: A>B, A=B, A<B

**Logic:**
1. Compare MSBs first
2. If equal, compare LSBs
3. If all equal, numbers are equal

**Equations:**
- A>B = A₁·B₁' + (A₁⊙B₁)·A₀·B₀'
- A=B = (A₁⊙B₁)·(A₀⊙B₀)
- A<B = A₁'·B₁ + (A₁⊙B₁)·A₀'·B₀

Where ⊙ is XNOR (equality)

### 4-Bit Comparator:

**Cascading Approach:**
- Compare bit by bit from MSB to LSB
- Use cascade inputs for expansion

**Equations:**
```
(A=B) = (A₃⊙B₃)·(A₂⊙B₂)·(A₁⊙B₁)·(A₀⊙B₀)

(A>B) = A₃·B₃' + (A₃⊙B₃)·A₂·B₂' + 
        (A₃⊙B₃)·(A₂⊙B₂)·A₁·B₁' +
        (A₃⊙B₃)·(A₂⊙B₂)·(A₁⊙B₁)·A₀·B₀'

(A<B) = similar, with A and B swapped
```

### Cascading Comparators:

For comparing larger numbers:
- Use multiple 4-bit comparators
- Connect cascade outputs to cascade inputs
- Compare from MSB to LSB

**Example: 8-bit comparison using two 4-bit comparators**
```
A₇-A₄, B₇-B₄ ──┐
               Comp1 ── (A>B)₁ ──┐
               (MSB)  ── (A=B)₁ ──┤
                      ── (A<B)₁ ──┤
                                  │
A₃-A₀, B₃-B₀ ──┐                  │
               Comp2 ──────────────┴── Final outputs
               (LSB)   Cascade in
```

---

## 4.9 Decoders

### What is a Decoder?

A decoder converts n-bit binary input to maximum 2ⁿ unique outputs.
- Only ONE output is active at a time
- Output corresponds to binary value of input

### n-to-2ⁿ Decoder:

**Characteristics:**
- n inputs
- 2ⁿ outputs
- Each output represents a minterm
- Exactly one output is HIGH (or LOW) at a time

### 2-to-4 Decoder:

**Inputs**: A₁, A₀
**Outputs**: D₀, D₁, D₂, D₃

**Truth Table:**
```
A₁ A₀ | D₀ D₁ D₂ D₃
------|-------------
0  0  | 1  0  0  0
0  1  | 0  1  0  0
1  0  | 0  0  1  0
1  1  | 0  0  0  1
```

**Equations:**
- D₀ = A₁'·A₀' (minterm m₀)
- D₁ = A₁'·A₀  (minterm m₁)
- D₂ = A₁·A₀'  (minterm m₂)
- D₃ = A₁·A₀   (minterm m₃)

**Implementation:**
- 2 NOT gates (for complements)
- 4 AND gates (one per output)

### 3-to-8 Decoder:

**Inputs**: A₂, A₁, A₀
**Outputs**: D₀ through D₇

**Truth Table:**
```
A₂ A₁ A₀ | Active Output
---------|---------------
0  0  0  | D₀
0  0  1  | D₁
0  1  0  | D₂
0  1  1  | D₃
1  0  0  | D₄
1  0  1  | D₅
1  1  0  | D₆
1  1  1  | D₇
```

Each output is a minterm of the three inputs.

### Decoder with Enable:

**Enable Input (E):**
- E = 1: Decoder operates normally
- E = 0: All outputs are 0 (disabled)

**Modified Equations:**
- D₀ = E·A₁'·A₀'
- D₁ = E·A₁'·A₀
- D₂ = E·A₁·A₀'
- D₃ = E·A₁·A₀

**Uses:**
- Power saving (disable when not needed)
- Cascading multiple decoders
- Time-multiplexing

### Decoder Expansion:

Build larger decoders from smaller ones.

**Example: 3-to-8 decoder using two 2-to-4 decoders**
```
A₂ (MSB) controls which 2-to-4 decoder is enabled:
- A₂=0: Enable first decoder (outputs D₀-D₃)
- A₂=1: Enable second decoder (outputs D₄-D₇)
A₁, A₀ connect to both decoders
```

**Example: 4-to-16 decoder using five 2-to-4 decoders**
```
One 2-to-4 decoder as "enable decoder"
Four 2-to-4 decoders as "output decoders"
```

### Implementing Boolean Functions with Decoders:

Decoders generate all minterms!

**Method:**
1. Decoder generates all minterms
2. OR the minterms where function = 1

**Example: F(A,B,C) = Σ(1,3,5,7)**
```
Use 3-to-8 decoder
OR together outputs D₁, D₃, D₅, D₇
F = D₁ + D₃ + D₅ + D₇
```

**Advantages:**
- Easy to implement any function
- Easy to modify function (just change OR connections)
- Good for functions with many minterms

**Disadvantages:**
- May require large decoder
- May need many-input OR gate

### Common Decoder ICs:

- **74138**: 3-to-8 decoder with enable
- **74139**: Dual 2-to-4 decoder
- **74154**: 4-to-16 decoder

### Applications:

1. **Memory Address Decoding**: Select memory chip
2. **I/O Port Selection**: Select I/O device
3. **Instruction Decoding**: Decode CPU instructions
4. **Seven-Segment Display**: BCD to 7-segment
5. **Demultiplexing**: Route data to one of many outputs

---

## 4.10 Encoders

### What is an Encoder?

Opposite of decoder:
- 2ⁿ (or fewer) inputs
- n-bit binary output
- Encodes input position to binary code

### 4-to-2 Encoder:

**Inputs**: D₀, D₁, D₂, D₃ (only one should be HIGH)
**Outputs**: A₁, A₀

**Truth Table:**
```
D₀ D₁ D₂ D₃ | A₁ A₀
------------|-------
1  0  0  0  | 0  0
0  1  0  0  | 0  1
0  0  1  0  | 1  0
0  0  0  1  | 1  1
```

**Equations:**
- A₀ = D₁ + D₃
- A₁ = D₂ + D₃

**Limitation:**
- Assumes only one input is HIGH
- If multiple inputs HIGH, output is ambiguous
- If all inputs LOW, output is 00 (same as D₀)

### 8-to-3 Encoder:

**Inputs**: D₀ through D₇
**Outputs**: A₂, A₁, A₀

**Equations:**
- A₀ = D₁ + D₃ + D₅ + D₇
- A₁ = D₂ + D₃ + D₆ + D₇
- A₂ = D₄ + D₅ + D₆ + D₇

### Priority Encoder:

Solves the problem of multiple active inputs.

**Features:**
- If multiple inputs are HIGH, encodes the highest priority input
- Usually highest-numbered input has highest priority
- Additional outputs indicate validity

**4-to-2 Priority Encoder:**

**Inputs**: D₀, D₁, D₂, D₃
**Outputs**: A₁, A₀, V (valid output)

**Truth Table:**
```
D₃ D₂ D₁ D₀ | A₁ A₀ V
------------|----------
0  0  0  0  | X  X  0  (no input, invalid)
0  0  0  1  | 0  0  1
0  0  1  X  | 0  1  1  (D₁ has priority over D₀)
0  1  X  X  | 1  0  1  (D₂ has priority)
1  X  X  X  | 1  1  1  (D₃ has highest priority)
```

**Equations:**
- A₁ = D₂ + D₃
- A₀ = D₃ + D₁·D₂'
- V = D₀ + D₁ + D₂ + D₃

### Applications:

1. **Keyboard Encoding**: Convert key press to code
2. **Interrupt Handling**: Prioritize interrupt requests
3. **Position Encoding**: Encode position of active sensor
4. **Data Compression**: Encode sparse data

### Encoder vs Decoder:

| Feature | Encoder | Decoder |
|---------|---------|---------|
| Inputs | 2ⁿ | n |
| Outputs | n | 2ⁿ |
| Function | Many to few | Few to many |
| Example | 8-to-3 | 3-to-8 |

---

## 4.11 Multiplexers

### What is a Multiplexer (MUX)?

A multiplexer selects one of many inputs and routes it to a single output.
- Also called: Data selector, MUX
- n select lines can choose from 2ⁿ inputs

### 2-to-1 Multiplexer:

**Inputs**: I₀, I₁ (data inputs), S (select)
**Output**: Y

**Truth Table:**
```
S | Y
--|----
0 | I₀
1 | I₁
```

**Equation:**
Y = S'·I₀ + S·I₁

**Circuit:**
```
I₀ ──┬── AND ──┐
     │         │
S ───┼── NOT   OR ── Y
     │         │
I₁ ──┴── AND ──┘
```

### 4-to-1 Multiplexer:

**Inputs**: I₀, I₁, I₂, I₃ (data), S₁, S₀ (select)
**Output**: Y

**Truth Table:**
```
S₁ S₀ | Y
------|----
0  0  | I₀
0  1  | I₁
1  0  | I₂
1  1  | I₃
```

**Equation:**
Y = S₁'·S₀'·I₀ + S₁'·S₀·I₁ + S₁·S₀'·I₂ + S₁·S₀·I₃

**Implementation:**
- 2-to-4 decoder (generates minterms)
- 4 AND gates (one per input)
- 4-input OR gate

### 8-to-1 Multiplexer:

**Inputs**: I₀ through I₇, S₂, S₁, S₀
**Output**: Y

**Equation:**
Y = Σ(Sᵢ·Iᵢ) for all 8 combinations

### Multiplexer with Enable:

**Enable Input (E):**
- E = 1: MUX operates normally
- E = 0: Output is 0 (or high-Z)

**Modified Equation:**
Y = E·(S₁'·S₀'·I₀ + S₁'·S₀·I₁ + ...)

### Multiplexer Expansion:

Build larger MUX from smaller ones.

**Example: 8-to-1 MUX using 2-to-1 MUXes**
```
Tree structure:
Level 1: Four 2-to-1 MUXes (controlled by S₀)
Level 2: Two 2-to-1 MUXes (controlled by S₁)
Level 3: One 2-to-1 MUX (controlled by S₂)
```

**Example: 8-to-1 MUX using two 4-to-1 MUXes**
```
I₀-I₃ ──┐
        4-to-1 MUX ──┐
S₁,S₀ ──┘            │
                     2-to-1 MUX ── Y
I₄-I₇ ──┐            │
        4-to-1 MUX ──┘
S₁,S₀ ──┘
         │
        S₂ (controls final MUX)
```

### Implementing Boolean Functions with Multiplexers:

MUX can implement any Boolean function!

**Method 1: Direct Implementation (n variables, 2ⁿ-to-1 MUX)**
1. Connect variables to select lines
2. Connect function values to data inputs
3. For each minterm, set corresponding input to 1 or 0

**Example: F(A,B,C) = Σ(1,3,5,7) using 8-to-1 MUX**
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

Result: F = B·C (can verify from pattern)
```

**Method 2: Reduced Implementation (n variables, 2ⁿ⁻¹-to-1 MUX)**
1. Connect n-1 variables to select lines
2. Remaining variable (and its complement) used for data inputs
3. Each data input is: 0, 1, variable, or variable'

**Example: F(A,B,C) = Σ(1,2,6,7) using 4-to-1 MUX**
```
Connect A,B to S₁,S₀
Analyze function for each AB combination:

AB=00: F=1 when C=1 → I₀ = C
AB=01: F=1 when C=0 → I₁ = C'
AB=10: F=1 when C=0 → I₂ = C'
AB=11: F=1 always  → I₃ = 1
```

**Procedure for Method 2:**
1. Make truth table
2. Group by n-1 variables
3. For each group, determine data input:
   - If F=0 for both values of last variable: Input = 0
   - If F=1 for both values: Input = 1
   - If F=0 when var=0, F=1 when var=1: Input = var
   - If F=1 when var=0, F=0 when var=1: Input = var'

### Three-State Gates:

Used with multiplexers for bus systems.

**States:**
1. Logic 0
2. Logic 1
3. High-impedance (Hi-Z) - disconnected

**Application:**
- Multiple devices share a bus
- Only one device drives bus at a time
- Others are in Hi-Z state

### Applications:

1. **Data Routing**: Select data from multiple sources
2. **Parallel-to-Serial Conversion**: Select bits sequentially
3. **Function Generation**: Implement Boolean functions
4. **Bus Systems**: Share communication lines
5. **ALU Operations**: Select operation result

### Common MUX ICs:

- **74151**: 8-to-1 MUX
- **74153**: Dual 4-to-1 MUX
- **74157**: Quad 2-to-1 MUX

---

## 4.12 HDL Models of Combinational Circuits

### Modeling Styles in Verilog:

1. **Gate-Level**: Instantiate primitive gates
2. **Dataflow**: Use continuous assignments
3. **Behavioral**: Use procedural blocks
4. **Structural**: Instantiate modules

### Gate-Level Modeling:

**Example: Half Adder**
```verilog
module half_adder_gate (A, B, Sum, Carry);
    input A, B;
    output Sum, Carry;
    
    xor (Sum, A, B);
    and (Carry, A, B);
endmodule
```

**Example: Full Adder**
```verilog
module full_adder_gate (A, B, Cin, Sum, Cout);
    input A, B, Cin;
    output Sum, Cout;
    wire w1, w2, w3;
    
    xor (w1, A, B);
    xor (Sum, w1, Cin);
    and (w2, A, B);
    and (w3, w1, Cin);
    or (Cout, w2, w3);
endmodule
```

### Dataflow Modeling:

**Example: 2-to-4 Decoder**
```verilog
module decoder_2to4 (A, B, D);
    input A, B;
    output [3:0] D;
    
    assign D[0] = ~A & ~B;
    assign D[1] = ~A & B;
    assign D[2] = A & ~B;
    assign D[3] = A & B;
endmodule
```

**Example: 4-to-1 Multiplexer**
```verilog
module mux_4to1 (I0, I1, I2, I3, S0, S1, Y);
    input I0, I1, I2, I3, S0, S1;
    output Y;
    
    assign Y = (~S1 & ~S0 & I0) |
               (~S1 & S0 & I1) |
               (S1 & ~S0 & I2) |
               (S1 & S0 & I3);
endmodule
```

**Alternative MUX using Conditional Operator:**
```verilog
module mux_4to1_conditional (I, S, Y);
    input [3:0] I;
    input [1:0] S;
    output Y;
    
    assign Y = (S == 2'b00) ? I[0] :
               (S == 2'b01) ? I[1] :
               (S == 2'b10) ? I[2] : I[3];
endmodule
```

### Behavioral Modeling:

**Example: 4-to-2 Priority Encoder**
```verilog
module priority_encoder (D, A, V);
    input [3:0] D;
    output reg [1:0] A;
    output reg V;
    
    always @(D)
    begin
        if (D[3]) begin
            A = 2'b11;
            V = 1'b1;
        end
        else if (D[2]) begin
            A = 2'b10;
            V = 1'b1;
        end
        else if (D[1]) begin
            A = 2'b01;
            V = 1'b1;
        end
        else if (D[0]) begin
            A = 2'b00;
            V = 1'b1;
        end
        else begin
            A = 2'bxx;
            V = 1'b0;
        end
    end
endmodule
```

**Example: 4-Bit Comparator**
```verilog
module comparator_4bit (A, B, AgtB, AeqB, AltB);
    input [3:0] A, B;
    output reg AgtB, AeqB, AltB;
    
    always @(A, B)
    begin
        if (A > B) begin
            AgtB = 1;
            AeqB = 0;
            AltB = 0;
        end
        else if (A == B) begin
            AgtB = 0;
            AeqB = 1;
            AltB = 0;
        end
        else begin
            AgtB = 0;
            AeqB = 0;
            AltB = 1;
        end
    end
endmodule
```

### Structural Modeling:

**Example: 4-Bit Ripple Carry Adder**
```verilog
module ripple_carry_adder_4bit (A, B, Cin, Sum, Cout);
    input [3:0] A, B;
    input Cin;
    output [3:0] Sum;
    output Cout;
    wire C1, C2, C3;
    
    full_adder FA0 (A[0], B[0], Cin, Sum[0], C1);
    full_adder FA1 (A[1], B[1], C1, Sum[1], C2);
    full_adder FA2 (A[2], B[2], C2, Sum[2], C3);
    full_adder FA3 (A[3], B[3], C3, Sum[3], Cout);
endmodule
```

**Example: 8-to-1 MUX using 4-to-1 MUXes**
```verilog
module mux_8to1 (I, S, Y);
    input [7:0] I;
    input [2:0] S;
    output Y;
    wire Y0, Y1;
    
    mux_4to1 MUX0 (I[0], I[1], I[2], I[3], S[0], S[1], Y0);
    mux_4to1 MUX1 (I[4], I[5], I[6], I[7], S[0], S[1], Y1);
    mux_2to1 MUX2 (Y0, Y1, S[2], Y);
endmodule
```

### Parameterized Modules:

**Example: N-Bit Adder**
```verilog
module adder_n_bit #(parameter N = 4) (A, B, Cin, Sum, Cout);
    input [N-1:0] A, B;
    input Cin;
    output [N-1:0] Sum;
    output Cout;
    
    assign {Cout, Sum} = A + B + Cin;
endmodule
```

### Testbench Example:

**Testing 4-to-1 MUX:**
```verilog
module mux_4to1_tb;
    reg [3:0] I;
    reg [1:0] S;
    wire Y;
    
    mux_4to1 UUT (I[0], I[1], I[2], I[3], S[0], S[1], Y);
    
    initial begin
        $monitor("Time=%0t I=%b S=%b Y=%b", $time, I, S, Y);
        
        I = 4'b1010; S = 2'b00; #10;
        I = 4'b1010; S = 2'b01; #10;
        I = 4'b1010; S = 2'b10; #10;
        I = 4'b1010; S = 2'b11; #10;
        
        $finish;
    end
endmodule
```

---

## Chapter 4 Summary - Key Concepts:

1. **Combinational Circuits**: Outputs depend only on current inputs

2. **Analysis**: Given circuit → find function (truth table/equations)

3. **Design**: Given specification → create circuit

4. **Half Adder**: S = A⊕B, C = A·B

5. **Full Adder**: S = A⊕B⊕Cin, Cout = A·B + (A⊕B)·Cin

6. **Ripple Carry Adder**: Chain full adders, slow but simple

7. **BCD Adder**: Add 6 when sum > 9 or carry generated

8. **Multiplier**: Array of AND gates and adders

9. **Comparator**: Compares magnitudes, outputs A>B, A=B, A<B

10. **Decoder**: n inputs → 2ⁿ outputs (one active)

11. **Encoder**: 2ⁿ inputs → n outputs (encodes position)

12. **Priority Encoder**: Handles multiple active inputs

13. **Multiplexer**: Selects one of many inputs, 2ⁿ inputs + n select → 1 output

14. **MUX for Functions**: Can implement any Boolean function

15. **HDL**: Gate-level, dataflow, behavioral, structural modeling

---

## Practice Problems:

1. Design a circuit that outputs 1 when a 3-bit number is prime
2. Analyze: F = (A⊕B)·C + A'·B
3. Design a 4-bit adder-subtractor with overflow detection
4. Implement F(A,B,C,D) = Σ(0,3,5,7,9,11,13,15) using:
   a) 3-to-8 decoder
   b) 8-to-1 multiplexer
5. Design a 3-bit priority encoder with valid output
6. Write Verilog for a 2-to-4 decoder with enable
7. Design a circuit to convert Gray code to binary (3 bits)
8. Implement a 4-bit magnitude comparator
9. Design a BCD to Excess-3 converter
10. Write testbench for a full adder

---

## Tips for Test Success:

1. **Know your truth tables**: Half adder, full adder, basic gates
2. **Practice K-maps**: Speed is important for objective tests
3. **Memorize key equations**: XOR, full adder, decoder, MUX
4. **Understand don't-cares**: When to use them, how they help
5. **Know conversions**: Binary, BCD, Gray code, Excess-3
6. **Practice circuit analysis**: Work backwards from outputs
7. **Understand cascading**: How to expand decoders, MUXes, comparators
8. **HDL basics**: Know assign, always, if-else, case statements
9. **Time management**: Don't spend too long on one problem
10. **Check your work**: Verify with simple test cases

Good luck on your test!
