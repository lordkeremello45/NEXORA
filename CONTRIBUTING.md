# Contributing to NEXORA

NEXORA is experimental. Contributions should prioritize correctness, security, testability, and clear separation between provider-specific behavior and shared orchestration.

## Before opening a change

- Read [README.md](README.md), [ARCHITECTURE.md](ARCHITECTURE.md), and [SECURITY.md](SECURITY.md).
- Keep changes focused and explain the user-visible or architectural reason.
- Do not commit credentials, tokens, private keys, personal data, or production logs.
- Do not introduce provider-private memory scraping or hidden cross-provider context sharing.
- Add or update tests for behavior changes.
- Document new permissions and tool side effects.

## Pull requests

A pull request should include:

1. Summary and motivation.
2. Technical approach and relevant design trade-offs.
3. Tests run and their results.
4. Security, privacy, and migration implications.
5. Screenshots or recordings for meaningful UI changes, where applicable.

## Development status

The repository is being scaffolded. Build scripts, coding conventions, and CI requirements will be documented when the initial workspace is added.
