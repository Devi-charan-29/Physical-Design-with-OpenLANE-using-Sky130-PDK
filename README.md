# Physical-Design-with-OpenLANE-using-Sky130-PDK
This project was completed for the VLSI System Design Corporation's "Advanced Physical Design using OpenLANE/Sky130" course. This project uses Skywater 130nm PDK and Openlane to run an entire RTL to GDSII sequence for the PicoRV32a SoC. Additionally employed in the flow are standard cells with a custom design and Sky130 PDK. There are timing optimisations made. Violations of slack are eliminated. DRC is confirmed.
# Inside a chip:
The chip is connected to the outside world by pads, and different signals are used to access the chip from there.
The ASIC's digital logic is located at the core.
The Die determines the IC's packaging or skeleton size.
The typical IC would include a SoC, SRAM, PLLs (to double or divide the main clock frequency), ADC and DAC blocks to enable analogue communication with the outside world, as well as a few more blocks. Foundry IPs, or "Foundry intellectual property," are the blocks.

The foundries are where the chips are made, and their research gives us the PDKs that are used to design the ICs. Since the research is expensive and The Foundry IPs are confidential,although there are open source PDKs like Skywater130, which is a 130nm process node, meaning the channel length between the source and drain is 130nm, the PDKs are extremely secret. There are ICs with a 5nm manufacturing node currently available.
Macro, such as the SoC depicted in the diagram, is fully digital logic that is built using a Hardware Description language.

Even for embedded designs, communication with the foundry is crucial because a different process node for a SoC with the same functionality could result in signal integrity problems for a PCB because the rise time for different SoCs manufactured with different process nodes would be different. As a result, the already tested and functional PCB with the SoC manufactured with a 130nm process node would experience these issues.

![Untitled](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/73e010e3-e5d4-4503-aea3-46605c252713)
![Untitled 2](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/1334bc54-9cc6-4d5c-b8bf-4e7b5bd940b9)

#Instruction Set Architecture (ISA)
The interface between a computer system's hardware and software is defined by a collection of guidelines and specifications called the Instruction collection Architecture (ISA). It establishes how a processor interprets and carries out instructions given by software applications. As long as they follow the instructions and rules specified by the ISA, it enables software developers to design programmes without worrying about the specifics of the underlying hardware.

Humans write a piece of code in a comprehensible language, which is then translated into Assembly code in accordance with an ISA. The assembly code is written in hexadecimal digits, which are then translated into binary numbers or the on/off of transistors laid out in a certain way that can run on the specific ISA for which the layout is intended. The bits enter the layout, and the output is produced.

RISC-V ISA is used as an illustration. An HDL language is used to design the ISA's layout, and an RTL description follows. The RISC-V architecture specifications are implemented in the RTL description, and an IC that can execute human-written code is created by following the RTL to GDSII path.

![Untitled 4](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/17a8be77-44eb-49f8-9e64-4ae03cb6310e)

# Hardware and Software Symbiosis
The system software, which consists of the operating system, compiler, and assembler, is used to read the application software. The application software is transformed into hardware-compatible binary code by the system software.

The OS compiles and translates the application programme into assembly code. Apart from memory allocation, processing IO operations, and low-level system tasks like memory management, process management, user interface, task scheduling, power management, error handling and logging, file system administration, networking, etc., this is the OS's primary job.
Small functions written in one of the languages, such as C, C++, Java, VB, etc., are the outputs of an OS. The assembly language code is then generated by compiling these short routines. The Hardware designed, for example, affects the syntax of the assembly code. Different assembly code syntaxes apply to RISC-V and Intel x86 devices, respectively. This syntax is known as ISA. The machine language, or binary language, that is provided to the hardware is converted by the assembler. The device outputs data in accordance with the pattern of the received binary digits.
![Untitled 6](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/151cfe45-c368-4f62-b059-6587d2efe19c)
![Untitled 7](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/79ace2e2-6cff-473a-81fd-8f715aa53939)

# SOC Design and Openlane 

