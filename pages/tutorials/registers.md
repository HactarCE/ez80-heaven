---
layout: page
title: Tutorial #1 - The Registers
permalink: /tutorials/registers.html
---

In the world of assembly, there are four main ways to store data:

Storage Type | Description/Use | Advantages | Disadvantages
--- | --- | --- | ---
AppVars | Long-term storage | Persistent between programs, can be archived for resistance against RAM clears | Somewhat difficult to set up and relatively slow to write to
SafeRAM | A large section of RAM which is safe to be used by your program | Easy to use; consistent within the program; lots of space | Filled with nonsense between program runs; not the fastest thing in the universe; must be allocated beforehand
The stack | A section of RAM used by the `push` and `pop` commands | SUPER easy and pretty quick to use; plenty of space (If you manage to overflow the stack then you are seriously overusing it) | Only useable linearly, ie. you can only push a value onto the top of the stack and only pop a value from the top of the stack; one too many `push` or `pop` could be fatal.
The registers | 1-byte, 2-byte, or 3-byte memory units handled by the processor that are designed for short-term storage and arithmetic | VERY fast; usable in arithmetic; can be pushed/popped to the stack for slightly longer-term storage | Very few registers; many ROM calls destroy some registers; only usable for short-term storage

For now, we will be talking about the registers and stack, the two short-term ways to store data. Much of assembly programming is simply managing the registers and occasionally storing the data in the RAM or AppVars. There are seven main 8-bit (1-byte) registers you will use in eZ80 assembly. They are `A`, `B`, `C`, `D`, `E`, `H` and `L`. (There's also `F`, but you cannot directly manipulate it so nobody really cares about it.)

* `A` is called the "*a*ccumulator" and is used for general 8-bit arithmetic
* `F` is the *f*lags register, and is never used in its 8-bit form
* `B` is often used as an 8-bit counter
* `C` is a miscellaneous 8-bit register more often than not paired with `B`
* `D` is a miscellaneous 8-bit register more often than not paired with `E`
* `E` is a miscellaneous 8-bit register more often than not paired with `D`
* `H` is a miscellaneous 8-bit register more often than not paired with `L`
* `L` is a miscellaneous 8-bit register more often than not paired with `H`
* `IXH` is an 8-bit register almost always paired with `IXL`
* `IXL` is an 8-bit register almost always paired with `IXH`
* `IYH` is an 8-bit register almost always paired with `IYL`
* `IYL` is an 8-bit register almost always paired with `IYH`

These registers are organized into register pairs, called (quite appropriately) `AF`, `BC`, `DE` and `HL`.

Logic dictates that if `B` is an 8-bit register and `C` is an 8-bit register, then `BC` is a 16-bit register pair, right? Nope. This is the most important change from the Z80 processor. `BC` is actually 24-bits. There is a magical 8-bit `BCU` _thing_ that is the upper 8 bits of `BC`. You can't manipulate it directly, but you can access it by `LD`ing something into `BC` or by doing math on `BC`. So `BC` ≠ `B` + `C`. `BC` = `BCU` + `B` + `C`. The same goes for `DE` and `HL`, but not `AF`. `AF` is not really a typical register pair. `A` and `F` are quite different, actually.

* `A` is called the "*a*ccumulator" and is used for general 8-bit arithmetic
* `F` is the "*f*lags" register (We'll talk more about this later on)
* `BC` is sometimes referred to as the "*b*yte *c*ounter"
* `DE` is sometimes used as the "*de*stination" for an operation
* `HL` is the general-use 24-bit register pair for arithmetic or locating stuff like images or text
* `IX` and `IY` are the "*I*ndex registers" (completely unrelated to `I` and `R` later on) usually used to store memory locations (Don't worry about `IX` and `IY` for now)

There are other registers too. Most of them aren't really very important for now, but here's a brief description of what they are:

* `I` is the 8-bit interrupt vector (used to configure interrupts; don't worry about it for now)
* `R` is the 8-bit refresh register (can be used to generate random numbers)
* `MB` is an 8-bit register and stands for "*MB*ase" or "*M*emory *B*ase" and is used when operating in Z80/non-ADL mode (more on this in later tutorials)
* `PC` is the 24-bit program counter and points to the currently executing command
* `SP` is the 24-bit stack pointer and points to the top of the stack (more on that later)

For now, all that really matter are `A`, `F`, `B`, `C`, `D`, `E`, `H` and `L` (and their combined forms of `AF`, `BC`, `DE`, and `HL`). When a page on this site refers to "any 8-bit register" it really means the main 7 registers, not including `F` unless explicitly stated.

---

To load a value into a register, you use the `LD` command.
`LD A,42`
This loads the decimal number 42 into register `A`. If you are used to computer programming, think of load like this: `LD X,Y` is like `X = Y`. So *the second operand is loaded into the first*. Any of the 7 common 8-bit registers (`A`, `B`, `C`, `D`, `E`, `H` and `L`) can be loaded into each other. So `LD H,C` is perfectly legal, as is the opposite, `LD C,H`. You can also load any number from 0-255 into any of these 8-bit registers just as in the first example.

You can also load values into the 24-bit register pairs `BC`, `DE` and `HL` (but not `AF`). When you load a-- `REDACTED`

This tutorial has been suspended temporarily. It will be continued whenever I feel like continuing it. For now, check out Z80 Heaven's tutorial on the same subject, but for the Z80: http://z80-heaven.wikidot.com/the-registers-and-memory
