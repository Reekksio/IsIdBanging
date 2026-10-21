# Measurement data attribution

Copyright Audio Science Review LLC. Adapted data and FIR kernels: CC BY-NC-SA 4.0.

Source: https://www.audiosciencereview.com/
License: https://creativecommons.org/licenses/by-nc-sa/4.0/
Original ASR notice and full legal text are included in ../licenses/.

Changes: selection of the On Axis series; linear interpolation in log frequency; subtraction of the interpolated 1 kHz level; minimum-phase reconstruction by real cepstrum; rate-specific FIR truncation with a smooth tail; no peak normalisation. Boundary values outside the measured range are held constant (extrapolation). These adaptations by skellow are shared under the same CC BY-NC-SA 4.0 licence. The original measuring author does not endorse IsIdBanging.

FactoryProfiles.json contains transformed amplitudes, source links, hashes and a byte index. FactoryBank.bin stores little-endian float32 FIR kernels in that index order. The data can be reused or adapted under CC BY-NC-SA 4.0 independently of the application licence.

## Edifier R1280T

- ID: SP04
- Original measurement: Audio Science Review LLC przez Spinorama
- Rig: Klippel NFS
- Source: https://github.com/pierreaubert/spinorama/blob/acc757bb98d63327092ee537bde25d9c227811f3/datas/measurements/Edifier%20R1280T/asr/CEA2034.txt
- Original SHA-256: 033d49ca76e26901682be2a7c30ccc8fd800d5cd6fd92d76492490e28f16413e
- Range: 20.5078 to 19999.5 Hz
- Main-series points: 194

## Ikea SYMFONISK Picture Frame

- ID: SP05
- Original measurement: Audio Science Review LLC przez Spinorama
- Rig: Klippel NFS
- Source: https://github.com/pierreaubert/spinorama/blob/acc757bb98d63327092ee537bde25d9c227811f3/datas/measurements/Ikea%20SYMFONISK%20Picture%20Frame/asr/CEA2034.txt
- Original SHA-256: a038756f3e6d2ba72ddee6a606105cb85a4d7ebf03abf08ad8c594a01c839ecb
- Range: 20.1416 to 19999.9 Hz
- Main-series points: 201

## Apple Homepod

- ID: SP06
- Original measurement: Audio Science Review LLC przez Spinorama
- Rig: Klippel NFS
- Source: https://github.com/pierreaubert/spinorama/blob/acc757bb98d63327092ee537bde25d9c227811f3/datas/measurements/Apple%20Homepod/asr/others/CEA2034.txt
- Original SHA-256: eb2d40e3b6855b81dfdde75eee5cb21ebb93c2ca83123ffc82be8ba65b302d37
- Range: 20.5078 to 19998.0 Hz
- Main-series points: 98
