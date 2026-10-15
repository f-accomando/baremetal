# Third-party components

bm itself is under the BM Community License 1.0 (see [LICENSE](LICENSE)). The following components keep their own licences.

| Component | Where | Licence |
|---|---|---|
| Lua 5.4.7 (two small marked changes, see `third_party/lua/README.bm`) | `third_party/lua/` | MIT (`third_party/lua/LICENSE`) |
| lwIP 2.2.0 | `third_party/lwip/` | BSD-3-Clause (`third_party/lwip/COPYING`) |
| Mbed TLS | `third_party/mbedtls/` | Apache-2.0 OR GPL-2.0-or-later; bm uses it under Apache-2.0 (`third_party/mbedtls/LICENSE`) |
| Console font (derived from Terminus Font) | `src/gfx/font*.c` | SIL Open Font License 1.1 (`docs/LICENSE.font`) |
| Root CA certificates for HTTPS | `boot/ca.pem` | public CA certificates (Mozilla CA store) |

Not in this repository: the Raspberry Pi boot firmware (`bootcode.bin`, `start.elf`, `fixup.dat`), the WiFi/Bluetooth chip
firmware and the RGB30 U-Boot and Realtek firmware. `make firmware` downloads them from their upstream projects
(raspberrypi/firmware, RPi-Distro, ROCKNIX, linux-firmware) under their own licences; they are not redistributed here.

`keys/` holds only the two **public** keys the kernel checks signatures with (releases and the Market catalog).
