# Security policy

## Reporting a vulnerability

Please do **not** open a public issue. Use GitHub's private reporting instead:
open this repository's **Security** tab and choose **Report a vulnerability**.

Include the steps to reproduce and the version or commit you tested.

## Scope

The only code that runs on your machine is `skills/brainstorm-studio/scripts/brain.py`
and `memlog.py`. Both use the Python standard library only and read or write files
inside the folders you point them at.

## Supported versions

| Version | Supported |
|---|---|
| 1.x | Yes |
