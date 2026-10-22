# IsIdBanging 1.0.2 — validation

22 October 2026. Windows x64 Release; JUCE 8.0.12; MSVC 19.29; Windows SDK 10.0.19041. Application sources remain local.

## Interface revision

The editor uses a cached textured faceplate, bevelled buttons, machined rotary controls, indicator lights and revised typography. Four listening categories and twelve original synthetic voicings remain. Device-model selection has been removed from the normal interface and keyboard navigation.

Profile details and file-loading errors now use editor-owned English dialogs with matching panel styling, contained placement, scrolling and close controls. Application tooltips and the file-picker title are also in English. Legacy licence descriptions are translated only for display; stored data and identities remain unchanged.

The 3D-scene and spectrum-rendering function bodies are unchanged from 1.0.0, verified by SHA-256 comparison. They retain their original canvas bounds. Audio processing and measurement kernels were not changed by this interface revision.

## Passed

- CTest DSP/editor suite: 1/1 passed. Covers stereo identity, exact 256-sample dry/bypass latency at 44.1/48/88.2/96 kHz, all original profiles, variable and empty blocks, automation smoothing, session state, offline protection, unsupported rates and nonfinite input.
- Updated UI checks: all category and voicing buttons, arrow-key wrapping within the twelve original voicings, return from a legacy session to an original voicing, absence of the removed device selector, A/B, bypass, zoom and file-drop filtering.
- Dialog checks: English profile content, contained bounds, close/reopen, Escape dismissal, keyboard and file-drop isolation, legacy attribution translation and a themed English file-error message. Editor destruction releases the owned dialog.
- Legacy compatibility: opening the revised editor preserves a saved measured-profile selection and output trim. Existing VST3 class IDs, parameter IDs, choice indices and measurement identities remain available to old sessions and host automation.
- File loading, resampled looping playback, missing-file handling, clearing and generated demo playback.
- All factory FIRs compared against a direct impulse reference at four sample rates, varying block sizes and independent L/R scaling; maximum sample error below 0.00002 and RMS below 0.000001 at the stated impulse level.
- Sleeping-FIR warmup, subsequent profile fade, final 2 kHz transfer, missing-data bypass and history clearing on reset.
- **pluginval v1.0.4, strictness 5: SUCCESS, exit code 0**, against the final 1.0.2 VST3 bundle. Covers discovery, editor creation and destruction, processing, automation, state and buses.
- Native standalone 1.0.2 starts successfully and creates its 1182 × 838 window, including wrapper controls, outside the sandbox.
- Ten native UI snapshots rendered and inspected: all four categories, 85% scale with non-default knob values, bypass, profile details at both scales, legacy details and a file-error dialog. The GitHub button and in-app author credit remain present.
- Standalone EXE and VST3 PE product versions both report **1.0.2**.
- FL Studio 2024 Plugin Manager 1.8.1.4285 verified the installed 1.0.2 VST3 on 22 October 2026. Its database and existing favourite resolve to the updated bundle; the installed binary matches the packaged build by SHA-256.

## Data and scope

Public legacy measurement data and adapted FIR kernels remain under CC BY-NC-SA 4.0 with attribution. Private user measurement banks stay local. This revision does not reprocess the workbook or alter its measurement values, reference domains, kernel hashes or data licences.

Earlier preparation checks found a maximum cached-workbook interpolation difference of approximately 1.42e-13 dB. The largest digital FIR approximation RMS error was approximately 0.0524 dB, with largest absolute error approximately 0.632 dB in 40 Hz–8 kHz. These retained numerical results describe filter-vs-target agreement, not physical device reconstruction accuracy.

Full DAW playback matrices, macOS, physical loopback and perceptual/device reconstruction are outside the verified scope. The binaries are unsigned. pluginval emits unrelated sandbox LV2-resource warnings; VST3 validation succeeds. No individual headphone calibration, calibrated SPL, measured car BRIR, ANC algorithm, true-peak metering or BS.1770 automatic level matching is claimed. Disable the monitor effect before exporting a master; the offline guard depends on host reporting.
