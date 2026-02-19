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
