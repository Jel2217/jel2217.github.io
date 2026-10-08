---
title: QSAT picosatellite payload
description: A picosatellite payload that detected its release from the rocket and took a photo on a film camera at apogee. I led the electrical design, and it worked on launch day.
order: 2
when: Summer 2024/25
context: Team of five students
role: Electrical design lead
status: Flown, worked as intended
tags: [Altium, 4-layer PCB, MSP430, ESP32, Servos]
image: /assets/img/projects/qsat-launch.jpg
image_alt: Two rockets lifting off from a field under a blue sky
image_caption: Launch day.
gallery:
  - src: /assets/img/projects/qsat-payload-camera.jpg
    alt: A compact film camera being fitted into a red 3D-printed mount labelled QSAT, with wired electronics beside it
    caption: The film camera going into its 3D-printed mount.
  - src: /assets/img/projects/qsat-aerial-1.jpg
    alt: Aerial view of farmland from high above
    caption: Taken from the payload during the flight.
  - src: /assets/img/projects/qsat-aerial-2.jpg
    alt: Aerial view of fields and farm tracks from high above
    caption: Another shot from the flight.
---

QSAT was a team of five students designing a picosatellite payload. Its job was to take a photo with a film camera at apogee.

I led the electrical design: the circuit design, a four-layer PCB in Altium, and assembling the full board.

The logic started out on an MSP430 and later moved to an ESP32. The payload detected its release from the rocket and triggered servos to take the shot on the film camera (yes, an actual film camera), with an ESP-Cam as a backup.

On launch day it worked as intended.
