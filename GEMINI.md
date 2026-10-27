# Cardwish: graded-card market data

Cardwish aggregates live listings and sold prices for graded trading cards
(Pokémon, Magic, Yu-Gi-Oh!, One Piece and more — PSA/BGS/CGC slabs) across
eBay, Catawiki, MySlabs, Goldin, Fanatics and Alt. The MCP tools return real
marketplace data, never estimates.

## Tool flow

1. **Always resolve the card first** with `search_cards` ("charizard base
   set", "LOB-001") — every other tool needs the card id it returns. If
   several printings match, ask the user which one they mean.
2. **"What is it worth?"** → `get_market_stats` (default 90d): sale count,
   min/median/max and last sale per grade × marketplace × currency, plus the
   live lowest ask. Lead with the median for the asked grade; mention sample
   size.
3. **Trends** → `get_price_history` (interval "day" for buckets, "raw" for
   individual sales).
4. **"Anything for sale?"** → `list_listings` (status "active") — always
   include each listing's `url`.
5. **"Watch it for me"** → `create_alert` (`price_below`/`price_above` need
   threshold + currency; `new_listing` fires on any new match).

## Rules

- Never mix or convert currencies — report each separately.
- Grades are not interchangeable; filter by grading_company + grade when the
  user names one.
- Caveat small samples: one sale in 90 days is an anecdote, not a market
  price.
- A 429 means the monthly quota is used up — point the user at
  https://my.cardwish.cc/usage/ instead of retrying.
