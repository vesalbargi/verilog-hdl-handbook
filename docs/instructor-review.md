# Instructor review list

Items found while converting the PDF. Each one is also marked with a `TODO(instructor)` HTML comment next to the affected text in the `.qmd` files (invisible on the website).

## Example numbering conflicts

1. **Boolean-equation example (source p. 7).** The code box is headed "HDL Example 3.2 (gate level model with propagation delay)", but the code has no delays and the body text calls it "HDL Example 3.4". The handbook uses **3.4** and a title that matches the content.
2. **UDP example (source p. 9).** The code box is headed "Example 3.4 (Combinational logic modeled with Boolean equations)", but it holds the UDP, and the body text on p. 8 calls it "HDL Example 3.5". The handbook uses **3.5**.
3. No separate Example 3.2 or 3.3 is present in the supplied pages (the only "3.2" is the mislabeled box above).

## Likely source errors (kept out of the explanations or flagged)

| Location | Issue |
|---|---|
| 1.1 | "end-module" printed with a hyphen in text; the code shows `endmodule`. |
| 2.1, Example 4.2 | Module name printed as `ripple_carry_ 4_bicadder`; text calls it `ripple_carry_4bit_adder` and suggests `adder_4_bit`. The 1995 comment lists ports `(Sum, C4, A, S, CO)` where `B` is expected. |
| 2.2 | `tri . m_out` (should be `tri m_out`); the text says high impedance is "symbolized by 1" (should be `z`). |
| 2.2 | "If an identifier is used but not declared, it is a wire" is broader than the Verilog rule (implicit nets apply in specific contexts). |
| 2.3 | Source lists the left-hand side of a *procedural* assignment as a net; procedural targets are `reg`. Omitted from the handbook. |
| 2.3, Example 4.6 | Text writes `OUT` where the module uses `m_out`. Same for the shorthand `if` in 2.4. |
| 2.4, Example 4.8 | Text says "output y"; code uses `m_out`. |
| 2.4 | `16'b0101_1110_0101_0011` is OCR'd with a letter "l" instead of "1". |
| 3.1 | Clock version 2 shows `initial 300 $finish;` (missing `#`) and a capital "Initial". |
| 3.1 | "Synthesis tools do not accept `initial`": some modern FPGA tools accept it for initial register values. Decide whether to qualify it for your toolchain. |
| 3.2, Example 5.1 | Text says "one blocking assignment" but the code uses `<=` (nonblocking). Alternative module named `D-latch` and missing a semicolon. |
| 3.2, Example 5.3 | `JKFF` declares `J,K,Clk,rst` as `inout`, instantiates `DDF` with five ports (the module is `DFF` with four), and never uses the wire `JK` it computes. |
| 3.2, Example 5.4 | The code of Example 5.4 (JK flip-flop with `case ({J,K})`) is missing: the box on p. 30 repeats the D flip-flop. |
| 3.3, Example 5.5 | `next_reset` (should be `next_state`); all case items read `S0`; "tare machine" (probably "zero-detector"); test bench lacks its module header and signal declarations; "intial" typo. |
| 3.3, Example 5.6 | All case items read `S0`; `enscase` (should be `endcase`). |
| 3.4, Example 5.7 | The PDF ends on p. 38 inside the alternative `Toggle_flip_flop`; the test bench is not included. Structural model instantiates `Toggle_flip_flop_3`, but the module shown is `Toggle_flip_flop`. OCR names: `Moore_ModeCFig_5_20`, `Moore_Model_STRJig_5_20`, `slate`, `xj n`. |

## Cross-references to the original textbook

The source cites sections and tables of the full textbook that are not part of these three chapters: Sections 2.8, 3.10, 4.11, 4.12, 5.6, 8.2, 10.10 and Table 8.1. The handbook points to its own chapters where the target is clear (for example, "next chapter" or "Chapter 3") and says "original textbook" otherwise.

## Content added or reorganized

- Each chapter has an unnumbered lead-in section ("Chapter Overview", "Modeling styles", "Overview") holding the text that precedes section x.1 in the PDF, plus a short learning-objectives block and chapter summary derived from the chapter's own content.
- Short unnumbered snippets (for example the `assign` statements in 1.2 and 2.3, the three-state instantiations, clock generators, and blocking/nonblocking pairs) are written out from the book's text; the clock version 2 uses `#300` and the shorthand `if` uses `m_out` to match Example 4.7.
- A few small comparison tables are summaries of source statements (design flow steps, three-state gates, V1995 vs V2001 syntax, Mealy vs Moore, `initial` vs `always`). They add no new technical facts.
- The cover page (VeriLogger Extreme images) and the Xilinx logos in code boxes are not reproduced.

## Code corrections applied

| Example | Book | Handbook code |
|---|---|---|
| 3.1 | `Simple_CIrcuit` | `Simple_Circuit` |
| 3.4 | Box titled 3.2, "gate level model with propagation delay" | Titled 3.4, Boolean equations (no delays in the code) |
| 3.5 | Box titled 3.4; `Option gate instance name omitted` | Titled 3.5; "Optional" |
| 4.1 | `decoder_2x4_9ates` | `decoder_2x4_gates` |
| 4.2 | `ripple_carry_ 4_bicadder`; 1995 comment lists `(Sum, C4, A, S, CO)`; `input (3: 0]`; `Veril09` | `ripple_carry_4_bit_adder`; `(Sum, C4, A, B, C0)`; `input [3:0]` |
| 4.2 | Garbled version comments | Rewritten as clean 1995 / 2001 comments |
| 5.1 | Alternative module `D-latch` and header without semicolon | `D_latch`, semicolon added |
| 5.3 | `JKFF` declared `output reg Q` and `inout J,K,Clk,rst`, instantiated `DDF JK1(Q,J,K,Clk,rst)` | `output Q`, `input J, K, Clk, rst`, `DFF JK1 (Q, JK, Clk, rst)` (uses the wire `JK`) |
| 5.4 | Code not present | Written from the description (`case ({J, K})`, positive-edge clock) |
| 5.5 | `next_reset`; all case items `S0:`; `intial` | `next_state`; `S0` to `S3`; `initial` |
| 5.5 | Test bench without module header or declarations | Added `t_Mealy_Zero_Detector` module, `wire t_y_out`, `reg t_x_in, t_clock, t_reset` |
| 5.6 | All case items `S0:`; `enscase` | `S0` to `S3`; `endcase` |
| 5.7 | `Sl`, `slate`, `xj n`, `Moore_Model_STRJig_5_20`, `Moore_ModeCFig_5_20`, `Toggle_flip_flop_3` | `S1`, `state`, `x_in`, `Moore_Model_STR_Fig_5_20`, `Moore_Model_Fig_5_20`, `Toggle_flip_flop` |
| 5.7 | Alternative toggle model cut off | Completed with `Q <= Q ^ T` |
| 5.7 | Test bench not included | Written from the description (eight clock cycles, `x_in` toggled at the negative clock edge); compare with Figure 5.24 |
| Clock snippets | `initial 300 $finish;`, capital `Initial` | `initial #300 $finish;`, lowercase |
| Inline snippets | `OUT` in `if (select) OUT = A;` | `m_out` |
