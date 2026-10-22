# EpicTexting: Send SMS from Your AI Agent (Twilio)

Your agent sends the text. EpicTexting sends SMS from your own Twilio number: one message or a personalised bulk text, with delivery status and replies.

It works in Claude Code, Codex, Cursor, Gemini CLI, OpenClaw, Hermes and any agent that reads [Agent Skills](https://agentskills.io) or speaks MCP.
Under the hood it is the hosted EpicTexting MCP server, `https://www.epictexting.app/api/mcp/mcp`, with a one-time OAuth sign-in and no API key. Website: https://www.epictexting.app/?ref=github-agent

## Install

| Agent | Install |
|---|---|
| **Any agent** ([skills.sh](https://skills.sh)) | `npx skills add IndianAppGuy/epictexting-agent` |
| **Claude Code** | `/plugin marketplace add IndianAppGuy/epictexting-agent` then `/plugin install epictexting@epictexting` |
| **Codex** | `codex mcp add epictexting --url https://www.epictexting.app/api/mcp/mcp` then `codex mcp login epictexting` (+ `npx skills add IndianAppGuy/epictexting-agent -a codex`) |
| **OpenClaw** | `openclaw skills install @theindianappguy/epictexting` |
| **Hermes Agent** | `hermes skills install IndianAppGuy/epictexting-agent/skills/epictexting` |
| **Gemini CLI** | `gemini extensions install https://github.com/IndianAppGuy/epictexting-agent` |
| **Cursor** | [![Add EpicTexting MCP to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=epictexting&config=eyJ1cmwiOiJodHRwczovL3d3dy5lcGljdGV4dGluZy5hcHAvYXBpL21jcC9tY3AifQ==) |
| **Claude.ai / ChatGPT / any MCP client** | Remote MCP server `https://www.epictexting.app/api/mcp/mcp` (Streamable HTTP, OAuth) |

Then ask your agent: *"Text +1 415 555 0134: running 10 minutes late, see you at 6:10."*

## Tools

| Tool | What it does | Kind |
|---|---|---|
| `get_account_status` | Twilio connected?, default sender, plan, SMS left this month | read-only |
| `list_sender_numbers` | Twilio numbers you can send from | read-only |
| `send_sms` | Send one SMS | **sends / acts** |
| `send_bulk_sms` | Send the same SMS to up to 50 people, personalised with {name} | **sends / acts** |
| `list_recent_messages` | Recent sent and received SMS | read-only |
| `get_message_status` | Delivery status of one message by SID | read-only |

## Safety

- **Always confirm before sending.** Show the user exactly who gets what text (every number and the final message, with `{name}` filled in for one example), and for bulk sends the count of SMS. Wait for a clear yes. One send per yes.
- Numbers must be international format (`+15551234567`, `+919876543210`).
- Only text people who expect to hear from the user. No spam, no purchased lists, no marketing to people who haven't opted in. Respect STOP replies.
- If a result has `connect_url`, Twilio isn't connected: give the user that link and stop. If it has `upgrade_url`, the monthly limit is reached: share it.

The full agent instructions are in [`skills/epictexting/SKILL.md`](skills/epictexting/SKILL.md).

## Links

[Website](https://www.epictexting.app/?ref=github-agent) · [Docs](https://www.epictexting.app/blog/send-sms-from-claude) · [Privacy](https://www.epictexting.app/privacy) · [Terms](https://www.epictexting.app/terms) · [Support](https://www.epictexting.app/support)

MIT licensed.