## Components of opensource digital ASIC design
Three enablers or pieces are needed to create a digital Application Specific Integrated Circuit (ASIC): Process create Kit (PDK) data, Electronic Design Automation (EDA) tools, and Resistor Transistor Logic Intellectual Property (RTL IPs).
![124005001-35a32a80-d9f6-11eb-8fcc-0917ad337699](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/a885ba9b-f9a8-4f32-9c05-3dbf48a2f444)
 1. Opensource RTL Designs: github, librecores, opencores
 2. Opensource EDA tools: QFlow, OpenROAD, OpenLANE
 3. Opensource PDK data: Google Skywater130 PDK
### Simplified RTL2GDS Flow

![124006238-a139c780-d9f7-11eb-8da9-6069b055fbe0](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/899ccdf7-663d-4103-bab6-0abfedb9674a)

![131134578-5cd34ec9-a388-476b-aa4b-914c250d7ec9](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/466e980b-2eea-4012-8598-10c964860d52)

1. Synthesis: RTL Converted to gate level netlist using standard cell libraries (SCL).
2. Floor & Power Planning: Planning of silicon area to ensure robust power distribution.
3. Placement: Placing cells on floorplan rows aligned with sites.
4. Global Placement: for optimal position of cells.
5. Detailed Placement: for legal positions.
6. Routing: Valid patterns for wires.
7. Signoff: Physical (DRC, LVS) and Timing verifications (STA).

#### Openlane asic flow

![185787620-8c999b89-2580-477d-aa20-1156d3e996c8](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/68a2dab8-a55b-46cb-9bb1-9574f7134cbc)

![131135115-46148ff1-9489-48f6-a334-6702c25def59](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/e38635b0-bd7b-4301-8e07-1f85715a7bfe)

From conception to product, the ASIC design flow is an iterative process that is not static for every design. The details of the flow may change depending on ECO’s, IP requirements, DFT insertion, and SDC constraints, however the base concepts still remain. The flow can be broken down into 11 steps:

Architectural Design – A system engineer will provide the VLSI engineer with specifications for the system that are determined through physical constraints. The VLSI engineer will be required to design a circuit that meets these constraints at a microarchitecture modeling level.

RTL Design/Behavioral Modeling – RTL design and behavioral modeling are performed with a hardware description language (HDL). EDA tools will use the HDL to perform mapping of higher-level components to the transistor level needed for physical implementation. HDL modeling is normally performed using either Verilog or VHDL. One of two design methods may be employed while creating the HDL of a microarchitecture:

a. RTL Design – Stands for Register Transfer Level. It provides an abstraction of the digital circuit using:

i. Combinational logic
ii. Registers
iii. Modules (IP’s or Soft Macros)
b. Behavioral Modeling – Allows the microarchitecture modeling to be performed with behavior-based modeling in HDL. This method bridges the gap between C and HDL allowing HDL design to be performed

RTL Verification - Behavioral verification of design

DFT Insertion - Design-for-Test Circuit Insertion

Logic Synthesis – Logic synthesis uses the RTL netlist to perform HDL technology mapping. The synthesis process is normally performed in two major steps:

GTECH Mapping – Consists of mapping the HDL netlist to generic gates what are used to perform logical optimization based on AIGERs and other topologies created from the generic mapped netlist.

Technology Mapping – Consists of mapping the post-optimized GTECH netlist to standard cells described in the PDK

Standard Cells – Standard cells are fixed height and a multiple of unit size width. This width is an integer multiple of the SITE size or the PR boundary. Each standard cell comes with SPICE, HDL, liberty, layout (detailed and abstract) files used by different tools at different stages in the RTL2GDS flow.

Post-Synthesis STA Analysis: Performs setup analysis on different path groups.

Floorplanning – Goal is to plan the silicon area and create a robust power distribution network (PDN) to power each of the individual components of the synthesized netlist. In addition, macro placement and blockages must be defined before placement occurs to ensure a legalized GDS file. In power planning we create the ring which is connected to the pads which brings power around the edges of the chip. We also include power straps to bring power to the middle of the chip using higher metal layers which reduces IR drop and electro-migration problem.

