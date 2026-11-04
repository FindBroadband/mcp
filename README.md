# FindBroadband MCP servers

<img src="assets/icon.png" alt="FindBroadband" width="64" align="right">

Two hosted [MCP](https://modelcontextprotocol.io) servers from [FindBroadband](https://www.findbroadbanddeals.com) for ChatGPT, Claude, Cursor and any other AI assistant that supports remote MCP servers:

- **FindBroadband (deals):** the broadband deals available at your exact UK address, priced on their true whole-contract cost, and whether your bill or renewal quote is too high.
- **Internet Outage Checker by FindBroadband:** whether a UK broadband provider is down right now, where, what the provider has said and how the last 30 days have gone.

Both are free, need no account or API key and only read FindBroadband's data. This repo holds the connection details and plugin manifests; the servers themselves run on findbroadbanddeals.com. Full documentation: **https://www.findbroadbanddeals.com/ai-assistants**

## Endpoints

| App | Claude | Cursor, VS Code and other MCP clients |
|---|---|---|
| Deals | `https://www.findbroadbanddeals.com/api/mcp/claude` | `https://www.findbroadbanddeals.com/api/mcp/standard` |
| Outage checker | `https://www.findbroadbanddeals.com/api/mcp/outages` | `https://www.findbroadbanddeals.com/api/mcp/outages` |

Streamable HTTP, no authentication. Both are listed in the official [MCP Registry](https://registry.modelcontextprotocol.io) as `com.findbroadbanddeals/broadband-deals` and `com.findbroadbanddeals/broadband-outages`.

## Connect

**Claude:** Settings, then Connectors, then Add custom connector, and paste the Claude link above.

**Claude Code:** install from this repo's plugin marketplace:

```
/plugin marketplace add FindBroadband/mcp
/plugin install internet-outage-checker@findbroadband
/plugin install findbroadband-deals@findbroadband
```

**ChatGPT:** install the [FindBroadband app](https://chatgpt.com/plugins/plugin_asdk_app_6a903582749c81918a70aeef2acfadbd). The outage checker is coming to ChatGPT soon.

**Cursor, VS Code and other clients:** add to your `mcp.json`:

```json
{
  "mcpServers": {
    "findbroadband": { "url": "https://www.findbroadbanddeals.com/api/mcp/standard" },
    "findbroadband-outages": { "url": "https://www.findbroadbanddeals.com/api/mcp/outages" }
  }
}
```

## Deals: tools

| Tool | What it does |
|---|---|
| `search_addresses` | Lists the addresses at a UK postcode, so results can be for your exact property. Broadband availability differs from one home to the next. |
| `find_broadband_deals` | The deals available at your address, with a best value, cheapest and fastest pick. Every deal shows its monthly price, contract length, speed and true whole-contract cost, with intro pricing, later price rises and setup fees included. |
| `check_if_overpaying` | Compares what you pay, or a renewal price your provider quoted, with comparable deals at your address and gives the saving over 24 months. |
| `get_deal_details` | The full terms of one deal: setup costs, price rises, what happens after the intro period and whether it's available at your address. |

Try asking:

- "Find broadband deals at 1 Fyfields, SS13 1HJ."
- "I'm with Sky paying £44 a month for 100Mb at SS13 1HJ. Am I overpaying?"
- "Find me full fibre under £30 a month with no mid-contract price rises."

The numbers come from FindBroadband, not the assistant. When you pick a deal, you switch on findbroadbanddeals.com. Nothing is bought inside the chat.

## Outage checker: tools

| Tool | What it does |
|---|---|
| `get_outage_overview` | Every UK provider FindBroadband tracks, with its status (Down, Issues earlier or Working fine) and the places affected. |
| `get_provider_outage_status` | One provider's status, the incidents going on now and recent ones in the provider's own words, and a day by day picture of the last 30 days. |
| `get_outage_history` | The outages a provider has had in the last 30 days, or which providers had problems on a given day. |

Try asking:

- "Is BT down right now?"
- "Is there a broadband outage in the UK at the moment?"
- "Has Virgin Media had any problems this week?"

Where FindBroadband can read a provider's own status page, that decides the status. For the rest it comes from public reports, which the provider hasn't confirmed. There is no outage data for individual addresses, so the assistant can say what's been reported and where, not whether your own line is affected.

## Your data

The deals app receives the postcode or address and the filters you ask about. The outage checker receives only a provider name, a number of days or a date. Neither receives your name, email or conversation. See the [privacy policy](https://www.findbroadbanddeals.com/privacy), under "Using FindBroadband in an AI assistant".

## Help

Email hello@findbroadbanddeals.com or use the [contact page](https://www.findbroadbanddeals.com/contact).

## Licence

The manifests and docs in this repo are MIT licensed. Use of the hosted servers is covered by FindBroadband's [terms](https://www.findbroadbanddeals.com/terms).
