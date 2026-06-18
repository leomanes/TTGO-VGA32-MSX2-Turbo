# fMSX2 - ESP32 / TTGO VGA32</b><br><br>
A tiny MSX2 emulator (fMSX core by Marat Fayzullin) running on a LilyGO TTGO VGA32 v1.4 <br>
VGA out, PS/2 keyboard, microSD. It boots straight to MSX-BASIC;<br>
Hit <b>F12</b> for the ROMS list and <b>F10</b> to switch turbo modes up to 7.2MHz.<bb>


---

<b>flash it</b><br><br>
easiest way - grab <code>firmware_full.bin</code> and write it at <code>0x0</code>:<br>
<code>esptool.py --chip esp32 --baud 115200 write_flash 0x0 firmware_full.bin</code><br><br>
or the separate pieces at their own offsets:<br>
<code>0x1000 bootloader.bin</code> · <code>0x8000 partitions.bin</code> · <code>0xe000 boot_app0.bin</code> · <code>0x10000 firmware.bin</code><br>
(just updating the app? reflash only <code>firmware.bin</code> at <code>0x10000</code>.)</sub>

---

<b>sd card layout</b><br><br>
format the card FAT32 and make these folders:<br><br>
<code>/sd/roms/msx/bios</code>&nbsp;&nbsp;← the BIOS files (see below)<br>
<code>/sd/roms/msx/games</code>&nbsp;← your games: <code>.rom</code><br><br>

---

<b>bios - Dump them from your real MSX2 and drop them into<br>
<b>/sd/roms/msx/bios</b><br>
• <code>MSX2.ROM</code> - main MSX2 BIOS + BASIC (32k)<br>
• <code>MSX2EXT.ROM</code> - MSX2 sub-ROM / system extensions (16k)<br>
• <code>DISK.ROM</code><br>
• <code>FMPAC.ROM</code><br>


---

<b>what i did for the bios</b><br><br>
I dumped mine off my Panasonic FS-A1mk2. I named them:<br>
• <code>fs-a1mk2_basic-bios2.rom</code> &nbsp;→ then renamed it to &nbsp; <code>MSX2.ROM</code><br>
• <code>fs-a1mk2_msx2sub.rom</code> &nbsp;→ then renamed it to &nbsp; <code>MSX2EXT.ROM</code><br><br>

---

<b>keys</b><br><br>
• <b>F12</b> - open the game list (up/down, enter, esc = cancel)<br>
• <b>F10</b> - cycle CPU turbo 0 → +100% in +20% steps (3.58 → ~7.16 MHz)<br>
• arrow keys + space/alt double as joystick 1</sub>
