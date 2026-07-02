Connect your Hermes agent to external MCP services — choose between native integration and mcporter, diagnose connection issues, and pick the right transport.

## What It Does

- **Choose the right path** — Hermes native MCP for lightweight tools, mcporter for heavy tool suites
- **Configure transports** — HTTP/SSE for remote services, stdio for local processes
- **Set up authentication** — API keys, bearer tokens, custom headers
- **Diagnose failures** — connection refused, timeout, tool discovery errors
- **Understand trade-offs** — token overhead vs. on-demand loading

## How to Use

Tell your agent which MCP service you want to connect (e.g., "connect me to the GitHub MCP server"). The agent picks the right approach, writes the config, and verifies the connection.

## When Not to Use

If you only need a single simple tool, use a direct API call instead of the full MCP stack.
