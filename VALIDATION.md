# IsIdBanging 1.0.0 — validation

21 October 2026. Windows x64 Release; JUCE 8.0.12; MSVC 19.29; Windows SDK 10.0.19041. Application code remains local.

## Passed

- CTest DSP/editor suite, including stereo identity, exact 256-sample dry/bypass PDC at 44.1/48/88.2/96 kHz, all original profiles, empty/variable blocks, automation smoothing, session state and invalid state, offline protection, unsupported Fs and nonfinite input.
- Every included measured-profile FIR compared with its direct impulse oracle at all four sample rates, with varying block sizes and independent L/R scaling. Maximum sample error below 0.00002 and RMS below 0.000001 at the stated impulse level.
- Sleeping-FIR warmup and subsequent linear profile fade, including a steady-state 2 kHz transfer check within 0.15 dB of the source-derived target.
- Host reset clears FIR, IIR, reflection and PDC history. Missing data cause clean delayed bypass. Measured-profile hashes survive session save/restore.
- Audio-file import, resampled looping playback, missing-file handling, clearing, generated demo, keyboard shortcuts, original category/preset buttons, zoom and file drop filtering.
- Native standalone 1.0.0 starts and creates an IsIdBanging window, 1182 × 838 including wrapper controls, using the local measurement bank outside the sandbox.
- Five native UI component snapshots, including the measured FR selector, GitHub button and made by skellow credit, rendered and inspected.
- **pluginval v1.0.4, strictness 5: SUCCESS, exit code 0**, against the final 1.0.0 VST3 bundle. Includes scan, opening, editor while processing, audio, automation, state and buses. The separate Steinberg validator was not configured.

## Measurement preparation

The supplied workbook was read without modification. Independent log-frequency interpolation and 1 kHz normalisation agree with its cached calculations to a maximum error of approximately 1.42e-13 dB. Missing values were retained as missing; raw rigs were not merged.

The complete local bank contains 25 measured curves. Sixteen compatible 5128 headphone curves and six speaker curves are renderable; three curves with unverified reference compatibility remain data-only. The public release contains only the three ASR datasets and their adapted filter data under CC BY-NC-SA 4.0. Other user-supplied data remain local.

Across prepared public/local FIRs at four rates, the largest digital approximation RMS error is approximately 0.0524 dB and the largest absolute error approximately 0.632 dB in 40 Hz–8 kHz. These are filter-vs-target errors, not physical device reconstruction accuracy. Phase is reconstructed, not measured; boundaries outside known FR are extended at constant level and labelled extrapolation.

## Performance observation

On this development computer, a local test processed four seconds of 48 kHz stereo in approximately 0.070 s for the original Night Drive model and 0.140 s for active Edifier R1280T or AirPods-derived FIR models. Measurements exclude device I/O and UI and are observations, not guarantees. Inactive FIRs sleep; a new FIR warms for its full approximately 0.69 s history before its 100 ms fade, while the previous model remains audible.

## Limits

The earlier 0.1 installation was detected and verified by FL Studio's scanner; 1.0 preserves its VST3 class IDs and standard installation layout. Full 1.0 DAW playback matrices, macOS, physical loopback and perceptual/device reconstruction are not claimed tested. Binaries are unsigned. pluginval may emit unrelated LV2-resource warnings in the sandbox; VST3 validation succeeds.

No individual headphone calibration, calibrated SPL, measured car BRIR, ANC algorithm, true-peak meter or BS.1770 automatic level matching is claimed. Disable monitor processing before exporting a master; the offline guard depends on host reporting.
