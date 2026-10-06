# BetBank MCP connector

Ask Claude about Australian sports betting markets and get answers from your own [BetBank](https://betbank.ai/) account: bookmaker odds compared, +EV picks, price moves, promotions, stats, and your own bets and results.

This is a **hosted** MCP server. There is nothing to install: you add one URL to your MCP client and sign in with your BetBank account.

```
https://betbank.ai/api/mcp
```

The tools answer for BetBank Gold members. See [betbank.ai/pricing](https://betbank.ai/pricing).

## Connect

**Claude (claude.ai and the desktop app):** Settings → Connectors → Add custom connector → paste `https://betbank.ai/api/mcp` → Connect, then approve on the BetBank page that opens.

**Claude Code:**

```bash
claude mcp add --transport http betbank https://betbank.ai/api/mcp
```

then run `/mcp` and choose betbank to sign in.

**Other MCP clients** (Cursor, VS Code, and anything that supports remote servers over Streamable HTTP with OAuth): add `https://betbank.ai/api/mcp` as a remote server. The client registers itself and opens BetBank's sign-in and consent page.

## What you can ask

| Tool | What it does |
| --- | --- |
| `get_todays_games` | Today's or tomorrow's fixtures, with live scores and statuses |
| `get_odds` | Current bookmaker odds for one match, best price first; pick a market or get the main one |
| `find_value` | Current arbitrage, middles and low-hold markets across bookmakers |
| `get_ev_picks` | BetBank's +EV picks: bets priced above a fair price |
| `get_price_movement` | The biggest recent odds moves, steaming or drifting |
| `get_stats` | Ladders, stat leaders, and team or player season summaries with recent form |
| `get_promotions` | Current bookmaker promotions, described and linked |
| `get_track_record` | BetBank's published betting performance, with its scope and as-of date |
| `get_my_bets` | Your own bets from your BetBank tracker |
| `get_my_performance` | Your own P&L, ROI, strike rate, CLV and per-league breakdown |
| `prefill_log_bet` | A link that opens your Bet Tracker with a bet filled in; you review and log it yourself |
| `create_price_alert` | Tell you (push or email) when a price reaches your target |
| `list_my_alerts` | Your active price alerts |
| `cancel_price_alert` | Cancel one of your alerts |
| `link_to_tool` | A link to the right page in BetBank when a page does the job better than chat |

Examples: "What's the best price on the Broncos tonight?", "Any arbs in the NBA right now?", "How am I going on NRL this season?", "Tell me if Collingwood gets to 2.10."

## How sign-in and your data work

- **OAuth 2.1 with PKCE.** Your MCP client never sees your BetBank password. You approve access on betbank.ai, and you can disconnect from your client at any time.
- **It acts as you.** Every request runs as your BetBank account, so the tools see only what your account can see, and only your own bets and alerts.
- **It never places a bet.** BetBank is an analytics and information tool, not a bookmaker. `prefill_log_bet` only fills in your own tracker for you to review.

## About

BetBank.ai is an Australian sports betting analytics tool. It does not accept bets, hold funds or arrange gambling transactions. Prices change quickly, and an odds comparison is information, not advice.

**18+ only. Gamble responsibly.** If gambling is causing harm for you or someone you know, call Gambling Help Online on 1800 858 858 (free, confidential, 24/7) or visit [gamblinghelponline.org.au](https://www.gamblinghelponline.org.au/).

Support: [betbank.ai](https://betbank.ai/) · This repository holds the listing only (README and registry metadata); the server is hosted by BetBank.
