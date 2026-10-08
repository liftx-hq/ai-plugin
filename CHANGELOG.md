# Changelog

## 0.1.2

- Updated Claude installation to use **Add → Add marketplace → Add from a repository**, alongside the Claude Code installation path.
- Clarified all five OAuth permission choices for the connector and plugin, with read enabled by default and selected access authorized through Continue and identity verification.
- Documented optional grant expiry and reconnecting to change granted permissions; remote MCP configuration remains discovery-based.
- Clarified how to distinguish client approval failures from Liftx command evidence without exposing credentials or replaying uncertain trades.

## 0.1.1

- Updated setup guidance for dedicated connection screens and the MCP integration selector.
- Documented Events navigation, on-demand refresh and receipt evidence.
- Aligned Disconnect guidance with namespace revocation and preserved position management.

## 0.1.0

- Remote HTTPS MCP connector with client-managed OAuth discovery.
- Read-only trading review and explicitly invoked position-management skills.
- Exact account/environment scope, user authorization and durable receipt guidance.
