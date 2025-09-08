<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works
The project implements an 8-bit Gray code counter. A Gray code sequence is a special form of binary counting in which only one bit changes between successive states, minimizing switching noise and avoiding errors in applications such as rotary encoders or clock-domain crossings.

The design is split into two main parts:

Binary counter using T flip-flops

The binary counter increments on each clock pulse.

The T input of each flip-flop is driven by the AND of all lower-order outputs (for example, T2 = B0 · B1).

This makes all flip-flops toggle synchronously with the clock, generating an 8-bit binary count.

Binary-to-Gray conversion

The binary counter output is fed into an XOR logic network that produces the Gray code:

G7 = B7

Gi = B(i+1) ⊕ Bi for i = 6 down to 0

The Gray sequence is then available at the output pins, ensuring only one bit changes at a time


## How to test

Simulation

In a simulator such as Logisim, place a clock source connected to the counter input.

Observe the outputs on LEDs or probes.

Verify that the binary counter increments normally and that the Gray outputs change one bit at a time.

Step mode

Use the simulation’s “tick once” feature or a manual clock button to increment step by step.

Record the sequence of outputs and compare them with a Gray code truth table.

Waveform verification (if using ModelSim, Vivado, etc.)

Run the design for several clock cycles.

Check the waveform to ensure that each Gray code output differs from the previous one by exactly one bit.

## External hardware

This project does not require any external hardware beyond the simulation environment. However, for physical implementation on FPGA or breadboard:

Clock source: an oscillator or push-button clock input.

LEDs or seven-segment display: to visualize the Gray code output.

Optional switches: to provide reset or enable signals to the counter.
