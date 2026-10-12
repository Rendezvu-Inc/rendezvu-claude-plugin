# Rendezvu for Claude

Rendezvu is the platform outdoor and endurance brands use to work with the athletes ("hosts") who recommend their gear. This plugin connects Claude to your brand's live Rendezvu data so you can ask about it in plain language: which hosts drove sales, how your conversion funnel is moving, where each campaign stands, and which gifts have shipped.

It is for **Rendezvu brand admins**. You sign in with the Rendezvu account you already have. Host and shopper accounts cannot connect.

## What this plugin contains

- **One remote MCP server**, declared in `.mcp.json`: `https://api.rendezvu.co/mcp`, operated by Rendezvu, Inc. over Streamable HTTP. It is the only network destination this plugin uses.
- **One skill**, `brand-performance-recap`, which tells Claude how to use the server's tools to build a performance recap. It is plain Markdown.

The plugin runs no local commands, scripts, hooks or packages, and it reads no files or environment variables on your machine.

## What it connects to and sends

- **Sign-in.** The first time Claude uses the server, it opens a Rendezvu sign-in page in your browser (OAuth 2.1 with PKCE). You sign in with your Rendezvu email and password, or with Google. Rendezvu then issues Claude an access token that lasts one hour and a refresh token that lasts 30 days. Rendezvu stores only hashes of them.
- **Requests.** When Claude calls a tool, it sends the tool name and its arguments (for example a date range, a host's username, or a campaign name) to `https://api.rendezvu.co/mcp`. Nothing else from your conversation is sent.
- **Results.** The server returns data for the brands your account administers, which Claude then uses in its reply.
- **What Rendezvu records.** For each request: the time, your account, the brands in scope, the client name, the tool name, whether it succeeded and how long it took. Not the arguments, the results or your conversation.

## Tools

Every tool is read only. Data is limited to the brands you administer, checked again on every request.

| Tool | What it returns |
|---|---|
| `get_brand_summary` | An overview of your brand: recommending hosts, products in active lists, top recommenders, recent activity and endorsement notes |
| `sales_attribution` | Attributed sales and commission by host, network, status and date range |
| `host_performance` | One host's views, clicks, sales, revenue and commission, or a ranked leaderboard of all hosts |
| `click_funnel` | The weekly funnel from profile view to sale, with the conversion rate at each step |
| `opportunity_pipeline` | Your campaigns by status, with host counts, payment states and deadlines |
| `get_opportunity` | One campaign in full: brief, deliverables, hosts and their codes, payment terms and invite states |
| `list_brand_gifts` | Your product gifts and their status, including the recipient name and shipping address a host submitted (never phone or email). Needs a plan with gifting |
| `gear_recommendation` | Your products best suited to a request, with the recommending host's notes |
| `find_brand_recommenders` | Hosts who carry a brand's products in their public gear lists. Needs a plan with Discover |
| `get_host_gear` | One host's public gear lists and endorsements. Needs a plan with Discover |
| `gear_list_insights` | Adoption roll-ups across public gear lists. Needs a plan with Discover |
| `get_skills` | Your brand's saved preferences, so you don't have to re-explain your brand |
| `rendezvu_docs` | Search of the public Rendezvu documentation |
| `rendezvu_brand_assets` | Official Rendezvu logo files and usage rules |

The server never returns passwords, payment card details, host email addresses or phone numbers, or another brand's sales, clicks, campaigns or gifts.

## Install and connect

1. Install the plugin from the Claude plugin directory, or straight from this repository in Claude Code:

   ```
   /plugin install rendezvu --marketplace Rendezvu-Inc/rendezvu-claude-plugin
   ```

2. Ask Claude something only your Rendezvu data can answer, such as "What does my Rendezvu brand summary look like?"
3. Sign in on the Rendezvu page that opens.

To disconnect, remove the plugin or the Rendezvu connector in Claude's settings. Removing someone's brand admin access in Rendezvu stops their access on the next request.

## Links

- Documentation: https://www.rendezvu.co/docs/brands/integrations/mcp
- Privacy policy: https://www.rendezvu.co/privacy-policy#ai-connectors
- Terms: https://www.rendezvu.co/terms-and-conditions#ai-connectors
- Support: support@rendezvu.co
