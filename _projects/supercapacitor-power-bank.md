---
title: Supercapacitor power bank
description: A smart power bank built on a hybrid supercapacitor bank, with a current-mode boost converter, digital PI control on an ATmega328PB, and over-voltage, over-current and over-temperature protection.
order: 4
when: Semester 2, 2026
context: ELECTENG 311, team of eight
role: Full-system schematic in Altium
status: In progress
tags: [UC3843, ATmega328PB, PI control, Altium, USB power]
parts:
  - part: UC3843
    role: Current-mode controller for the 5 V boost converter
  - part: ATmega328PB
    role: Digital PI control, sensing and protection
  - part: Hybrid supercapacitors
    role: Energy storage
---

This is our ELECTENG 311 (Electrical Engineering Design) project. We’re a team of eight, and we’ve committed to the full design: all three subsystems (the charger, the output boost converter and the smart features) plus integrating them.

The bank stores its energy in hybrid supercapacitors. Power comes in over USB micro-B through a linear regulator charger, and a UC3843 current-mode boost converter steps the capacitor voltage up to a regulated 5 V USB-A output. An ATmega328PB runs the digital PI control, and there’s touch control, over-voltage, over-current and over-temperature protection, and UART diagnostics.

The electronics are split across two boards. The protection board (an ATmega328PB at 16 MHz doing the ADC sensing) sends state of charge, state of health, temperature, capacitor voltage and output power to the smarts board over UART at 9600 baud, and the smarts board can send back a shutdown command. An auxiliary power module uses a power mux to pick between USB VBUS and the capacitor bank, and feeds both a 5 V and a 10 V boost converter.

I’m working on the full-system schematic in Altium, which brings all the subsystems together, including the hardware fault-logic network.

## Sizing the capacitor bank

I’m sizing the bank from the worst case. Each cell runs from 3.5 V when full down to 2.5 V when empty, and the boost converter has to deliver its full output at 2.5 V. With each cap rated at 0.655 A and 80% efficiency, that works out to about four caps per amp of 5 V output: 4, 6 or 12 caps for 1 A, 1.5 A or 3 A out.

## Extension

Because we’re a team of eight, a pair from the team also works on an extension. One option we’re looking at is a single bidirectional USB-C port (5 V at 0.5 A in, 5 V at 1.5 A out) to replace the separate micro-B input and USB-A output.
