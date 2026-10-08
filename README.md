# Liftx for Claude

The Liftx plugin connects Claude to Liftx for trading review and explicitly authorized position management. It contains two skills and one remote MCP configuration. Execution, permissions, subscription eligibility and command receipts remain owned by Liftx.

Connect with personal OAuth access and choose the account scope and permissions in Liftx. All five [permission choices](SETUP.md#permissions) are available; only read starts enabled. Installing the plugin does not grant trading access. This repository is maintained by Liftx; no Anthropic directory listing, review or endorsement is claimed.

## Install

### Claude

1. Open [Customize → Plugins](https://claude.ai/customize/plugins), then choose **Add → Add marketplace**.
2. Choose **Add from a repository**, paste `https://github.com/liftx-hq/ai-plugin` and click **Sync**.
3. Open **Liftx** in the marketplace and click **Add**.
4. Connect the plugin's **Liftx** connector, then sign in to **Liftx** and approve your chosen access.

### Claude Code

```text
/plugin marketplace add liftx-hq/ai-plugin
/plugin install liftx@liftx
```

Open `/mcp`, select the Liftx plugin connector and follow the browser OAuth flow. The only server URL is `https://mcp.liftx.io/mcp`. Begin with read access, review the account and exact linked-account/instrument scope, and grant trading permissions only when intended. Never paste a Liftx API key, TradingView capability, password or OAuth token into a conversation or plugin file. See [setup](SETUP.md).

| Skill | Use |
| --- | --- |
| `/liftx:review` | Inspect current positions, attached orders, protections and receipts; explain exposure and gaps without trading. |
| `/liftx:manage` | Prepare an exact position action, obtain explicit approval, submit once and report its durable receipt. User invocation is required. |

Examples:

- “Review my demo positions and identify any missing or pending protection.”
- “Explain why this command is unresolved without retrying the trade.”
- “`/liftx:manage` Prepare a stop adjustment for this exact position, then show me the change before submitting.”

Read results are observations, not execution guarantees. Acceptance, handoff or `execution_observed` does not prove a fill, completed modification, or flat exposure. An uncertain command is never retried under a new identity or compensated automatically.

See [Claude's plugin guide](https://support.claude.com/en/articles/13837440-use-plugins-in-claude) for supported clients and organization marketplace policies. To connect without the bundled skills, follow the [remote connector instructions](https://docs.liftx.io/mcp/claude#remote-connector).

Use **MCP** in [Liftx Integrations](https://app.liftx.io/settings/integrations) to inspect or disconnect an authorized client. The header’s **Events** button opens command receipts; acceptance does not establish a fill or closure. See [connection management](SETUP.md#connections-and-command-evidence-in-liftx).

See [security](SECURITY.md), [release notes](CHANGELOG.md) and [Liftx documentation](https://docs.liftx.io). General support: support@liftx.io.
