# Source-aware review of existing CAN evidence — 2026-10-16

> Superseded by the [complete available-raw review](full_raw_review_20261017.md), including corrected current interpretation and complementary-field exceptions.


This review joins existing signal observations with the established frame publishers. It is a re-evaluation of saved derived data, **not a fresh scan of all raw recordings**. No new CAN signal definitions, confirmed control commands, or status promotions are introduced. The existing CSV matrices and workbook remain unchanged.

## What source attribution changes

| Relationship | Current interpretation | Limitation |
|---|---|---|
| VCU 0x050 and FrontDrive 0x095 | Leading candidate for a front-drive request/feedback relationship | Destination, causal role and physical shaft scaling are unconfirmed |
| VCU 0x04B and RearDrive 0x04C | Priority pair for a separate rear-drive investigation | Existing E304 regressions have held-out RMSE about 30 on a displayed range 0–161; no accepted pair decoder |
| FrontDrive 0x13A, two fields | Symmetric bounds or redundant representation from one drive | Not front/rear actual torque; two independent bounds are not established |
| RearDrive 0x063 and BECM 0x143 | Electrical-current/power interpretation deserves priority over a direct torque interpretation | Comparisons used raw windows; a common operating trend can create correlation |
| Unknown publishers 0x036/0x041 | Intervention/bound hypotheses remain separate from ordinary continuous torque requests | No publisher or units established |
| CDD 0x149 and VCU 0x148 in a selector timing screen | Timing resemblance is insufficient to identify a selector command | CDD may reflect a mode indirectly; publisher alone does not determine meaning |

For 0x050/0x095, saved level correlations are positive in nine informative recordings (0.9333–0.9986). These correlations do not measure ECU causality. First-difference associations are weaker and the selected lag varies.

For 0x063/0x143, correlations in seven motion recordings range from 0.9850 to 0.9976. During reverse motion, the raw-window relationship between 0x050 and 0x063 is negative (−0.7835), whereas 0x063/0x143 remains positive (0.9850). This is useful evidence against casually treating both 0x050 and 0x063 as interchangeable motor torque signals. Stationary recordings do not preserve the same association. Current, power, retransmission and a torque-speed product remain competing explanations.

The saved 0x13A symmetry inventory contains 17,667 frames across 14 recordings, all with A+B=16376. Under the existing display candidate offset −8188, the fields are opposites. The raw frames were not reprocessed for this review. A symmetric limit model and redundant coding must both remain open.

## State and electrical evidence

An existing selector screen contained 365 overlapping windows: 215 from VCU, 139 from BECM and 11 from CDD. These are not 365 independent signals. The best duration match was in CDD 0x149, illustrating why a ten-second state alone does not establish D or R.

Eleven messages absent from the initial window of an AC-start recording also appeared after the baseline in an unlock recording. Message presence therefore cannot identify charging by itself. The unlock baseline already had sustained traffic; full sleep was not demonstrated.

BECM publishes 0x141/0x142/0x143/0x178. This supports the context of existing voltage/current/SOC candidates but does not identify contactor states or measurement locations. The supposed AC-voltage field in 0x178 was constant while the CDD diagnostic value changed; that interpretation remains unvalidated.

## Next raw-data checks

1. Verify hashes and account for every recording, duplicate, clock discontinuity and missing file.
2. Recheck fixed candidates before searching new windows; freeze models on separate recordings and use reverse/regen/standstill as controls.
3. Examine the 0x04B/0x04C pair and distinguish electrical versus mechanical interpretations of 0x063.
4. Keep diagnostic E304, EEB5, E308, E314 and E315 separate. Sequential diagnostic columns are not simultaneous measurements, and matching a display is not physical calibration.
5. Separate request, current/actual torque, positive/negative capability, enable and mode for each drive. Do not force the protocol into an assumed count of six values.

This note revises priorities only. It provides no replay or actuator-control sequence. Source attribution and payload decoding remain distinct evidence layers; raw recordings are not publicly distributed in this snapshot.
