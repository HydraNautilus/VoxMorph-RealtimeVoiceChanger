<p align="center">
  <img src="https://i.postimg.cc/VkqVhzGC/banner.png" alt="VoxMorph Real-Time Voice Changer — Low-Latency Voice Modulator for Discord & Games" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Realtime%20Voice%20Changer-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-voxmorph--v1.2-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# VoxMorph Real-Time Voice Changer — Low-Latency Voice Modulator for Discord & Games

**Tired of paying monthly subscriptions for Voicemod just to use basic pitch/formant presets, radio filters, or custom voice models in Discord and games? Run a fast, 100% local real-time voice processor on Windows with sub-15ms DSP latency.**

VoxMorph Real-Time Voice Changer processes your microphone stream locally in real time: **combining instant DSP presets (Deep Bass, Radio/Walkie-Talkie, Robot, Pitch/Formant Shift, Studio Compressor) with optional local ONNX/RVC voice model inference and global hotkey switching**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) gamers, roleplayers, VTubers, and streamers** routing live voice effects into Discord, OBS, VRChat, and in-game voice chat.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Commercial voice changers lock presets behind monthly subscriptions | Cloud-tethered voice apps restrict free users to 3 rotating voices | Unlock unlimited local presets, custom EQ/formant curves & local models |
| High audio delay makes it hard to speak naturally | Large 4096-sample audio buffers add 200+ ms echo delay | Use low-latency WASAPI buffers (`12 ms` DSP mode) with toggleable sidetone |
| Background keyboard clicks get amplified by voice effects | Raw mic signal lacks a noise gate before pitch shifting | Built-in **Noise Gate + High-Pass Filter** cleans input before modulation |
| Need to toggle normal voice vs. character voice mid-match | Alt-tabbing to click presets breaks immersion | Bind global hotkeys (`Numpad 1–9`) + instant **Bypass / Clean Mic** toggle |

## Download for Windows

[**Download VoxMorph.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/VoxMorph.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `VoxMorph.exe`? (Key features)

- Ultra-low-latency (`~12 ms`) real-time **Pitch**, **Formant**, **Radio/Comms**, **Reverb**, and **Studio EQ** DSP chain.
- Supports loading local `.onnx` / RVC voice models on GPU or CPU for character voice conversion.
- Built-in **Noise Gate** and **Limiter** prevent background keyboard noise and clipping.
- Global hotkeys switch presets or bypass effects back to your clean microphone instantaneously.

### Sample Output

```text
[VoxMorph] WASAPI Low-Latency Engine Started (Sample Rate: 48 kHz | Buffer: 12 ms)
[OK]   Input Mic        : Shure MV7 USB Microphone
[OK]   Virtual Output   : CABLE Input (VB-Audio Virtual Cable)
[INFO] Active Preset    : Tactical_Radio (Pitch: -1.5 st | Formant: -2.0 | Noise Gate: -42 dB)
```

The release ZIP is named `VoxMorph.zip`; the Windows executable inside is named `VoxMorph.exe`.

1. Close VoxMorph before updating or replacing executable files.
2. Click **Download VoxMorph.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `VoxMorph.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit) with a microphone and VB-Audio Virtual Cable (for routing to Discord/games).

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `VoxMorph.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Zero subscriptions, accounts, or internet requirement

Runs 100% locally on your Windows PC.

### Clean voice chain with Noise Gate + Limiter

Ensures teammates hear crisp modulated speech without keyboard clatter or distortion.

### Instant Bypass hotkey for normal callouts

One keystroke switches back to your dry, unedited voice immediately.

### Works with Discord, OBS, Steam Voice, and VRChat

Routes cleanly through any Windows Virtual Audio Cable.

## Default folders and configuration paths

VoxMorph saves voice presets and hotkey bindings in `%APPDATA%\VoxMorph`:

```text
%APPDATA%\VoxMorph\presets\
```

Typical directory layout:

```text
VoxMorph Signal Chain:
Physical Mic -> [Noise Gate] -> [Pitch/Formant or RVC Model] -> [Limiter]
                                                                    │
                                    ┌───────────────────────────────┴──┐
                                    ▼                                  ▼
                       Virtual Cable (Discord/Game)        Headphones (Optional Monitor)
```

Keep **Monitor Self** turned off during normal gameplay unless testing a preset, as hearing your own voice delayed can be distracting.

## Quick start guide

Follow these steps to get started:

1. **Extract `VoxMorph.zip` and launch `VoxMorph.exe`.** Select your physical Microphone as Input and `CABLE Input` as Output.
2. **Speak normally and adjust the **Noise Gate** slider until idle keyboard noise disappears.** Test built-in presets or adjust Pitch & Formant sliders.
3. **In Discord / Windows Sound settings, select `CABLE Output` as your input device.** Bind a global hotkey for **Bypass (Clean Mic)**.

### Data safety note

VoxMorph processes live audio streams in memory without modifying Windows audio drivers.

## What the status summary shows

VoxMorph displays **input/output endpoints, active DSP/model latency in ms, noise gate threshold, and bound hotkeys**.

## FAQ

**How do I connect VoxMorph to Discord or in-game voice chat?**

Install the free VB-Audio Virtual Cable, set VoxMorph's Output to `CABLE Input`, and pick `CABLE Output` as your microphone in Discord.

**Does VoxMorph require an internet connection or login?**

No. Everything runs 100% offline on your PC.

**Can I turn off the voice effect instantly during a match?**

Yes—press your bound Bypass hotkey to switch immediately to clean, unmodified mic audio.

## Useful reading

- [VB-Audio Virtual Cable Official Page](https://vb-audio.com/Cable/)

## More Windows Desktop Utilities

- [SoundDeck-MicSoundboard](../SoundDeck-MicSoundboard) — Lightweight virtual-mic soundboard for Discord, OBS & voice chat
- [AudioSwitch-HotkeyToggle](../AudioSwitch-HotkeyToggle) — One-key headphones, speakers & microphone switcher
- [StemSplit-OfflineVocalRemover](../StemSplit-OfflineVocalRemover) — Offline AI vocal & instrumental stem separator
- [OBSProfile-SceneBackupVault](../OBSProfile-SceneBackupVault) — 1-click OBS Studio scenes, profiles & plugins backup vault

*Independent open-source desktop utility for Windows.*
