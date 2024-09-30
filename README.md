# NASSCOM_SOC_VSD_REPO
This repository is for the Lab Acitivites of the NASSCOM VSD SoC design program.

# **NASSCOM VSD DIGITAL VLSI SOC Design and Planning**

- This workshop, organized by **VLSI SYSTEM DESIGN (VSD) in collaboration with NASSCOM, focuses on Digital VLSI SoC (System on Chip) design and planning**.

- This workshop focuses on SoC design and planning, specifically using the Google-SkyWater 130nm open-source process and the OpenLANE flow. It guides us through the Physical Design (PnR) process, transforming an RTL netlist into a finalized chip design, covering the challenges of each stage. The workshop aims to empower participants to explore ASIC design flow and create their own chips, leveraging this innovative, open-source technology for accessible and automated chip design.


# DAY-1 

# Sky130 - Inception of open-source EDA, OpenLANE and Sky130 PDK
# Section-1 : How to talk to computers
## L1 - Introduction to QFN-48 Package, chip, pads, core, die, and IPs

- A **PACKAGE** refers to the physical enclosure that surrounds an integrated circuit (IC) or electronic component. It provides both mechanical protection and electrical connections between the component (like a chip or IC) and the circuit board (PCB). The package type is important as it impacts the size, assembly method, and performance of the electronic circuit. So here in our workshop, we use **QFN-48 (Quad Flat No-lead) package**,  It is a type of surface-mount integrated circuit package. The number "48" refers to the number of pins or connections it has, meaning it has 48 leads. These leads are usually exposed on the bottom of the package instead of extending out like traditional leads in other IC packages.
- A package is the outer shell or enclosure that surrounds the chip (also known as the die) inside. The chip is the actual semiconductor component where all the electronic circuits and functions are embedded, while the package provides the necessary protection and external connections for the chip to communicate with other components on a circuit board. which is shown in the below figure,

