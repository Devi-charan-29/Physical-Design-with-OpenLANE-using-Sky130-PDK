# Physical-Design-with-OpenLANE-using-Sky130-PDK
This project was completed for the VLSI System Design Corporation's "Advanced Physical Design using OpenLANE/Sky130" course. This project uses Skywater 130nm PDK and Openlane to run an entire RTL to GDSII sequence for the PicoRV32a SoC. Additionally employed in the flow are standard cells with a custom design and Sky130 PDK. There are timing optimisations made. Violations of slack are eliminated. DRC is confirmed.
Inside a chip:
The chip is interfaced to the outside world using pads, from there the chip is accessed with different signals.

The core is where the digital logic of the ASIC sits.

The Die is the size of the package or the skeleton for the IC.

The IC would generally consist an SoC, SRAM, PLLs (to divide or multiple the main clock frequency), ADC and DAC blocks in order to communicate with the outside world which is analog and couple of more blocks. The blocks are called Foundry IPs (Foundry intellectual property).

Foundry is where the chips are manufactured and their research gives us the PDKs according to which the ICs are designed. The Foundry IPs are proprietary and since the research costs a lot of money, the PDKs are highly confidential; although there are open source PDKs such as Skywater130, which is a 130nm process node meaning the channel length between the source and drain is 130nm. Currently there are ICs which has 5nm process node.

Macro is a purely digital logic that is designed using a Hardware Description language, for ex. the SoC shown in the figure is a Macro.

💡 Communication with the foundry is very important even for embedded designs, because for an SoC with same functionality having different process node could cause signal integrity issues for a PCB as rise time would be different for SoCs manufactured with different process node; so for the already tested and working PCB with the SoC manufactured with 130nm process node would cause signal integrity issues if the SoC is replaced with SoC manufactured with 7nm process node. Hence the decisions are to be made keeping in mind what the foundry offers.
