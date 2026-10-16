# bm (BareMetal)

bm is a bare-metal console: a kernel with no operating system underneath, a Lua 5.4 runtime and a small
cartridge format (`.bm`; `.b16` for handhelds). It runs on the **Raspberry Pi Zero W** (BCM2835, ARM1176) and on the
**PowKiddy RGB30** (RK3566, AArch64). This repository holds both kernels, the boot chain, the on-console
development suite (SDK, Code, Pixel, Studio, Animator, Mesh, Sound, Write), the system libraries
(`bmlib`, `bmnet`, `bmui`, `riff`), the PC tools that pack cartridges, the API documentation and the tests.

```sh
make                        # Pi Zero W kernel: build/kernel.img (+ build/carts/*.bm)
make TARGET=rgb30           # RGB30 kernel: build/rgb30/kernel8.img
make firmware               # download the Pi boot firmware once (make TARGET=rgb30 firmware for the RGB30)
make sdcard                 # Pi: SD card contents in dist/ (or: make image; make TARGET=rgb30 image)
./easy_install.sh           # guided build + install onto a card
```

Needs `gcc-arm-none-eabi` (Pi), `gcc-aarch64-linux-gnu` + `picolibc-aarch64-linux-gnu` (RGB30), `python3`, `make`;
`qemu-system-arm`, `qemu-system-aarch64`, `dosfstools`, `mtools`, `python3-numpy`, `python3-pil` for the tests.
Start with [docs/API.md](docs/API.md), [docs/GAME-GUIDE.md](docs/GAME-GUIDE.md), [docs/HARDWARE.md](docs/HARDWARE.md)
and the PDF manuals in [manuals/pdf](manuals/pdf). Licence: see [LICENSE](LICENSE) and [THIRD-PARTY.md](THIRD-PARTY.md).

## Progress

Newest first. Dates are commit dates of the original development history.

- **2026-10-15 Assistant and mesh detail**: detail and polygon-reduction notes, new low-poly entries in the assistant's knowledge base (`mesh.biped`, `mesh.chameleon`), network retrained.
- **2026-10-13 Manuals and one list of tools**: PDF manuals of bm Code, bm Write and bm SDK rebuilt (English and Italian); the tool file names live in one list (`src/kernel/toolnames.h`) used by the Pi and RGB30 menus.
- **2026-10-12 RGB30 in the loop**: Start+Select freezes the running cartridge and the menu resumes it, as on the Pi.
- **2026-10-11 bm SDK for the RGB30**: the 360x360, pad-driven `.b16` edition of the SDK runs as a tool of `kernel8.img`.
- **2026-10-10 riff effects**: new effects (`crush`, `coarse`, `vowel`, `chorus`, `trem`, `duck`) and a drum kit by name (`bd sd hh`).
- **2026-10-06 bm Write and the Lua debugger**: a word processor with documents in `/docs` and PDF export; breakpoints in bm Code.
- **2026-10-06 Audio 2 (M46)**: hi-fi stereo synth, instruments, music assistant and the `riff` pattern language.
- **2026-10-05 CI and releases**: the tests run on six machines at once, a release is not tested twice; the releases milestone (M19) is closed.
- **2026-10-05 RGB30 Mali GPU**: the Mali-G52 driver powers the GPU, runs jobs and clears a surface; the first triangle is written, not yet tried on the device.
- **2026-10-04 bm SDK hub**: the project hub of the suite with a 3D page, dev kit and assistant guides; map layers and tile flags.
- **2026-10-03 Updates from the console**: the kernel fetches updates from GitHub (M19.4); the V3D vertex shader places meshes (M36, step 1).
- **2026-10-02 Pi Zero 2 W**: `kernel7.img`, the same sources built for ARMv7 (M31).
- **2026-10-01 RGB30 base kernel**: AArch64 boot, MMU, GICv3, timer, Lua and QEMU `virt` tests; WiFi bring-up on its RTL8821CS follows the same day.
- **2026-10-01 Market and mouse**: the signed Market catalog and publishing from the console (M25); USB mice, right stick as pointer and `mouse()` for cartridges (M31).
- **2026-10-01 bm Pixel, bm Animator, Sound**: pixel art of a `.bm` on the console (M22.2), rigging and keyframes, sound banks with a sequencer in the audio interrupt and the Sound editor.
- **2026-09-30 bm Studio and Pi 1 B**: 3D models inside the `.bm` (MESH section, `model()`, `bounds3d()`); Pi 1 B support with USB hub, split transactions and LAN9512 Ethernet.
- **2026-09-29 Gouraud, WiFi stack, suspend**: Gouraud shading and gradient triangles (M14), lwIP 2.2.0 on the WiFi data path with a DHCP address (M18.6), games stay suspended in memory when left from the menu (M21).
- **2026-09-28 DMA and textures**: DMA fills and copies, VFP RunFast, watchdog with breadcrumbs, textured triangles and cartridge covers.
- **2026-09-27 Audio, Bluetooth, SD writes**: HDMI audio with an 8-voice synth (M10), a DualShock 4 paired over Bluetooth (M12), SD block writes and FAT write with settings in `config.txt` (M11).
- **2026-09-27 Cartridge menu and SD image**: the console boots straight to the cartridge menu (M9); `make image` produces a 64 MiB SD image.
- **2026-09-26 USB host, SD and FAT32**: DWC2 USB host with HID keyboard and gamepads, SD card, FAT32 and the cartridge menu (M8).
- **2026-09-26 Native cartridges and 3D (M7)**: `.bm` cartridges with Lua 5.4 and C graphics at 640x360 RGB565, rendering stress test and software 3D.
- **2026-09-26 Embedded Lua (M5)**: Lua 5.4.7 with a serial REPL and boot script.
- **2026-09-26 Interrupts and 60 fps (M4)**: 1 kHz tick, double buffering and a 60 fps demo.
- **2026-09-26 MMU and caches (M3)**: MMU, caches, full ARM clock, heap and newlib.
- **2026-09-26 Text console (M2)**: framebuffer console with ANSI colours and a status bar.
- **2026-09-25 Serial and chainloader (M1)**: serial console, exception handling, a serial chainloader, QEMU tests and CI.
- **2026-09-25 Boot (M0)**: bare-metal boot and an HDMI colour test pattern on the Pi Zero W (verified on the real board on 2026-09-26).
