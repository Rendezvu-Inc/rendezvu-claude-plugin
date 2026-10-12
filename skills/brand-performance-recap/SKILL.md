---
name: brand-performance-recap
description: Build a performance recap of a brand's Rendezvu ambassador program (sales, top hosts, funnel, campaigns, gifting) from live data through the Rendezvu MCP tools. Use when a Rendezvu brand admin asks for a monthly or quarterly recap, a leadership or board update, a program review, or "how is our ambassador program doing?".
---

# Brand performance recap

Use this when a Rendezvu brand admin wants a written summary of how their ambassador program performed over a period. Every number in the recap must come from a Rendezvu tool call made in this conversation. Never estimate, fill in, or carry a number over from memory.

## 1. Settle the period and the brand

- Use the period the user names. If they name none, use the last full calendar month and say so at the top of the recap.
- Most tools default to the last 30 days, and `click_funnel` to the last eight weeks. Always pass the period explicitly so every section covers the same window.
- If the account administers more than one brand and the user did not say which one, ask before pulling anything.

## 2. Pull the data

Call these tools for the period. Skip any that return a plan or permission message, and say in the recap which section is missing and why.

1. `get_brand_summary` for the headline: recommending hosts, products in active lists, top recommenders.
2. `sales_attribution` for attributed sales, revenue and commission. Note the networks involved.
3. `host_performance` with `username: "all"` for the ranked host leaderboard.
4. `click_funnel` for the conversion rate at each step, and how it moved week to week.
5. `opportunity_pipeline` for campaigns by status, upcoming deadlines, and anything stuck.
6. `list_brand_gifts` for gifts sent, accepted, shipped and complete in the period. Do not repeat shipping addresses in the recap.

If `get_skills` returns saved brand preferences, follow their voice and goals.

## 3. Write the recap

Keep it to one page:

- **Headline.** Revenue and commission for the period, and the change against the previous period if the user asked for a comparison (pull the previous period with the same tools; do not guess it).
- **Top hosts.** The top five by revenue, each with one line on what drove it.
- **Funnel.** Conversion at each step, and the single biggest drop-off.
- **Campaigns.** What is live, what finished, what is stuck, and the next deadlines.
- **Gifting.** Counts by status.
- **What to do next.** Two or three suggestions, each tied to a number above.

Show each figure the way the tool returned it, with its currency, and state the date range once at the top. If a tool returned no data for the period, write that plainly rather than leaving the section out.
