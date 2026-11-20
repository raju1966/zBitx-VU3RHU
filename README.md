# zBitx with VU3RHU DSP features

Firmware enhancements for the HF Signals **zBitx**, built on
[afarhan/zbitx](https://github.com/afarhan/zbitx) (`sbitx v3.052`).

These are the DSP and UI features developed for the sBitx v3, ported to the
zBitx and reached from a new **DSP page** on the radio's own touch screen —
no HDMI monitor needed in normal use.

---

## What it adds

All features ship **switched off**. Nothing changes until you turn it on.

| Control | What it does | Range |
|---|---|---|
| **NRVL** | Noise reduction level | 0–20 |
| **NBVL** | Noise blanker level | 0–20 |
| **FMNT** | Formant envelope tracking | 0–20 |
| **FVLY** | Formant valley depth | 1–20 |
| **AINR** | AI noise reduction, RNNoise (SSB/AM only) | 0–20 |
| **ABST** | Audio boost | 0–20 |
| **NOTC / NFRQ / NWTH** | Notch filter, frequency, width | ON·OFF / 100–3000 Hz / N·M·W |
| **CONT / CFRQ / CONW** | Contour filter, frequency, width | ON·OFF / 100–3000 Hz / N·M·W |
| **MCMP** | Microphone compression | 0–20 |
| **VOXT / VXTH / VXHT** | VOX, threshold, hang time | ON·OFF / 0–20 / 0–20 |
| **BSAV** | Save all settings for the current band | press |
| **WIFI / BLTH** | WiFi and Bluetooth on/off from the screen | ON·OFF |

**BSAV** is the one to know. Set a band up the way you like it — filters, noise
reduction, power, compression — and press BSAV. Those settings return
automatically whenever you come back to that band.

---

## Download

Get the latest release from the **[Releases](../../releases)** page.
Download `zBitx-VU3RHU-Build.zip`, unzip it, and open
`zBitx_Enhanced_Build_Installation_Guide.pdf`. It assumes no Linux knowledge.

You do **not** need git, and you do not need to clone this repository.

---

## What is in the package

| | |
|---|---|
| `START_HERE.txt` | Read first |
| `zBitx_Enhanced_Build_Installation_Guide.pdf` | Full illustrated instructions |
| `windows-rndis-driver/` | USB driver so Windows can see the radio over a cable |
| `zbitx-vu3rhu-radio-install.zip` | The radio software, with its installer |
| `zbitx-vu3rhu-panel-source.zip` | Touch panel firmware that adds the DSP page |
| `zbitx-panel-STOCK-v1.07d-recovery.uf2` | Stock panel firmware, kept as a fallback |

---

## Two halves

The zBitx has two computers inside it. The **Raspberry Pi** runs the radio
software; a **Raspberry Pi Pico** drives the touch screen and has its own
firmware.

* The **radio half** adds the DSP features.
* The **panel half** adds the DSP page you reach them from.

Install the radio half first. Until the panel half is flashed, the features are
present but have no button.

---

## Status

**Version 1.0 — not yet field tested.** The build compiles cleanly against
`afarhan/zbitx` and every panel control has been checked to resolve to a real
radio command, but it has not yet been run on the air by anyone.

There is no pre-compiled `.uf2` for the panel yet. Until someone builds one with
the Arduino IDE (instructions are in the panel package), the DSP button will not
appear. The radio half installs and runs regardless.

Reports welcome in [Issues](../../issues) — please say what you saw, on which
band and mode.

---

## Safety

The installer backs up every file it replaces into `~/sbitx-backup-<date>` and
prints how to undo. Your logbook, settings and saved data are not touched.

## Credit

Built on Farhan VU2ESE's [zbitx](https://github.com/afarhan/zbitx).
DSP work and UI by **Rajesh Huddar, VU3RHU** (MK68JW), developed with Claude.

73
