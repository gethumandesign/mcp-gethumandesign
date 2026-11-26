# Human Design MCP Server

The hosted MCP server of [gethumandesign](https://www.gethumandesign.com). It
lets an AI assistant calculate Human Design bodygraph charts from birth data,
keep the people you care about in your account, compare two charts, read a
group as a Penta, and read today's transits and your life cycles against your
chart.

This repository holds this README only. The server is hosted; there is nothing
to install or run. Full guide: [gethumandesign.com/mcp-docs](https://www.gethumandesign.com/mcp-docs/).

- **Endpoint:** `https://api.gethumandesign.com/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth 2.0 with a gethumandesign account (email and
  password, Google or GitHub). The first connection opens a sign-in page,
  which also asks for your birth details so your own chart is ready.
- **Registry name:** `com.gethumandesign.www/mcp` in the
  [MCP registry](https://registry.modelcontextprotocol.io)

## Connect

gethumandesign is in the ChatGPT plugin directory (search "gethumandesign") and
in Claude's connector directory (as "Human Design"). Any other MCP client
connects by URL.

**Claude.ai or Claude Desktop:** Connectors → Manage connectors → Add custom
connector, with the URL above.

**Claude Code:**

```bash
claude mcp add --transport http --scope user gethumandesign https://api.gethumandesign.com/mcp
```

**Codex CLI:**

```bash
codex mcp add gethumandesign --url https://api.gethumandesign.com/mcp
codex mcp login gethumandesign
```

**Gemini CLI:**

```bash
gemini mcp add --transport http gethumandesign https://api.gethumandesign.com/mcp
```

**Cursor, VS Code, Windsurf and other clients** that take a JSON config:

```json
{
  "mcpServers": {
    "gethumandesign": {
      "url": "https://api.gethumandesign.com/mcp"
    }
  }
}
```

The setup steps for ChatGPT, Gemini on the web, Grok, Perplexity and Mistral Le
Chat are in the [guide](https://www.gethumandesign.com/mcp-docs/#setup).

## What you can ask

- "What's my type, strategy and authority?"
- "Save my sister: born 14 March 1991, 08:20, in Utrecht."
- "Compare me with my partner. Which channels do we form together?"
- "Which of my saved people have gate 49? Who are the Projectors?"
- "My birth time is only roughly known. What in my chart would change?"
- "Read my family as a Penta." (Pro)
- "What is today's sky doing to my chart?" "When is my Saturn return?" (Pro)

In Claude, ChatGPT and Grok the chart tools also answer with an interactive
card; other clients get the same data as text.

## Tools

The server registers 23 tools.

| Tool | What it does |
| --- | --- |
| `calculate_chart` | Calculate a chart from birth data for someone who is not saved |
| `get_my_design` | The account holder's own chart |
| `get_person_design` | A saved person's chart, by their full name as saved |
| `compare_charts` | Compare two saved people's charts for relationship dynamics |
| `list_people` | List the saved people, with the birth data that tells them apart |
| `find_people` | One question about several saved people at once: who has gate 49, who has an undefined Solar Plexus, everyone's type and authority in one table |
| `save_person` | Save a new person's birth data |
| `update_person` | Correct a saved person: name, birth data, or which of them is you |
| `set_birth_time` | Correct a saved person's birth time, and how sure you are of it |
| `check_birth_time_stability` | How much of a chart the birth day settles, whatever the hour |
| `compare_birth_times` | Compare candidate birth times for a saved person and report what differs |
| `save_group` | Create or update a group in one call (Pro) |
| `list_groups` | List the groups with their members (Pro) |
| `analyse_group` | Penta analysis of a saved group or of 3 to 5 saved people (Pro) |
| `get_transits` | Where every planet is now or on a given day, read against nobody's chart (Pro) |
| `get_person_transits` | The transit field over one saved person's bodygraph, now or on a given day (Pro) |
| `get_pair_transits` | The transit field over two saved people at once (Pro) |
| `rank_transits` | Which saved people today's sky is doing the most to, as one ranked table (Pro) |
| `next_transit` | Search the sky, past or future, for when a gate is entered or an open center activated (Pro) |
| `get_cycles` | The cycles of a saved person's life, dated from the ephemeris (Pro) |
| `read_skill` | One of our written guides to a Human Design topic, by name |
| `get_guidance` | The reference for reading this server's results |
| `send_feedback` | Send feedback to the gethumandesign team |

Deleting is not a tool, on purpose: remove a person or a group on the People
or Groups page in the app. Each tool declares MCP annotations (`readOnlyHint`,
`destructiveHint`, `openWorldHint`); the
[guide](https://www.gethumandesign.com/mcp-docs/) lists them per tool.

## Plans

**Free:** 15 chart calculations per 30 days over MCP and 10 messages per 7 days
in the app's built-in chat. Each window opens on the first use and resets that
long afterwards. Saving people is unlimited.

**Pro:** €3.99 a month or €39.99 a year on the web, VAT included. Charts and
chat within fair use, plus group (Penta) analysis, transits, cycles and
returns, birth-time precision for every gate, channel and center, Color, Tone
and Base on all 26 activations with Variable, and the deepest AI readings. Bought
in the iOS or Android app, Pro costs €4.99 a month or €47.99 a year.

[Pricing](https://www.gethumandesign.com/#pricing)

## How charts are calculated

Planetary positions come from the JPL DE421 ephemeris. Each chart has gate,
line, color, tone and base for all 13 bodies, Personality and Design.

## Links

- Website and app: [gethumandesign.com](https://www.gethumandesign.com)
- MCP guide: [gethumandesign.com/mcp-docs](https://www.gethumandesign.com/mcp-docs/)
- Human Design knowledge base: [gethumandesign.com/docs](https://www.gethumandesign.com/docs/)
- Privacy: [gethumandesign.com/privacy](https://www.gethumandesign.com/privacy/).
  Conversations held through an MCP client are not stored.
- Support: hello@gethumandesign.com

gethumandesign is made by Vink Data en AI B.V., the Netherlands.
