# Renderific
An SVG renderer for Atari 8-bit computers, written in Turbo-BASIC XL

Renderific 1.0 - Readme
===================
Renderific is an SVG renderer for Atari 8-bit computers, written in Turbo-BASIC XL. It tries to parse SVG Tiny files and draw them on screen and/or on an Atari 1020 plotter.

Sample output:

![Sample Image 1 - flower](https://github.com/savetz/Renderific/blob/master/sample_images/renderific1.png)
![Sample Image 2 - curve](https://github.com/savetz/Renderific/blob/master/sample_images/renderific2.png)
![Sample Image 3 - triangle maze](https://github.com/savetz/Renderific/blob/master/sample_images/renderific3.png)
![Sample Image 4 - Atari 800 logo](https://github.com/savetz/Renderific/blob/master/sample_images/renderific4.png)
![Sample Image 5 - woodsy scene from Transylvania game](https://github.com/savetz/Renderific/blob/master/sample_images/renderific5.png)
![Sample Image 6 - ANTIC podcast logo](https://github.com/savetz/Renderific/blob/master/sample_images/renderific6.png)
![Sample Image 7 - circuit diagram](https://github.com/savetz/Renderific/blob/master/sample_images/renderific7.png)
![Sample Image 8 - twisted polygon](https://github.com/savetz/Renderific/blob/master/sample_images/renderific8.png)

It is copyright 2019 by Kevin Savetz (@KevinSavetz) and released under the MIT license.

The SVG Tiny spec is at https://www.w3.org/TR/SVGTiny12/ 

Thanks to @PneumaticDeath for help on the Bézier math, and @BillLange1968 for plotter testing.

Fun places to get/make SVGs:
Mazes: http://www.mazegenerator.net

Flowers: https://bleeptrack.itch.io/overflower

Twisted Polygon Generator: https://msurguy.github.io/polygon-tool/

Flags: https://github.com/lipis/flag-icon-css

Bugs and things
---------------
I've found some SVGs that seem to intentionally draw in negative regions. I'm not sure what their intention is - is the viewport moved to include part of the negative quadrants? Anyway, Renderific doesn't support that. Many of the SVG flags at https://github.com/lipis/flag-icon-css do this. (I'm looking at you, Djibouti and Bouvet Island.)

I kind of wanted to add the "a"rc path command, although it is not in SVG Tiny. It looks complicated.
https://www.w3.org/TR/SVG11/paths.html#PathDataEllipticalArcCommands

It doesn't handle FILLs. 

I did not support the SVG TEXT command while rendering to the plotter. It's probably easy to add but given the other plotter issues I thought it best to wait.

The program really wants the file to end with &lt;/svg&gt;, otherwise you'll get an EOF error.

If any single command in the SVG file (e.g. very long PATH commands) exceeds the DIMensioned length of A$ (10000 characters) the program will crash.

However, the program should nicely handle SVG files with any type of line ending, e.g. Atari, Mac, Windows, whatever.
