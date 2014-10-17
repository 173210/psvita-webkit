PSVita Webkit Exploit

This is a PoC of webkit exploit running on psvita.
The PoC will work on firmware 2.60 only, but should be simple to adapt to new firmwares.

The modified PoC removes the JIT working of the exploit and replaces it with the ability
to launch ROP based scripts. This will allow interested developers to play around with
ROP and learn about the securities of modern day systems.

Web: http://lolhax.org
Twitter: https://twitter.com/DaveeFTW

Here are the gadgets used:

ROM:81DE45CA                 LDR             R2, [R0,#0x48]
ROM:81DE45CC                 MOV             R7, 0x8224F950
ROM:81DE45D4                 MOVS            R0, R6
ROM:81DE45D6                 MOVS            R1, R4
ROM:81DE45D8                 BLX             R2

ROM:81A8A3C0                 LDR             R1, [R1]
ROM:81A8A3C2                 CBZ             R1, loc_81A8A3CC
ROM:81A8A3C4                 LDR             R2, [R1]
ROM:81A8A3C6                 LDR             R2, [R2,#8]
ROM:81A8A3C8                 BLX             R2

ROM:81AE84D4                 LDR             R0, [R1]
ROM:81AE84D6                 MOVS            R2, #0
ROM:81AE84D8                 LDR.W           R3, [R0,#0xA4]
ROM:81AE84DC                 ADD             R0, SP, #0x20+var_20
ROM:81AE84DE                 BLX             R3

ROM:81EABC02                 MOVS.W          R2, #0x400
ROM:81EABC06                 BLX             memcpy
ROM:81EABC0A                 POP             {R4-R6,PC}
