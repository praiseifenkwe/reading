# CSC 313 Quick Reference Guide - Chapters 1-4

## Number Systems & Conversions

### Binary to Decimal
(1101)₂ = 1×2³ + 1×2² + 0×2¹ + 1×2⁰ = 8+4+0+1 = 13

### Decimal to Binary
Divide by 2, record remainders bottom-to-top

### Hex/Octal Shortcuts
- 4 binary bits = 1 hex digit
- 3 binary bits = 1 octal digit

### Hex Table
| Hex | Binary | Decimal |
|-----|--------|---------|
| A   | 1010   | 10      |
| B   | 1011   | 11      |
| C   | 1100   | 12      |
| D   | 1101   | 13      |
| E   | 1110   | 14      |
| F   | 1111   | 15      |

---

## Complements & Signed Numbers

### 1's Complement
Flip all bits: 1011 → 0100

### 2's Complement
Flip all bits and add 1: 1011 → 0100 + 1 = 0101

### 2's Complement Range
n-bit: -2^(n-1) to +2^(n-1) - 1
- 4-bit: -8 to +7
- 8-bit: -128 to +127

### Subtraction Using 2's Complement
A - B = A + (2's complement of B)

---

## Binary Codes

### BCD (Binary Coded Decimal)
Each decimal digit → 4 bits
395 = 0011 1001 0101

### Gray Code
Only one bit changes between consecutive numbers
Used in K-maps

### ASCII
7-bit character code
- 'A' = 65 (1000001)
- '0' = 48 (0110000)

---

## Boolean Algebra - Key Theorems

### Basic Laws
- A + 0 = A
- A · 1 = A
- A + 1 = 1
- A · 0 = 0
- A + A = A
- A · A = A
- A + A' = 1
- A · A' = 0
- (A')' = A

### DeMorgan's Theorems (CRITICAL!)
- (A + B)' = A' · B'
- (A · B)' = A' + B'

### Absorption
- A + A·B = A
- A·(A + B) = A
- A + A'·B = A + B

### Consensus
- A·B + A'·C + B·C = A·B + A'·C

---

## Canonical Forms

### Minterms (m)
Product terms where function = 1
F = Σ(1,3,5,7) = m₁ + m₃ + m₅ + m₇

### Maxterms (M)
Sum terms where function = 0
F = Π(0,2,4,6) = M₀ · M₂ · M₄ · M₆

### Relationship
Σ(1,3,5,7) = Π(0,2,4,6) (same function!)

---

## K-Map Rules

### Grouping
- Sizes: 1, 2, 4, 8, 16 (powers of 2 only!)
- Make groups as LARGE as possible
- Groups can overlap
- Edges wrap around (top-bottom, left-right)
- Corners are adjacent in 4-variable maps

### Gray Code Order
- 2-var: 00, 01, 11, 10
- 4-var rows: 00, 01, 11, 10
- 4-var cols: 00, 01, 11, 10

### Don't-Cares (X)
- Include in groups if helpful
- Don't create groups just for X's
- Goal: maximize group size

### Reading Groups
- Variable doesn't change → keep it
- Variable changes → eliminate it
- Always 0 → use complement (A')
- Always 1 → use normal (A)

---

## XOR Properties (MEMORIZE!)

- A ⊕ 0 = A
- A ⊕ 1 = A'
- A ⊕ A = 0
- A ⊕ A' = 1
- A ⊕ B = A'·B + A·B'
- A ⊕ B ⊕ C = 1 when ODD number of 1s

---

## Gate Implementations

### NAND-NAND
Implements SOP directly
F = A·B + C·D → Use NAND gates

### NOR-NOR
Implements POS directly
F = (A+B)·(C+D) → Use NOR gates

### Universal Gates
- NAND can implement AND, OR, NOT
- NOR can implement AND, OR, NOT

---

## Combinational Circuits

### Half Adder
- S = A ⊕ B
- C = A · B

### Full Adder
- S = A ⊕ B ⊕ Cin
- Cout = A·B + A·Cin + B·Cin
- Alternative: Cout = A·B + (A⊕B)·Cin

### BCD Adder
Add 6 (0110) when:
- Sum > 9, OR
- Carry out = 1

### 2×2 Multiplier
4 AND gates + adders
Result is 4 bits

---

## MSI Components

### Decoder (n-to-2ⁿ)
- n inputs → 2ⁿ outputs
- Only ONE output active
- Each output = minterm
- Example: 3-to-8 decoder

### Encoder (2ⁿ-to-n)
- 2ⁿ inputs → n outputs
- Encodes position to binary
- Priority encoder handles multiple inputs

### Multiplexer (2ⁿ-to-1)
- 2ⁿ data inputs
- n select inputs
- 1 output
- Selects one input to route to output
- Can implement ANY Boolean function!

### Comparator
Compares two numbers
- Outputs: A>B, A=B, A<B
- Can cascade for larger numbers

---

## MUX Function Implementation

### Method 1: Direct (n vars, 2ⁿ-to-1 MUX)
- Variables → select lines
- Function values → data inputs

### Method 2: Reduced (n vars, 2ⁿ⁻¹-to-1 MUX)
- n-1 variables → select lines
- Last variable used in data inputs
- Data inputs: 0, 1, var, or var'

---

## Verilog Basics

### Operators
- & (AND)
- | (OR)
- ~ (NOT)
- ^ (XOR)
- ~^ or ^~ (XNOR)

### Dataflow
```verilog
assign Y = A & B | C;
```

### Behavioral
```verilog
always @(A, B)
begin
    if (A > B)
        Y = 1;
    else
        Y = 0;
end
```

---

## Common Mistakes to Avoid

1. ❌ Forgetting Gray code order in K-maps
2. ❌ Not wrapping around edges in K-maps
3. ❌ Wrong group sizes (must be powers of 2)
4. ❌ Confusing minterms (Σ) with maxterms (Π)
5. ❌ Forgetting to add 6 in BCD addition
6. ❌ Wrong 2's complement range
7. ❌ Applying DeMorgan's incorrectly
8. ❌ Not using don't-cares to simplify
9. ❌ Confusing encoder and decoder
10. ❌ Wrong MUX select line count

---

## Test-Taking Strategy

1. **Read carefully**: Understand what's being asked
2. **Show work**: Partial credit is possible
3. **Check units**: Binary, decimal, hex?
4. **Verify**: Test your answer with simple case
5. **Time management**: Don't get stuck on one problem
6. **K-maps**: Draw carefully, use ruler if needed
7. **Truth tables**: Be systematic, don't skip rows
8. **Simplify**: Always look for simplification opportunities
9. **Label clearly**: Especially in circuit diagrams
10. **Stay calm**: You've got this!

---

## Formula Sheet

### Number Systems
- Binary to Decimal: Σ(bit × 2^position)
- 2's Complement: Flip bits + 1
- Range (n-bit 2's comp): -2^(n-1) to 2^(n-1)-1

### Boolean Algebra
- DeMorgan's: (A+B)' = A'·B', (A·B)' = A'+B'
- XOR: A⊕B = A'·B + A·B'

### Adders
- Half Adder: S=A⊕B, C=A·B
- Full Adder: S=A⊕B⊕Cin, Cout=A·B+(A⊕B)·Cin

### MSI
- Decoder: n inputs, 2ⁿ outputs
- Encoder: 2ⁿ inputs, n outputs
- MUX: 2ⁿ data + n select → 1 output

Good luck! 🎓
