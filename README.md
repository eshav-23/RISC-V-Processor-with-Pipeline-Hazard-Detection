# RISC-V Processor with Pipeline Hazard Detection

This project implements a **5-stage pipelined RISC-V processor** in Verilog, extended from a baseline single-cycle design.  
The design improves **instruction throughput** and **parallelism** while handling hazards using **stalling**, **forwarding**, and a **hazard detection unit**.

---

## Features

- **5-Stage Pipeline**  
  - **IF**: Instruction Fetch  
  - **ID**: Instruction Decode & Register Fetch  
  - **EX**: Execute / ALU Operations  
  - **MEM**: Memory Access  
  - **WB**: Write Back

## Pipeline Registers

  - The processor uses dedicated **pipeline registers** between stages to hold instruction and data values as they move forward.  
  - These registers maintain **stage isolation**, ensuring that multiple instructions can execute in parallel without interfering with each other.

  - **IF/ID Register** → Holds instruction and PC from **Instruction Fetch** to **Instruction Decode**.  
  - **ID/EX Register** → Transfers control signals, register values, and immediate values to the **Execute** stage.  
  - **EX/MEM Register** → Passes ALU results, target addresses, and control signals to the **Memory Access** stage.  
  - **MEM/WB Register** → Carries memory output or ALU results to the **Write Back** stage.  

- **Hazard Handling Mechanisms**
  - **Data Hazards**
    - Implemented **forwarding paths** to resolve Read-After-Write (RAW) hazards.  
    - **Stall logic** introduced when forwarding is not possible.  
  - **Structural Hazards**
    - Analyzed pipeline resources and ensured proper sequencing to prevent simultaneous conflicts.  
    - Balanced memory and execution stage usage to avoid contention.  

- **Hazard Detection Unit**
  - Detects pipeline conflicts at runtime.  
  - Inserts stalls or triggers forwarding as needed.  
  - Maintains **correct program execution** while minimizing performance penalties.  

- **Performance Enhancements**
  - Increased **parallel instruction execution**.  
  - Reduced pipeline delays through selective forwarding.
  - Balanced trade-offs between hardware complexity and performance gains.  

---

## Tools & Environment

- **Language**: Verilog HDL  
- **Simulation & Synthesis**: Xilinx Vivado

- ## Usage

1. Clone the repository to your local machine:
    
    ```
    git clone <https://github.com/eshav-23/RISC-V-Processor-with-Pipeline-Hazard-Detection>
    
    ```
    
2. Open XILINX Vivado and create a new project.
3. Add the Verilog source files from the cloned repository to your project.
4. Synthesize and implement the design.