Placement – Place the standard cells on the floorplane rows, aligned with sites defined in the technology lef file. Placement is done in two steps: Global and Detailed. In Global placement tries to find optimal position for all cells but they may be overlapping and not aligned to rows, detailed placement takes the global placement and legalizes all of the placements trying to adhere to what the global placement wants.

CTS – Clock tree synteshsis is used to create the clock distribution network that is used to deliver the clock to all sequential elements. The main goal is to create a network with minimal skew across the chip. H-trees are a common network topology that is used to achieve this goal.

Routing – Implements the interconnect system between standard cells using the remaining available metal layers after CTS and PDN generation. The routing is performed on routing grids to ensure minimal DRC errors.

The Skywater 130nm PDK uses 6 metal layers to perform CTS, PDN generation, and interconnect routing.

Opensource EDA tools
OpenLANE utilises a variety of opensource tools in the execution of the ASIC flow:

Task	Tool/s
RTL Synthesis & Technology Mapping	yosys, abc
Floorplan & PDN	init_fp, ioPlacer, pdn and tapcell
Placement	RePLace, Resizer, OpenPhySyn & OpenDP
Static Timing Analysis	OpenSTA
Clock Tree Synthesis	TritonCTS
Routing	FastRoute and TritonRoute
SPEF Extraction	SPEF-Extractor
DRC Checks, GDSII Streaming out	Magic, Klayout
LVS check	Netgen
Circuit validity checker	CVC
OpenLANE design stages
Synthesis
yosys - Performs RTL synthesis
abc - Performs technology mapping
OpenSTA - Performs static timing analysis on the resulting netlist to generate timing reports
Floorplan and PDN
init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
ioplacer - Places the macro input and output ports
pdn - Generates the power distribution network
tapcell - Inserts welltap and decap cells in the floorplan
Placement
RePLace - Performs global placement
Resizer - Performs optional optimizations on the design
OpenDP - Perfroms detailed placement to legalize the globally placed components
CTS
TritonCTS - Synthesizes the clock distribution network (the clock tree)
Routing
FastRoute - Performs global routing to generate a guide file for the detailed router
CU-GR - Another option for performing global routing.
TritonRoute - Performs detailed routing
SPEF-Extractor - Performs SPEF extraction
GDSII Generation
Magic - Streams out the final GDSII layout file from the routed def
Klayout - Streams out the final GDSII layout file from the routed def as a back-up
Checks
Magic - Performs DRC Checks & Antenna Checks
Klayout - Performs DRC Checks
Netgen - Performs LVS Checks
CVC - Performs Circuit Validity Checks
OpenLANE Files
The openLANE file structure looks something like this:

skywater-pdk: contains PDK files provided by foundry
open_pdks: contains scripts to setup pdks for opensource tools
sky130A: contains sky130 pdk files


# Labs
## 1. Initiating Openlane, Design setup stage and synthesis

1. Go to the OpenLane directory using “ cd ” command.
2. Initiate Docker using : docker
3. To strat the openlane : ./flow.tcl -interactive
 
![Untitled 1](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/bb40f722-006c-495c-a2f3-8fc1f8a52f3f)

4. For the packages to be installed we use : package require openlane 0.9

The Picorv32a design is investigated in this case. The source files are already provided in the designs folder, and the design has already been adjusted for the best results. At least three files, src, config.tcl, and sky130A_sky130_fd_sc_hd_config.tcl, are present in the folder.

The verilog files and SDC "Synopsys Design Constraint" file are both located in the src folder. Almost all Synthesis, PnR, and other tools support SDC, a common format for design constraints.

The default settings made by openlane can be changed or overridden by editing the config.tcl file.

sky130A_sky130_fd_sc_hd can be interpreted as (pdk variation)_(pdk)_(foundry)_(standard cell)_(high density). There can be other variations of PDK with acronyms: hdll - ms - ls - hs -
sky130A_sky130_fd_sc_hd_config.tcl file contains another design tweaks that can be done to modify the design.

