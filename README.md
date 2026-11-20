# Verilog HDL Handbook

A course handbook for **Computer Architecture Laboratory (LAB3114)**, designed to introduce hardware description languages and digital circuit modeling using Verilog. It guides students through the fundamentals of HDL, progressing from gate-level modeling to combinational circuits, flip-flops, and finite state machines. Each chapter includes numbered examples, textbook figures, and practical Verilog code ready to use in your simulator.

## Contents

1. **Hardware Description Language**: the HDL design flow, Verilog modules, Boolean expressions, and user-defined primitives.
2. **HDL Models of Combinational Circuits**: gate-level, dataflow, and behavioral modeling; three-state gates; hierarchical design.
3. **Synthesizable HDL Models of Sequential Circuits**: latches and flip-flops, blocking and nonblocking assignments, Mealy and Moore state machines, and structural description of clocked circuits.

## Learning Objectives

After working through the handbook you should be able to:

- Explain what an HDL is and name the steps of an HDL-based design flow.
- Read and write a Verilog module with ports, wires, and gate instances.
- Model combinational logic with gates, Boolean equations, operators, and `always` blocks.
- Build hierarchical designs by instantiating modules inside other modules.
- Model three-state gates and nets with several drivers.
- Choose between blocking and nonblocking assignments.
- Write latches, flip-flops with asynchronous reset, and finite state machines that a synthesis tool can implement.

## Getting Started

You need [Quarto](https://quarto.org/docs/get-started/) 1.4 or newer.

```bash
git clone https://github.com/vesalbargi/verilog-hdl-handbook.git
quarto preview
```

`quarto preview` opens the site in your browser and reloads it when you edit a file. To build the final site into `_site/`, run:

```bash
quarto render
```

## Project Structure

```text
├── index.qmd        # homepage
├── chapters/        # one file per chapter
├── figures/         # figures used in the chapters
├── styles/          # light and dark themes
├── assets/          # fonts, favicon, small scripts
├── docs/            # notes for maintainers
└── _quarto.yml      # site configuration
```

## License

This project is licensed under the MIT License.

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)