# Evidence and interpretation

Source attribution and payload decoding are independent. A CONFIRMED source means the maintainer has confirmed the listed ECU association using the stated evidence. It does not establish destination, command semantics or whether the ECU generated or routed the information.

## Source attribution

- EXP-0041: VCU isolated-side recording; 46 IDs.
- EXP-0042: BECM isolated-side recording; 34 IDs.
- EXP-0043: rear-drive source group; 16 IDs, confirmed by the maintainer from an isolated-side recording.
- EXP-0044: front-drive source group; 14 IDs, identified by comparing established source groups and subsequently confirmed by the maintainer. No additional independent physical recheck is claimed.
- EXP-0038/run7: 11 regular CDD-side IDs: 0x12A, 0x149, 0x14B, 0x19A, 0x216, 0x218, 0x311, 0x411, 0x455, 0x5C4, 0x5C5. Rare/transient IDs from this recording are not automatically attributed to CDD.
- Stalk switch: 0x135, 0x136, 0x516, identified and confirmed by the maintainer. A separate isolation procedure was not supplied.

All 124 current assignments were subsequently confirmed by the maintainer. Seventeen other observed IDs are outside current scope and remain unassigned.

## Signal evidence

`database/can_signals.csv` preserves field definitions, method identifiers, experiment identifiers, external source references where available, and SHA-256/line references into retained recordings. References identify evidence; they do not make unpublished recordings publicly accessible. External definitions are leads, not proof of applicability to Zeekr X.

The four CONFIRMED fields describe the multiplexed VIN layout on 0x477. Validation used page concatenation and comparison with an owner-provided identifier. Neither the identifier nor identifying payloads are published. The frame remains PARTIAL.

Other entries are candidates or unknowns. A fit obtained on one recording is not independent validation. Constant-value matches, shared IDs across models and strong correlations are insufficient on their own.

## Publication boundaries

This is an English, curated data snapshot. Original recordings, personal identifiers, screenshots, full diagnostic exports and OEM manuals are not included. No raw payload examples are published in this release. Consequently, independent reproduction of all reported findings is not yet possible from this repository alone. Contributors can supply separately reviewed recordings and validation scripts to improve that coverage.

`Bit_Map_LSB0` describes observed variability only; it is not a signal definition. Source hashes refer to original recordings. Any future redacted sample must receive its own hash and an explicit transformation record.