The priority order is sky130A_sky130_fd_sc_hd_config.tcl > config.tcl > Default configurations.

How to decide priority in:

sky130A_sky130_fd_sc_hd_config.tcl
sky130A_sky130_fd_sc_hdll_config.tcl
sky130A_sky130_fd_sc_ms_config.tcl
sky130A_sky130_fd_sc_ls_config.tcl
sky130A_sky130_fd_sc_hs_config.tcl

### Designing the setup stage
We must set up a file system that is tailored to the flow. The design preparation stage creates the locations needed for the files to be fetched at each phase of the flow. The following command is used:   prep -design picorv32a

The "prep" command is used to create the basic environment, input files, and configurations needed for the succeeding OpenLane flow phases.

The "-design" option or flag is used in conjunction with the "prep" command to define the design that needs to be created. The name of the provided design in this instance is "picorv32a". It means that the environment will be particularly set up for the "picorv32a" design by using the "prep" command.

In this phase, the LEF files at the cell level and the technology level are combined into a single file so that the openlane flow does not need to access several files to obtain data on cell geometry, layers, etc. Cell level LEF defines the physical and electrical characteristics of each individual standard cell inside a given library or cell set, whereas technology level LEF describes the general process technology features. One file called merged.lef is created by merging these two LEF files.

Its initials stand for "Library Exchange Format." The physical and electrical characteristics of library cells or standard cells are described in LEF files. Within the electrical design automation (EDA) toolchain, these files provide crucial information for the physical design stages, such as location and routing.

Cell Geometries: Specifies the dimensions of standard cells, such as their height, breadth, and layer.
The pins and ports connected to each cell are referred to as pins and ports. For metal connections, these definitions provide details about name, direction (input or output), and layer.
Describe the various layers that were employed in the design, such as the diffusion, polysilicon, and metal layers. The name, type, direction, and other attributes of each layer are defined, enabling the physical design tools to comprehend the layers that are accessible for routing and manufacturing.
Information on the site, which is the area or grid that a cell is placed in, as well as its symmetry. To describe the symmetrical characteristics of the cells, they might contain symmetry information. Electrical Information: Capacitance is one of the electrical properties of cells.

![picking up the files](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/e7fa7588-cf04-40c5-8bd9-1dedd064e9a0)


The “ results ” folder will have files generated when different steps such as floor planning, CTS, synthesis etc are performed. Similiarly for reports folder.

This file again has config.tcl shows what parameters have been modified. With every step performed there will be a config.tcl file generated, which will inform about what changes have been made.

![folder is created](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/8c29352d-1796-42a7-8815-9fc3dbaf2ae4)

We can see the results of all folders that are created

![there are separate results for each of them](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/8b295aa3-2a92-43fd-9953-1aa836bc4a53)

The merged.lef file can be accessed in the tmp folder, by using the command:  less merged.lef
to exit we use q 

## Synthesis 

The yosys and ABC tools are utilized to convert RTL to gate level netlist. After the design setup is ready, To run the synthesis and generate gate-level netlist by command: run_synthesis

In the report generated by synthesis, we are interested in chip module area and Flop ratio as of now:

Flop ratio = no. of D-flip flops used/no. of cells used.

here, flop ratio = 1613/14876 = 0.1084

The statistics report of the synthesis is generated in the reports folder in the synthesis directory, and it is accessed using “less” command. The file is named “yosys_4.stat.rpt”

![no of d flipflops](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/e21dba3f-b0e2-4d59-a817-67705a167b71)

The synthesis was succesful

![synthesis successful](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/c5383790-9c31-430e-86bd-f9324d8cb9a3)

## 2. Floorplanning and placement

We are interested in two parameters as of now, Utilisation Factor and Aspect Ratio. They are defined as follows:

Utilisation Factor =  Area occupied by netlist/Total area of core

Aspect Ratio =  Height/ Width
              

A Utilization Factor of 1 signifies 100% utilization leaving no space for extra cells such as buffer. However, practically, the Utilisation Factor is 0.5-0.6. Likewise, an Aspect ratio of 1 implies that the chip is square shaped. Any value other than 1 implies rectangular chip.

