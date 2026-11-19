# NEXORA

**Independent Minds. One Workspace.**

NEXORA is an unofficial, experimental multi-agent AI workspace — an **AI Birleştirici** that brings independent AI models and a human operator into one shared workspace through API integrations and the Model Context Protocol (MCP).

> **Experimental software:** Outputs may be inaccurate, incomplete, or unreliable. Verify important results before acting on them.

NEXORA is an independent project and is **not affiliated with, endorsed by, or officially connected to OpenAI, Anthropic, or any other model provider**. Product and company names are used only to identify compatible services.

## Project direction

- A shared workspace for the user, ChatGPT-compatible models, and Claude-compatible models.
- Separate provider conversations and private memories; only explicitly shared session content is exchanged.
- A common MCP tool catalog with consistent schemas and permission policies.
- Human-controlled collaboration modes: **Peer Review**, **Joint Thinking**, and **Debate**.
- Bounded model-to-model collaboration with pause, resume, and stop controls.
- GitHub workflows through authorized integrations, with explicit approval for sensitive writes.
- Session-only data by default; persistence is opt-in.

## Architecture at a glance

- **Web app:** TypeScript, React
- **Backend:** TypeScript, Node.js, WebSocket
- **Storage:** PostgreSQL; Redis may be added where justified
- **Integrations:** OpenAI API, Anthropic API, shared MCP client/tool gateway, GitHub MCP
- **Credentials:** BYOK and server-provided credentials, isolated and encrypted

The application is designed to run as its own web service. GitHub Pages can host static documentation or a marketing site, but it cannot host the Node.js backend, WebSocket service, or secret-bearing API operations.

## Important API billing note

ChatGPT and Claude subscriptions do not automatically include API usage. Connecting a provider generally requires a separately configured API key or an explicitly provided server-side key, and API charges may apply.

## Status

NEXORA is in the initial design and scaffolding phase. Features described above are project goals, not claims that they are already implemented.

## Security

Read [SECURITY.md](SECURITY.md) before reporting a vulnerability. Never commit API keys, access tokens, private keys, or personal credentials.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). The architecture and security model are expected to evolve as implementation and testing progress.

## License

The application source is intended to be licensed under **GNU AGPL-3.0**. Third-party components retain their respective licenses; see [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md). Documentation may be separately identified as CC BY 4.0 where explicitly marked.
