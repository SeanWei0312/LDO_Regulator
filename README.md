# 1.2 V Low-Dropout Linear Regulator in 0.18 µm CMOS

This project implements a 180-nm CMOS low-dropout (LDO) linear regulator with an ultra-low-output-resistance buffer. The repository includes the Markdown project report, report figures, the class submission PDF, and Spectre-format netlists for the buffered and unbuffered LDO designs.

## Project Summary

This is the final project for ELEN E6340 Analog Integrated Circuits, Spring 2026.

The LDO regulates a 1.2 V output from a 1.4 V to 2.5 V input supply range. The design uses a two-stage error amplifier, a PMOS pass transistor, a resistive feedback divider, and a dual-feedback buffer inserted between the error amplifier and the pass-device gate. The buffer lowers the gate-drive output impedance, pushes the non-dominant gate pole to higher frequency, and improves transient response compared with an LDO that drives the pass transistor directly.

The design targets low quiescent current, stable operation across load and temperature variation, strong low-frequency PSRR, and fast recovery under supply and load disturbances.

## Contributors

Zijian Shang, Yi-Hsiang Wei, Yuxiao Ma, and Chenxi Shen are students in Columbia University's Department of Electrical Engineering.

- Zijian Shang: LDO architecture study, report writing, and simulation result organization.
- Yi-Hsiang Wei: transistor-level design support, simulation analysis, and report preparation.
- Yuxiao Ma: error amplifier and buffer analysis, figure preparation, and result review.
- Chenxi Shen: load, temperature, and efficiency analysis support.

## Key Results

| Metric | Result |
| --- | ---: |
| Process | TSMC 180 nm |
| Input voltage range | 1.4-2.5 V |
| Regulated output voltage | 1.2 V |
| Dropout voltage | 200 mV |
| Maximum load current | 40 mA |
| Quiescent current | 104.2 uA |
| DC loop gain | 96 dB |
| Phase margin | 17.961 degrees |
| Unity-gain frequency | 1.1852 MHz |
| PSRR | >70 dB at 1 kHz |
| Output capacitor range | 1-100 pF |
| Temperature coefficient | 2.62 ppm/degC |
| Output-voltage drift | 0.52 mV from -40 degC to 125 degC |

## Files

- [LDO_Project_Report.md](LDO_Project_Report.md) - complete Markdown report.
- [ELEN6340_Submission/docs/elen6340_submission.pdf](ELEN6340_Submission/docs/elen6340_submission.pdf) - class submission report.
- [ELEN6340_Submission/LDO.txt](ELEN6340_Submission/LDO.txt) - Spectre-format testbench and design netlist for the LDO with buffer compensation.
- [ELEN6340_Submission/SimpleLDO.txt](ELEN6340_Submission/SimpleLDO.txt) - Spectre-format testbench and design netlist for the LDO without buffer compensation.
- [ELEN6340_Submission/README.txt](ELEN6340_Submission/README.txt) - short notes on the submitted netlist files.
- `figures/` - report images referenced by `LDO_Project_Report.md`.
- `ELEN6340_Submission/` - organized submission package with netlists and final PDF.

## Repository Layout

```text
figures/                  Images used by LDO_Project_Report.md
ELEN6340_Submission/
  LDO.txt                 Buffered LDO netlist and testbench
  SimpleLDO.txt           Unbuffered LDO comparison netlist and testbench
  README.txt              Submission notes
  docs/
    elen6340_submission.pdf
LDO_Project_Report.md     Markdown project report
README.md                 Project overview
```

## Running Spectre Simulations

The submitted simulation inputs are in `ELEN6340_Submission/`. The main buffered design is in `LDO.txt`, which includes the `EA2` error-amplifier subcircuit, the `EA_BUFFER` buffer subcircuit, and the `NewLDO` testbench. The comparison design without the buffer is in `SimpleLDO.txt`.

The testbenches include an absolute model path from the original environment:

```spectre
include "/home/minlei/Desktop/EE4312/tsmc018.scs"
```

Update this path before running the simulations locally.

Example:

```sh
spectre ELEN6340_Submission/LDO.txt
```

Useful simulation files:

- `ELEN6340_Submission/LDO.txt`
- `ELEN6340_Submission/SimpleLDO.txt`

## Report Figures

The Markdown report references figures from the `figures/` folder using relative paths. Each figure uses a centered HTML wrapper and an italicized caption so the report renders cleanly on GitHub.

Key figure groups include:

- `figures/fig01-ldo-structure.png` through `figures/fig05-ultra-low-output-resistance-buffer.png` - architecture, error amplifier, and buffer design.
- `figures/fig06-output-impedance-testbench.png` through `figures/fig12-psrr-analysis.png` - impedance, DC, transient, AC, and PSRR simulations.
- `figures/fig13-bias-current-variation.png` through `figures/fig17-temperature-output-voltage-variation.png` - bias, load, efficiency, and temperature results.
