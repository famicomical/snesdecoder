# SNES Controller Decoder #
Serial to Parallel controller decoder with open drain outputs. no CPU or FPGA.
This board acts as a receiver for the Super Nintendo Controller.
It was designed with open drain outputs to emulate the behavior of an OFF-ON
switch whose two states are either OPEN or conneted to GND.

I use it to drive the button inputs on the IS-NITRO CAPTURE dev console.
With some soldering skills, one could adapt it for any application where up
to twelve switches are to be controlled from a distance.

This repo hosts the KiCAD project files and some documentation

## Principle of operation ##
The SNES controller takes 4 inputs (GND, 5V, CLK, and LATCH) and sends one output for button press data
This board provides power to the controller, a clock signal to drive the it, and a latch to poll the buttons.
The Data output is then passed through the two shift registers which are activated at each polling instance.

The clock is generated using a ring oscillator whose period is set by an external RC time constant. See [Fairchild AN-118](https://www.onsemi.com/pub/Collateral/AN-118.pdf.pdf). 

Detailed info about the SNES contoller can be found on [GameSX](https://gamesx.com/controldata/snesdat.htm)

## Motivation ##
This project was inspired by an [old forum post](https://nfggames.com/forum2/index.php?msg=26296) on NFGgames
I wanted to use my SNES controller on other consoles, but I felt a universal computational machine would be 
overkill for accomplishing that. All of the existing solutions that I'm aware of use custom logic. 
With discrete components that don't require programming, this design is trasparent about what it does, and is
reminiscent of the simpler times when transistors were more expensive and packaging less so by comparison :P
