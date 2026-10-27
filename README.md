# foto foto MCP server

<img src="logo.png" alt="foto foto" width="96" align="right">

Turn your photos or a public iCloud Shared Album into a printed hardcover photo book.

Attach photos to the chat, give direct image links, or paste the link to a public iCloud Shared Album, and ask for a photo book. foto foto designs every spread and returns a preview link. The person saves the book with their email on [fotofoto.app](https://fotofoto.app), where they can swap photos, change the cover and the title, and order the printed book. A book starts at 24 pages, so bring at least 24 photos.

foto foto works in English and Dutch.

- **Endpoint:** `https://fotofoto.app/mcp` (Streamable HTTP)
- **Auth:** none. Book creation is free and needs no account or API key. Each book returns a private `bookToken` that only opens that book.
- **Docs:** [fotofoto.app/developers](https://fotofoto.app/developers) · [connectors.md](https://fotofoto.app/connectors.md) · [server card](https://fotofoto.app/.well-known/mcp/server-card.json)

## Tools

| Tool | What it does |
| --- | --- |
| `get_catalog` | Lists book types, shipping countries and photo requirements. |
| `compare_photo_book_prices` | Prices one book at foto foto and at other photo book services. |
| `start_photo_book` | Shows a card where the person picks photos, in apps that render MCP Apps cards. |
| `create_book` | Designs a draft book from photos, image links or a public iCloud Shared Album. Nothing is ordered. |
| `get_book` | Shows a book and its price for one copy including shipping. |
| `create_checkout` | Prepares a Stripe checkout link. No charge until the person pays at Stripe. |
| `create_payment_quote` | Prepares a fixed quote for agent payments (MPP, and x402 where listed). |
| `pay_book` | Buys the quoted book with MPP, only after the buyer approves the total and address. |

## Add it to your client

**Claude** (claude.ai, Claude Desktop): Settings → Connectors → Add custom connector → `https://fotofoto.app/mcp`.

**Claude Code**

```bash
claude mcp add --transport http fotofoto https://fotofoto.app/mcp
```

**Cursor** (`~/.cursor/mcp.json`), **Windsurf**, **Cline** and other clients that take a URL:

```json
{
  "mcpServers": {
    "fotofoto": { "url": "https://fotofoto.app/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "fotofoto": { "type": "http", "url": "https://fotofoto.app/mcp" }
  }
}
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/nternet-company/fotofoto-mcp
```

Clients that only speak stdio:

```json
{
  "mcpServers": {
    "fotofoto": { "command": "npx", "args": ["-y", "mcp-remote", "https://fotofoto.app/mcp"] }
  }
}
```

## Try it

- "Make a photo book from the photos I attach."
- "Turn my iCloud Shared Album into a printed photo book: https://www.icloud.com/sharedalbum/#..."
- "What does a 40-page layflat photo book cost, and who else sells one?"

## Privacy and support

[Privacy policy](https://fotofoto.app/privacy) · [Terms](https://fotofoto.app/terms) · [Support](https://fotofoto.app/help/support) · fotofoto@nternet.company

This repository holds the listing files for the hosted server. The server itself runs at fotofoto.app.
