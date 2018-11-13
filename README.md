## This project has been merged in to the drcf2018 project see:
[drcf2018] (https://github.com/cwmaloney/drcf2018)

# GridzillaTransform
This project provides a javascript class that will transform a screen buffer to ArtNet data for the Gridzilla light display.

## Assumptions
The screen buffer uses a logical X,Y coordinate system where the origin is in the lower left corner.   
Logically, the format of the screen buffer is a two dimensional array where each cell contains a 3 eleemnt array of RGB values.  
The screen buffer is represented by a object that has the method `getPixelColors(x, y)` which returns a 3 element array;
The screen buffer has a resolution of 168 x 36.  All coordinate values are positive.  The lower left most posistion is (0, 0).  
The upper right most position is (167, 35).

The Gridzilla layout is as follows:
There are 3 controllers and a total of 36 universes arranged as follows:

```
 Controller 1   |  Controller 2   |  Controller 3
U01 U02 U03 U04 | U13 U14 U15 U16 | U25 U26 U27 U28
U05 U06 U07 U08 | U17 U18 U19 U20 | U29 U30 U31 U32
U09 U10 U11 U12 | U21 U22 U23 U24 | U33 U34 U35 U36
```

Within a universe, the pixels are arranged in a zig-zag pattern starting in the lower left
and moving upward, as follows:

```
012 013 036 ... 156 157
011 014 035 ... 155 158
... ... ... ... ... ...
002 023 026 ... 146 167
001 024 025 ... 145 168
```

## Tests
Unit tests use the mocha test framework.
To install mocha: `npm install mocha`
To run the tests: `npm test`
Or you can run them from IDE, which will give you the ability to debug.  In VS Code, select the run config 'Mocha Tests'
