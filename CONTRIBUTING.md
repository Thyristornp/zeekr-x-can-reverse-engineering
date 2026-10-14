# Contributing

Open an issue for a proposed signal or submit a pull request updating CSV data. Please include:

- Vehicle model year, drivetrain and relevant ECU/software version, if known. Do not include a VIN.
- Physical bus and capture-channel mapping; adapter, bitrate and timestamp clock.
- Experiment procedure, operating state and timestamped events.
- CAN ID in hexadecimal, byte length, start bit, width, bit-numbering convention, byte order and signedness.
- Scale, offset, unit and supporting diagnostic or physical measurement.
- A trace reference and checksum, plus the evidence needed to review the result.
- Alternative explanations and an independent repeat or validation recording.

Do not promote a candidate based only on a foreign DBC, one matching value or correlation. Explain whether a change concerns the transmitter or the meaning of the payload.

Review recordings for vehicle identifiers and personal data before sharing. Publish only material you are entitled to share; do not upload proprietary manuals or diagnostic software packages.

Run `python scripts/build_excel.py` and `python scripts/validate_snapshot.py` after changing public matrices. Edit CSV data rather than the generated workbook. English is used throughout the public repository.
