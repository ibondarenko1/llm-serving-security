# Contributing

This is a security reference. Accuracy matters more than completeness - a wrong
row is worse than a missing one.

## Adding a CVE or advisory row

1. The row goes in [cve-matrix.md](cve-matrix.md), under the framework's section.
2. It must be backed by an upstream advisory: a CVE record, a GHSA, or a vendor
   security note. Link the ID to that advisory.
3. Fill the vulnerability **Class** from
   [vulnerability-classes.md](vulnerability-classes.md). If the bug is a new
   class, add the class there first.
4. `Affected` and `Fixed in` come from the advisory, not from memory. If a
   version cannot be confirmed, leave it `verify` rather than guessing.
5. Keep the summary to one line: the sink and the trigger.

## Adding a hardening item

1. It goes in [hardening.md](hardening.md), in the baseline or a framework
   section.
2. State it as a checkable action, not a principle.
3. It should map to a vulnerability class.

## Scope

In scope: the serving and inference layer - the framework process, request
handling, model loading, the inter-process and network surface.

Out of scope: prompt injection, jailbreaks, training-time attacks, and model
alignment. Those are covered well by other projects; this one stays narrow on
purpose.
