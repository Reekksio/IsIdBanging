# Third-party notices — IsIdBanging 1.0.2

Original IsIdBanging application materials: Copyright (c) 2026 skellow. See `LICENSE.txt` for the freeware licence. Third-party copyrights and licences are retained and are not assigned to skellow.

- **JUCE 8.0.12**, revision `29396c22c93392d6738e021b83196283d6e4d850`, copyright Raw Material Software Limited. This release uses the JUCE 8 Starter EULA route for a qualifying free individual project, not the AGPL distribution route. The relevant EULA remains at https://juce.com/legal/juce-8-licence/. Continued eligibility is governed by that EULA, including its revenue/funding provisions. `licenses/JUCE-LICENSE.md` contains JUCE's licensing notice.
- **Steinberg VST3 SDK 3.8.0**, bundled with the pinned JUCE revision: MIT, see `licenses/VST3-SDK-LICENSE.txt`. VST is a trademark of Steinberg Media Technologies GmbH.
- **FLAC**, **Ogg Vorbis**, **JPEG**, **PNG**, **zlib**, **HarfBuzz**, **SheenBidi** and JUCE's included **LV2** support retain their bundled notices in `licenses`. These are framework dependencies; no separate LV2 plugin is distributed.
- **ASR measurement data and derived FIR data**: Audio Science Review LLC, CC BY-NC-SA 4.0. The three included datasets are Edifier R1280T, IKEA SYMFONISK Picture Frame and Apple HomePod (ASR; generation unspecified). The public release provides the transformed curves and FIR bank in `data` under that same licence, including attribution, pinned source links, original hashes, method, and the full licence text. See `data/ATTRIBUTION.md`.
- The twelve original synthetic profiles and the procedurally generated demonstration loop are original IsIdBanging materials. No third-party audio recording, HRTF or BRIR is included.
- Private measurement banks supplied by an individual user are not part of the public release and remain subject to their own source terms.
- **Python / NumPy** are used locally to prepare and validate measurement filters. They are not required or bundled for running the program. **pluginval** is a separate development validation tool; it is not linked into or distributed with the plugin.

Device names identify the source of measurements and do not imply endorsement or certification. No manufacturer logos are used.
