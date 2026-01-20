# HOL Cursor Rules

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | **Cursor AI rules for the Universal Agentic Registry.** Build AI agents that discover and connect with 59,000+ agents across NANDA, MCP, A2A, Virtuals, and more.<br><br>[📚 SDK Documentation](https://hol.org/docs/libraries/standards-sdk/)<br>[📖 API Documentation](https://hol.org/docs/registry-broker/) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

[![npm version](https://img.shields.io/npm/v/@hashgraphonline/standards-sdk?style=for-the-badge&logo=npm&logoColor=white&label=standards-sdk)](https://www.npmjs.com/package/@hashgraphonline/standards-sdk)
[![Run in Postman](https://img.shields.io/badge/Run_in-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99%26entityType%3Dcollection%26workspaceId%3Dfb06c3a9-4aab-4418-8435-cf73197beb57)
[![OpenAPI Spec](https://img.shields.io/badge/OpenAPI-3.1.0-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)](https://hol.org/registry/api/v1/openapi.json)

[![Open in CodeSandbox](https://img.shields.io/badge/Open_in-CodeSandbox-blue?style=for-the-badge&logo=codesandbox&logoColor=white)](https://codesandbox.io/s/github/hashgraph-online/hol-cursorrules)
[![Open in StackBlitz](https://img.shields.io/badge/Open_in-StackBlitz-1269D3?style=for-the-badge&logo=stackblitz&logoColor=white)](https://stackblitz.com/github/hashgraph-online/hol-cursorrules)
[![Open in Gitpod](https://img.shields.io/badge/Open_in-Gitpod-FFAE33?style=for-the-badge&logo=gitpod&logoColor=white)](https://gitpod.io/#https://github.com/hashgraph-online/hol-cursorrules)

## What is the Universal Registry?

The [Universal Agentic Registry](https://hol.org/docs/registry-broker/) is the connectivity layer for the autonomous web. One standards-compliant API to access agents from:

| Protocol | Description |
|----------|-------------|
| **Virtuals** | Tokenized AI agents |
| **A2A** | Google's Agent-to-Agent protocol |
| **MCP** | Anthropic's Model Context Protocol |
| **ERC-8004** | On-chain agent verification |
| **x402 Bazaar** | Agent payment rails |
| **OpenConvAI** | Conversational AI standard |
| **XMTP** | Decentralized messaging |
| **ANS** | Agent Name Service |

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

## API & Documentation

| Resource | Link |
|----------|------|
| **Live Registry** | [hol.org/registry](https://hol.org/registry) |
| **API Documentation** | [hol.org/docs/registry-broker](https://hol.org/docs/registry-broker/) |
| **SDK Reference** | [hol.org/docs/libraries/standards-sdk](https://hol.org/docs/libraries/standards-sdk/) |
| **Postman Collection** | [Run in Postman](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99) |
| **OpenAPI Spec** | [openapi.json](https://hol.org/registry/api/v1/openapi.json) |
| **npm Package** | [@hashgraphonline/standards-sdk](https://www.npmjs.com/package/@hashgraphonline/standards-sdk) |

## Related Repositories

- [`standards-sdk`](https://github.com/hashgraph-online/standards-sdk) - The core SDK powering the registry client
- [`hol-claude-skills`](https://github.com/hashgraph-online/hol-claude-skills) - Claude Code slash commands for HOL
- [`hol-claude-md`](https://github.com/hashgraph-online/hol-claude-md) - CLAUDE.md templates for HOL projects

## 🏆 Score HOL Points

Contribute to this repository and score [HOL Points](https://hol.org/points)! 

- 🔧 **Fix bugs** or improve documentation
- ✨ **Add new features** or examples
- 📝 **Submit pull requests** to score points

Points can be used across the HOL ecosystem. [Learn more →](https://hol.org/points)

## License

MIT License - see [LICENSE](LICENSE) for details.
