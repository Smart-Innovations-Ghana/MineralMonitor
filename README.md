# MineralMonitor

**Real-time intelligence dashboard** — AI-powered GIS aggregation, geopolitical monitoring, and mineral tracking in a unified situational awareness interface.

[![GitHub stars](https://img.shields.io/github/stars/Smart-Innovations-Ghana/MineralMonitor?style=social)](https://github.com/Smart-Innovations-Ghana/MineralMonitor/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Smart-Innovations-Ghana/MineralMonitor?style=social)](https://github.com/Smart-Innovations-Ghana/MineralMonitor/network/members)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Last commit](https://img.shields.io/github/last-commit/Smart-Innovations-Ghana/MineralMonitor)](https://github.com/Smart-Innovations-Ghana/MineralMonitor/commits/main)

---

## What It Does

- **Real-time data aggregation** across 30+ external data sources
- **Dual map engine** — 3D globe (globe.gl) and WebGL flat map (deck.gl) with multiple data layers
- **Cross-stream correlation** — monitoring for signals across multiple intelligence categories
- **AI-powered synthesis** — aggregated intelligence briefs and analysis
- **Finance & commodity tracking** — market monitoring and indicators
- **Local AI support** — run with Ollama, no API keys required
- **Multi-variant support** — 5 site variants from a single codebase
- **Native desktop app** (Tauri 2) for macOS, Windows, and Linux
- **Multi-language support** with RTL support

---

## Quick Start

```bash
git clone https://github.com/Smart-Innovations-Ghana/MineralMonitor.git
cd MineralMonitor
npm install
npm run dev
```

Open [localhost:5173](http://localhost:5173). No environment variables required for basic operation.

For variant-specific development:

```bash
npm run dev:tech       # Tech variant
npm run dev:finance    # Finance variant
npm run dev:commodity  # Commodity variant
npm run dev:happy      # Happy variant
```

---

## Development

```bash
npm run typecheck        # Type checking
npm run typecheck:api    # API layer type checking
npm run test:data        # Run unit/integration tests
npm run test:sidecar     # Run sidecar tests
npm run test:e2e         # Run Playwright E2E tests
npm run build:full       # Production build
make generate            # Regenerate proto stubs and API specs
```

---

## Tech Stack

| Category | Technologies |
|----------|-------------|
| **Frontend** | TypeScript, Vite, Preact, globe.gl + Three.js, deck.gl + MapLibre GL |
| **Desktop** | Tauri 2 (Rust) with Node.js sidecar |
| **AI/ML** | Ollama / Groq / OpenRouter, Transformers.js (browser-side) |
| **API Contracts** | Protocol Buffers, sebuf HTTP annotations |
| **Deployment** | Vercel Edge Functions, Railway relay, Tauri, PWA |
| **Caching** | Redis (Upstash), 3-tier cache, CDN, service worker |

---

## Project Structure

```
.
├── src/                    # Browser SPA (TypeScript, class-based components)
│   ├── app/                # App orchestration
│   ├── components/         # 86 UI panels + map components
│   ├── config/             # Variant configs and definitions
│   ├── services/           # Business logic (120+ service files)
│   ├── types/              # TypeScript type definitions
│   ├── utils/              # Shared utilities
│   ├── workers/            # Web Workers
│   ├── generated/          # Proto-generated stubs (DO NOT EDIT)
│   ├── locales/            # i18n translation files
│   └── App.ts              # Main application entry
├── api/                    # Vercel Edge Functions
│   ├── _*.js               # Shared helpers
│   ├── health.js           # Health check
│   └── <domain>/           # Domain-specific endpoints
├── server/                 # Server-side shared code
│   ├── _shared/            # Redis, rate-limiting, LLM helpers
│   ├── gateway.ts          # Domain gateway factory
│   └── worldmonitor/       # Domain handlers
├── proto/                  # Protobuf definitions
├── shared/                 # Cross-platform configs
├── scripts/                # Build and seed scripts
├── src-tauri/              # Tauri desktop shell
├── tests/                  # Unit/integration tests
├── e2e/                    # Playwright E2E specs
└── docs/                   # Documentation
```

---

## Architecture

### Dependency Direction

```
types → config → services → components → app → App.ts
```

- `types/` has zero internal imports
- `config/` imports only from `types/`
- `services/` imports from `types/` and `config/`
- `components/` imports from all above
- `app/` orchestrates components and services

### API Layer Constraints

- Edge Functions are self-contained JavaScript only
- No imports from `src/` or cross-runtime dependencies
- Only same-directory helpers and npm packages
- Enforced by build-time checks

---

## Contributing

Contributions welcome! Please follow the guidelines in [CONTRIBUTING.md](./CONTRIBUTING.md).

---

## License

**AGPL-3.0** for non-commercial use. **Commercial license** required for commercial use.

| Use Case | Allowed? |
|----------|----------|
| Personal / research / educational | Yes |
| Self-hosted (non-commercial) | Yes, with attribution |
| Fork and modify (non-commercial) | Yes, share source under AGPL-3.0 |
| Commercial use / SaaS / rebranding | Requires commercial license |

See [LICENSE](LICENSE) for full terms.

---

## Support & Community

- **Documentation**: Check the [docs/](./docs/) folder
- **Issues**: Report bugs via [GitHub Issues](https://github.com/Smart-Innovations-Ghana/MineralMonitor/issues)
- **Contributing**: See [CONTRIBUTING.md](./CONTRIBUTING.md)

---

<p align="center">
  Built with TypeScript • Vite • Preact • Tauri
</p>
