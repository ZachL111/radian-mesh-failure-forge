# Radian Mesh Failure Forge Walkthrough

I use this file as a small checklist before changing the SQL implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 169 | ship |
| stress | lease drift | 172 | ship |
| edge | replica lag | 176 | ship |
| recovery | membership churn | 216 | ship |
| stale | quorum health | 209 | ship |

Start with `recovery` and `baseline`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

`recovery` is the optimistic case; use it to make sure the scoring path still rewards strong signal.
