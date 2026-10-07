# Connect to Liftx

Use the hosted remote connector at `https://mcp.liftx.io/mcp` after Liftx announces availability. The package contains no shared credential, embedded OAuth client secret or local server. OAuth discovery and browser authorization belong to the client and Liftx; do not manually construct an authorization URL or add an Authorization header.

1. Install the plugin using the README instructions. In Claude Code, open `/mcp` and authenticate the Liftx plugin connector. For Claude's custom-connector UI, select **Register automatically** for the OAuth client; the published-identity/CIMD option is not supported by this Liftx implementation.
2. Confirm that the browser authorization page belongs to Liftx. Review the signed-in account, requested operations, exact linked accounts and instruments. Distinguish **demo** from **live** before granting access.
3. Start with read permission. Authorize trading separately in Liftx only for the operations and scope you intend. A client tool prompt cannot expand the server grant.
4. Discover the server's actual tools and schemas, then perform a bounded read to verify account, link, environment and instrument authority. Do not infer an exchange or instrument from a ticker string.
5. For a write, use the management skill and approve the concrete action. A request to inspect or suggest changes never authorizes a trade.

Liftx enforces Pro/trial eligibility, current scope, expiry and revocation. Plugin installation and paid Claude access do not grant Liftx entitlement. If the endpoint is unavailable or authentication fails, stop and report that boundary; do not switch to API keys, browser-session extraction, direct exchange access or another host.

## Reconnect and revoke

Use the client's OAuth reconnect flow for expired authentication. Do not send tokens or callback URLs in a chat or issue report. Reconnecting does not authorize replaying an uncertain mutation: recover the original command identity and receipt first.

Revoke the Liftx grant in Liftx to end server access, then disconnect or uninstall the connector in Claude. Client removal alone is not proof of server revocation. Revocation blocks new authorized handoffs; it does not interrupt protection, termination or recovery already owned by Liftx.

## Client format references

This package follows Claude's documented [plugin manifest](https://code.claude.com/docs/en/plugins-reference), [marketplace](https://code.claude.com/docs/en/plugin-marketplaces), [remote MCP](https://code.claude.com/docs/en/mcp) and [skill](https://code.claude.com/docs/en/skills) formats. Configuration-format compatibility does not attest hosted OAuth or trading behavior; those require separate release qualification.

ChatGPT connects through its own remote-MCP setup. This repository does not claim an installed OpenAI plugin or directory listing. OpenAI documents a separate [Claude-plugin import and submission workflow](https://developers.openai.com/plugins/guides/submit-claude-plugin); publication here does not perform that workflow or grant approval.
