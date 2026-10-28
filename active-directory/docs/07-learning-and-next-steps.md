# Learning sources and next steps

[Back to overview](../README.md)

## Learning source

This lab was built while following **Labs Hands On — Mastering Active Directory (AD DS)**, presented by **Vikas Singh**. The supplied material contains the introduction/fundamentals transcript and a pasted page containing the lab setup, AD installation and post-configuration lesson. Four copies of the fundamentals transcript are identical.

The course supports the learning context. Completion claims in this project are based on the lab screenshots, recordings and original project notes. A course playlist listing later topics is not evidence that those topics have been completed. The full transcripts are not reproduced in this repository.

A verified course/video URL can be added when supplied; no URL has been guessed.

## Reflections from the lab

- Object organisation makes administration easier to explain and repeat.
- A computer object in AD, a successful user sign-in and access to a resource are distinct results.
- Seeing an object through two controllers is useful evidence, but replication health needs more than matching names.
- Site objects describe a location model; networking and controller placement must support that model.
- Troubleshooting is stronger when the exact change and before/after outputs are recorded.

## Planned work

1. Finish the [validation checklist](06-validation-and-troubleshooting.md), including final group memberships and account-state tests.
2. Capture DC inventory, replication diagnostics and exact site/subnet names.
3. Build a departmental file-access example and prove allowed and denied access through security-group membership.
4. Apply a scoped workstation GPO and verify the client result.
5. Test a routed branch site and document client site discovery.
6. Add a tested recovery exercise before claiming backup/recovery capability.

These are future exercises. GPO deployment, delegated administration, FSMO transfer, RODC deployment, backup/restore, production failover and SQL integration are not claimed as completed here.
