# 32-bit-RISC-V-Processor-single-cycle-and-5-staged-pipeline-cpu
A 32-bit RISC-V (RV32I) processor core implemented in Verilog, featuring both a baseline single-cycle architecture and a high-performance 5-stage pipelined design.
# 32-bit RISC-V Processor (RV32I) 🚀

## 📌 Overview
This repository contains the RTL source code and verification environment for a **32-bit RISC-V microprocessor** implementing the standard RV32I Base Integer Instruction Set. 

To explore different architectural trade-offs between area, latency, and throughput, this project includes two distinct implementations:
1. **Single-Cycle Architecture:** A baseline processor where each instruction executes completely within a single clock cycle. Ideal for understanding the fundamental data flow and instruction decoding.
2. **5-Stage Pipelined Architecture:** A high-performance variant that divides instruction execution into five distinct stages, maximizing clock frequency and instruction throughput (IPC).

## ✨ Key Features
* **RV32I Compliance:** Fully supports the foundational RISC-V 32-bit integer instructions (R-type, I-type, S-type, B-type, U-type, and J-type).
* **Dual Architectures:** Side-by-side single-cycle and pipelined cores for comparative analysis.
* **Hierarchical Modeling:** Clean, modular instantiation of components (ALU, Register File, Control Unit, Memory Interfaces) facilitating easy debugging and scalability.
* **Refined Control Logic:** Architected with independent, separate reset inputs for specific modules rather than relying solely on a global asynchronous reset network, allowing for precise initialization control.
* **Hazard Handling (Pipelined):** Includes data forwarding paths and hazard detection units to resolve data and control hazards without excessive pipeline stalling.

## 🏗️ Pipelined Architecture Breakdown
The 5-stage pipelined core follows the classic RISC methodology:
1. **Instruction Fetch (IF):** Fetches the instruction from instruction memory and computes the next PC.
2. **Instruction Decode (ID):** Decodes the instruction, generates control signals, and reads operands from the Register File.
3. **Execute (EX):** The ALU performs arithmetic/logical operations or calculates memory addresses/branch targets.
4. **Memory (MEM):** Reads from or writes to the Data Memory.
5. **Write Back (WB):** Writes the final ALU result or memory data back to the destination register.

## 📂 Repository Structure
```text
📦 RISCV-32bit-Processor
 ┣ 📂 src
 ┃ ┣ 📂 single_cycle      # RTL for the single-cycle implementation
 ┃ ┃ ┣ 📜 riscv_core.v
 ┃ ┃ ┣ 📜 alu.v
 ┃ ┃ ┗ 📜 reg_file.v
 ┃ ┣ 📂 pipelined         # RTL for the 5-stage pipelined implementation
 ┃ ┃ ┣ 📜 pipeline_top.v
 ┃ ┃ ┣ 📜 hazard_unit.v
 ┃ ┃ ┗ 📜 forwarding.v
 ┃ ┗ 📂 common            # Shared modules (Instruction/Data memory)
 ┣ 📂 tb                  # Verification environment
 ┃ ┣ 📜 tb_single.v
 ┃ ┗ 📜 tb_pipeline.v
 ┣ 📂 programs            # RISC-V assembly programs and hex dumps for testing
 ┃ ┗ 📜 fibonacci.hex     # Hex machine code for memory initialization
 ┗ 📜 README.md
