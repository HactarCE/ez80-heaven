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

For now, we will be talking about the registers and stack, the two short-term ways to store data. Much of assembly programming is simply managing the registers and occasionally storing the data in the RAM or AppVars. There are seven main 8-bit (1-byte) registers you will use in eZ80 assembly. They are `A`, `B`, `C`, `D`, `E`, `H` and `L`. (There's also `F`, but you cannot directly manipulate it so nobody really cares about it.) These registers are organized into register pairs, called (quite appropriately) `AF`, `BC`, `DE` and `HL`.

Logic dictates that if `B` is an 8-bit register and `C` is an 8-bit register, then `BC` is a 16-bit register pair, right? Nope. This is the most important change from the Z80 processor. `BC` is actually 24-bits. There is a magical 8-bit `BCU` _thing_ that is the upper 8 bits of `BC`. You can't manipulate it directly, but you can access it by `LD`ing something into `BC` or by doing math on `BC`. So `BC` ≠ `B` + `C`. `BC` = `BCU` + `B` + `C`. The same goes for `DE` and `HL`, but not `AF`. `AF` is not really a typical register pair. `A` and `F` are quite different, actually.

`A` is called the "*a*ccumulator" and is used for general 8-bit arithmetic
<br>
`F` is the "*f*lags" register (We'll talk more about this later on)
<br>
`BC` is often referred to as the "*b*yte *c*ounter"
<br>
`DE` is sometimes used as the "*de*stination" for an operation
<br>
`HL` is the general-use register pair for arithmetic