Priority order of configuration files to be used by the Openlane flow:

sky130A_sky130_fd_sc_hd_config.tcl

conifg.tcl

floorplan.tcl - System default variables.

The variables we are interested in as of now:

Floorplan environment variables or switches:

FP_CORE_UTIL - floorplan core utilization
FP_ASPECT_RATIO - floorplan aspect ratio
FP_CORE_MARGIN - Core to die margin area
FP_IO_MODE - defines pin configurations (1 = equidistant/0 = not equidistant)
FP_CORE_VMETAL - vertical metal layer
FP_CORE_HMETAL - horizontal metal layer
Note: Vertical metal layer and Horizontal metal layer values will be 1 more than that specified in the files.

After setting the desired variables, to run the picorv32a floorplan in openLANE:

run_floorplan

A.def file will have been produced in the results/floorplan directory following the floorplan run. The switches set in conifg.tcl and sky130A_sky130_fd_sc_hd_config.tcl will have overridden the system defaults, respectively. Using the magic tool, we can examine floorplan files.

Decoupling capacitors: 
Pre-placed cells must then be surrounded with decoupling capacitors (decaps). The resistances and capacitances associated with long wire lengths can cause the power supply voltage to drop significantly before reaching the logic circuits. This can lead to the signal value entering into the undefined region, outside the noise margin range. Decaps are huge capacitors charged to power supply voltage and placed close the logic circuit. Their role is to decouple the circuit from power supply by supplying the necessary amount of current to the circuit. They pervent crosstalk and enable local communication.


![applying decoupling capacitors](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/46f74740-9544-4301-bce6-4c9d8b93d23f)



After navigating to the results/floorplan directory, where the floorplan's.def file is generated, Magic is used to examine the floorplan. It is necessary to specify the location of the PDK's tech lef file, which can be found in the /openlane_working_dir/pdks/sky130A/libs.tech/magic folder. It's vital to note that the command also includes the name of the.tech file; otherwise, the tool won't be able to locate it. The command's syntax is as follows:

magic -T <path to .tech file> read lef <path to .lef file> read def <path to .def file>
 
 The Command is :
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
 
  ![Untitled 6 (1)](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/4aaa43f1-5c4b-4b67-8e73-c46014a6b3b2)

![4 florr planning and showing what is what cell](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/3387077f-a87b-4a1c-82fc-86bde6ea6ceb)

### Placement
 
 Placement is the following stage in the OpenLANE ASIC flow. The floorplan will then be populated with the synthesised netlist. Placement is done in two steps:

Global Positioning: It determines the best position for every cell, even if it may not be legal or if some cells may overlap. Optimisation is carried out by cutting the parameter wire length in half.
Detailed Placement: It moves cells after global placement to make them legal.

#### Placement run on OpenLANE & view in Magic
 The objective of placement is the convergence of overflow value. If overflow value reduces during the placement run it means that the design will converge and placement will be successful. The design can be viewed on magic within results/placement directory:
The command used is : run_floorplan  the magic T used is 
 
magic -T /home/aastha/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
 
 ![8](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/ab80dc6a-197c-4552-9b34-d0560c1bbb39)
 
 
 ![9 standard cellplacements](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/1f66d873-c68e-48b5-bec7-fb117eaaefd9)
 
 ### Standard cell design flow
 Standard cell design flow steps are:

1. Inputs: PDKs, DRC & LVS rules, SPICE models, libraries, user-defined specifications
2. Design steps: Circuit design, Layout design, Extraction of parasitics, Characterization (timing, noise, power)
3. Outputs: CDL (circuit description language), LEF, GDSII, extracted SPICE netlist (.cir), timing, noise and power .lib files

### Standard Cell Characterization Flow
 A typical standard cell characterization flow includes the following steps:

1. Read in the models and tech files
2. Read extracted spice netlist
3. Recognize behavior of the cell
4. Read the subcircuits
5. Attach power sources
6. Apply stimulus to characterization setup
7. Give necessary output capacitance loads
8. Give necessary simulation commands
 
