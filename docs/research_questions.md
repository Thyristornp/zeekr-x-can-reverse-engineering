# Open research questions

1. Independently validate rear-drive motor speed and actual torque against simultaneous diagnostics, using the established rear-drive source group.
2. Check 0x095, 0x13A, 0x180 and 0x275 on the front-drive side. Distinguish historical diagnostic labels from physical ECU identity.
3. Validate BECM voltage/current and multiplexing candidates across operating ranges and separate recordings.
4. Determine whether 0x12A contains DC/DC high-voltage input, using synchronized voltage measurements rather than range matching.
5. Separate counters, checksums and physical fields using many frames and held-out recordings.
6. Identify individual stalk-switch fields in 0x135, 0x136 and 0x516 with one switch action per experiment.
7. Contribute a reviewed, non-identifying sample dataset with timestamps and an executable validation procedure.

No completed motor enable, torque-control sequence, checksum algorithm or E2E implementation is claimed.
