# Evidence status

Readers should be able to tell what was tested, what was reported earlier, and what remains an idea. Attach status to the specific claim rather than giving an entire map or method a blanket “verified” label.

## Evidence labels

| Label | Meaning | What the record must say |
| --- | --- | --- |
| **Verified in the stated environment** | A documented check was actually run on the identified inputs and its result was inspected. | Source revision, environment/version, date, check, result, evidence, and limits |
| **Historical / reported** | The statement comes from an earlier source, report, review, or recorded test and has not been freshly reproduced for the current task. | Original source, known context/date, what it reports, and missing details |
| **Experimental** | An approach or implementation exists but has incomplete validation for the intended use. | What exists, what has been observed, and the checks still needed |
| **Unverified** | The claim is a proposal, inference, undocumented assumption, or statement without sufficient evidence. | Why it is unverified and what would establish it |

“Verified” is always bounded. A checksum check verifies file integrity; it does not verify art quality. A successful test in one client version does not establish compatibility with every version or device.

The same rule applies across BAWES Universe and WorkAdventure: name the implementation and revision actually tested. Leave other forks or versions unverified until supported by their own evidence.

## Keep outcome separate from evidence

The evidence label describes how a claim is supported. The outcome describes what the attempt achieved.

Useful outcome descriptions include:

- **Accepted for the stated purpose:** the named reviewer accepted the result against stated criteria.
- **Needs revision:** useful progress, with remaining defects or unmet criteria.
- **Rejected for the intended direction:** the result did not meet that goal; narrower lessons may still be useful.
- **Preserved as reference:** retained for comparison or history without a readiness claim.
- **Not reviewed:** no acceptance decision has been recorded.

An unsuccessful experiment can have strong evidence. A polished-looking proposal can have weak evidence. Preserve both distinctions.

## Archive interpretation

**10 October 2026 update:** the [current pinned archive](https://github.com/BAWES-Universe/universe-maps/tree/03d83f2dd74108a6f75847bd2f7d03c5d619c950/map-mocks) has 26 records. The [versioned catalogue](catalogue/README.md) also tracks later maps and Wokas. The following fourteen-entry description applies to the original snapshot, not the expanded archive.


The [pinned map archive](https://github.com/BAWES-Universe/universe-maps/tree/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks) has 14 entries: 10 Tiled candidates, three visual-only proposals, and one art/lighting study. Treat archive reports as historical evidence unless a contribution includes a fresh, fully identified reproduction.

The archive's [verification report](https://github.com/BAWES-Universe/universe-maps/blob/d818e6c4c001e5fa7ba76e02663a1fb9ce9460fd/map-mocks/VERIFICATION.md) describes its own checks and exclusions. Cite those checks at their actual scope. Archive integrity and offline checks are not current full-client, multiplayer, device, or visual acceptance.

Do not replace a preserved status with “ready” simply because the source has been indexed here. See [experiment history](experiment-history.md) for individual outcomes and known limitations.

## A compact claim record

Use these fields when adding a reusable finding:

- **Claim:** one specific behavior or result.
- **Evidence label:** one of the labels above.
- **Source:** repository, exact revision, and path or immutable artifact identity.
- **Test context:** tool/runtime version, environment, date, and tester, or `not recorded`.
- **Observed result:** what the evidence actually demonstrates.
- **Evidence:** direct link to the report, image, recording, or output.
- **Limits:** what was not tested or cannot be concluded.
- **Outcome:** the acceptance or rejection decision and its scope.
- **Next check:** the smallest useful step needed to increase confidence.

The [experiment template](../templates/experiment.md) provides a fuller record.

## Updating a claim

When a later test changes the conclusion, keep the earlier source and explain the difference. Identify whether the inputs, runtime, method, or acceptance criteria changed.

If a source becomes unavailable, flag the access problem. Do not invent its contents or quietly transfer its confidence to a replacement. If the original source can only be described from an earlier report, label it historical/reported and retain that limitation.

[Back to the kit](../README.md) · [Validation guide](validation.md)

