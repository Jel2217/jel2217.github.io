---
title: Flappy Goose
description: A Flappy Bird-style game written entirely in VHDL for a Cyclone V FPGA, with a scrolling background, sprite physics and randomly generated pipes.
order: 6
when: 2026
context: COMPSYS 305
tags: [VHDL, Cyclone V, Quartus, State machines]
---

Flappy Goose is a game built in hardware for COMPSYS 305. It’s written in VHDL and runs on a Cyclone V FPGA, built in Quartus.

The design is split into modules:

- pipe generation, using a Galois LFSR for randomness, along with collision detection, scoring and power-up logic
- a scrolling background stored in MIF-based ROM
- the goose sprite, with its own physics
- a text overlay drawn from a bitmap font ROM
- a game state machine, and a renderer MUX that picks what gets drawn in each state

Part of the work was estimating the FPGA resources the design needs: logic elements and ALMs, M9K/M10K memory blocks, and the PLL configuration.
