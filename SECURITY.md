# Security Policy

## Reporting a vulnerability

Please do not disclose exploitable vulnerabilities in public issues. Until a dedicated private security contact is established, use GitHub's private vulnerability reporting feature for this repository if it is enabled. Include affected versions or commits, reproduction steps, impact, and any suggested mitigation.

Do not include real API keys, access tokens, passwords, private keys, or personal data in reports.

## Security expectations

NEXORA handles model-provider credentials and may execute actions against connected services. Security is a core requirement, not an optional feature.

- Provider credentials must be encrypted at rest and isolated by user/provider.
- Secrets must never be sent to the browser unless strictly required (provider keys should remain server-side).
- Secrets must not appear in prompts, logs, traces, error messages, or audit payloads.
- Integrations must use least-privilege permissions.
- Tool execution must be authorized by backend policy, not by model-generated claims.
- Retrieved repository content and external documents are untrusted and may contain prompt-injection attempts.
- Sensitive writes and destructive operations require explicit user approval.
- Sessions must be isolated; shared context must be explicit.
- Rate limits, cost controls, and auditable action records are required.

## Scope and maturity

NEXORA is experimental and is not yet suitable for production use. This policy describes intended security requirements; it does not claim that all controls are already implemented.
