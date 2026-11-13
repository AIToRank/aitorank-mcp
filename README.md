<p align="center"><img src="assets/logo.png" width="96" alt="AIToRank logo"></p>

# AIToRank: your AI writes, your blog publishes

**AIToRank** is a remote MCP server that lets your AI assistant write and publish on your company blog. The blog lives on your own domain (`blog.yoursite.com`), styled automatically from your website. Claude, ChatGPT, Cursor or any MCP client reads your brand profile and writing guide, writes the article, and publishes it now, schedules it or saves it as a draft. Every article gets an AI cover image.

- 🌐 Website: https://aitorank.com
- 🔌 MCP server URL: `https://aitorank.com/mcp`
- 🔐 Auth: OAuth 2.1 (sign in with Google or GitHub, no API key to copy)
- 📇 Official MCP Registry name: `com.aitorank/aitorank`
- 📖 Connector page: https://aitorank.com/ai-blog-connector

<p align="center"><img src="assets/og.png" alt="AIToRank: an SEO blog on your own domain, written by AI" width="800"></p>

> This repository is the public presentation of AIToRank (docs, setup). The service itself is hosted at aitorank.com.

---

## Why

AI assistants write good articles, but getting them online is the slow part: copy, paste into a CMS, find an image, format, schedule. With AIToRank, one prompt does it:

> "Read my blog's writing guide, pick a topic we haven't covered yet, write it and schedule it for my next free day."

…and the article is live on `blog.yoursite.com`, with its cover, its SEO metadata and links to your other articles.

## Connect your AI

The server uses **streamable HTTP** at `https://aitorank.com/mcp`. On first use you'll be redirected to aitorank.com to sign in and approve access.

### Claude (claude.ai, desktop, mobile)
Add a **custom connector** in Claude's connector settings and paste:
```
https://aitorank.com/mcp
```

### Claude Code
```bash
claude mcp add --transport http aitorank https://aitorank.com/mcp
```

### Cursor
[![Add AIToRank to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=aitorank&config=eyJ1cmwiOiJodHRwczovL2FpdG9yYW5rLmNvbS9tY3AifQ==)

Or by hand, in `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):
```json
{
  "mcpServers": {
    "aitorank": {
      "url": "https://aitorank.com/mcp"
    }
  }
}
```

### ChatGPT
Enable **developer mode** in ChatGPT, then add a custom connector with the URL `https://aitorank.com/mcp`. (Availability depends on your ChatGPT plan.)

### Other MCP clients
Any client that supports remote MCP servers with OAuth works: point it at `https://aitorank.com/mcp`.

## Tools

| Tool | What it does |
|---|---|
| `get_writing_guide` | Start here: your blog (address, plan), business profile (what you sell, readers, tone, topics to avoid), the rules for an article and the existing articles with their internal links |
| `list_articles` / `get_article` | Browse articles and read one in full (Markdown, FAQ), with status, URL and cover |
| `get_planning` | Scheduled and recent articles, the next free publication slot, how many articles your AI can still publish |
| `create_article` | Saves a new article and publishes it now, schedules it or keeps it as a draft. Checked first (length, sections); a cover is generated automatically |
| `update_article` | Changes the title, body, description, target search or FAQ; published articles keep their URL |
| `schedule_article` | Publish now, schedule, unpublish or archive. Nothing is ever deleted |
| `set_cover` | Use your own image as the cover, or generate a new 16:9 AI cover |
| `list_pending` | Topics and articles AIToRank prepared that wait for your decision *(Pro)* |
| `review_topic` | Approve or reject a proposed topic *(Pro)* |

## Example prompts

- "Look at my blog and suggest 5 topics we haven't covered yet."
- "Write an article on how to choose an accountant as a freelancer, following my writing guide, and schedule it for my next free day."
- "Turn these meeting notes into a blog article and keep it as a draft."
- "Update last week's article with the new pricing and keep the same URL."
- "Generate a new cover for my latest article."
- "What's waiting for my review this week?"

## Plans

| | Bring your own AI | Pro |
|---|---|---|
| Blog on `blog.yoursite.com` with HTTPS | ✅ | ✅ |
| Styled from your website automatically | ✅ | ✅ |
| AI cover for every article (or your own) | ✅ | ✅ |
| MCP connector for your AI | ✅ | ✅ |
| Sitemap, RSS, schema.org, Markdown export | ✅ | ✅ |
| 2 researched SEO articles a week written for you | — | ✅ |
| Topic ideas, review or autopilot | — | ✅ |
| 18 AI revisions a month | — | ✅ |
| Price | $7/month or $70/year | $19/month or $190/year |

Try it free first: paste your website on https://aitorank.com to preview your blog with 3 article ideas, one written in full. You can connect your AI during the preview; publishing needs a plan.

## Limits & safety

- Your AI can publish one article per publishing day you chose in Settings; drafts don't count. 3 generated covers a day.
- Each article is checked before it's saved (300 to 4,000 words, at least two `##` sections, no scripts).
- Nothing is ever deleted through the connector: articles can only be archived (restorable from the dashboard).
- OAuth 2.1 with PKCE, short-lived access tokens, disconnect your AI anytime from Settings.
- Hosted in Europe. Contact: contact@aitorank.com · Abuse: abuse@aitorank.com

---

Made in France by Anthony Perinot · https://aitorank.com
