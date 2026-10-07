---
title: Electric Valve Instrument
description: An electronic brass instrument. It measures the player’s air pressure and the frequency of their buzz, works out the pitch they’re aiming for and synthesises the sound in real time.
order: 1
when: 2026
context: Personal project
status: In progress
tags: [STM32, YIN pitch detection, I²S audio, Li-ion power, KiCad]
parts:
  - part: STM32
    role: Microcontroller, running the pitch detection
  - part: PCM5102A
    role: I²S audio DAC
  - part: MAX98357A
    role: Class D amp for the internal speaker
  - part: MCP6002
    role: Op-amp for the mic front end
  - part: BQ24074
    role: Li-ion charger
  - part: TPS63020
    role: Buck-boost converter for the 3.3 V rail
---

The EVI is my attempt at an electronic alternative to the trumpet or horn. It measures the player’s air pressure and the frequency of their buzz, works out the pitch they’re aiming for, and synthesises the sound in real time. It started out as an "electric trumpet" and has since grown into the EVI.

## Proof of concept

The proof of concept runs the YIN pitch detection algorithm on an STM32, along with the signal conditioning and audio output around it. Before settling on YIN I also looked at detecting pitch in hardware with a CD4046 PLL.

YIN runs at 8 kHz, decimated from a 48 kHz ADC. The buffer size is a trade-off between latency and the lowest note it can pick up. With quite aggressive overlap it works out to a floor of around 80 Hz and a pitch update roughly every 32 ms.

Breath is humid, so part of the design is managing airflow around the moisture-sensitive electronics inside the brass piping.

## Hardware

I’ve drawn the schematics in KiCad, including a Li-ion protection circuit that went through several rounds of review.

Power comes from a single 18650 cell. A BQ24074 handles charging and a TPS63020 buck-boost makes the 3.3 V rail. The BQ24074 only covers the charging side, so over-discharge and short circuits on the load side need their own protection circuit. Power on and off is a soft latch through the charger’s SYSOFF pin, with the microcontroller holding the system on through an open-drain output. USB-C passes data through and has CC resistors and ESD protection.

The mic goes through an MCP6002 op-amp stage. It’s biased at mid-rail (1.65 V) and AC-coupled, with a gain stage to suit the ADC’s 0 to 3.3 V range.

The audio side is built around a PCM5102A DAC over I²S, with three outputs: an internal speaker on a MAX98357A Class D amp, a 3.5 mm stereo line out, and MIDI out on a TRS (Type A) jack at 31,250 baud. Mono is summed to stereo in firmware rather than passively, which keeps stereo effects possible later on.

The earlier electric trumpet version had a separate bell module with its own battery, a 12 V boost converter and a TPA3118D2 Class D amp, and a TPS2121 power mux choosing between USB-C, the bell battery and the internal battery.

## What’s next

Next is MIDI: note on and off, 14-bit pitch bend to follow the pitch, and CC2 and CC11 for breath and expression. After that comes a more brass-like sound from wavetable synthesis (summing harmonics in brass-like proportions), through a biquad low-pass filter whose cutoff follows breath pressure. I’m also still choosing a headphone driver.
