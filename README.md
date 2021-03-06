Introduction
============

Electronics Arduino project, to connect an IBM TrackPoint as an external
pointing device via USB.

Features:

  * TrackPoint fully works, incl. buttons.

  * Adjustable sensitivity with potentiometer.

  * Middle button scrolling.

  * An RGB LED cycles, showing how the program loops.


Circuit
=======

![Photos of circuit, front and back][4]

For the schematic, see the included [EAGLE][2] project.

The PS/2 connection is done with a detachable cable. This allows:

  * testing the Arduino code with an external PS/2 mouse,
  
  * using the TrackPoint as a PS/2 mouse directly on a computer (didn't get
    that to work).

Some components were recycled:

  * TrackPoint board: Broken off from the keyboard of an iSeries 1200
    (1161-267), my first ThinkPad (bought in 2000).

  * Button switches: Taken from an old Logitech mouse.
  
  * PS/2 cable: Cut off an old and broken Cherry keyboard.
  
  * Back metal plate: From the keyboard that provided the TrackPoint board.
  
  * Front metal plate: Cut from a plate found inside a ThinkPad X41, then
    drilled.
  
  * M2 screws: From some ThinkPad.
  
  * M2 nuts: Insert nuts found in ThinkPad X41 plastic parts.

For cycling the RGB LED, a decade counter is used, partly as an exercise for
the author.


Arduino code
============

See comments at top of `.ino` file.


Trackpoint PCB
==============

To figure out the pinout of the TrackPoint PCB, the key steps were:

  * I looked at the FFC connecting the ThinkPad's mainboard, the keyboard, and
    the TrackPoint:
    
      + Two wires were dimensioned wider: power supply
      
      + Three lines lead into the keyboard: TrackPoint buttons

  * Using a multimeter and the ThinkPad turned on, I checked the voltage of the
    power supply wires in the FFC: One is ground, one +5V.

  * I connected the broken off board using individual wires to the ThinkPad. By
    trial and error, I figured out that in addition to the power supply, three
    wires are needed (CLK, DATA, RESET).
    
    Fortunately, the keyboard/TrackPoint FCB receptacles in this ThinkPad are
    big enough to hold the FFC plus 0.3 mm copper wire.

  * With the TrackPoint board connected to an Arduino, I figured out by trial
    and error:
    
      + Which wire is CLK, which one is DATA, and which one is RESET?
      
      + Which of the button wires is for LEFT, which one for RIGHT, which one
        for MIDDLE?

TrackPoint PCB soldered to board with 0.3 mm enameled copper wire:

![Photo of TrackPoint on board][1]


License
=======

Copyright (C) 2013 [Felix E. Klee](mailto:felix.klee@inka.de)

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


[1]: images/2013-08-16+02_TrackPoint_annotated.png
[2]: http://en.wikipedia.org/wiki/EAGLE
[3]: https://github.com/feklee/arduino-trackpoint
[4]: images/2013-08-16+02_circuit.jpg
