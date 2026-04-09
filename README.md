# 🛍️ Salla MCP Server

[![Deploy to Cloudflare Workers](https://img.shields.io/badge/Deploy%20to-Cloudflare%20Workers-F38020?logo=cloudflare-workers&logoColor=white)](https://workers.cloudflare.com/)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue)](https://modelcontextprotocol.io/)
[![Salla](https://img.shields.io/badge/Salla-E--commerce-00b8d4)](https://salla.sa/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Transform your Salla store management with the power of AI. This Model Context Protocol (MCP) server bridges AI assistants (like Claude and Cursor) directly to your Salla store, enabling natural language operations for products, orders, and analytics.

> [!TIP]
> **Ready to use!** This server is already deployed and usable at:  
> `https://salla-mcp-server.inlustris.workers.dev/sse`

[Live Demo](https://salla-mcp-server.inlustris.workers.dev/) • [Salla Partners](https://salla.partners/) • [MCP Documentation](https://modelcontextprotocol.io/introduction)

---

## ✨ Key Capabilities

- **🗣️ Natural Language Ops:** "Show me orders from yesterday," or "Update the price of iPhone 15 to 3000 SAR."
- **📊 Real-time Analytics:** Access abandoned carts, hourly visitors, and store performance summaries instantly.
- **📦 Inventory Management:** Create, update, and browse products and categories with ease.
- **👥 Customer Insights:** Search and retrieve detailed customer profiles and order histories.
- **⚡ Edge-Powered:** Built on Cloudflare Workers for ultra-low latency and global availability.

---

## 🛠️ Available AI Tools

| Category | Tools | Description |
|----------|-------|-------------|
| **Store** | `salla-store-info`, `salla-categories-list`, `salla-brands-list` | Manage store metadata, categories, and brands. |
| **Products** | `salla-products-list`, `salla-product-details`, `salla-product-create`, `salla-product-update` | Full CRUD and search for your product catalog. |
| **Orders** | `salla-orders-list`, `salla-order-details`, `salla-order-status-update` | Track shipments, update statuses, and filter orders. |
| **Customers**| `salla-customers-list`, `salla-customer-details` | Access customer profiles and engagement data. |
| **Analytics** | `salla-abandoned-carts`, `salla-hourly-visitors`, `salla-summary-report`, `salla-latest-orders`, `salla-general-statistics` | Deep dive into store performance and visitor metrics. |

---

## 🚀 Quick Start

### 1. Prerequisites
- [Node.js](https://nodejs.org/) & [Cloudflare Account](https://dash.cloudflare.com/sign-up)
- [Salla Partner Portal](https://salla.partners/) account with an active OAuth App.

### 2. Installation
```bash
git clone https://github.com/your-username/salla-mcp-server.git
cd salla-mcp-server
npm install
```

### 3. Configuration
Copy the example environment file:
```bash
cp .dev.vars.example .dev.vars
```

Update `.dev.vars` with your Salla credentials:
```ini
SALLA_CLIENT_ID="your_client_id"
SALLA_CLIENT_SECRET="your_client_secret"
ENCRYPTION_KEY="generate_using_openssl_rand_hex_32"
# ... other vars from .dev.vars.example
```

### 4. Development & Local Testing
```bash
npm run dev
```
Your server will run at `http://localhost:8787`. The MCP endpoint is `/sse`.

---

## 🤖 Using with AI Assistants

### Claude Desktop
Add this to your `claude_desktop_config.json`. You can use the **live hosted version** directly:

```json
{
  "mcpServers": {
    "salla": {
      "command": "npx",
      "args": ["mcp-remote", "https://salla-mcp-server.inlustris.workers.dev/sse"]
    }
  }
}
```

*Or use `http://localhost:8787/sse` if running locally.*

### Example Prompts to Try:
- 🛒 *"List all products in the 'Electronics' category that are on sale."*
- 📈 *"Give me a summary of my store's performance for this month."*
- 📦 *"What's the status of order #123456? If it's processing, mark it as shipped."*
- 👥 *"Find customers who haven't ordered anything in the last 30 days."*

---

## 🌐 Deployment

Deploy to your own Cloudflare account in seconds:

```bash
npx wrangler deploy
```

**Note:** Don't forget to add your Salla Redirect URI in the Partner Portal:
`https://your-worker.your-subdomain.workers.dev/callback/salla`

---

## 🤝 Contributing

We love contributions! Whether it's adding new Salla API endpoints or improving the AI prompts.

1. Fork the repo
2. Create your branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---

<p align="center">
  Built with ❤️ for the Salla Community
</p>
