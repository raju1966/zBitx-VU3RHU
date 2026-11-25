## WITHDRAWN — do not use the v1.0 release

**The v1.0 release was withdrawn on 25 November 2026 and has been deleted.**

Six of the DSP controls in that build (ABST, NRVL, NBVL, MCMP, FVLY and FMNT) set a value but never switched the feature on. They changed the number on the screen and did nothing else. The release notes said they worked. Apologies to anyone who downloaded it.

A corrected build is being prepared and will be published here.

# zBitx with VU3RHU DSP features

DSP and UI enhancements for the HF Signals **zBitx**, built on
[afarhan/zbitx](https://github.com/afarhan/zbitx) (`sbitx v3.052`).

These are the features developed for the sBitx v3, ported to the zBitx and
reached from new pages on the radio's **own touch screen** — no HDMI monitor
needed in normal use.

---

## What it adds

Everything ships **switched off**. Nothing changes until you turn it on.

### The DSP page — MENU → DSP

| Control | What it does | Range |
|---|---|---|
| **NRVL** | Noise reduction level | 0–20 |
| **NBVL** | Noise blanker level | 0–20 |
| **FMNT** | Formant envelope tracking | 0–20 |
| **FVLY** | Formant valley depth | 1–20 |
| **AINR** | AI noise reduction, RNNoise (SSB/AM only) | 0–20 |
| **ABST** | Audio boost | 0–20 |
| **NOTC / NFRQ / NWTH** | Notch: on/off, frequency, width | ON·OFF / 100–3000 Hz / N·M·W |
| **CONT / CFRQ / CONW** | Contour: on/off, frequency, width | ON·OFF / 100–3000 Hz / N·M·W |
| **MCMP** | Microphone compression | 0–20 |
| **VOXT / VXTH / VXHT** | VOX, threshold, hang time | ON·OFF / 0–20 / 0–20 |
| **BSAV** | Save every setting above against this band | press |
| **WIFI / BLTH** | WiFi and Bluetooth on/off | ON·OFF |
| **NFLR** | Measured noise floor, dB | readout |
| **NRDB** | Reduction the noise reduction is achieving, dB | readout |

### Pages reached from it

| Button | Page | What's on it |
|---|---|---|
| **ERX** | RX EQ | On/off plus six bands at 300, 600, 1k, 1.5k, 2k, 2.8k Hz, −20…+20 dB |
| **ETX** | TX EQ | The same six bands for transmitted audio, kept separate |
| **REC** | Recorder | CHAN, RECD, PLAY, VOLM, ERAS, EXPT — four channels, WAV export |
| **SWR** | SWR sweep | SWIT passes averaged, SWPW drive, SWPT starts it |
| **FDV** | FreeDV | Mode select |

### On the waterfall

Waveform and waterfall are now **two-colour: blue is noise, red is a signal
standing clear of it**. The noise floor is measured afresh for every line, so
the colouring holds up across band and gain changes.

**BSAV** is the one to know about. Set a band up the way you like it, press
BSAV, and those settings come back on their own whenever you return to it.

---

## Download

Get the latest from the **[Releases](../../releases)** page: one file,
`zBitx-VU3RHU-Build-COMPLETE-<date>.zip`. Unzip it and read `START_HERE.txt`.

Page 2 of the included PDF is the whole job in 12 steps. You do **not** need
git and you do not need to clone this repository.

---

## What's in the package

| | |
|---|---|
| `START_HERE.txt` | Read first |
| `zBitx_Enhanced_Build_Installation_Guide.pdf` | 12 pages: summary, full walkthrough, and the complete build spec as Annexure A |
| `zbitx-panel-VU3RHU-v1.0.uf2` | **Panel firmware, already compiled.** No Arduino needed |
| `zbitx-panel-STOCK-v1.07d-recovery.uf2` | The original unmodified panel firmware, kept as a fallback |
| `zbitx-vu3rhu-radio-install.zip` | The radio software and its installer |
| `zbitx-vu3rhu-panel-source.zip` | Panel source, only if you want to change it |
| `windows-rndis-driver/` | USB driver so Windows can see the radio over a cable |
| `zBitx_build_spec_20Nov26.xlsx` | Every feature, where it can be reached from, what was and wasn't included |

---

## Two halves

The zBitx has two computers inside it. The **Raspberry Pi** runs the radio
software; a **Raspberry Pi Pico** drives the touch screen and has its own
firmware.

* The **radio half** adds the DSP.
* The **panel half** adds the pages you reach it from.

Both are in the package, and both are needed. Install the radio half first.

**Flashing the panel needs no case opening.** With the radio off, connect the
panel's micro-USB port to a laptop, hold the **knob** pressed in, and power the
radio on: the Pico puts itself into update mode and an `RPI-RP2` drive appears.
Drag the `.uf2` onto it. That shortcut is Farhan's, built into the firmware.

---

## Installing

The installer does the lot: backs up the files it replaces, rebuilds the radio
software, sets the USB sound-card slot, and builds FreeDV last.

```
bash zbitx-vu3rhu/install.sh
```

Your logbook, settings and saved data are not touched. It prints how to undo
before it starts.

The FreeDV step takes about 20 minutes because codec2 is not packaged for the
Pi and has to be compiled. It runs last, so everything else is already working
by the time it starts; if it fails, the rest is unaffected.

---

## Status

**Version 1.0.** The panel firmware is compiled and verified as a valid RP2040
image. The radio software compiles clean against `afarhan/zbitx`, and every
panel control has been checked to resolve to a real radio command.

**Not yet used on the air by anyone.** The FreeDV path in particular has not
been run end to end, because codec2 could not be built on the machine this was
prepared on.

Reports welcome in [Issues](../../issues) — please say what you saw, on which
band and mode, and paste the last 20 lines if a build failed.

---

## Credit

Built on Farhan VU2ESE's [zbitx](https://github.com/afarhan/zbitx).
DSP work and UI by **Rajesh Huddar, VU3RHU** (MK68JW), developed with Claude.

73
