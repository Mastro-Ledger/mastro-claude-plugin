# Mastro for Claude

[Mastro](https://mastroledger.com) is bookkeeping software for CPA firms. This plugin connects
Claude to Mastro, so Claude works in your clients' books live, signed in as you, with exactly your
rights in Mastro.

## What you can do

- Ask about a client's books: balances, reports, spending, and what changed.
- Work the review queue: Claude suggests a category for each bank line, and you approve.
- Check where a reconciliation stands, and what's still outstanding.
- See what's keeping a month from closing.
- Have Claude do the work: categorize bank lines, post journal entries, add rules, and draft
  questions for the client.

Where Claude can draw them, Mastro's own screens (the review queue, a reconciliation, the
month-end close) open in the chat, with their buttons.

Try:

- "List my Mastro clients."
- "What did Craig's Landscaping spend on materials in September?"
- "Go through the review queue and suggest a category for each bank line."
- "Show me where the checking reconciliation stands."
- "What's keeping August from closing?"

## Install

In Claude Code (2.1.275 or later):

```
/plugin install mastro --marketplace Mastro-Ledger/mastro-claude-plugin
```

In Claude or Claude Desktop without the plugin, add a custom connector (Settings → Connectors →
Add custom connector) with the address below.

## Before you start

You need a Mastro account at a firm. Claude reaches only the clients that have Mastro's AI module,
and only what you can already see in Mastro. Your firm decides, area by area in Settings → AI,
whether Claude makes each kind of change, asks first (the change waits for a person at the firm to
approve it), or can't.

## What this plugin contains and connects to

This plugin is configuration only. It runs no code on your computer and installs no packages. It
adds one remote MCP server, Mastro's own:

```
https://app.mastroledger.com/api/mcp
```

When you first use it, Claude opens Mastro's sign-in page. You sign in to Mastro there (Claude
never sees your password) and allow Claude on Mastro's consent page. After that, Claude sends each
tool call to that server, as you, and nowhere else.

## Privacy

- Social Security, tax ID, bank account, and card numbers reach Claude with only their last four
  digits. Employees' pay, withholding, and home addresses never reach it.
- Every call is kept in the client's activity feed in Mastro, with its input scrubbed and a count
  of what came back, never the data read.
- Mastro's privacy policy: <https://mastroledger.com/privacy>

## Help

- Setup and usage: <https://mastroledger.com/claude>
- Support: support@mastroledger.com

## License

MIT for the files in this repository. Mastro itself is a hosted service under its own terms.
