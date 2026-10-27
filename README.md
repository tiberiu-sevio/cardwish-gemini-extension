# Cardwish for Gemini CLI

Graded trading-card market data inside Gemini CLI: search cards, read live
listings, sold-price history and market stats, and manage price alerts across
eBay, Catawiki, MySlabs, Goldin, Fanatics and Alt.

## Install

1. Get a free API key at [cardwish.cc](https://cardwish.cc) — the free plan
   includes 10,000 requests a month, no card needed. Keys live in your
   [developer portal](https://my.cardwish.cc/keys/).
2. Export it and install the extension:

```bash
export CARDWISH_API_KEY=cw_live_...   # add to your shell profile
gemini extensions install https://github.com/tiberiu-sevio/cardwish-gemini-extension
```

3. Ask away:

```
gemini "What's a PSA 10 Base Set Charizard selling for lately?"
```

### Keyless (OAuth) alternative

Gemini CLI can also connect with OAuth instead of a key — skip the extension
and add the server directly, then authenticate with `/mcp auth cardwish`:

```bash
gemini mcp add --transport http cardwish https://mcp.cardwish.cc/
```

## What you get

`search_cards`, `get_card`, `get_market_stats`, `get_price_history`,
`list_listings`, `create_alert`, `list_alerts`, `test_alert`, `delete_alert`
and `get_usage` — the same data as the [REST API](https://api.cardwish.cc/docs),
shaped for conversation. The bundled GEMINI.md context teaches Gemini the
house rules: resolve the card id first, never mix currencies, caveat small
samples.

## Other clients

Claude, ChatGPT, Cursor and plain MCP setups are covered at
[cardwish.cc/connect](https://cardwish.cc/connect/).
