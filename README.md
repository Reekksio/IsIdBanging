# IsIdBanging 1.0.0

**Listen outside your bubble.** A free listening-translation plugin for comparing how a mix's tonal balance changes across playback scenarios. Available as a native **VST3 plugin and standalone Windows x64 application**.

## Download

Get `IsIdBanging-1.0.0-Windows-x64.zip` from [Releases](https://github.com/Reekksio/IsIdBanging/releases/latest) and extract the entire folder. This repository contains documentation, licences and public measurement data. Application source code is not currently published.

## Standalone application

Open `IsIdBanging.exe`, then choose **PLAY DEMO** or **LOAD TRACK**. Supported files: WAV, AIFF, FLAC and MP3. You can also drop a file onto the window. Playback loops; tracks are limited to ten minutes. Select your output device under **Options → Audio/MIDI Settings** if needed.

## Install the VST3 plugin

1. Close existing IsIdBanging instances in your DAW.
2. Right-click **Install-VST3.cmd → Run as administrator**.
3. The installer copies the complete bundle to `C:\Program Files\Common Files\VST3\IsIdBanging.vst3` and verifies its SHA-256 checksums.

In FL Studio, open **Options → Manage plugins**, enable **Verify plugins** and select **Find installed plugins**. For an update, also enable **Rescan previously verified plugins** and **Rescan plugins with errors**. Load **IsIdBanging** from a **Mixer effect slot → More plugins** and mark its star to add it to your favourites.

FL Studio discovers VST3 plugins in standard VST3 locations. Adding a project folder to Plugin search paths is insufficient. See the [Image-Line installation guide](https://www.image-line.com/fl-studio-learning/fl-studio-online-manual/html/basics_externalplugins.htm#vstfolders).

## Listening controls

- Four categories: **IN-EAR, OVER-EAR, CAR CHECK and SPEAKERS**.
- Twelve original synthetic profiles, three in each category.
- **MEASURED / TONAL** selects installed profiles derived from numerical frequency-response data.
- The public package includes three measured profiles: **Edifier R1280T, IKEA SYMFONISK Picture Frame and Apple HomePod (ASR; generation unspecified)**. Their data and adapted FIR kernels are distributed separately under CC BY-NC-SA 4.0.
- **A / ORIGINAL** and **B / SIMULATION** share the output trim. **BYPASS** also bypasses trim. **SIMULATION** sets the processed-signal blend.
- Profile changes use a 100 ms linear fade. A newly selected inactive FIR first warms its approximately 0.69-second history while the previous profile remains audible and **PREPARING FIR** is displayed. Trim and A/B transitions are smoothed over 20 ms. All paths retain 256 samples of latency.
- An animated 3D scene, waveform, FFT spectrum and sample-peak meters react to the audio. **FREEZE** pauses scene movement.
- Keyboard controls: **A**, **B** and **X** for comparison and bypass; **← / →** for available profiles; **Space** for transport. Double-click a knob to restore its default. Choose **85% / 100%** to resize the interface.
- The **GITHUB** button opens this repository.

## What measured profiles represent

**M-FR** identifies a measured magnitude-response source. Playback is a **tonal approximation with reconstructed minimum phase**. It does not claim to reproduce a physical device exactly. **PROFILE INFO** explains each profile's source, method and reference.

The FIR filters use complete numerical series rather than the rounded PDF table. Separate filters are prepared for **44.1, 48, 88.2 and 96 kHz**. Speaker curves represent on-axis response normalised at 1 kHz. No invented room response or HRTF is added. Values outside the measured frequency range are held at the nearest boundary and explicitly treated as extrapolation. Missing measured phase, separate L/R responses, ANC, nonlinear dynamics and SPL are not reconstructed.

The application can load a private user bank from `%APPDATA%\skellow\IsIdBanging\data`. The local integration of the supplied workbook contains 25 measured curves: 22 have a compatible playback reference, while three remain inactive because reference compatibility is unverified. Raw B&K 5128, HMS II.3 and unspecified oratory1990 rig domains are kept separate. The 5128 profiles use the compatible DF 5128 reference and remain listening approximations. This private bank is excluded from public downloads; its data retain their original source terms.

No measured responses of specific cars are included. **CAR CHECK** contains explicitly synthetic scenarios. Missing data are not replaced with a flat curve or relabelled as a newer device.

## Monitoring and export

Use the plugin on your monitoring path. **Disable it before exporting a master.** Export Guard bypasses processing only when the host reports offline rendering; it cannot cover every real-time export. Full bypass also bypasses trim and may increase level. Meters display sample peak rather than true peak; reduce trim if clipping occurs. There is no hidden limiter.

Individual headphone calibration, calibrated SPL, BS.1770 automatic level matching and measured BRIR are outside version 1.0. File playback uses linear interpolation for sample-rate conversion; use the DAW input for critical work. Unsupported sample rates or missing required data produce clean, latency-preserving bypass. The binaries are unsigned.

## Languages and libraries

| Component | Technology |
| --- | --- |
| Plugin, DSP and interface | **C++20**, **JUCE 8.0.12** |
| Plugin format | **Steinberg VST3 SDK 3.8.0**, bundled with the pinned JUCE version |
| Measured profiles | Minimum-phase FIR; partitioned `juce::dsp::Convolution` |
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
