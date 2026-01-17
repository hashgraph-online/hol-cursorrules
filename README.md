# HOL Cursor Rules

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | A lightweight SDK providing reference implementations for Hashgraph Consensus Standards (HCS) created by Hashgraph Online.<br><br>This SDK is built and maintained by [Hashgraph Online](https://hashgraphonline.com), a consortium of leading Hedera Organizations within the Hedera ecosystem.<br><br>[📚 Standards SDK Documentation](https://hashgraphonline.com/docs/libraries/standards-sdk/)<br>[📖 HCS Standards Documentation](https://hashgraphonline.com/docs/standards) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |


[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Cursor AI rules for [Hashgraph Online (HOL)](https://hol.org) development - building AI agents and decentralized applications on Hedera with TypeScript.

## What is HOL?

[Hashgraph Online (HOL)](https://hol.org) is an open-source SDK ecosystem for building AI agents and decentralized applications on the Hedera network. It provides:

- **Standards SDK** - TypeScript SDK implementing HCS standards and the Registry Broker client
- **Registry Broker** - Universal agent discovery and chat infrastructure
- **MCP Server** - Model Context Protocol integration for AI assistants

## Installation

Copy `.cursorrules` to your project root:

```bash
curl -O https://raw.githubusercontent.com/hashgraph-online/hol-cursorrules/main/.cursorrules
```

## What's Included

The `.cursorrules` file configures Cursor AI with:

### Technology Stack
- TypeScript strict mode with proper typing
- Node.js 20+ with pnpm
- Jest testing with @swc/jest
- Next.js 14+ for frontend (when applicable)

### HOL SDK Integration

Real, working code examples for:

- **RegistryBrokerClient initialization** with API keys
- **Agent search** with filters and pagination
- **UAID resolution** for agent discovery
- **Agent registration** with auto top-up
- **Chat conversations** with agents
- **Vector search** for semantic agent discovery
- **Stats and registry queries**

### Code Quality
- Strict TypeScript rules (no `any`)
- File naming conventions (kebab-case)
- Max 500 lines per file
- TDD workflow (red → green → refactor)

## Example: Search for Agents

```typescript
import { RegistryBrokerClient } from '@hashgraphonline/standards-sdk';

const client = new RegistryBrokerClient();

const results = await client.search({
  q: 'weather',
  registry: 'hcs-10',
  limit: 10,
});

results.hits.forEach(agent => {
  console.log(`${agent.name}: ${agent.description}`);
});
```

## Example: Chat with an Agent

```typescript
const conversation = await client.chat.start({
  uaid: 'hcs10://0.0.123456/weather-agent',
  auth: {
    accountId: process.env.HEDERA_OPERATOR_ID!,
    privateKey: process.env.HEDERA_OPERATOR_KEY!,
  },
});

const response = await conversation.sendMessage({
  content: 'What is the weather in New York?',
});
```

## Resources

- [HOL Website](https://hol.org)
- [HOL Registry](https://hol.org/registry)
- [Standards SDK Docs](https://hol.org/docs/libraries/standards-sdk/overview/)
- [Registry Broker Client](https://hol.org/docs/libraries/standards-sdk/registry-broker-client/)
- [GitHub](https://github.com/hashgraph-online)
- [NPM](https://www.npmjs.com/package/@hashgraphonline/standards-sdk)

## License

MIT License - see [LICENSE](LICENSE) for details.
