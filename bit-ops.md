### Bit Operations

These are the most common operations for interacting with data on the bit level. All of the opcodes for these instructions take up two bytes. Assume "any 8-bit register" to be one of `A`, `B`, `C`, `D`, `E`, `H` or `L`

<br>

![][rl] | RL R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate left
Description | Rotates the contents of `r` left by one bit. The leaving (7th) bit is moved into the carry and the carry is moved into the first bit of `r`.

![][rr] | RR R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate right
Description | Rotates the contents of `r` right by one bit. The leaving (0th) bit is moved into the carry and the carry is moved into the last bit of `r`.

![][rlc] | RLC R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate left with carry
Description | Rotates the contents of `r` left by one bit. The leaving (7th) bit is copied into the carry, and into the last bit of `r`.

![][rrc] | RRC R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate right with carry
Description | Rotates the contents of `r` right by one bit. The leaving (0th) bit is copied into the carry, and into the last bit of `r`.

![][sla] | SLA R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Shift left arithmetic
Description | Rotates the contents of `r` left by one bit. The leaving (7th) bit is moved into the carry, and the first bit of `r` is reset.

![][sra] | SRA R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate left
Description | Rotates the contents of `r` right by one bit, but the 7th bit stays the same. The leaving (0th) bit is moved into the carry.

![][srl] | SRL R
--- | ---
Arguments | `r` - Any 8-bit register or `(HL)`,`(IX)`,`(IY)`,`(IX+n)`
Summary | Rotate left
Description | Rotates the contents of `r` right by one bit. The leaving (0th) bit is moved into the carry, and the first bit of `r` is reset.

[rl]: img/bit-ops/small/rl.png
[rr]: img/bit-ops/small/rr.png
[rlc]: img/bit-ops/small/rlc.png
[rrc]: img/bit-ops/small/rrc.png
[sla]: img/bit-ops/small/sla.png
[sra]: img/bit-ops/small/sra.png
[srl]: img/bit-ops/small/srl.png
