# fMSX2+ Version 2.1 - ESP32 / TTGO VGA32
<br>
A tiny MSX2 / MSX2+ emulator (fMSX core by Marat Fayzullin) running on a LilyGO TTGO VGA32 v1.4<br>
VGA out, PS/2 keyboard, microSD. Boots straight to MSX-BASIC / MSX-DOS or a GAME MENU.<br>
<br>

---

The TTGO-ESP-VGA32 can barely run the fMSX2+ emulator so you can use:<br>
Frameskip->F8 / Turbo->F10 / FM OFF->F11 to speed things up a little.

---

<b>Flash it using Flash Download Tool </b><br><br>
<code>firmware_full.bin</code> and write it at <code>0x0</code><br>

---

<b>sd card layout</b><br><br>
format the card FAT32 and create these folders<br><br>
<code>/sd/fmsx/bios</code> &nbsp; BIOS files (see below)<br>
<code>/sd/fmsx/games</code> &nbsp; games - <code>.rom</code> <code>.mx1</code> <code>.mx2</code> <code>.dsk</code> <code>.cas</code><br>

---

<b>bios</b><br><br>
dump them from your real MSX2 and MSX2+ and drop them into <code>/sd/fmsx/bios</code><br>
BIOS must be 60Hz. Switch VDP model in F11 settings.<br><br>
MSX2 (V9938)<br>
• <code>MSX2.ROM</code> - main BIOS + BASIC (32k)<br>
• <code>MSX2EXT.ROM</code> - sub-ROM / extensions (16k)<br>

MSX2+ (V9958)<br>
• <code>MSX2P.ROM</code> - main BIOS + BASIC (32k)<br>
• <code>MSX2PEXT.ROM</code> - sub-ROM / extensions (16k)<br>

Other files needed in the BIOS folder:<br>
• <code>CARTS.SHA</code> - auto mapper selector - visit romdb.vampier.net<br>
• <code>DISK.ROM</code> - Floppy driver<br>
• <code>FMPAC.ROM</code> - FM driver<br>
• <code>MSXDOS2.ROM</code> - DOS driver<br>

---

<b>msxdos2 boot</b><br><br>
drop <code>MSXDOS2.ROM</code> into <code>/sd/fmsx/bios</code> and <code>MSXDOS.dsk</code> into <code>/sd/fmsx/games</code><br>
the emulator boots straight into DOS on startup<br>
If you want a DSK loaded into drive B, press F12 and select the DSK.<br>
<br>
If you are not booting to DOS and just want to boot to a DSK, select the DSK using F12 and press CONTROL+ALT+DEL to reboot.

---

<b>keys</b><br><br>
• <b>F7</b> &nbsp;&nbsp; arrow key routing - cycles KBD / JOY / KBD+JOY<br>
• <b>F8</b> &nbsp;&nbsp; frame-skip - cycles QUALITY / NORMAL / SPEED (default)<br>
• <b>F9</b> &nbsp;&nbsp; manual mapper override (use if a ROM loads incorrectly. Hit it when the game is booting)<br>
• <b>F10</b> &nbsp; CPU turbo - cycles 3.58MHz up to ~7.16MHz in +20% steps<br>
• <b>F11</b> &nbsp; settings - VDP model, boot mode, PSG / SCC / FM volume and enable<br>
• <b>F12</b> &nbsp; game list - loads <code>.rom</code> <code>.mx1</code> <code>.mx2</code> <code>.dsk</code> <code>.cas</code><br>
• <b>Ctrl+Alt+Del</b> &nbsp; warm MSX reset<br>

---

<b>How do you get the bios files?</b><br><br>
I dumped mine off my Panasonic FS-A1mk2. I named them:<br>
• <code>fs-a1mk2_basic-bios2.rom</code> &nbsp; then renamed it to &nbsp; <code>MSX2.ROM</code><br>
• <code>fs-a1mk2_msx2sub.rom</code> &nbsp; then renamed it to &nbsp; <code>MSX2EXT.ROM</code><br>

<b>For the MSX2+ bios I used my Sanyo WAVY FD-70</b>
• <code>phc-70fd2_basic-bios2p.rom</code> &nbsp; then renamed it to &nbsp; <code>MSX2P.ROM</code><br>
• <code>phc-70fd2_msx2psub.rom</code> &nbsp; then renamed it to &nbsp; <code>MSX2PEXT.ROM</code><br>

---

<b>credits</b><br><br>
fMSX core by Marat Fayzullin<br>
VGA32 port by Leo Manes<br>
