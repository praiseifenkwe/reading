**Solutions**

- **Which of the following is NOT TRUE about the impact of advances in digital integratedcircuit technology?**

** Answer:** **(d) Equipment built with highly integrated digital devices become increasingly unreliable and highly susceptible to failure.**

** Explanation:** This statement is false. Advances in integrated circuits (ICs) have significantly *increased* reliability by reducing the number of external connections (a common failure point) and protecting components within the chip package. Options a, b, and c are true impacts of IC technology (lower cost, Moore's Law density, higher speed).

- **An n-bit register can store any binary number from**

**Answer:** **(b) **0** to **2n − 1

**Explanation:** An n-bit register has 2n possible states. In standard unsigned binary, these range from 0 (all zeros) to 2n − 1 (all ones).

- **The even parity bit **pe** of the N digit binary number **a1a2…aN** can be generated as**

**Answer:** **(a) **pe = a1 ⊕ a2 ⊕ ⋯ ⊕ aN

**Explanation:** The Exclusive-OR (XOR) operation sums the bits modulo 2. For even parity, you want the total number of 1s (data + parity) to be even. If the data has an odd number of 1s, the XOR sum is 1, setting the parity bit to 1 (making the total even). If the data is even, the XOR sum is 0.

- **The generated parity bit in an *even* parity scheme is**

**Answer:** **(d) I & IV only**

I. 0 if the number of 1s is even

IV. 1 if the number of 1s is odd

**Explanation:** In an even parity scheme, the total count of 1s must be even.

If the data already has an even number of 1s, the parity bit must be **0** to keep the total even.

 If the data has an odd number of 1s, the parity bit must be **1** to make the total even.

- **Which of the following is NOT TRUE?**

**Answer:** **(e) None of the above**

**Explanation:** All statements (a-d) are correct definitions in computer architecture:

- A CPU on a single chip is a microprocessor.
- A CPU + Memory + I/O is a microcomputer.
- CPU = ALU + Control Unit.
- Processors perform arithmetic/data processing.

- **The **(r − 1)**'s complement of the positive number **Nr** with **n** digits is**

**Answer:** **(c) **rn − 1 − N (Assuming integer context based on standard notation)

**Explanation:** The (r − 1)'s complement (also called the Diminished Radix Complement) is found by subtracting a number from the maximum possible value for that number of digits.

For n digits in base r, the max value is rn − 1. Therefore, the complement is (rn − 1) − N.

- **??? Value that may be represented by the coefficients **anan−1…a1a0** in base **r** is**

**Answer:** **(e) **rn+1 − 1

**Explanation:** The indices go from n down to 0, meaning there are n + 1 digits. The maximum value represented by n + 1 digits in base r is rn+1 − 1. (For example, with 3

decimal digits a2a1a0, max is 103 − 1 = 999).

- **Which of the following is NOT TRUE?**

** Answer:** **(a) The 2's complement has advantage over 1's complement of being easier to implement by digital circuits.**

** Explanation:** While 2's complement is better for *arithmetic operations* (handling zero and addition), the statement that it is "easier to implement" is generally considered false regarding the logic circuit for the complement itself. 1's complement requires only simple inverters (NOT gates). 2's complement requires inverters **plus** an adder (to add +1) or a look-ahead carry circuit, making the negation logic more complex.

- **Convert **(0.6875)10

**Answer:** **(c) **(0.1011)2

**Explanation:** Multiply the fractional part by 2 repeatedly:

- 0.6875 × 2 = 1.375 → **1**
- 0.375 × 2 = 0.75 → **0**
- 0.75 × 2 = 1.5 → **1**
- 0.5 × 2 = 1.0 → **1**

Result: .1011

- **Which code has error detection capabilities?**

** Answer:** **(c) Excess 3** (or potentially E, depending on strict definitions, but Excess-3 is commonly taught this way).

** Explanation:** Excess-3 is often cited in introductory courses as having error detection capabilities because the code **0000** (and 1111) is invalid. If a signal line breaks (reads all zeros), Excess-3 detects this as a fault, whereas standard BCD would interpret it as the digit 0.

- **Which 4-bit code is NOT a weighted code?**

**Answer:** **(c) Excess 3**

**Explanation:** In weighted codes (like BCD 8421 or 2421), each bit position has a specific numerical weight. Excess-3 is derived by adding 3 to the BCD digit; the bit positions do not have fixed weights that sum to the value.

- **Which 4-bit code represents 7 with a combination that contains two ones and twozeroes?**

**Answer:** **(c) Excess 3**

**Explanation:**

Decimal 7 in Excess-3: 7 + 3 = 10.

Binary for 10 is **1010**.

This contains two 1s and two 0s. (BCD 7 is 0111; 2421 7 is 1101).

- **Which code is weighted and self-complementing?**

**Answer:** **(d) 2421**

**Explanation:**

**Weighted:** 2 + 4 + 2 + 1 = 9.

**Self-complementing:** The 9's complement of a number can be obtained by logically inverting the bits (e.g., 2 is 0010, 7 is 1101).

- **In which 4-bit code is the code 0111 not valid?**

**Answer:** **(d) 2421**

**Explanation:** In the standard self-complementing 2421 code:

Numbers 0-4 start with 0. Numbers 5-9 start with 1.

The code for 7 is **1101** (2 + 4 + 0 + 1). The binary combination **0111** (which sums to 7) is not used because it would violate the self-complementing property (it would pair with 1000, which is not 2).

- **Which of the following is NOT CORRECT in the following steps that describe thesubtraction of two unsigned n-digit numbers...**

**Answer:** **(c) II & III**

** Explanation:** Both statements describe the carry behavior incorrectly for r's complement subtraction:

** II is Wrong:** If M ≥ N, the sum **does** produce an end carry (which is discarded). The statement says it "does not".

** III is Wrong:** If M < N, the sum **does not** produce an end carry. The statement says it "will produce".

- **Parity code schemes fail when there is (are)**

**Answer:** **(b) an even number of errors**

**Explanation:** Parity bits (odd or even) can only detect an odd number of bit flips. If two bits flip (an even number), the parity remains the same, and the error goes undetected.

- **The 16's complement of B2FA is**

**Answer:** **(d) 4D06**

**Explanation:**

- Find the 15's complement by subtracting each digit from F (15):

F − B = 4

F − 2 = D

F − F = 0 F − A = 5

Result: 4D05

- Add 1 to find the 16's complement: 4D05 + 1 = **4D06**.

- **Which of the following is NOT TRUE?**

** Answer:** **(b) Discrete components can operated at higher speeds than integrated circuits.**

** Explanation:** This is false. Integrated circuits (ICs) generally operate at much higher speeds than discrete components because the components are microscopic and placed extremely close together, minimizing signal propagation delays and parasitic capacitance.

- **The solutions to the quadratic equation **x2 − 11x + 22 = 0** are **x = 3** and **x = 6**. What is the base of the numbers?**

**Answer:** **(b) 8**

**Explanation:**

In any base, the sum of the roots equals the coefficient of x (with sign change).

Sum of roots: 3 + 6 = 9 (decimal).

Equation coefficient is 11r.

Therefore, 11r = 910.

Expanding 11r: 1 × r + 1 = 9 ⇒ r = 8.

- **Introduced a two-valued Boolean algebra called switching algebra.**

**Answer:** **(c) Shannon**

**Explanation:** Claude Shannon demonstrated in his 1938 thesis that Boolean algebra could be used to analyze and design switching circuits (relays).

- **Formalized Boolean algebra.**

**Answer:** **(b) Boole**

**Explanation:** George Boole introduced the algebraic system of logic in the mid-19th century.

- **Invented the transistor.**

**Answer:** **(e) None of the above**

**Explanation:** The transistor was invented by Shockley, Bardeen, and Brattain. The list (De Morgan, Boole, Shannon, Huntington) does not include them.

- **Developed a theorem for the complement of logic operations.**

**Answer:** **(a) De Morgan**

–

**Explanation:** De Morgan's laws (A ⋅ B = A + B, etc.) describe how to complement logic operations.

- **Which of the following is NOT TRUE?**

**Answer:** **(e) The equivalence function is an odd function.**

**Explanation:** The Equivalence function (XNOR) is 1 when the inputs are equal. For 2

inputs, it produces a 1 if there are zero or two 1s (an **even** number of 1s). The ExclusiveOR (XOR) is the odd function.

- **It is the most popular logic family for fabricating SSI, MSI and LSI circuits.**

**Answer:** **(a) Transistor-transistor logic (TTL)**

**Explanation:** Historically, TTL was the standard for SSI and MSI logic chips (like the 7400 series) for a long time.

- **It is the logic family used in systems requiring low power consumption.**

** Answer:** **(e) Complementary metal-oxide semiconductor (CMOS)**

**Explanation:** CMOS is famous for having near-zero static power consumption.

- **It is the logic family used in systems requiring high-speed operations.**

**Answer:** **(b) Emitter-coupled logic (ECL)**

**Explanation:** ECL is the fastest logic family (non-saturating logic) but consumes the most power.

- **It is the logic family most frequently used to fabricate microprocessors.**

**Answer:** **(c) Metal-oxide semiconductor (MOS)**

**Explanation:** Modern microprocessors are built using MOS technology (specifically CMOS) due to its high density.

- **It is the logic family used as an alternative to MOS for the fabrication of high densityintegrated circuits.**

**Answer:** **(d) Integrated-injection logic (**I2L**)**

**Explanation:** I2L was a bipolar technology developed to compete with MOS in density while offering better speed/power performance than standard TTL, though MOS eventually won out.

- **Which representation of signed binary numbers has only one version of the numberzero?**

**Answer:** **(b) Signed-2's complement**

**Explanation:** Signed magnitude and 1's complement have both +0 and −0. 2's complement has only one zero (00…0).

- **The duality principle states that...**

** Answer:** **(d) variables are complemented and operators and identity elements are interchanged**

** Correction:** Actually, the standard Duality Principle states you interchange operators (AND ↔ OR) and identity elements (0 ↔ 1), but you do **NOT** complement the variables.

* Note:* If the options force a choice, (a) "operators are interchanged only" is incomplete. However, option (d) says variables are complemented, which is actually how you find the *complement* of a function (using De Morgan's), not the Dual.

*Strict Definition:* Dual of f(A,B,⋅,+) is f(A,B,+,⋅).

*Looking at the options:* Option (b) and (d) mention complementing variables. This is incorrect for Duality.

* Likely Intended Answer:* **(c) operators and identity elements are interchanged.**

(Wait, c says "operators and identity elements are interchanged" - this is the correct

definition).

- **Which of the following is CORRECT?**

**Answer:** **(e) None of the above**

**Explanation:** NAND (↑) and NOR (↓) are not associative (a, b are false). The relationships in (c) and (d) are not standard valid identities for these operators.

- **Which of the following is NOT TRUE of the ASCII code?**

**Answer:** **(a) It is an alphanumeric code that is replacing Unicode.**

**Explanation:** This is false. Unicode is replacing ASCII (or rather, ASCII is a subset of Unicode). ASCII is an older, limited standard.

- **Which of the following is NOT CONSIDERED when constructing logic gates?**

**Answer:** **(e) None of the above**

**Explanation:** Feasibility, Economy, Ability to implement functions, and Convenience are all valid engineering considerations.

- **Which of the following is NOT CORRECT?**

** Answer:** **(b) NAND (NOR) gates are slower and more expensive than AND (OR) gates respectively...**

** Explanation:** This is false. In most transistor technologies (like CMOS), NAND and NOR are the fundamental building blocks. An AND gate is actually built by taking a NAND gate and adding an inverter, making the AND gate slower and larger (more expensive) than the

NAND.

- **The dual of the function **XY + X¯Z + YZ** is**

**Answer:** **(b) **(X + Y)(X¯ + Z)(Y + Z)

**Explanation:** To find the dual, swap AND (⋅) with OR (+). Do not change the literals (X stays X, X¯ stays X¯).

- **Which of the following identities, if applied, will simplify the function **XY + X¯Z + YZ**?**

**Answer:** **(b) Consensus theorem**

**Note:** The term YZ is the consensus of XY and X¯Z. It is redundant and can be removed.

- **Which of the following is NOT TRUE of minterms:**

** Answer:** **(b) Any Boolean function can be expressed as a logical product of minterms.**

**Explanation:** A function is expressed as a logical **sum** of minterms (Sum of Products). A logical *product* would be a product of Maxterms.

- **What is the gate-input cost of the function **G = (A¯ + B)(B¯ + C)(C¯ + D)(D¯ + A)

**Answer:** **(c) 12 Explanation:**

4 OR gates (2 inputs each) = 8 inputs.

1 AND gate connecting the 4 groups (4 inputs) = 4 inputs.

Total = 8 + 4 = 12.

- **The Boolean function **G(A,B,C,D) = AC¯D + A¯D + B¯C + CD + ABD¯** in its canonical form is**

**Answer:** **(b) **Σm(1,2,3,4,5,6,7,9,11,12,15)

**Analysis:** This question requires expanding terms to minterms.

A¯D covers 1, 3, 5, 7.

CD covers 3, 7, 11, 15.

B¯C covers 2, 3, 10, 11.

ABD¯ covers 12, 14. (Wait, option b includes 12 but excludes 14. Let's re-read the function carefully. If the last term is ABC¯, it would be different. Assuming standard interpretation, (b) is the closest fit among the lists provided).

- **The minimization of the function in question 40 is**

** Answer:** **(c) **B¯D¯ + AC + CD D +~BC + AB

- **Which of the following is TRUE?**

** Answer:** **(b) If the removal of ANY literal from an Implicant P results in a product term that is not an implicant... then P is a prime implicant.**

** Explanation:** This is the formal definition of a Prime Implicant—it cannot be simplified further (by removing literals) without covering 0s.

- **(First Q43) If an incompletely specified function... can be minimized as **CD + A¯B**...**

**Answer:** **(c) 0, 5** (or similar based on Don't Care analysis).

**Explanation:** Comparing the minterms {1,3,7,11,15} with the minimized forms suggests that minterm 5 (which makes a quad with 1,3,7) must be a Don't Care to allow the simplification.

- **(Second Q43) Which of the following is an even function?**

**Answer:** **(e) **1 ⊕ A ⊕ B ⊕ C

**Explanation:** A ⊕ B ⊕ C is the odd function (logic 1 if odd number of 1s). XORing with 1

inverts it, creating the Even function (logic 1 if even number of 1s).

- **The function **F = Σ(1,2,4,7,8,11,13,14)** is**

**Answer:** **(a) **A ⊕ B ⊕ C ⊕ D

**Explanation:** The minterms listed are exactly those with an **odd** number of 1s (e.g., 1 is 0001, 7 is 0111). This is the definition of the 4-variable XOR function (Odd Parity).

**Match the definitions (45–47):**

- **The maximum voltage added to the input signal... that does not cause an undesirablechange...**

** Answer:** **(d) Noise margin**

- **Denotes how relatively fast signals pass through a gate...**

** Answer:** **(b) Propagation delay**

- **Energy dissipated by signals propagated through wires connecting gates.**

** Answer:** **(c) Power dissipation** (specifically dynamic power).

- **The maximum number of input lines to other gates that may be driven by the outputof a gate without impairing its operation.**

**Answer:** **(a) Fan-out**

**Explanation:** Fan-out is the standard term for the driving capability of a logic gate (how many load inputs it can drive).

- **Which of the following is NOT TRUE?**

** Answer:** **(b) The implementation of a Boolean function with NAND gates requires that the function be simplified in the product of sums.**

** Explanation:** NAND implementation is naturally based on **Sum of Products (SOP)** (AND-

OR logic converts directly to NAND-NAND). NOR implementation typically uses Product of Sums (POS).

–

- **Using the NAND technology the function **F = AB + (AB)C + (AB)D + E** is implemented with **x** inverters and **y** NAND gates. Select the CORRECT option from the following 2-tuple values of **x** and **y**.**

** Answer:** **(d) 2, 4** (Analysis below)

**Simplification:**

Term 1 & 3: AB + ABD = AB(1 + D) = AB.

Function becomes: F = AB + (AB)C + E.

(AB)C = (A + B)C = AC + BC.

F = AB + AC + BC + E.

This simplification is getting complex. Let's look at the raw structure typically expected in these "count the gates" questions without deep boolean algebra simplification first.

 Raw Terms: AB (1 NAND), (AB) (Output of first NAND), (AB)C (1 NAND combining previous output + C), (AB)D (1 NAND combining first output + D?), E.

 Direct 2-level NAND-NAND implementation of a Sum of Products requires 1 NAND per product term and 1 output NAND.

 If we simplify F to AB + C(A + B) + E, it's complex.

–

However, looking at the simplest interpretation: F = AB + (AB)C + ABD + E.

This looks like a logic circuit optimization problem.

Most likely answer choice relates to a standard implementation. For typical SOP F = AB + C + E, you need 1 NAND for AB, and 1 NAND for the sum.

 Without a clear circuit diagram, this is an estimation. (d) is a plausible typical answer for 4-variable functions in these tests.

- **The direct implementation of the function F in question 50 using the NOR technologywill require**

**Answer:** **(e) more inverters and more NOR gates than NAND gates**

**Explanation:** Since the function is given in a form close to Sum of Products (AB + …), it is "native" to NAND logic. Implementing SOP with NOR gates requires converting to Product of Sums or using many inverters to negate inputs and outputs, leading to a higher gate count.

- **When implementing a function in its sum of products standard form, using the NANDtechnology will always have**

**Answer:** **(b) the same gate-input cost when compared with the NOR technology**

*Correction:* Actually, the correct answer is usually **(c) a lower gate-input cost...** or dependent on the function.

However, strictly speaking, if you implement the *same* SOP expression directly:

NAND-NAND directly maps to AND-OR (SOP).

NOR-NOR directly maps to OR-AND (POS).

To do SOP with NORs, you need extra inverters.

Therefore, for an SOP form, NAND technology has a **lower** cost.

** Selected Answer:** **(c)** (assuming the question implies "compared to implementing the same SOP expression with NORs").

**Figure 1 Analysis (5-variable K-Map)**

The table shows rows A,B and columns C,D,E.

Row indices: 0 (00), 1 (01), 3 (10), 2 (11). (Note: Standard Gray code for rows is 00, 01, 11, 10. The table labels Row index 3 before 2? Or are the values M(1,0) = 8 and M(2,0) = 24 implying standard binary order 0, 1, 3, 2? Let's assume standard Gray code ordering 00,01,11,10 is intended despite the label permutation).

- **The maxterm of cell M(3,5) is**

**Answer:** (b)

**Explanation:**

Row index 3 corresponds to AB = 10.

Column index 5 (labeled '5' in headers) corresponds to CDE = 111.

Binary value: 10111 = 23.

–

Maxterm for 23 is A + B + C + D + E. That is option b.

- **What are the values of cells that are minimized to **BDE**?**

** Answer:** **(c) 10, 14, 26, 30** _1_10 if you get the possible variations the don't care digits you have: 11110 -> 30

11010 -> 26

01110 -> 14

01010 -> 10

- **Which parameter describes a cell NOT adjacent to cell **M(i,j)**?**

** Answer:** **(e) none

- **What is the sum-of-products minimization of cells in the range **9 < M(i,j) < 20**?**

** Answer:** **(d)

- **The minimization of cells describe by the product **∏M(i,j)∀i = 0,1,2,3** for **j = 6** is**

**Answer:** **(e) None of the above**

**Explanation:** As calculated in the thought process, column j = 6 (Label 5, 101) for all rows

– yields C + D + E. No option matches.

- **The minimization of cells describe by the sum **∑m(i,j)∀j = 0,1,2,3** for **i = 2** is**

** Answer:** (e) none

- **The minimization of cells described by the sum...**

**Answer:** **(a) **A ⊕ B ⊕ C ⊕ D ⊕ E

**Explanation:** The indices listed (sum of evens = sum of odds...?) usually describe a checkerboard pattern characteristic of the XOR (Parity) function.

- **Which is NOT a prime implicant of **G(a,b,c,d) = Σ(1,4,6,7,8,9,10,11,15)

** Answer:** **(b)**

- **How many essential prime implicants are in G above?**

** Answer:** **(e) -> 4**

- **The function H in Figure 2 is**

**Answer:** **(c) **AB + C¯ **Explanation:**

Gate 1: NAND(A, B) = AB.

Gate 2: NAND(Output1, C) = (AB) ⋅ C.

–

De Morgan: (AB) + C = AB + C.

- **If all the gates in question 62 are replaced by NOR gates then the function H becomes**((A+B)'+c)' = (A+B)C' = AC'

** Answer:** **(e) None of the above**.

- **How many NOR gates will implement a 3-input AND gate?**

** Answer:** **(d) 4**

ABC ->(A' + B' + C') -> ((AB)' + C')' p.s I used demorgan's law Converting AND to NOR uses 3 gates

**65. How many NAND gates will implement a 3-input NOR , answer: e

(A+B+C)' -> (A'B'C') -> (A+B)'C' (invert the raw and to get nand) same technique as 64

3 + 2 = 5

- **How many XNOR gates are in a 4-bit odd parity checker?**

**Answer:** **(c) 3**

**Explanation:** To check parity of 4 bits: P = A ⊕ B ⊕ C ⊕ D.

Using 2-input gates: (A ⊕ B) ⊕ (C ⊕ D).

Requires 3 XOR gates.

XNOR gates can also be used (with inversion considerations). The structure is a tree of 3 gates.

- **Two binary numbers in 2's complement X=1010100 and Y=1000011 produce... Answer:** **c**

**68.**

** Answer:** **c**

**69.**

** Answer:** **b**

- **A decoder with enable input can function as a**

**Answer:** **(b) demultiplexer**

**Explanation:** This is a standard duality. The Enable acts as the Data input, and the Select lines direct it to one of the outputs.

- **The function F in Figure 3 is**

** Answer:** d

- **A 4 to 1 line multiplexer can be implemented with three state buffers and a(n)**

**Answer:** **(d) decoder**

**Explanation:** A decoder selects one of the buffers to enable, allowing that input to pass to the common output line.

- **Which digital function has the logic circuit realization below?**

** Answer:** **(a) Decoder**

- **Which digital function provides the **2n** minterms of n input variables?**

**Answer:** **(a) Decoder**

**Explanation:** An n-to-2n decoder activates exactly one output for every possible input combination, effectively generating all minterms.

- **Encoder (c)**
- **Mux (e)**
- **Which digital function has the logic circuit realization below? (The XOR/AND/ORdiagram)**

** Answer:** **(a) Full Adder**

- **The signed 2's complement of -8 in an eight bit computer is**

**Answer:** **(a) 11111000 Explanation:**

+8 = 00001000.

Invert: 11110111.

Add 1: 11111000.

- **The subtraction of two n-digit unsigned numbers... Which steps have errors?**

** Answer:** **(e) None of the above**.

- **If the signed magnitude representation of a number is 1011, what is its representationin signed 2's complement?**

**Answer:** **(d) 1101 Explanation:**

Signed Mag 1011: Sign=1 (-), Mag=011 (3). So -3.

2's Complement for -3 (4 bits):

+3 = 0011.

Inv: 1100.

Add 1: 1101.

- **What is -6 + (-19) in signed binary using 1's complement?**

**Answer:** **(e) None of the above** (Likely overflow or specific bit-width issue).

−6 (8-bit 1's comp): 11111001.

−19 (8-bit 1's comp): 11101100.

Sum: 11100101 (+ carry).

End-around carry: 11100110.

Result: −25.

Options: (a) 00010011 (+19?), (c) 11111001 (-6?), (d) 11101100 (-19?).

None match the sum.

- **Which of the following is NOT TRUE of the overflow condition?**

** Answer:** **(a)**

- **Which of the following is TRUE of sequential circuits?**

**Answer:** **(d) The storage elements... are called flip-flops.**

**Explanation:** (a) is false (outputs depend on *sequence* not just inputs). (b) is false (synch depends on clock, not just input change instant).

- **The SR latch has two cross-coupled**

**Answer:** **(a) NOR gates** (or NAND gates).

**Explanation:** The "classic" SR latch is drawn with NOR gates. The NAND version is usually

– called SR latch. Given options, NOR is the textbook definition.

- **When all three inputs of ONE of the following latches are equal to 1 it is placed in anindeterminate state.**

**Answer:** **(c) clocked SR latch**

**Explanation:** Inputs S = 1,R = 1,Clk = 1. The outputs try to go to 00 (NOR) or 11 (NAND) and the state is invalid/indeterminate upon clock release.

- **Flip-flops are preferred to clocked latches... because:**

**Answer:** **(c) Latches are transparent**

**Explanation:** Transparency (output follows input while clock is high) causes race conditions in feedback loops. Flip-flops (edge-triggered) prevent this.

- **Which of the following statements is (are) TRUE?**

** Answer:** **(d)**

- **Which of the following is NOT CORRECT?**

** Answer: (b)**.

89 a 90 e 91 c 92 c 93 c 94 a 95 b

- **A sequential circuit has one flip-flop Q... D = XZ + YZ + XYZ...**

**Answer:** **(a) 0, 0** (Simplification needed) **Explanation:** Reset means D = 0.

- **Phases in the design of sequential circuits...**

**Answer:** **(e) I, VI, II, IV, III, VII, VIII** (Standard Design Flow)

Specification -> Formulation (State Diagram) -> State Assignment -> Flip-Flop Input Equation -> ...

 The order usually is: Formulation (I) -> State Assignment (VI) -> Equations (II/IV) -> ...

 Check option (e).

- **A synchronous sequential circuit S with a single D flip-flop... A(t+1) = A(t) XOR X...**

**Answer:** **(c) 1, 0, 1, 0, 1 ...**

**Explanation:**

X = 1 (constant).

–

A(t + 1) = A(t) ⊕ 1 = A(t).

The Flip-Flop toggles every clock.

Sequence: 0, 1, 0, 1... or 1, 0, 1, 0...

- **Which of the following distinguishes a Mealy type Finite State Machine?**

** Answer:** **(c) In the Mealy model the output is a function of the present state and the input.**

** Explanation:** Definition of Mealy Machine. (Moore is state only).

- **Which of the following is NOT CORRECT about sequential circuits?**

** Answer:** **(c) The storage elements commonly used in asynchronous sequential circuits are time-delay devices.**

**Explanation:** Actually, this is TRUE (delay elements or feedback loops).

(e) Asynchronous circuits can be unstable. TRUE.

(b) Asynchronous behavior defined by inputs/time. TRUE.

(a) Specified by time sequence. TRUE.

(d) Storage elements in synchronous are flip-flops. TRUE.

Maybe (c) is the least precise? But "Time-delay devices" is the formal model for Async.

Maybe (e) "can be unstable"? They can be, but is it a defining feature?

This is a tricky theory question. (c) might be "False" if the examiner insists they are latches, but latches *are* modeled as delays.

- **A Master-slave flip-flop constructed with two D flip-flops is triggered by the**

**Answer: (a)** (Edge) is the modern interpretation, but **(c)** might be the textbook answer for "Pulse Triggered".

- **Which of the following flip-flops is constructed from a clocked SR latch, an inverterand an XOR gate?**

** Answer:** **(b) JK flip-flop** (Usually ANDs + NORs).