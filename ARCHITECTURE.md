# NEXORA — Initial Architecture

**Status:** Design baseline; implementation details remain subject to review.

## 1. Product boundaries

NEXORA is an independent application that coordinates model providers through their public APIs. It does not scrape private ChatGPT or Claude interfaces, extract provider-private memory, or impersonate either provider's official product.

## 2. Logical components

1. **Web client (React + TypeScript)**
   - Three visible participants: user, model A, and model B.
   - Shared conversation timeline, code workspace, file area, and agent/task status.
   - Explicit controls for pause, resume, stop, and approval.
2. **Application backend (Node.js + TypeScript)**
   - Authentication and session lifecycle.
   - Message routing and collaboration orchestration.
   - Provider adapters and MCP tool gateway.
   - WebSocket event delivery.
3. **Provider adapters**
   - OpenAI API adapter.
   - Anthropic API adapter.
   - Normalized internal message and tool-call contracts.
4. **MCP gateway**
   - Shared tool catalog and schemas.
   - Central authorization and policy enforcement.
   - Tool execution results returned to the requesting model and user-visible session.
5. **Persistence**
   - PostgreSQL for explicitly retained users, sessions, settings, and audit records.
   - Session-only operation by default.
   - Redis is optional and should be introduced only for a demonstrated need such as distributed presence or job coordination.

## 3. Memory and data isolation

- Provider-private memory and conversation history are not imported or exposed.
- Each provider adapter receives only the context explicitly assembled for that request.
- The shared session transcript is a separate data domain.
- Users choose which messages, files, and tool outputs enter shared context.
- Credentials are never included in model prompts or shared transcripts.

## 4. Collaboration orchestration

Initial modes:

- **Peer Review:** one model produces work; the other reviews it.
- **Joint Thinking:** models contribute complementary approaches.
- **Debate:** models challenge assumptions and compare positions.

Safety and control requirements:

- Bounded automatic collaboration; default maximum: five rounds.
- User can pause, resume, or stop at any time.
- Tool calls pass through the same authorization gateway regardless of which model requested them.
- Sensitive or destructive operations require explicit user approval.
- No model may silently expand its own permissions.

## 5. GitHub integration

Use an authorized GitHub integration, preferably the official GitHub MCP Server where appropriate. Scope permissions narrowly. Read operations and write operations must be distinguishable; commits, pushes, releases, issue mutations, and workflow changes require policy checks and user approval.

## 6. Security baseline

- Encrypt provider credentials at rest; isolate them by user and provider.
- Never log raw secrets.
- Enforce least-privilege OAuth scopes.
- Validate tool arguments against registered schemas.
- Treat model output, repository content, issues, and external documents as untrusted input.
- Defend against prompt injection by separating instructions from retrieved content and enforcing permissions outside the model.
- Apply rate limits, usage limits, audit logs, and session isolation.
- Keep the backend secret-bearing; never ship provider keys in frontend bundles.

## 7. Deployment

The complete application requires a backend-capable host. GitHub Pages is suitable only for static documentation or a static landing page; it cannot run the Node.js service or WebSocket backend.

## 8. Initial implementation sequence

1. Repository and TypeScript workspace foundation.
2. Session lifecycle, event model, and WebSocket transport.
3. Provider adapters and credential boundary.
4. Shared MCP catalog and policy gateway.
5. Collaboration orchestrator with bounded rounds.
6. React workspace UI.
7. Persistence, audit, authentication, and deployment hardening.

## 9. Open design decisions

- Authentication and account model.
- Exact provider model selection and streaming contract.
- MCP server process/remote transport lifecycle.
- File storage and retention policy.
- Deployment topology and operational monitoring.
- Automated test strategy and threat-model review.
