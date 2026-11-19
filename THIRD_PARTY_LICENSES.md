# Third-Party License Register

This file tracks third-party software and services used by NEXORA. It is an initial register, not a complete software bill of materials.

| Component | Intended use | License / terms | Notes |
|---|---|---|---|
| GitHub MCP Server | Optional GitHub tool integration | MIT (upstream project) | Preserve upstream copyright and license notices if code is redistributed. |
| OpenAI API | Model provider integration | OpenAI service and API terms | API access and billing are separate from ChatGPT subscriptions. |
| Anthropic API | Model provider integration | Anthropic service and API terms | API access and billing are separate from Claude subscriptions. |
| Model Context Protocol (MCP) | Tool interoperability protocol | Check the license of each SDK/server used | Protocol implementations may have different licenses. |

Before release:
- Generate and review a dependency inventory/SBOM.
- Verify each dependency's exact license and version.
- Preserve required copyright and attribution notices.
- Review compatibility with the project's AGPL-3.0 licensing.
- Do not assume that using an external service grants rights to redistribute its software.
