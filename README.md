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
