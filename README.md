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
