# Chapter 3: Gate-Level Minimization

## 3.1 Introduction

### Why Minimize?
- Reduce number of gates → Lower cost
- Reduce circuit complexity → Easier to build
- Reduce propagation delay → Faster circuits
- Reduce power consumption → Better efficiency

### Minimization Goals:
1. Minimize number of literals
2. Minimize number of terms
3. Minimize number of gate levels

### Methods:
- **Algebraic manipulation**: Using Boolean theorems (tedious, no systematic approach)
- **Karnaugh Maps (K-maps)**: Visual/graphical method (up to 6 variables)
- **Quine-McCluskey**: Tabular method (any number of variables, computer-friendly)

---

## 3.2 The Map Method (Karnaugh Maps)

### What is a K-Map?
- Visual representation of truth table
- Diagram made up of squares (cells)
- Each cell represents a minterm
- Adjacent cells differ by only ONE variable
- Uses Gray code ordering

### Two-Variable K-Map:

```
     B
    0  1
A 0 │m₀│m₁│
  1 │m₂│m₃│
```

**Example: F(A,B) = Σ(1,3) = A'·B + A·B**
```
     B
    0  1
A 0 │0 │1 │
  1 │0 │1 │
```
Simplification: Group the two 1s vertically → F = B

### Three-Variable K-Map:

```
      BC
     00 01 11 10
A 0 │m₀│m₁│m₃│m₂│
  1 │m₄│m₅│m₇│m₆│
```

**Important**: Column order is 00, 01, 11, 10 (Gray code!)

**Example: F(A,B,C) = Σ(0,2,4,6)**
```
      BC
     00 01 11 10
A 0 │1 │0 │0 │1 │
  1 │1 │0 │0 │1 │
```
Simplification: Group four 1s vertically → F = C'

### K-Map Simplification Rules:

1. **Group adjacent 1s**:
   - Groups must be rectangular
   - Group sizes: 1, 2, 4, 8, 16 (powers of 2)
   - Larger groups = simpler terms

2. **Adjacency**:
   - Horizontal neighbors
   - Vertical neighbors
   - Edges wrap around (top-bottom, left-right)
   - Corners are adjacent

3. **Grouping Strategy**:
   - Make groups as large as possible
   - Use minimum number of groups
   - Each 1 must be in at least one group
   - Groups can overlap

4. **Reading Groups**:
   - Variables that don't change in group → keep
   - Variables that change → eliminate
   - If variable is always 0 → use complement
   - If variable is always 1 → use normal form

### Three-Variable Examples:

**Example 1: F(A,B,C) = Σ(3,4,6,7)**
```
      BC
     00 01 11 10
A 0 │0 │0 │1 │0 │  Group 1: m₃,m₇ → A·B
  1 │1 │0 │1 │1 │  Group 2: m₄,m₆ → A·C'
```
F = A·B + A·C'

**Example 2: F(A,B,C) = Σ(0,1,2,3,7)**
```
      BC
     00 01 11 10
A 0 │1 │1 │1 │1 │  Group 1: m₀,m₁,m₂,m₃ → A'
  1 │0 │0 │1 │0 │  Group 2: m₃,m₇ → B·C
```
F = A' + B·C

---

## 3.3 Four-Variable K-Map

### Four-Variable K-Map Layout:

```
       CD
      00 01 11 10
AB 00│m₀│m₁│m₃│m₂│
   01│m₄│m₅│m₇│m₆│
   11│m₁₂│m₁₃│m₁₅│m₁₄│
   10│m₈│m₉│m₁₁│m₁₀│
```

**Note**: Both rows and columns use Gray code ordering!

### Adjacency in 4-Variable K-Map:
- Horizontal neighbors
- Vertical neighbors
- Top row adjacent to bottom row
- Left column adjacent to right column
- Four corners are adjacent!

### Example 1: F(A,B,C,D) = Σ(0,1,2,5,8,9,10)

```
       CD
      00 01 11 10
AB 00│1 │1 │0 │1 │  Group 1: m₀,m₁,m₂ (size 2+1)
   01│0 │1 │0 │0 │  Group 2: m₀,m₂,m₈,m₁₀ (size 4)
   11│0 │0 │0 │0 │  Group 3: m₁,m₅ (size 2)
   10│1 │1 │0 │1 │
```

