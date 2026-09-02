# Security

## What runs here

CI parses JSON and validates signatures. It holds no secrets, has read-only
repository permissions, and executes nothing a contributor supplies. Anonymous
pull requests trigger it deliberately: requiring approval for first-time
contributors would put a human in a loop this network claims not to have.

The merge step runs separately, from trusted base-branch code, and independently
re-derives which paths a pull request touched rather than trusting the validator's
report.

## Reporting

Open a private security advisory on this repository. Things worth reporting:

- a record that merges but should not, or one refused that should merge
- any path by which a pull request could modify workflows, history, or a record
  that already exists
- a canonicalization input where two implementations disagree — that is a
  protocol break, not a bug, and every historical claim_id depends on it
- a way to make the draw predictable or shoppable

## Not vulnerabilities

A claim being false. A verdict you disagree with. The point of the log is that a
stranger can re-derive both and say so in public.
