---
title: Band cue lights
description: A wired cue light system for the Engineering Revue band. Four piano sustain pedals drive up to 20 lights on music stands, over Cat5 rather than crowded wireless.
order: 5
when: Semester 2, 2026
context: Personal project for the Engineering Revue
tags: [ESP32, SMPS, PCB design, Cat5, 3D printing]
---

Theatre cue light systems are expensive, so I designed one for the Engineering Revue band instead.

A central controller takes four piano sustain pedal inputs and drives up to 20 cue lights. It’s a single PCB with its own switch-mode supply and one ESP32 driving all the signals.

The lights mount on music stands, up to about 10 m from the controller. They’re passive units: the controller switches DC down Cat5e cable, with daisy-chained connection points for the full band. Going wired avoids the congested RF bands that wireless theatre gear has to deal with, although there’s an optional ESP-NOW wireless link for remote units.

The enclosures are 3D-printed in PETG.
