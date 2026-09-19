---
description: Isn't is beautiful? And YOU made it!
icon: flag-checkered
---

# Full implementation

```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/2/ALU.hdl
/**
 * ALU (Arithmetic Logic Unit):
 * Computes out = one of the following functions:
 *                0, 1, -1,
 *                x, y, !x, !y, -x, -y,
 *                x + 1, y + 1, x - 1, y - 1,
 *                x + y, x - y, y - x,
 *                x & y, x | y
 * on the 16-bit inputs x, y,
 * according to the input bits zx, nx, zy, ny, f, no.
 * In addition, computes the two output bits:
 * if (out == 0) zr = 1, else zr = 0
 * if (out < 0)  ng = 1, else ng = 0
 */
// Implementation: Manipulates the x and y inputs
// and operates on the resulting values, as follows:
// if (zx == 1) sets x = 0        // 16-bit constant
// if (nx == 1) sets x = !x       // bitwise not
// if (zy == 1) sets y = 0        // 16-bit constant
// if (ny == 1) sets y = !y       // bitwise not
// if (f == 1)  sets out = x + y  // integer 2's complement addition
// if (f == 0)  sets out = x & y  // bitwise and
// if (no == 1) sets out = !out   // bitwise not

CHIP ALU {
    IN  
        x[16], y[16],  // 16-bit inputs        
        zx, // zero the x input?
        nx, // negate the x input?
        zy, // zero the y input?
        ny, // negate the y input?
        f,  // compute (out = x + y) or (out = x & y)?
        no; // negate the out output?
    OUT 
        out[16], // 16-bit output
        zr,      // if (out == 0) equals 1, else 0
        ng;      // if (out < 0)  equals 1, else 0

    PARTS:
    // == zx => zxdone == //
    Mux16(a=x, b=false, sel=zx, out=zxdone);

    // == nx => xdone == //
    Not16(in=zxdone, out=antizxdone);
    Mux16(a=zxdone, b=antizxdone, sel=nx, out=xdone);

    // == zy => zydone == //
    Mux16(a=y, b=false, sel=zy, out=zydone);

    // == ny => ydone == //
    Not16(in=zydone, out=antizydone);
    Mux16(a=zydone, b=antizydone, sel=ny, out=ydone);

    // == f => alldone == //
    And16(a=xdone, b=ydone, out=xANDy);
    Add16(a=xdone, b=ydone, out=xADDy);
    Mux16(a=xANDy, b=xADDy, sel=f, out=alldone);  

    // == no => out (+ng) == //
    Not16(in=alldone, out=antialldone);
    Mux16(a=alldone, b=antialldone, sel=no, out=out, out=output, out[15]=firstdigit, out[15]=ng);

    // ==> zr //
        // negate the bus (if first digit stays the same then zr=1)
    Not16(in=output, out=antiout);
    Inc16(in=antiout, out[15]=firstinvdigit);

        // NOR = true only if both are the same
    Or(a=firstdigit, b=firstinvdigit, out=antizr);
    Not(in=antizr, out=zr);
}
```
