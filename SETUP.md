# Connect to Liftx

Use the hosted remote connector at `https://mcp.liftx.io/mcp`. The package contains no shared credential, embedded OAuth client secret or local server. OAuth discovery and browser authorization belong to the client and Liftx; do not manually construct an authorization URL or add an Authorization header.

1. Install the plugin using the README instructions. In Claude Code, open `/mcp` and authenticate the Liftx plugin connector. For Claude's custom-connector UI, select **Register automatically** for the OAuth client; the published-identity/CIMD option is not supported by this Liftx implementation.
2. Confirm that the browser authorization page belongs to Liftx. Review the signed-in account, requested operations, exact linked accounts and instruments. Distinguish **demo** from **live** before granting access.
3. Start with read permission. Authorize trading separately in Liftx only for the operations and scope you intend. A client tool prompt cannot expand the server grant.
4. Discover the server's actual tools and schemas, then perform a bounded read to verify account, link, environment and instrument authority. Do not infer an exchange or instrument from a ticker string.
5. For a write, use the management skill and approve the concrete action. A request to inspect or suggest changes never authorizes a trade.

Liftx enforces Pro/trial eligibility, current scope, expiry and revocation. Plugin installation and paid Claude access do not grant Liftx entitlement. If the endpoint is unavailable or authentication fails, stop and report that boundary; do not switch to API keys, browser-session extraction, direct exchange access or another host.

## Connections and command evidence in Liftx

Open [Settings → Integrations](https://app.liftx.io/settings/integrations) and select **MCP** in the integration dropdown. **Connect** opens the [New MCP connection screen](https://app.liftx.io/settings/integrations/mcp/new-connection), with ChatGPT and Claude instructions, copy controls and a button to open the chosen client. OAuth starts from that client; visiting the Liftx setup screen alone creates no connection. Back returns to the connection list.

After consent, use the list's **Refresh** icon to reload connection metadata. **Authorized** describes the grant's lifetime, not a successful trading command. Use the header's **Events** button, or open [Events](https://app.liftx.io/settings/integrations/events), to inspect command receipts. Its header **Refresh** loads the latest events; scrolling loads older receipts within a bounded history window. The screen does not poll. Verify execution against the actual position and orders.

## Reconnect and disconnect

Use the client's OAuth reconnect flow for expired authentication. Do not send tokens or callback URLs in a chat or issue report. Reconnecting does not authorize replaying an uncertain mutation: recover the original command identity and receipt first.

In Liftx Integrations, select **MCP** and choose **Disconnect** on the connection to end server access, then disconnect or uninstall the connector in Claude. A confirmed disconnect removes the item and blocks new requests through its integration namespace. Client removal alone is not proof of server revocation. Existing positions and their protection, termination and recovery continue; disconnecting does not close exposure. Inspect metadata after an uncertain response before an explicit retry.

## Client format references

This package follows Claude's documented [plugin manifest](https://code.claude.com/docs/en/plugins-reference), [marketplace](https://code.claude.com/docs/en/plugin-marketplaces), [remote MCP](https://code.claude.com/docs/en/mcp) and [skill](https://code.claude.com/docs/en/skills) formats.

ChatGPT connects through its own [remote-MCP setup](https://docs.liftx.io/mcp/chatgpt). This repository does not claim an installed OpenAI plugin or directory listing. OpenAI documents a separate [Claude-plugin import and submission workflow](https://developers.openai.com/plugins/guides/submit-claude-plugin); publication here does not perform that workflow or grant approval.