Groups:
- m₀,m₂,m₈,m₁₀ (corners + middle) → B'·D'
- m₀,m₁ → A'·B'·C'
- m₈,m₉,m₁₀ → A·B'

F = B'·D' + A'·B'·C' + A·B'
Can be simplified further: F = B'·D' + A'·B'·C'

### Example 2: F(A,B,C,D) = Σ(0,2,5,7,8,10,13,15)

```
       CD
      00 01 11 10
AB 00│1 │0 │0 │1 │  Group 1: m₀,m₂,m₈,m₁₀ → B'·D'
   01│0 │1 │1 │0 │  Group 2: m₅,m₇,m₁₃,m₁₅ → B·D
   11│0 │1 │1 │0 │
   10│1 │0 │0 │1 │
```

F = B'·D' + B·D = B ⊕ D (XOR function!)

### Example 3: Larger Groups

```
       CD
      00 01 11 10
AB 00│1 │1 │1 │1 │  All of row 00 → A'·B'
   01│1 │1 │0 │0 │  Left half of row 01 → A'·B·C'
   11│0 │0 │0 │0 │
   10│0 │0 │0 │0 │
```

F = A'·B' + A'·B·C' = A'·(B' + B·C') = A'·(B' + C')

### Prime Implicants:

**Definitions:**
- **Implicant**: A product term that implies the function (any group of 1s)
- **Prime Implicant**: An implicant that cannot be combined with another to eliminate a variable (maximal group)
- **Essential Prime Implicant**: A prime implicant that covers at least one minterm not covered by any other prime implicant

**Strategy:**
1. Find all prime implicants
2. Identify essential prime implicants (must include)
3. Select minimum number of remaining prime implicants to cover all 1s

### Example with Prime Implicants:

F(A,B,C,D) = Σ(0,2,3,5,7,8,10,11,14,15)

```
       CD
      00 01 11 10
AB 00│1 │0 │1 │1 │
   01│0 │1 │1 │0 │
   11│0 │0 │1 │1 │
   10│1 │0 │1 │1 │
```

Prime Implicants:
- m₀,m₂,m₈,m₁₀ → B'·D' (essential)
- m₃,m₇,m₁₁,m₁₅ → C·D (essential)
- m₂,m₃ → A'·B'·C
- m₁₀,m₁₁,m₁₄,m₁₅ → A·C

Minimal: F = B'·D' + C·D + A·C

---

## 3.4 Product-of-Sums Simplification

### POS from K-Map:
Instead of grouping 1s, group 0s to get F', then complement to get F in POS form.

### Procedure:
1. Mark 0s in K-map
2. Group 0s (same rules as grouping 1s)
3. Read groups to get F' in SOP form
4. Apply DeMorgan's to get F in POS form

### Example: F(A,B,C,D) = Σ(0,1,2,5,8,9,10)

First, find which minterms are 0:
0s are at: 3,4,6,7,11,12,13,14,15

```
       CD
      00 01 11 10
AB 00│1 │1 │0 │1 │
   01│0 │1 │0 │0 │
   11│0 │0 │0 │0 │
   10│1 │1 │0 │1 │
```

Group 0s:
- m₃,m₇,m₁₁,m₁₅ → C·D
- m₄,m₆,m₁₂,m₁₄ → B·D'
- m₁₁,m₁₅ (already covered)

F' = C·D + B·D'
F = (C·D + B·D')'
F = (C·D)' · (B·D')'  [DeMorgan's]
F = (C'+D') · (B'+D)  [DeMorgan's]

This is POS form!

### SOP vs POS:
- Use SOP when function has fewer 1s
- Use POS when function has fewer 0s
- Both give equivalent functions
- Choose form with fewer terms

### Maxterm Notation:
F = Π(3,4,6,7,11,12,13,14,15)
This means F = M₃·M₄·M₆·M₇·M₁₁·M₁₂·M₁₃·M₁₄·M₁₅

---

## 3.5 Don't-Care Conditions

### What are Don't-Cares?
- Input combinations that will never occur, OR
- Output values that don't matter for certain inputs
- Denoted by X or d or φ
- Can be treated as either 0 or 1 (whichever helps minimization)

