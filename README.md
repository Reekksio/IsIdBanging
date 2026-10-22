# IsIdBanging 1.0.2

**Listen outside your bubble.** A free listening-translation plugin for comparing how a mix's tonal balance changes across playback scenarios. Available as a native **VST3 plugin and standalone Windows x64 application**.

## Download

Extract the entire Windows x64 ZIP before use. Published builds are available from [Releases](https://github.com/Reekksio/IsIdBanging/releases/latest). This project publishes documentation, licences and public measurement data. Application source code is not currently published.

## Standalone application

Open `IsIdBanging.exe`, then choose **Demo** or **Load track**. Supported files: WAV, AIFF, FLAC and MP3. You can also drop a file onto the window. Playback loops; tracks are limited to ten minutes. Select your output device under **Options → Audio/MIDI Settings** if needed.

## Install the VST3 plugin

1. Close existing IsIdBanging instances in your DAW.
2. Right-click **Install-VST3.cmd → Run as administrator**.
3. The installer copies the complete bundle to `C:\Program Files\Common Files\VST3\IsIdBanging.vst3` and verifies its SHA-256 checksums.

In FL Studio, open **Options → Manage plugins**, enable **Verify plugins** and select **Find installed plugins**. For an update, also enable **Rescan previously verified plugins** and **Rescan plugins with errors**. Load **IsIdBanging** from a **Mixer effect slot → More plugins** and mark its star to add it to your favourites.

FL Studio discovers VST3 plugins in standard VST3 locations. Adding a project folder to Plugin search paths is insufficient. See the [Image-Line installation guide](https://www.image-line.com/fl-studio-learning/fl-studio-online-manual/html/basics_externalplugins.htm#vstfolders).

## Listening controls

- Four categories: **IN-EAR, OVER-EAR, CAR CHECK and SPEAKERS**.
- Twelve original synthetic profiles, three in each category.
- Select a category and one of its three **Voicing** buttons. Device-model menus have been removed.
- **A Original** and **B Simulation** share the output trim. **Bypass** also bypasses trim. **Simulation** sets the processed-signal blend.
- Original profile changes use a 100 ms linear fade. Legacy FIR changes requested through an older session or host automation first warm the filter history while the previous profile remains audible. Trim and A/B transitions are smoothed over 20 ms. All paths retain 256 samples of latency.
- An animated 3D scene, waveform, FFT spectrum and sample-peak meters react to the audio. **Freeze** pauses scene movement. The panel has a subtly textured hardware finish, bevelled controls and calibrated knob markings; the original scene and spectrum renderers are preserved.
- Keyboard controls: **A**, **B** and **X** for comparison and bypass; **← / →** for available profiles; **Space** for transport. Double-click a knob to restore its default. Choose **85% / 100%** to resize the interface.
- The **GITHUB** button opens this repository.
- **Profile details** opens an English dialog inside the editor, styled to match the panel. Text is selectable and scrollable. Close it with **Done**, **x**, **Esc** or a click outside the dialog. Monitoring shortcuts and file drops are suspended while it is open. File-loading errors use the same theme, and application tooltips and file-picker titles are in English.

## Previous sessions

Device-model selection has been removed from the interface and arrow-key navigation. The four categories and twelve original synthetic voicings remain available. Existing plugin class IDs and parameter identities are retained.

Opening an older session preserves its previously saved voicing and sound. A previous device-profile selection is displayed as **Saved voicing**; choosing an original voicing replaces it. The legacy profile parameter and measurement data remain internally available for compatibility, including host automation. They are not offered by the normal plugin controls.

Legacy FIRs use minimum-phase reconstruction at **44.1, 48, 88.2 and 96 kHz**. They approximate tonal balance rather than physical devices. Compatible local banks can still be loaded from `%APPDATA%\skellow\IsIdBanging\data`. Missing data produce clean, latency-preserving bypass. Public legacy speaker data and adapted kernels retain their independent CC BY-NC-SA 4.0 terms; see [data/ATTRIBUTION.md](data/ATTRIBUTION.md).

**CAR CHECK** continues to contain explicitly synthetic scenarios. No measured responses of specific cars are claimed.

## Monitoring and export

Use the plugin on your monitoring path. **Disable it before exporting a master.** Export Guard bypasses processing only when the host reports offline rendering; it cannot cover every real-time export. Full bypass also bypasses trim and may increase level. Meters display sample peak rather than true peak; reduce trim if clipping occurs. There is no hidden limiter.

Individual headphone calibration, calibrated SPL, BS.1770 automatic level matching and measured BRIR are outside version 1.0. File playback uses linear interpolation for sample-rate conversion; use the DAW input for critical work. Unsupported sample rates or missing required data produce clean, latency-preserving bypass. The binaries are unsigned.

## Languages and libraries

| Component | Technology |
| --- | --- |
| Plugin, DSP and interface | **C++20**, **JUCE 8.0.12** |
| Plugin format | **Steinberg VST3 SDK 3.8.0**, bundled with the pinned JUCE version |
| Legacy measured-session playback | Minimum-phase FIR; partitioned `juce::dsp::Convolution` |
| Original profiles | Cascaded IIR filters, stereo/mono routing and modelled delayed reflections |
| Analysis and integrity | FFT and **SHA-256** from JUCE modules |
| Local data preparation | **Python 3**, **NumPy**, XML/XLSX reading without modifying the workbook |
| Windows build | **CMake**, **MSVC / Visual Studio Build Tools**, Windows SDK |
| Installer | **PowerShell** and **Windows CMD** |
| Validation | CTest, C++ tests and **pluginval** |

JUCE is used under the JUCE 8 Starter terms for an eligible free project. See the [JUCE 8 EULA](https://juce.com/legal/juce-8-licence/). Dependency notices and licence texts are provided in `licenses` and [NOTICE.md](NOTICE.md).

## Licence and ownership

**Free to use and share; sale of the application is prohibited.** The rights holder retains ownership of the original code, interface, branding and synthetic profiles. You may use the application to create and release your own music, including professionally. See [LICENSE.txt](LICENSE.txt).

Third-party libraries and data retain their own licences. ASR measurement data and adapted FIR files are licensed under **CC BY-NC-SA 4.0**; see [data/ATTRIBUTION.md](data/ATTRIBUTION.md). The application licence does not override those rights. This repository is not currently an open-source release; any future source release will be published separately.
