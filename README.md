# Zeekr X CAN reverse engineering

An independent research project documenting CAN traffic and ECU diagnostics on a **2023 Zeekr X AWD**. The aim is an evidence-based network model: ECU → frame → signal → physical meaning.

**[Download the English Excel matrix](reports/Zeekr_X_CAN_Matrix_EN.xlsx)** · [Frame matrix](database/can_frames.csv) · [Signal candidates](database/can_signals.csv) · [Evidence and limitations](docs/evidence.md) · [Contributing](CONTRIBUTING.md)

## Current results

| ECU / component | Assigned IDs | Attribution basis |
|---|---:|---|
| VCU | 46 | Isolated-side recording and maintainer confirmation |
| BECM | 34 | Isolated-side recording and maintainer confirmation |
| Rear drive / inverter | 16 | Isolated-side recording and maintainer confirmation |
| Front drive / inverter | 14 | Bridge-side comparison and maintainer confirmation |
| DC/DC (CDD) | 11 | Regular isolated-side traffic and maintainer confirmation |
| Stalk switch | 3 | Maintainer identification and confirmation |
| Other / unassigned | 17 | Outside current research scope |

**124 of 141 observed IDs have assigned transmitters (87.9%). This is not 87.9% signal decoding.** The inventory may grow in other operating modes.

The signal matrix contains **41 entries: 35 candidates, 2 unknown fields and 4 confirmed VIN-layout fields**. Frame decoding remains **118 UNKNOWN, 22 CANDIDATE and 1 PARTIAL**. No fully decoded frame or complete drive-control protocol is claimed. Vehicle identifiers are not included.

**[Full raw-trace review, 17 October 2026](reports/full_raw_review_20261017.md)**: 17.3 million received frames reviewed, new rear-drive candidates, complementary-field exceptions, and a high-load counterexample to the old battery-current formula. No new physical signal is promoted to confirmed.

## Research focus

- Front and rear drive: speed, torque, current, voltage, temperature and operating state.
- VCU: vehicle requests, brake-related fields and coordination with drive units.
- BECM: battery voltage/current, state of charge and charging-related data.
- DC/DC: voltage, state and recurring message structure.
- Stalk switch: identify fields associated with individual switch positions.

Candidates include `0x095` torque-related data, `0x13A` current/torque-related fields, `0x180` motor rotation, `0x142` battery voltage and `0x143` battery current. These names express hypotheses, not validated specifications. Historical diagnostic names such as MGM/IEM do not by themselves identify an axle.

## Front and rear drive attribution

The source matrix distinguishes **16 rear-drive IDs** from **14 front-drive IDs**. Use the ECU association in the matrix when evaluating signals; historical diagnostic labels alone do not identify an axle.

## Rebuild the workbook

```sh
python -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python scripts/build_excel.py
.venv/bin/python scripts/validate_snapshot.py
```

CSV files are the public source of truth; the workbook is generated. [Methodology](docs/methodology.md) describes the workflow and bit conventions. Raw recordings and private diagnostic exports are not bundled; see the evidence policy before treating any finding as independently reproducible.

## Looking for collaborators

We are researching the CAN bus and ECU diagnostics of the **2023 Zeekr X AWD** and looking for others working on similar projects.

Our current focus includes the VCU, BECM, front and rear drive units, DC/DC converter, and stalk switch. We have attributed **124 observed CAN IDs to these components** and published an English CAN matrix with signal candidates, evidence references, and remaining unknowns.

We would welcome help with:

- Validating signal locations, scaling, and physical meaning.
- Mapping diagnostic requests and responses.
- Identifying counters, checksums, and E2E protection.
- Comparing findings across vehicles and software versions.

If you have relevant experience, recordings, or independently decoded signals, we would be glad to exchange findings. **Candidates are clearly separated from confirmed results.**

Start with the [open research questions](docs/research_questions.md). Submit an issue or pull request following the [contribution guidelines](CONTRIBUTING.md), or contact the maintainer directly.

**Contact: [thyristor@yandex.ru](mailto:thyristor@yandex.ru)**

Contributions, corrections, and technical discussions are welcome!

This project is not affiliated with Zeekr or Geely. No OEM specification or completeness guarantee is implied. Research tools in this repository are offline only.