### Timing Parameters
 |slew_low_rise_thr  | 20% value |
 |      :---:        |  :----:   |
 |slew_high_rise_thr | 80% value |
 |slew_low_fall_thr  | 20% value |
 |slew_high_falle_thr| 80% value |
 |in_rise_thr        | 50% value |
 |in_fall_thr        | 50% value |
 |out_rise_thr       | 50% value |
 |out_fall_thr       | 50% value |
 
rise delay =  time(out_fall_thr) - time(in_rise_thr)

Fall transition time: time(slew_high_fall_thr) - time(slew_low_fall_thr)

Rise transition time: time(slew_high_rise_thr) - time(slew_low_rise_thr)
 
## Design Library Cell
 
Users of OpenLANE can instantly modify environment variables. For instance, in the openLANE flow, we could do the following if we wanted to switch the pin location from equidistant to another style of placement:
 
set ::env(FP_IO_MODE) 2
 
## SPICE Deck creation & Simulation

 A SPICE deck includes information about the following:

1. Model description
2. Netlist description
3. Component connectivity
4. Component values
5. Capacitance load
6. Nodes
7. Simulation type and parameters
8. Libraries included
 
 ## 16 Mask CMOS Fabrication 
 
1. Selection of subtrate: Secting the body/substrate material.
2. Creating active region for transistors: Isolation between active region pockets by SiO2 and Si3N4 deposition followed by photolithography and etching.
3. N-well and P-well formation: Ion implanation by Boron for P-well and by Phosphorous for N-well formation.
4. Formation of gate terminal: NMOS and PMOS gates formed by photolithography techniques.
5. LDD (lightly doped drain) formation: LDD formed to prevent hot electron effect.
6. Source & drain formation: Screen oxide added to avoid channelling during implants followed by Aresenic implantation and annealing.
7. Local interconnect formation: Removal of screen oxide by HF etching. Deposition of Ti for low resistant contacts.
8. Higher level metal formation: CMP for planarization followed by TiN and Tungsten deposition. Top SiN layer for chip protection.
 
  ![Schematic-representation-of-a-CMOS-fabrication-process-with-SiGe-MBE](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/3fcb653b-b552-460e-9413-4b10b3a4ca8f)
 
## Inverter Standard cell Layout & SPICE extraction
 
To integrate the CMOS inverter with the picorv32a design, the Magic layout of an inverter will be employed. This is accomplished by cloning the inverter magic file from vsdstdcelldesign and placing it in the openlane_working_dir/openlane directory as shown below:
 
 git clone https://github.com/nickson-jose/vsdstdcelldesign
 
This creates a vsdstdcelldesign named folder in the openlane directory.

To invoke magic to view the sky130_inv.mag file, the sky130A.tech file must be included in the command along with its path. To ease up the complexity of this command, the tech file can be copied from the magic folder to the vsdstdcelldesign folder.
 
 magic -T sky130A.tech sky130_inv.mag &
 
 
![7 itshows the n and p diff regions](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/d5bee43e-ed24-4990-8287-a643f0a450b0)

 
 ![4 mac cmos layout](https://github.com/Devi-charan-29/Physical-Design-with-OpenLANE-using-Sky130-PDK/assets/95524221/54970f50-10a7-412c-9db4-648772fdabd2)
 
The local interconnect layer, or Locali, is the top layer of Sky130.

Verification of P-diffusion and N-diffusion areas with Polysilicon can be seen to see if the architecture is that of a CMOS inverter.

Checking the connections between the drain and source is another verification step. Both PMOS and NMOS must have their sources and drains connected to the power supply VDD (in this case, VPWR) and output port, respectively.

The LEF, or library exchange format, provides information about cell boundaries, VDD lines, and GND lines. It is used to safeguard the IP but does not carry any information about the circuit logic.

The following commands are used in tkcon within the Magic environment to achieve.mag to.spice extraction:
 
extract all
ext2spice cthresh 0 rethresh 0
ext2spice
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 


 






