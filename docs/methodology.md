# Methodology

1. Identify the physical interface and ECU wiring. Do not infer Classical CAN, CAN FD or LIN from component purpose or an eight-byte payload.
2. Record a passive baseline with channel mapping, timestamps, hardware settings and vehicle state.
3. Record diagnostic values and CAN traffic on a justified common timeline. Keep clock offsets and uncertainty explicit.
4. Change one variable per experiment, then repeat in different conditions.
5. Examine message periods, changing bits and plausible signed/unsigned representations.
6. Compare physical values using `physical = raw * scale + offset`; diagnostic and realtime representations may differ.
7. Validate candidates on a separate recording. Correlation alone does not establish a command or its direction.
8. Record source evidence, bit convention, scaling, unit, limitations and remaining unknowns.

## Bit conventions

- LSB0: bit 0 is the least significant bit of byte 0.
- MSB0_LINEAR: bit 0 is the most significant bit of byte 0; indices increase toward the least significant bit, then continue at the next byte.
- DBC Motorola start bits use a different convention. Never copy an MSB0_LINEAR position into a DBC without conversion.
- Blank fields mean unknown or not supplied, not zero.

## Statuses

UNKNOWN: no supported interpretation. CANDIDATE: testable hypothesis. PARTIAL: only part of a frame understood. CONFIRMED: supported within the explicitly stated scope. Source_Status is separate from Frame_status and signal Status.

Original traces must remain immutable and carry SHA-256 hashes. Keep derived results separately. A new subsystem follows the same workflow. The wider data model may later include CAN FD, LIN and other transports; no LIN network is claimed here.

Begin with passive observation. Do not inject or replay control traffic while driving. This release provides no live vehicle-control code.
