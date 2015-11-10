In the world of assembly, there are four main ways to store data:

Storage Type | Description/Use | Advantages | Disadvantages
--- | --- | --- | ---
AppVars | Long-term storage | Persistent between programs, can be archived for resistance against RAM clears | Somewhat difficult to set up and relatively slow to write to
SafeRAM | A large section of RAM which is safe to be used by your program | Easy to use | Filled with nonsense between program runs; not the fastest thing in the universe; must be allocated beforehand
The stack | A section of RAM used by the `push` and `pop` commands | SUPER easy and pretty quick to use | Only useable linearly, ie. you can only push a value onto the top of the stack and only pop a value from the top of the stack
The registers | short-term 1-byte, 2-byte, or 3-byte memory units handled by the processor | VERY fast; usable in arithmetic; can be pushed/popped to the stack for slightly longer-term storage | Very few registers; many ROM calls destroy some registers; only usable for short-term storage

For now, we will be talking about the registers and stack, the two short-term ways to store data. Much of assembly programming is simply managing the registers and occasionally storing the data in the RAM or AppVars. There are seven main 8-bit (1-byte) registers you will use in eZ80 assembly. They are `A`, `B`, `C`, `D`, `E`, `H` and `L`. (There's also `F`, but you cannot directly manipulate it so nobody really cares about `F`.) These registers are organized into register pairs, called (quite appropriately) `AF`, `BC`, `DE` and `HL`
