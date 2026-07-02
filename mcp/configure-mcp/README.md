# Configure MCP Services

Connect your Hermes agent to external MCP (Model Context Protocol) services — choose between native integration and mcporter, diagnose connection issues, and pick the right transport.

## What It Does

This skill walks through every step of MCP setup:

- **Choose the right path** — Hermes native MCP for lightweight tools, mcporter for heavy tool suites
- **Configure transports** — HTTP/SSE for remote services, stdio for local processes
- **Set up authentication** — API keys, bearer tokens, custom headers
- **Diagnose failures** — connection refused, timeout, tool discovery errors
- **Understand trade-offs** — token overhead vs. on-demand loading

## How to Use

Tell your agent which MCP service you want to connect (e.g., "connect me to the GitHub MCP server"). The agent will pick the right approach, write the config, and verify the connection.

## Why

MCP servers vary wildly in tool count and schema complexity. Connecting the wrong way means either blowing your context window with constant tool schemas, or having tools unavailable when needed. This skill picks the right path for each service.
