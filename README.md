# Liftx for Claude

The Liftx plugin connects Claude to Liftx for trading review and explicitly authorized position management. It contains two skills and one remote MCP configuration. Execution, permissions, subscription eligibility and command receipts remain owned by Liftx.

**Availability:** this package is prepared for release. Hosted OAuth/MCP access must pass release qualification before it is advertised as available. Installing these files does not activate Liftx MCP or grant trading access. This repository is maintained by Liftx; no Anthropic directory listing, review or endorsement is claimed.

## Install when released

In Claude Code:

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

Claude also documents [custom plugin upload](https://support.claude.com/en/articles/13837440-use-plugins-in-claude). Use only an official reviewed Liftx release archive when available. Public GitHub marketplace installation in Claude Code is distinct from organization repository syncing; the latter currently requires a private/internal repository. Where only custom remote connectors are supported, add the same MCP URL using that client's connector settings; this does not install the bundled skills. Check current client support and organizational policy.

See [security](SECURITY.md), [release notes](CHANGELOG.md) and [Liftx documentation](https://docs.liftx.io). General support: support@liftx.io.