![vg](https://github.com/user-attachments/assets/09c2db49-e366-43fd-8938-bd9f3e1794ab)

- Inside the package, **wire bonds** are tiny wires (usually made of gold, aluminum, or copper) that connect the internal chip to the external leads or pads on the package. These wire bonds allow electrical signals, power, and data to flow between the chip and the circuit board, enabling the chip to function in electronic devices.
- The QFN-48 PACKAGE with size 7nm x 7nm is shown below.

![Screenshot (509)](https://github.com/user-attachments/assets/53d8b313-47a6-4261-904c-bcd2b7764f9d)

![Screenshot (507)](https://github.com/user-attachments/assets/1d330338-f6a4-42ba-9ece-012f640e2784)

- In the above figure, the chip which is originated in the middle shares the signals to the external world using **PADS**.

### **PADS** :
  - Pads are critical for making electrical connections between components and the different parts of a package.
  
### **DIE** :
  - The die is the size of the actual chip within an integrated circuit (IC). It contains the transistors and other electronic components.
  
### **CORE** :
  - A core refers to the main processing unit of a chip. Like all the digital logic takes place. It is a section of the die that performs 
    computing tasks by executing instructions. Modern processors often have multiple cores (e.g., quad-core, octa-core), allowing them to 
    perform multiple tasks simultaneously (multithreading/multiprocessing).

  ![JNSKJDS](https://github.com/user-attachments/assets/839d3067-abb9-4deb-bd4f-2d1d1726d91d) 

- A typical chip consists of a SOC, SRAM, ADC, DAC, PLL, and other components. The PLL, ADC, DAC, and SRAM are actually Foundry IPs.
  
### **Foundry** :
  - A foundry is a company that manufactures semiconductor chips for other companies. The foundry doesn't design the chips; it only 
    handles the fabrication process.These companies, like TSMC (Taiwan Semiconductor Manufacturing Company) and GlobalFoundries, 
    specialize in the production of semiconductor chips but do not design their own.

### **Foundry IPs (Intellectual Property)** :
  - IPs require significant expertise and intelligence to build particular Blocks. It actually refers to pre-designed and verified 
    building blocks 
    (often called IP blocks) that a foundry offers to chip designers. These IPs help designers accelerate the development of their chips 
    without having to design everything from scratch.

   ![Screenshot (513)](https://github.com/user-attachments/assets/f93cb0a9-f43a-4a57-93e2-4f6445072982)

## L2 :  Introduction to RISC-V

### **ISA (Instruction Set Architecture)**
 - In general terms, an Instruction Set Architecture (ISA) is the set of instructions that a computer's processor (CPU) can execute. It 
   defines the interface between software and hardware, specifying how software controls the hardware. Like it's nothing but a language 
   of a computer.
 - You can think of an Instruction Set Architecture (ISA) as the "language" of a computer's processor. Just like a human language has 
   grammar and vocabulary that define how words and sentences are constructed and understood, an ISA defines how instructions are 
   formatted, what operations the CPU can perform, and how it interacts with memory and other components.
   * *1) Instructions:* * The "words" in this language are the instructions that the CPU can execute, such as arithmetic operations, 
      data transfers, and control instructions.
   * *2) Syntax and Semantics:* * The ISA specifies the syntax (format) and semantics (meaning) of each instruction, dictating how 
      instructions should be written and what they do.
   * *3) Communication:* * Just as languages facilitate communication between people, an ISA facilitates communication between software 
      and hardware, enabling programs to control the CPU and perform tasks.

 ## L3 : From Software Applications to Hardware

 - When you use an app on your computer, it sends commands to the system software (like the operating system), which acts as a translator 
   between your app and the hardware. The system software converts these commands into binary code (the language of the hardware), which 
   the CPU and other components then execute. The results are then sent back through the system software to the app, allowing you to see 
   the outcome of your actions.
 - So the Application software enters the block called System software and then the application program converts into the binary language 
   which is understandable for the hardware.
 - Application Software is like MS Office, Firefox, Acrobat Reader DC, etc.
 - For System Software the major components are OS, Compiler, and Assembler.

![Screenshot (516)](https://github.com/user-attachments/assets/33456517-57ec-43fe-8961-346de33150eb)


### Operating System (OS) :
 - The operating system (OS) is responsible for handling input/output operations, allocating memory, and managing low-level system 
   functions. Its main role is to translate a specific application into its respective assembly language program and ultimately into 
   binary language, making it understandable by the hardware. This is the primary function of the OS.
   
### Compiler :
 - The compiler is used to convert the respective program or any standard format to its respective language based on the hardware we are 
   using. The Output of the Compiler i.e. the syntax of `.exe file` depends on the hardware we are using.
 - The `.exe file` consist of instructions that has been implemented by the particular hardware. The hardware here is RISC V.

### Assembler :
 - Once we receive instructions from the compiler, the assembler will take each instruction and convert it into its respective binary 
   numbers, also known as a machine language program. Finally, the binary language is sent to the hardware. When the hardware receives a 
   specific pattern or information, it performs a task and generates the output accordingly.

- The instructions we receive from the compiler serve as the interface between the C language and the hardware. These instructions are 
  known as the ISA or computer architecture. The interface is referred to as the abstract interface.

![Screenshot (520)](https://github.com/user-attachments/assets/df4c46ad-9378-4833-80d2-e613e3a51cde)
![Screenshot (521)](https://github.com/user-attachments/assets/126624e4-a859-4654-bb45-3b4ffead7dc3)
 

- If we delve deeper, there is another interface that plays a major role in reaching the hardware: Hardware Description Language (HDL).
- First, we need to write the HDL for the instruction. Then we synthesize it into the Gate Level Netlist, followed by converting the 
  Gate Level Netlist into its respective Layout based on the general RTL2GDS Flow.
   
![Screenshot (522)](https://github.com/user-attachments/assets/f362374f-6045-4fe8-a49f-971d54dd2e2d)

# Section-2 : SoC design and OpenLANE
## L1 - Introduction to all components of open-source digital ASIC design

![Screenshot (524)](https://github.com/user-attachments/assets/7b638600-88ba-45ea-afbd-382ef803b7d7)

- The components of open-source digital ASIC design involve as follows,
### RTL Design: 
  - Register-Transfer Level (RTL) is a critical design abstraction that models the flow of digital signals between hardware 
    registers in a synchronous digital circuit. The logical operations performed on these signals are also part of this model. A variety 
    of open-source platforms are available for RTL design, including Librecores, Opencores, and repositories on GitHub. These resources 
    have been instrumental in accelerating my understanding of RTL design.
### EDA Tools: 
- Electronic Design Automation (EDA) refers to the suite of tools used to design and verify integrated circuits (ICs), printed circuit 
  boards (PCBs), and other electronic systems. Several open-source EDA tools, like Qflow, OpenROAD, and OpenLANE, are available. Today, 
  I focused on OpenLANE, which is particularly effective for open-source digital ASIC design. These tools are central to automating and 
  verifying the design process.
### PDK Data: 
- The Process Design Kit (PDK) is an essential interface between the fabrication process (FAB) and the design stage. The PDK includes 
  collections of files such as process design rules (DRC, LVS, REX), digital standard cell libraries, and I/O libraries, which are used 
  by EDA tools to model and simulate IC fabrication.

![Screenshot (525)](https://github.com/user-attachments/assets/bde588ef-09f4-40c4-8177-2251a6506409)

- An example of an open-source PDK is the SkyWater 130nm process, released in collaboration with Google in 2020. Though newer 
  fabrication technologies, like the cutting-edge 5nm process, are available, the 130nm process remains relevant for many applications 
  due to its lower cost and sufficient processing speed for most use cases. For example, Intel’s P4EE @ 3.46 GHz (released in Q4 '04) 
  and Sky130_OSU (a single-cycle RV32i CPU) pipeline can achieve over 1 GHz clock speeds using this technology.

![Screenshot (526)](https://github.com/user-attachments/assets/99d28ef2-8db9-4ce4-bfa8-40fa8e3126c8)

## L2 - Simplified RTL2GDS flow 
- The  simplifying RTL to GDSII flow, breaking it down step by step to streamline the understanding of this complex process. Below is an 
  Outline the major phases involved in this flow.

![Screenshot (529)](https://github.com/user-attachments/assets/c0f09633-6584-420a-9bcf-d10ce48342ed)

### Synthesis: 
- The synthesis phase converts the RTL design into a circuit, leveraging the standard cell library (SCL). The end result is a gate-level 
  netlist that represents the same functionality as the RTL but at a lower abstraction level. This netlist, described in hardware 
  description languages (HDL) like Verilog or VHDL, connects standard cells, which have regular layouts akin to electrical components, 
  such as HDL, SPICE models, etc.

![Screenshot (530)](https://github.com/user-attachments/assets/4498f11e-325a-4a74-8562-f0deaf55b986)  ![Screenshot (531)](https://github.com/user-attachments/assets/8651bc6c-556e-4b98-919d-31d39cac7745)

### Floor/Power Planning:
- In this stage, The planning of the silicon area and distributing power across the entire circuit takes place. At the chip level floor 
  planning involves dividing the chip die into different blocks and positioning the I/O pads. In micro-level floor planning involves 
  dimensions, pin locations, and rows are defined. Power planning is also crucial here, where the power distribution network is 
  constructed, typically using multiple VDD and GND lines. Metal strips are laid horizontally and vertically in parallel to minimize 
  resistance, with upper metal layers (which are thicker and more resistant to electromigration) being preferred for power distribution.

![Screenshot (534)](https://github.com/user-attachments/assets/fa4299ae-c50e-42b6-9762-ff79c4c4880d)
![Screenshot (533)](https://github.com/user-attachments/assets/a7fc7e24-c2ba-4425-a4d4-56fde156182a)
![Screenshot (535)](https://github.com/user-attachments/assets/50091cd1-5e13-4045-9267-cd79ca639231)

### Placement: 
- The next step is to place the gate-level netlist onto the floor-planned rows, aligning them with the available sites. Cells should be 
  placed as closely as possible to minimize interconnect delays. Placement is typically divided into two stages:

![Screenshot (536)](https://github.com/user-attachments/assets/5eb04d3f-8f95-492b-a15a-8a1a5ac9bcfa)

   1) **Global Placement:** In this initial stage, cells are roughly positioned within the core area, balancing timing and congestion 
           constraints. It provides a broad view of the netlist but may not strictly adhere to all placement rules.
   2) **Detailed Placement:** Here, the exact routes and layers for each netlist are determined, ensuring valid routing while 
           optimizing for area and timing constraints. Minimizing vias and power consumption are also key objectives in this stage.

![Screenshot (538)](https://github.com/user-attachments/assets/2ba3d11a-e854-4032-bc13-1de6e3ed9065)

### Clock Tree Synthesis (CTS): 
- Before signal routing, the clock must be routed. Clock tree synthesis ensures that the clock is distributed to all sequential 
  elements, such as flip-flops and registers. The clock network resembles a tree, with the clock source at the root and the sequential 
  elements at the leaves. The goal of CTS is to minimize clock skew while ensuring the clock network maintains good shape and 
  performance. Typically, H-trees or X-trees are used to reduce skew, with some devices offering specialized global routing resources to 
  further optimize clock signal distribution.
  
    **Clock Skew & Clock Jitter :** Clock skew is two different flip flops receive the clock signal at slightly different times due to 
      differences in clock net length but clock jitter is on the same flip flop but the position of the clock edge moves edge to edge 
      due to some noise in oscillator. 

![Screenshot (539)](https://github.com/user-attachments/assets/19b6e017-d831-4220-a491-8fed042befff)

### Routing: 
- Once the clock is routed, the signal routing begins. This involves making physical connections between signal pins using metal layers. 
  Signal routing is divided into two parts:

  1) **Global Routing:** This step generates guides for routing the signals.

  2) **Detailed Routing:** The actual physical connections (wires) are implemented using these guides. Special attention is given 
       to the clock and power/ground nets. The Sky130 PDK defines six routing layers, with the lowest being the local interconnect 
       layer made of titanium nitride, and the remaining five layers being aluminum.

![Screenshot (541)](https://github.com/user-attachments/assets/12ce3eed-42f4-47ad-bea3-013b2505f423)

- As the Routing grid is huge,  A divide-and-conquer approach is used to handle the large routing grids effectively. first global 
  routing is performed then detail routing uses the fine grids and the routing guides to implement the actual wiring.

![Screenshot (543)](https://github.com/user-attachments/assets/92e56365-c494-4b69-a698-453fa4789d8d)


### Sign-Off: 
- After routing, the final layout is constructed, and the design enters the verification phase. There are two key types of verification:

   1) **Physical Verification:** This checks the design for adherence to fabrication rules through Design Rule Checking (DRC) and 
        Layout vs. Schematic (LVS) verification.

   2) **Timing Verification:** Static Timing Analysis (STA) ensures that the design meets timing constraints across all operating 
        conditions.

![Screenshot (542)](https://github.com/user-attachments/assets/c49d4e33-1907-4195-b0f9-d9478a065d86)


## L3 & L4 - Introduction to OpenLANE detailed ASIC design flow and Strive chipsets

OpenLANE is an advanced, open-source framework designed for automating the ASIC (Application-Specific Integrated Circuit) design process. It leverages several key open-source tools to guide a design from RTL (Register Transfer Level) to a finalized GDSII layout. Here is a detailed breakdown of the OpenLANE design flow and its tools:

![Screenshot (545)](https://github.com/user-attachments/assets/dc957a22-2262-4499-855d-a0147e9b3488)

### Key Open-Source Tools:
-  Yosys: RTL-to-Gates synthesis tool.
-  ABC: Logic synthesis and optimization tool.
-  OpenROAD: Complete toolchain for physical design automation, including floorplanning, placement, clock tree synthesis, and routing.
-  MAGIC: VLSI layout tool used for Design Rule Checking (DRC) and Layout vs. Schematic (LVS) checks.
-  Netgen: Tool for LVS, comparing SPICE extracted from layout with Verilog netlist.
-  OpenSTA: Static Timing Analysis (STA) tool.
-  KLayout: Layout viewer and editor.
-  Fault: Tool for Design for Test (DFT) tasks, including scan insertion and ATPG (Automatic Test Pattern Generation).
-  Qflow: Toolchain for digital synthesis and placement/routing


### 1. RTL to Logic Circuit Conversion:
-  Tool: Yosys
-  Process: The design starts with RTL code, which is processed by Yosys. Yosys translates the RTL description into a logic circuit         representation using various digital components.
-  Optimization and Mapping: This logic circuit is then optimized and mapped into standard cells from a synthesis library using ABC. ABC    requires guidance via an ABC Script, which defines synthesis strategies aimed at either minimizing area or optimizing timing. The        selection of strategies depends on design objectives.
  
### 2. Synthesis Exploration:
-  Purpose: To evaluate different synthesis strategies and their impact on design delay and area.
-  Utility: The Synthesis Exploration Utility generates reports that compare the effects of various strategies. These reports help          identify the most effective strategy for the design.
  
### 3. Design Exploration and Regression Testing:
-  Tool: Design Exploration Utility
-  Process: This utility performs design configuration sweeps to identify optimal settings. It produces reports showing the design          matrix and layout violations. This exploration is crucial for finding the best configurations and is also used for regression testing    by comparing results from approximately 70 designs against established benchmarks.
  
### 4. Design for Test (DFT):
-  Tool: Fault
-  Purpose: To prepare the design for testing post-fabrication. This optional step includes:
   -  Scan Insertion: Incorporates scan chains to facilitate testing.
   -  Automatic Test Pattern Generation (ATPG): Creates test patterns for the design.
   -  Test Pattern Compaction: Reduces the number of test patterns needed.
   -  Fault Coverage and Simulation: Ensures comprehensive fault coverage and simulates test patterns to verify design functionality.

![Screenshot (546)](https://github.com/user-attachments/assets/52bb1616-3b20-44c7-a58f-41ceadc41181)
     
### 5. Physical Implementation (Place and Route - PnR):
-  Tool: OpenROAD
-  Steps:
    -  Floor/Power Planning: Defines the chip layout and plans power distribution across the design.
    -  End Decoupling Capacitors and Tap Cells Insertion: Adds capacitors and tap cells to enhance performance and reliability.
-  Placement:
    -  Global Placement: Initial placement of cells to address congestion and timing.
    -  Detailed Placement: Fine-tunes cell positions to meet precise timing and routing constraints.
    -  Post Placement Optimization: Further optimization after initial placement to improve performance.
-  Clock Tree Synthesis (CTS): Distributes the clock signal to all sequential elements like flip-flops and registers.
-  Routing:
    -  Global Routing: Establishes general routing paths for connections.
    -  Detailed Routing: Finalizes metal tracks to connect standard cells, macros, and I/O pins.
      
### 6. Logic Equivalence Checking (LEC):
-  Tool: Yosys
-  Purpose: To ensure that the netlist resulting from physical implementation is functionally equivalent to the original gate-level         netlist from synthesis. This is crucial as the netlist may be modified during various stages of physical implementation.
  
### 7. Antenna Rule Violation Handling:
-  Process: Metal wires can act as antennas, accumulating charges that can damage transistor gates during fabrication.
-  Preventive Approach: Fake Antenna Diode Insertion Script adds fake antenna diodes next to each cell input after placement. An antenna    checker (MAGIC) runs on the routed layout. If violations are found, fake diodes are replaced with real ones.

![Screenshot (548)](https://github.com/user-attachments/assets/fe9f7243-6110-4fed-a4cd-1692d8331f17)
![Screenshot (550)](https://github.com/user-attachments/assets/bfdf111f-471d-4e78-ab21-5a3766c289dc)

  
### 8. Final Verification:
-  Timing Verification:
  -  Static Timing Analysis (STA)
      -  Tool: OpenSTA (OpenROAD)
      -  Process: Involves extracting interconnect RC parameters and performing timing analysis to identify any timing violations.                Timing reports are generated to ensure the design meets performance requirements.

![Screenshot (551)](https://github.com/user-attachments/assets/0f7ede8e-29a2-4d9d-aa23-c12ab14f0993)

  -  Physical Verification:
      -  Design Rule Checking (DRC): Conducted using MAGIC to ensure the layout adheres to design rules.
      -  Layout vs. Schematic (LVS): MAGIC and Netgen are used to compare the extracted SPICE model from the layout with the Verilog              netlist. This comparison ensures that the layout matches the intended schematic.
    
-  One of the most exciting aspects of OpenLANE is its integration with **StriVe**, a family of fully open-source System-on-Chips (SoCs)    that utilizes open-source PDKs, EDA tools, and RTL designs. StriVe exemplifies the power of open collaboration, where every layer        of the SoC, from design to fabrication, is accessible to the public.

![Screenshot (544)](https://github.com/user-attachments/assets/02bd6182-67e5-42af-9c24-8de1ca1090a5)
  
-  The ultimate goal of OpenLANE is to generate a clean GDSII file, which is the final representation of the chip design, free from any     issues or violations. When we say “clean,” it means:
    -  No LVS (Layout vs. Schematic) violations: Ensures the layout corresponds correctly to the design schematic.
    -  No DRC (Design Rule Check) violations: Ensures the design complies with the fabrication process rules.
    -  No timing violations: Guarantees that the design meets all timing constraints, which is crucial for the correct operation
    -  high-speed circuits.
-  By integrating these tools and processes, OpenLANE provides a robust, automated flow for ASIC design, ensuring accuracy and efficiency from initial RTL code to final layout.

## Day-1 Using OpenLANE flow and performing synthesis

Objectives: 
1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the flop ratio based on synthesis results.


### Task 1: Running 'picorv32a' Design Synthesis using OpenLANE

Steps to perform synthesis:
  1.Change to the OpenLANE flow directory:

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
  2.(Optional) Set up Docker alias if needed:
  ```bash
alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
```
![image](https://github.com/user-attachments/assets/53f47296-e21b-4049-acda-a1e6a28c6a71)

3.Start the Docker container:
```bash
docker
```
4.Enter OpenLANE interactive mode:
```tcl
./flow.tcl -interactive
```
5.Load the OpenLANE package:
```tcl
package require openlane 0.9
```
6.Prepare the design 'picorv32a':
```tcl
prep -design picorv32a
```
7.Perform the synthesis:
```tcl
run_synthesis
```
8.Exit the OpenLANE flow:
```tcl
exit
```
Synthesis Output:
Below are screenshots showcasing the execution of synthesis:
* Preparation Completion:
  ![image](https://github.com/user-attachments/assets/a5d5b1e7-cfe1-4917-9dad-8bf575f3f1a3)

  

* Synthesis Running:
![image](https://github.com/user-attachments/assets/3f29b930-4a48-42bb-8edb-5fd2fcf3f432)
  


### Task 2: Calculating Flop Ratio
We calculate the Flop Ratio and the percentage of D Flip-Flops (DFF) using the synthesis statistics report.
Formulae:

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100
```
Synthesis Report:
Below is the synthesis statistics report with relevant values highlighted:
![image](https://github.com/user-attachments/assets/082845dd-2f17-400c-a6f0-ce8d87dc3da2)






Values from the Report:
* Number of D Flip-Flops: 1613
* Total Number of Cells: 14876


Calculation:

```math
Flop\ Ratio = \frac{1613}{14876} = 0.108429685
```
```math
Percentage\ of\ DFF's = 0.108429685 * 100 = 10.84296854\ \%
```

![image](https://github.com/user-attachments/assets/bec3a9d0-768f-4626-86af-264f0ecb47ca)

## Section 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cell 

### Implementation
Objectives: 
1.Run 'picorv32a' Design Floorplan Using OpenLANE.

2.Calculate Die Area in Microns.

3.Load Floorplan DEF in Magic Tool.

4.Run Congestion-Aware Placement.

5.Load Placement DEF in Magic Tool.

### Task 1: Run 'picorv32a' Design Floorplan Using OpenLANE.

Steps to perform Floorplan:
  1.Change to the OpenLANE flow directory:

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
  2.(Optional) Set up Docker alias if needed:
  ```bash
alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
```
3.Start the Docker container:
```bash
docker
```
4.Enter OpenLANE interactive mode:
```tcl
./flow.tcl -interactive
```
5.Load the OpenLANE package:
```tcl
package require openlane 0.9
```
6.Prepare the design 'picorv32a':
```tcl
prep -design picorv32a
```
7.Perform the synthesis:
```tcl
run_synthesis
```
8.Run the floorplan step:
```tcl
run_floorplan
```
9.Exit the OpenLANE flow:
```tcl
exit
```

Floorplan Output:
Below are screenshots showcasing the execution of Floorplan:
![image](https://github.com/user-attachments/assets/e485cb97-d9e6-4680-b3b7-7946cadf02ff)

----------



![image](https://github.com/user-attachments/assets/06f090fd-c90b-4123-b007-3b75919b781c)

------------

![image](https://github.com/user-attachments/assets/5cfedad4-1a89-47aa-9226-2635feacdafc)

#### Task 2: Calculate Die Area in Microns.

According to floorplan def

```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```

### Task 3: Load Floorplan DEF in Magic Tool.

Commands to Load Floorplan DEF in Magic:
1.Change directory to path containing generated floorplan def
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/07-09_20-37/results/floorplan/
```
2.Command to load the floorplan def in magic tool
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

![image](https://github.com/user-attachments/assets/584b7f4a-ea74-4118-a748-7508f9492b6f)

* Floorplan Loaded in Magic:

The floorplan DEF file has been successfully loaded into Magic for visualization.
![image](https://github.com/user-attachments/assets/635653ab-baf5-4d90-ae36-d696bbe96229)





* Equidistant Placement of Ports:

This image showcases the equidistant placement of ports, which was configured in the config.tcl file to ensure optimal distribution.

![image](https://github.com/user-attachments/assets/445fa91d-9549-41e2-ad95-738d15fb3e1e)

![image](https://github.com/user-attachments/assets/66ed8ac8-65b9-49ca-9ac6-7610c1235be6)

### Task 4:Run Congestion-Aware Placement.

Command to run placement
```bash
run_placement
```
* Placement Completion:


  The placement run has successfully completed, with the design placed according to congestion and timing constraints.
  ![image](https://github.com/user-attachments/assets/c56d4a51-9483-4ceb-9aa8-a3086bda80fd)

  

### Task 5: Load Placement DEF in Magic Tool.
To load the generated placement DEF file in the Magic tool, use the following commands in a separate terminal:
Commands to Load Placement DEF in Magic
1.Navigate to the directory containing the placement DEF file:
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/07-09_20-37/results/placement/
```
2.Load the placement DEF in Magic:
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech \
lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
* Placement DEF Loaded in Magic
  
  The placement DEF file has been successfully loaded into Magic, showing the placement of standard cells and other components.
  ![image](https://github.com/user-attachments/assets/9c73ea5b-536c-4852-a8bb-0d625d0ba085)


* Legally Placed Standard Cells
  
  This screenshot shows the standard cells placed legally according to the design rules, ensuring a functional and optimized layout.

  ![image](https://github.com/user-attachments/assets/52b76d9d-ea48-4e72-9827-262c903b2b67)



Commands to exit from current run

```tcl
# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

## Section 3 - Design library cell using Magic Layout and ngspice characterization 

### Implementation

Objectives: 

1.Clone the GitHub repository for the Standard Cell Design and Characterization using the OpenLANE flow: [Standard cell design](https://github.com/nickson-jose/vsdstdcelldesign).

2.Open the custom inverter layout in Magic for inspection and exploration.

3.Perform SPICE extraction of the inverter design using Magic.

4.Modify the SPICE model file for further analysis and simulation.

5.Conduct post-layout simulations using ngspice.

6.Rise and Fall Transition Time Calculations.

7.Cell Delay Calculations.

8.Correcting DRC Errors in SkyWater SKY130 Process Using Magic VLSI Layout Tool.

### Task 1: Cloning Custom Inverter Standard Cell Design from GitHub Repository
1.Navigate to the OpenLANE working directory:

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
  2.Clone the custom inverter design repository
  ```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign
```
3.Move into the repository's directory
```bash
cd vsdstdcelldesign
```
4.Copy the Magic tech file for easier access
```bash
cp ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .
```
5.Verify the contents of the directory
```bash
ls
```
6.Open the custom inverter layout in Magic
```bash
magic -T sky130A.tech sky130_inv.mag &
```

Ensure that you have successfully cloned the repository and opened the custom inverter layout using Magic for further exploration. The screenshot of the commands run is also shown below.

### Task 2: Open the custom inverter layout in Magic for inspection and exploration.

After opening the custom inverter layout into Magic, the design exploration can be conducted by identifying critical components and connections, including NMOS, PMOS, and various signal paths.
* Steps:
  1.Load the layout in Magic:
  ```bash
  magic -T sky130A.tech sky130_inv.mag &
  ```

  ![image](https://github.com/user-attachments/assets/8f6c2d21-eb5c-44e0-947e-469e9a6f03c2)


  ![image](https://github.com/user-attachments/assets/16f4a4a3-af38-4f27-9772-b20a4df3b504)


    2.NMOS and PMOS Identified:
  * Both NMOS and PMOS transistors were identified within the layout. Screenshots of these are provided below.

    ![nmos](https://github.com/user-attachments/assets/4729a844-f352-4b25-9b40-79412e2609ed)

    ![pmos](https://github.com/user-attachments/assets/8ede3280-0270-44a7-9073-e8906eacd4cc)

  3.Verification of Output (Y) Connectivity to PMOS and NMOS Drain:
  * The connectivity from the output Y to the PMOS and NMOS drains was checked and verified.

    ![y output](https://github.com/user-attachments/assets/a8975c27-de7a-4a42-8a24-214b5c31e9ac)
    

  4.PMOS Source Connectivity to VDD (VPWR) Verified:
  
  * The source of the PMOS was verified to be correctly connected to VDD (VPWR).

   ![vdd](https://github.com/user-attachments/assets/697efc0c-addb-4024-8fac-5cbb75b7f856)


  5.NMOS Source Connectivity to VSS (VGND) Verified:

  * The source of the NMOS was verified to be connected to VSS (VGND).
 
   ![vss](https://github.com/user-attachments/assets/a0d858c7-6cff-4bc8-a316-a5451b4fa543)


  6.Testing DRC Errors:

  * A portion of the layout was deliberately deleted to trigger a DRC (Design Rule Check) error, and the tool successfully flagged the error.
 
    ![drc error](https://github.com/user-attachments/assets/61913715-91cd-493a-86af-83400e8f28da)
    
### Task 3: Perform SPICE extraction of the inverter design using Magic.
To extract the SPICE netlist from the custom inverter layout in Magic, follow these steps in the tkcon window:

Commands for SPICE Extraction:
1.Check the current directory
```bash
pwd
```
2.Extract the layout into .ext format
```bash
extract all
```
3.Enable parasitic extraction (capacitance and resistance thresholds set to 0 for full extraction)
```bash
ext2spice cthresh 0 rthresh 0
```
4.Convert .ext file to SPICE format
```bash
ext2spice
```
Screenshots:

1.TKcon window after running extraction commands:

![extract spice](https://github.com/user-attachments/assets/5d43cd61-3f33-4392-8e5c-44c1d97831b7)

2.Generated SPICE file:

![extract spice file](https://github.com/user-attachments/assets/a3d6cf78-e031-40e1-ac32-f60bbe901a19)

### Task 4: Modify the SPICE model file for further analysis and simulation.
* Measuring Unit Distance in Layout Grid

  Before editing the SPICE model file, ensure the grid spacing and unit distance in the layout are accurate. This will help in verifying and adjusting the extracted device dimensions.

  Screenshot: Measuring unit distance in layout grid

  ![box](https://github.com/user-attachments/assets/80ee2f3f-30f6-401b-9bd0-94a9e2b4c215)


* Final Edited SPICE File for ngspice Simulation

  After extracting the SPICE file, review and edit it as needed for ngspice simulation. Ensure that the netlist includes accurate connections and the appropriate device models for the Skywater 130nm process.

* Screenshot: Edited SPICE file

![edited](https://github.com/user-attachments/assets/3dbad5c8-479f-4b1a-b2d5-d013a64f11ee)




### Task 5: Conduct post-layout simulations using ngspice.

* Running the SPICE Simulation

  To run a post-layout simulation in ngspice, use the following commands to load the SPICE file and plot the output.

  1.Load the SPICE file into ngspice
  ```bash
  ngspice sky130_inv.spice
  ```
  2.Plot output y vs time a (input)
  ```bash
  plot y vs time a
  ```


* Screenshot: Running the ngspice simulation


  
![ngspice](https://github.com/user-attachments/assets/ccdd6206-2f49-4069-a8be-29174eebdbe7)


![plot](https://github.com/user-attachments/assets/6abc4893-da8c-4f58-b3ff-3aba8245c31d)


  
* Screenshot: Generated plot

  
![graph1](https://github.com/user-attachments/assets/56d9f6d4-bf24-4601-9dd2-438c91795873)



### Task 6:  Rise and Fall Transition Time Calculations:

1. Rise Transition Time Calculation:

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

* Screenshots: 20% Output

![rise20](https://github.com/user-attachments/assets/d2fa1c0b-ddcc-497b-b422-61307910e4c1)

![rise20terminal](https://github.com/user-attachments/assets/a4c0d720-2e34-4720-8c4e-5c0065610020)



* Screenshots: 80% Output


![rise80](https://github.com/user-attachments/assets/c9b1d67d-5d08-4c98-8afe-9323ec508834)

![rise80terminal](https://github.com/user-attachments/assets/a66d15b6-44d9-407c-9d74-3f967caaccb6)




```math
Rise\ transition\ time = 2.24592 - 2.18213 = 0.06376\ ns = 63.76\ ps
```

2. Fall Transition Time Calculation:

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

* Screenshots: 20% Output

![fall20](https://github.com/user-attachments/assets/b0f21670-69b3-4a2b-a203-86ce7afb4c5c)

![fall20terminal](https://github.com/user-attachments/assets/c51a5ea2-7160-470c-b63a-053d70842746)



* Screenshots: 80% Output

  ![fall80](https://github.com/user-attachments/assets/f117d411-271d-4aad-8d9b-ce4d0443bd72)

  ![fall80terminal](https://github.com/user-attachments/assets/54fe2768-a796-42d5-80b8-ac23719939b9)


```math
Fall\ transition\ time = 4.09507 - 4.05269 = 0.04238\ ns = 42.38\ ps
```

### Task 7:  Cell Delay Calculations:

1.Rise Cell Delay Calculation:

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```
* Screenshots: 50% Output

![rise50](https://github.com/user-attachments/assets/90eed95b-f9c6-4296-8e93-fcb8cc489ced)

![rise50terminal](https://github.com/user-attachments/assets/83612071-ac89-4a53-a43a-ddfde1f1bc6c)

![rise50terminal2](https://github.com/user-attachments/assets/c7bb50c6-fd17-4655-b179-251eadf4e55e)

   

```math
Rise\ Cell\ Delay = 2.21109 - 2.15 = 0.06109\ ns = 61.09\ ps
```

2. Fall Cell Delay Calculation:
    
```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

* Screenshots: 50% Output

![fall50](https://github.com/user-attachments/assets/5a5b633c-a38d-4726-9241-39533c476307)

![fall50terminal](https://github.com/user-attachments/assets/4a83f82d-4c64-447e-874d-351c5710c390)

  
```math
Fall\ Cell\ Delay = 4.07765 - 4.05 = 0.02765\ ns = 27.65\ ps
```

### Task 8: Correcting DRC Errors in SkyWater SKY130 Process Using Magic VLSI Layout Tool

1.Download and Extract the DRC Test Files

Start by downloading the required test files and extracting them in your home directory.

  1. Change to the Home Directory:

     ```bash
     cd
     ```
  2. Download the Lab Files:

     ```bash
     wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz\
     ```
  3. Extract the Compressed Files:

     ```bash
     tar xfz drc_tests.tgz
     ```
  4. Navigate to the Lab Directory:

     ```bash
     cd drc_tests
     ```
  5. List the Contents of the Directory:
     ```bash
     ls -al
     ```
  
  

  * Screenshots of Commands Executed:

    ![magic_commands](https://github.com/user-attachments/assets/48eef415-2a62-4459-818a-fa5ccbeb127f)

2.View the .magicrc Configuration File

Before proceeding, it’s a good idea to inspect the .magicrc file to ensure that Magic is configured properly.

  * Viewing the .magicrc File:

    
     ```bash
     # Open the .magicrc file in a text editor
     gvim .magicrc
     ```

    ![magicfile](https://github.com/user-attachments/assets/b597ceb6-0454-4926-ac93-76c14bd5c205)

3.Open the Magic Tool with the Updated Tech File

Start Magic in a better graphics mode to view the design and identify DRC violations.

```bash
# Open Magic in XR mode
magic -d XR &
```

4.Fixing Incorrectly Implemented poly.9 Rule

The poly.9 rule defines a minimum spacing rule that was not properly enforced. We will update the DRC rule and verify the correction.

Screenshot of poly rules:


![poly 9 rule](https://github.com/user-attachments/assets/a692e665-8d3d-4d9f-8c06-030f2a905698)

Problem: No DRC violation occurred for spacing < 0.48u as required by poly.9.


![poly 9 error](https://github.com/user-attachments/assets/c653abde-0a3c-4055-ad20-37815b3a2537)

Solution: Update the Sky130 DRC tech file.

Inserting New Commands into sky130A.tech File:

open sky130A.tech file

```bash
gvim sky130A.tech
```

Screenshot after Inserting new commands into sky130A.tech file


![edited poly 9 1](https://github.com/user-attachments/assets/0b9d6289-2db0-49aa-a08e-54903e47e76d)


![edited poly 9 2](https://github.com/user-attachments/assets/97dc33f5-92e3-4d2c-b8e9-23e163678f42)

Commands to Run:

```tcl
# Load the updated tech file
tech load sky130A.tech
```
```tcl
# Run DRC check
drc check

```
```tcl
# Select region with errors and view messages
drc why
```

Post-fix Screenshot:

![poly 9 corrected](https://github.com/user-attachments/assets/df147bb8-70c9-47bd-945f-cf37685c2ea9)

5.Fixing Incorrectly Implemented difftap.2 Rule

The difftap.2 rule was improperly implemented, with no DRC violation for spacing < 0.42u.

Screenshot of difftap rules:

![difftap 2](https://github.com/user-attachments/assets/d9bde2af-03a0-46d6-9d4f-5f6669ecc7a8)

Problem: No violation occurred for difftap spacing < 0.42u.

![difftap error](https://github.com/user-attachments/assets/82625354-1267-45f5-bb10-6320d79d90ee)

Solution: Update the Sky130 DRC tech file.

Inserting New Commands into sky130A.tech File:

![edited difftap 2](https://github.com/user-attachments/assets/04840728-0ba4-4b31-9dc6-94145be686e8)

Commands to Run:

```tcl
# Load the updated tech file
tech load sky130A.tech
```
```tcl
# Run DRC check
drc check

```
```tcl
# Select region with errors and view messages
drc why
```

Post-fix Screenshot:

![difftap corrected](https://github.com/user-attachments/assets/ede865a5-c634-4b5f-8108-8af527ffc36b)

6.Fixing Incorrectly Implemented nwell.4 Rule

The nwell.4 rule, which enforces the presence of a tap within the nwell, was also improperly implemented.

Screenshot of nwell rules:

![nwell 4 rule](https://github.com/user-attachments/assets/55d3fec3-0227-44c0-a70b-73ca6ecf8131)

Problem: No DRC violation occurred even though a tap was missing from the nwell.


![nwell error](https://github.com/user-attachments/assets/ce14dc30-1fe4-4633-afa1-b433bdcd8efd)



Solution: Update the Sky130 DRC tech file.

Inserting New Commands into sky130A.tech File:

![edited nwel 1](https://github.com/user-attachments/assets/65398b05-5cf4-4e76-9a49-200181c51eab)

![edited nwel 2](https://github.com/user-attachments/assets/79c55f1a-65cd-4713-92df-df7be286a766)


Commands to Run:

```tcl
# Load the updated tech file
tech load sky130A.tech
```

```tcl
# Change drc style to drc full
drc style drc(full)
```

```tcl
# Run DRC check
drc check

```
```tcl
# Select region with errors and view messages
drc why
```

Post-fix Screenshot:

![corrected nwell](https://github.com/user-attachments/assets/40f87039-fefe-46ed-8cbe-113875dc8314)






  






