### Sources of Don't-Cares:

1. **Invalid Input Combinations**:
   - BCD code: 1010-1111 never occur
   - Example: BCD digit input (only 0-9 valid, 10-15 are don't-cares)

2. **Unspecified Outputs**:
   - Designer doesn't care about output for certain inputs
   - Can choose output to simplify circuit

### Using Don't-Cares in K-Maps:

**Strategy:**
- Mark don't-cares with X in K-map
- Include X in groups if it helps make larger groups
- Don't include X if it doesn't help
- Goal: Maximize group sizes to minimize expression

### Example 1: F(A,B,C,D) = Σ(1,3,7,11,15), d(0,2,5)

```
       CD
      00 01 11 10
AB 00│X │1 │1 │X │  Group 1: m₁,m₃,m₅,m₇ → B·C
   01│X │0 │1 │0 │  (include X at m₅)
   11│0 │0 │1 │0 │
   10│0 │0 │0 │0 │
```

Without don't-cares: F = A'·B·C + B·C·D
With don't-cares: F = B·C (much simpler!)

### Example 2: BCD to Seven-Segment

BCD inputs: 0000-1001 (valid)
Don't-cares: 1010-1111 (invalid BCD)

For segment 'a': F(A,B,C,D) = Σ(0,2,3,5,6,7,8,9), d(10,11,12,13,14,15)

```
       CD
      00 01 11 10
AB 00│1 │0 │1 │1 │  Can make very large groups
   01│0 │1 │1 │1 │  using don't-cares!
   11│X │X │X │X │
   10│1 │1 │X │X │
```

Groups (using X's strategically):
- Large group including many X's → simplified expression

F = A + C + B·D' + B'·D

### Example 3: Multiple Don't-Cares

F(A,B,C,D) = Σ(0,1,5,7), d(10,11,14,15)

```
       CD
      00 01 11 10
AB 00│1 │1 │0 │0 │  Group 1: m₀,m₁ → A'·B'·C'
   01│0 │1 │1 │0 │  Group 2: m₁,m₅ → A'·C'·D
   11│0 │0 │X │X │  Group 3: m₅,m₇ → A'·B·D
   10│X │X │X │X │  Or use X's differently
```

Best solution (using X's):
- m₀,m₁,m₁₀,m₁₁ → C'·D' (include X's)
- m₅,m₇,m₁₅ → B·D (include one X)

F = C'·D' + B·D

### Important Notes:
- Don't-cares are optional in groups
- Use them to make groups larger
- Don't create extra groups just for don't-cares
- In truth table notation: F(A,B,C,D) = Σ(minterms) + d(don't-cares)

---

## 3.6 NAND and NOR Implementation

### Why NAND and NOR?
- Universal gates (can implement any function)
- Easier to fabricate than AND/OR gates
- Faster in some technologies
- NAND is most common in TTL
- NOR is common in CMOS

### Two-Level NAND Implementation:

#### NAND-NAND Implementation:
Implements SOP expressions directly

**Principle:**
- F = A·B + C·D (SOP form)
- F = ((A·B + C·D)')' (double complement)
- F = ((A·B)' · (C·D)')' (DeMorgan's)
- This is NAND-NAND form!

**Procedure:**
1. Get function in SOP form
2. Draw AND-OR circuit
3. Replace all gates with NAND gates
4. Add inverters for single literals if needed

**Example: F = A·B + C·D'**

```
Original (AND-OR):
A ──┐
    AND──┐
B ──┘    │
         OR── F
C ──┐    │
    AND──┘
D'──┘

NAND-NAND:
A ──┐
    NAND──┐
B ──┘     │
          NAND── F
C ──┐     │
    NAND──┘
D ──NOT
```

### Two-Level NOR Implementation:

#### NOR-NOR Implementation:
Implements POS expressions directly

**Principle:**
- F = (A+B)·(C+D) (POS form)
- F = ((A+B)·(C+D)')' (double complement)
- F = ((A+B)' + (C+D)')' (DeMorgan's)
- This is NOR-NOR form!

**Procedure:**
1. Get function in POS form
2. Draw OR-AND circuit
3. Replace all gates with NOR gates
4. Add inverters for single literals if needed

**Example: F = (A+B)·(C+D')**

```
Original (OR-AND):
A ──┐
    OR──┐
B ──┘   │
        AND── F
C ──┐   │
    OR──┘
D'──┘

NOR-NOR:
A ──┐
    NOR──┐
B ──┘    │
         NOR── F
C ──┐    │
    NOR──┘
D ──NOT
```

### Multilevel NAND Circuits:

**Conversion Rules:**
1. Replace AND gates with NAND gates
2. Replace OR gates with NAND gates with inverted inputs
3. Check for double inversions and cancel them

**Example: F = A·(B+C·D)**

```
Step 1: Draw with AND/OR gates
Step 2: Convert to NAND
- Inner OR becomes NAND with inverted inputs
- Outer AND becomes NAND
```

### Multilevel NOR Circuits:

**Conversion Rules:**
1. Replace OR gates with NOR gates
2. Replace AND gates with NOR gates with inverted inputs
3. Check for double inversions and cancel them

---

## 3.7 Other Two-Level Implementations

### Eight Possible Two-Level Forms:

Using AND, OR, NAND, NOR gates, we can create 8 different two-level implementations:

1. **AND-OR** (SOP)
2. **OR-AND** (POS)
3. **NAND-NAND** (SOP equivalent)
4. **NOR-NOR** (POS equivalent)
5. **OR-NAND**
6. **AND-NOR**
7. **NOR-OR**
8. **NAND-AND**

### Degenerate Forms:

Some forms require inverters at inputs or outputs:

#### 1. AND-OR (Standard SOP):
- F = A·B + C·D
- Most intuitive form

#### 2. OR-AND (Standard POS):
- F = (A+B)·(C+D)
- Dual of AND-OR

#### 3. NAND-NAND:
- Equivalent to AND-OR
- F = ((A·B)'·(C·D)')'

#### 4. NOR-NOR:
- Equivalent to OR-AND
- F = ((A+B)'+(C+D)')'

#### 5. OR-NAND:
- Implements complement of SOP
- F' in SOP form → F in OR-NAND
- Example: If F' = A·B + C·D, then F = (A+B)'·(C+D)'

#### 6. AND-NOR:
- Implements complement of POS
- F' in POS form → F in AND-NOR
- Example: If F' = (A+B)·(C+D), then F = (A·B)'+(C·D)'

#### 7. NOR-OR:
- Requires inverters at inputs
- Less commonly used

#### 8. NAND-AND:
- Requires inverters at inputs
- Less commonly used

### Conversion Procedure:

**To implement F in any form:**

1. **For AND-OR**: Express F in SOP
2. **For OR-AND**: Express F in POS
3. **For NAND-NAND**: Express F in SOP, convert to NAND
4. **For NOR-NOR**: Express F in POS, convert to NOR
5. **For OR-NAND**: Express F' in SOP, use OR-NAND
6. **For AND-NOR**: Express F' in POS, use AND-NOR

### Example: F(A,B,C) = Σ(1,2,3,5,7)

**Step 1: Simplify using K-map**
```
      BC
     00 01 11 10
A 0 │0 │1 │1 │1 │
  1 │0 │1 │1 │0 │
```
F = A'·B + A·B·C + A'·C = A'·B + A'·C + A·B·C

**Step 2: Different implementations**

**AND-OR (SOP):**
F = A'·B + A'·C + A·B·C

**NAND-NAND:**
Same as AND-OR but with NAND gates

**OR-AND (POS):**
First find F in POS form by grouping 0s:
F' = A·B' + B'·C' + A'·B'·C'
F = (A'+B)·(B+C)·(A+B+C)

**NOR-NOR:**
Same as OR-AND but with NOR gates

### Wired Logic:

**Wired-AND:**
- Connect outputs of gates with open-collector
- Implements AND function
- Used with TTL

**Wired-OR:**
- Connect outputs of gates
- Implements OR function
- Used with ECL

### Non-Degenerate Forms:

Forms that don't require input inverters:
- AND-OR
- OR-AND
- NAND-NAND
- NOR-NOR

These are preferred for practical implementation.

---

## 3.8 Exclusive-OR Function

### XOR Properties (Review):

1. **A ⊕ 0 = A** (Identity)
2. **A ⊕ 1 = A'** (Complement)
3. **A ⊕ A = 0** (Self-inverse)
4. **A ⊕ A' = 1** (Complement)
5. **A ⊕ B = B ⊕ A** (Commutative)
6. **(A ⊕ B) ⊕ C = A ⊕ (B ⊕ C)** (Associative)
7. **A ⊕ B = A'·B + A·B'** (SOP form)
8. **A ⊕ B = (A+B)·(A'+B')** (POS form)

### Multi-Variable XOR:

**Three Variables:**
A ⊕ B ⊕ C = (A ⊕ B) ⊕ C

Truth table:
```
A B C | A⊕B⊕C
------|-------
0 0 0 |   0
0 0 1 |   1
0 1 0 |   1
0 1 1 |   0
1 0 0 |   1
1 0 1 |   0
1 1 0 |   0
1 1 1 |   1
```

**Pattern**: Output = 1 when ODD number of inputs are 1

### Odd and Even Functions:

**Odd Function:**
- F = A ⊕ B ⊕ C ⊕ ... (XOR of all variables)
- Output = 1 for odd number of 1s
- Used for odd parity generation

**Even Function:**
- F = (A ⊕ B ⊕ C ⊕ ...)' (XNOR of all variables)
- Output = 1 for even number of 1s
- Used for even parity generation

### XOR Implementation:

**Using NAND gates:**
A ⊕ B requires 4 NAND gates:
```
A ──NAND──┐
    │     NAND── A⊕B
B ──NAND──┘
│         │
└─NAND────┘
```

**Using AND-OR:**
A ⊕ B = A'·B + A·B'

### Parity Generation:

**Even Parity:**
- Add parity bit to make total number of 1s even
- Parity bit = A ⊕ B ⊕ C ⊕ ...

**Odd Parity:**
- Add parity bit to make total number of 1s odd
- Parity bit = (A ⊕ B ⊕ C ⊕ ...)'

**Example: 3-bit data with even parity**
- Data: 101 (two 1s - even)
- Parity bit: 0
- Transmitted: 1010

- Data: 110 (two 1s - even)
- Parity bit: 0
- Transmitted: 1100

- Data: 111 (three 1s - odd)
- Parity bit: 1
- Transmitted: 1111

### Parity Checking:

**Receiver:**
- XOR all received bits (including parity)
- Result = 0: No error detected
- Result = 1: Error detected

**Limitation:**
- Detects odd number of errors
- Cannot detect even number of errors
- Cannot correct errors

### XOR Applications:

1. **Arithmetic**: Half adder, full adder
2. **Parity**: Generation and checking
3. **Comparator**: A ⊕ B = 0 when A = B
4. **Controlled Inverter**: A ⊕ 1 = A'
5. **Programmable Inverter**: A ⊕ B (B controls inversion)

---

## 3.9 Hardware Description Language (HDL)

### What is HDL?

Hardware Description Language is a specialized language for:
- Describing digital circuits
- Simulating circuit behavior
- Synthesizing hardware from description

### Two Major HDLs:

1. **Verilog**: C-like syntax, widely used in industry
2. **VHDL**: Ada-like syntax, used in aerospace/defense

### Levels of Abstraction:

1. **Behavioral Level**: Describes what circuit does (high-level)
2. **Dataflow Level**: Describes how data flows (medium-level)
3. **Structural Level**: Describes gate connections (low-level)

### Verilog Basics:

#### Module Structure:
```verilog
module module_name (input_list, output_list);
    // Declarations
    input ...;
    output ...;
    
    // Circuit description
    
endmodule
```

#### Example 1: Simple Gate (Behavioral):
```verilog
module and_gate (A, B, F);
    input A, B;
    output F;
    
    assign F = A & B;
endmodule
```

#### Example 2: OR Gate:
```verilog
module or_gate (A, B, F);
    input A, B;
    output F;
    
    assign F = A | B;
endmodule
```

#### Example 3: NOT Gate:
```verilog
module not_gate (A, F);
    input A;
    output F;
    
    assign F = ~A;
endmodule
```

### Verilog Operators:

**Logic Operators:**
- `&` : AND
- `|` : OR
- `~` : NOT
- `^` : XOR
- `~^` or `^~` : XNOR

**Example: Complex Function**
```verilog
module complex_function (A, B, C, D, F);
    input A, B, C, D;
    output F;
    
    assign F = (A & B) | (C & ~D);
endmodule
```

### Dataflow Modeling:

Uses continuous assignment with `assign` keyword.

**Example: 2-to-1 Multiplexer**
```verilog
module mux2to1 (A, B, S, Y);
    input A, B, S;
    output Y;
    
    assign Y = (S & B) | (~S & A);
endmodule
```

**Example: Full Adder**
```verilog
module full_adder (A, B, Cin, Sum, Cout);
    input A, B, Cin;
    output Sum, Cout;
    
    assign Sum = A ^ B ^ Cin;
    assign Cout = (A & B) | (B & Cin) | (A & Cin);
endmodule
```

### Structural Modeling:

Describes circuit by instantiating gates and modules.

**Example: Half Adder using Gates**
```verilog
module half_adder (A, B, Sum, Carry);
    input A, B;
    output Sum, Carry;
    
    xor (Sum, A, B);
    and (Carry, A, B);
endmodule
```

**Example: Full Adder using Half Adders**
```verilog
module full_adder_structural (A, B, Cin, Sum, Cout);
    input A, B, Cin;
    output Sum, Cout;
    wire S1, C1, C2;
    
    half_adder HA1 (A, B, S1, C1);
    half_adder HA2 (S1, Cin, Sum, C2);
    or (Cout, C1, C2);
endmodule
```

### Behavioral Modeling:

Uses procedural blocks (`always`, `initial`).

**Example: 4-to-1 Multiplexer**
```verilog
module mux4to1 (I0, I1, I2, I3, S0, S1, Y);
    input I0, I1, I2, I3, S0, S1;
    output reg Y;
    
    always @(I0, I1, I2, I3, S0, S1)
    begin
        case ({S1, S0})
            2'b00: Y = I0;
            2'b01: Y = I1;
            2'b10: Y = I2;
            2'b11: Y = I3;
        endcase
    end
endmodule
```

### Testbenches:

Used to simulate and verify circuits.

**Example: Testbench for AND gate**
```verilog
module and_gate_tb;
    reg A, B;
    wire F;
    
    and_gate UUT (A, B, F);
    
    initial begin
        A = 0; B = 0; #10;
        A = 0; B = 1; #10;
        A = 1; B = 0; #10;
        A = 1; B = 1; #10;
        $finish;
    end
endmodule
```

### Key HDL Concepts:

1. **Concurrent Execution**: All `assign` statements execute simultaneously
2. **Sensitivity List**: Specifies when `always` block executes
3. **Blocking vs Non-blocking**: 
   - `=` : Blocking assignment
   - `<=` : Non-blocking assignment
4. **Synthesis**: Converting HDL to actual hardware

---

## Chapter 3 Summary - Key Concepts:

1. **K-Map Rules**:
   - Group sizes: 1, 2, 4, 8, 16 (powers of 2)
   - Make groups as large as possible
   - Edges and corners wrap around
   - Use Gray code ordering

2. **Four-Variable K-Map**: 4×4 grid with Gray code on both axes

3. **POS Minimization**: Group 0s instead of 1s

4. **Don't-Cares**: Use X's to make larger groups, but only if helpful

5. **NAND-NAND**: Implements SOP directly

6. **NOR-NOR**: Implements POS directly

7. **XOR Properties**:
   - A ⊕ 0 = A
   - A ⊕ 1 = A'
   - A ⊕ A = 0
   - Associative and commutative

8. **Parity**: XOR of all bits for odd parity

9. **HDL**: Describes hardware at different abstraction levels

---

## Practice Problems:

1. Minimize using K-map: F(A,B,C,D) = Σ(0,1,2,5,6,7,8,9,14)
2. Find POS form: F(A,B,C,D) = Σ(1,3,5,7,9,15)
3. Minimize with don't-cares: F = Σ(1,3,5,7), d(2,6,10,14)
4. Implement F = A·B + C using only NAND gates
5. Implement F = (A+B)·C using only NOR gates
6. Design 3-bit even parity generator
7. Write Verilog for: F = A'·B + B·C'
