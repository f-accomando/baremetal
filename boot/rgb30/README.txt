bm for the PowKiddy RGB30
=========================

This card boots bm on the RGB30: put it in slot TF1 (the one ROCKNIX boots
from). Switch on with the power button (not by plugging in the charger).

  kernel8.img       the bm kernel: update it from System > Updates (over
                    WiFi), or by replacing this file
  extlinux/         the instructions for U-Boot (do not touch)
  bm/               .b16 games, settings (config.txt), Bluetooth firmware,
                    bootlog.txt (what happened at the last boot)

LEDs: red on = booting; green blinking = bm is running; steady red with the
green blinking = display problem (read bm/bootlog.txt on a PC); red blinking
N times = error N.
If it hangs when the screen is switched on, the steady LEDs say where: red and
green = clock, green only = video controller, none = DSI/panel.

WiFi: write the lines wifi_ssid=NetworkName and wifi_psk=password in
bm/config.txt (and wifi_boot=1 to connect at every boot); in the menu, WiFi:
B scans, X joins.

Buttons: B confirms, A goes back (confirm=a in bm/config.txt swaps them).
Menu: three tabs, Games, Dev (3D Bench, screen and button tests, boot log) and
System (Bluetooth, WiFi, Updates, system); L1/R1 change tab.
The 3D Bench saves its report in bm/bench.

Tests: the Games tab lists and starts the Pi's .bm cartridges (show_bm=0 in
bm/config.txt hides them). Start + Select leaves a game.

Do not format or repartition the card: the boot loader lives outside the
partition. To make a new one: make TARGET=rgb30 image, then write the image.
