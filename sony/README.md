# Sony Ayu2 / Ayu2L BootROMs

These are 64 KiB dumps of the big endian MIPS standby-core mask ROM used by
Sony's 2013 RB1 TV platform. The ROM is mapped at `0xbfc10000`; the ARM core
starts later in the boot process. The two images differ by 457 bytes.

| File | SoC | SHA-256 |
| --- | --- | --- |
| `cxd4745gb-ayu2.bootrom.bin` | CXD4745GB (Ayu2) | `499715ddd02195854470a73606492af40127262eeb1bb2eaab3d48f7727c5a34` |
| `cxd4748gb-ayu2l.bootrom.bin` | CXD4748GB (Ayu2L) | `0797cd9052c532c6a4a7323b2bc20aa5e08ba3af2d9b3b81c14218654fa81125` |

Source: [theubusu's Sony TV notes, RB1 BootROM directory](https://github.com/theubusu/sony_tv_notes/tree/master/platform/RB1/bootrom),
with [boot-process notes](https://github.com/theubusu/sony_tv_notes/blob/master/platform/RB1/boot.md).
The filenames and chip mapping follow those notes. Both files were copied byte
for byte from that repository; the hashes above can be used to verify them.

The ROM images are distinct from Sony's GPL kernel source release; no GPL
license for the ROM images is asserted here.
