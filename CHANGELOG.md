# Changelog

## 1.0.0 — 2026-10-21

- Added a measured FR selector and minimum-phase FIR playback, with rate-specific filters for 44.1, 48, 88.2 and 96 kHz.
- Included three ASR-derived speaker profiles with CC BY-NC-SA 4.0 data, attribution, source hashes and a separately distributable adapted-data bank.
- Added local private-bank loading for user-supplied measurements. Rig domains remain separate; curves without a verified compatible reference are disabled for audio.
- Preserved the twelve original synthetic profiles and the four listening categories. Car profiles remain explicitly synthetic because no applicable car measurement was supplied.
- Preserved 256-sample PDC for simulation, A/B and bypass, 100 ms profile fades, and existing session profile IDs.
- Added measurement-bank and kernel SHA-256 validation and stored data identity with session state.
- Added an in-app author credit and a GitHub repository button.
- Added the freeware licence: free use and free redistribution of the original application, with sale prohibited. Third-party licences remain independent.
- Finalised Windows x64 VST3 and standalone EXE distribution, installation instructions and release packages.

## 0.1.0 — 2026-10-20

- Initial Windows VST3 and standalone MVP, twelve synthetic profiles, reactive wireframe graphics, A/B, bypass, audio-file playback and a generated demo loop.
- Corrected FL Studio installation by using the standard Windows VST3 directory.
