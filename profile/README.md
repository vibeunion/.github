# VibeUnion

<p align="center">
  <strong>Infrastructure for vibecoding. / 为 vibecoding 而生的基础设施。</strong>
</p>

<p align="center">
  <a href="#english">English</a> · <a href="#中文">中文</a>
</p>

---

<a id="english"></a>

## English

**VibeUnion** builds open-source infrastructure for vibecoding — the practice of steering AI agents to ship production software by intent. Our stack covers platform-as-a-service, admin frameworks, and database tooling, all in TypeScript and designed to compose.

### Projects

| Project | What it is | Stack |
| --- | --- | --- |
| [supacloud](https://github.com/vibeunion/supacloud) | Ultra-lightweight, self-hosted Supabase PaaS. Run 100+ isolated projects on a $5 VPS with shared Postgres, Garage S3, and a Caddy gateway. Includes a Bun-native single-project Lite edition. | Bun · Elysia · Pigsty · SvelteKit |
| [svadmin](https://github.com/vibeunion/svadmin) | Headless admin framework for Svelte 5. 30+ reactive hooks, 16 field components, 16 data providers, RBAC, i18n, dark mode, Inferencer, and a CLI scaffold. Bring your own backend. | Svelte 5 · TanStack Query · shadcn-svelte |
| [postgresx](https://github.com/vibeunion/postgresx) | PostgreSQL-backed replacement toolkit for Redis + Postgres architectures. KV/TTL cache, collections, counters, advisory locks, rate limiting, pub/sub, and durable outbox — no Redis required. | Bun · PostgreSQL · `pg` |

### How they compose

- **supacloud** hosts your backend (Postgres, Auth, Storage, Edge Functions, Realtime) and can serve as the data source for a **svadmin** dashboard.
- **postgresx** removes Redis from your stack by reimplementing cache, queue, and realtime primitives on Postgres — useful inside supacloud tenants or standalone services.
- **svadmin** is backend-agnostic and ships a `@svadmin/supabase` data provider, so it connects to supacloud-hosted projects out of the box.

### Skills

We publish [Codex skills](https://developers.openai.com/codex) to help AI agents work with these projects. See [our skills guide](./SKILLS.md) for installation and usage.

---

<a id="中文"></a>

## 中文

**VibeUnion** 为 vibecoding 打造开源基础设施——用意图驱动 AI Agent 交付生产级软件。我们的技术栈覆盖 PaaS、管理后台框架和数据库工具，全部基于 TypeScript，可组合使用。

### 项目

| 项目 | 简介 | 技术栈 |
| --- | --- | --- |
| [supacloud](https://github.com/vibeunion/supacloud) | 超轻量自托管 Supabase PaaS。在 5 美元 VPS 上运行 100+ 隔离项目，共享 Postgres、Garage S3 和 Caddy 网关。内置 Bun 原生单项目 Lite 版。 | Bun · Elysia · Pigsty · SvelteKit |
| [svadmin](https://github.com/vibeunion/svadmin) | 面向 Svelte 5 的 Headless 管理后台框架。30+ 响应式 Hook、16 种字段组件、16 种数据适配器、RBAC 权限、国际化、暗色模式、推断器、CLI 脚手架。自带后端适配。 | Svelte 5 · TanStack Query · shadcn-svelte |
| [postgresx](https://github.com/vibeunion/postgresx) | 基于 PostgreSQL 的 Redis 替代工具包。KV/TTL 缓存、集合、计数器、咨询锁、限流、发布订阅、持久化发件箱——无需 Redis。 | Bun · PostgreSQL · `pg` |

### 如何组合

- **supacloud** 托管你的后端（Postgres、认证、存储、Edge Functions、实时推送），可作为 **svadmin** 仪表盘的数据源。
- **postgresx** 用 Postgres 重新实现缓存、队列和实时原语，帮你从架构中移除 Redis——可在 supacloud 租户内或独立服务中使用。
- **svadmin** 后端无关，内置 `@svadmin/supabase` 数据适配器，开箱即用连接 supacloud 托管的项目。

### Skills

我们发布了 [Codex skills](https://developers.openai.com/codex)，帮助 AI Agent 更好地使用这些项目。安装与使用请参考 [skills 指南](./SKILLS.md)。

---

<p align="center">
  <sub>Built with intent. / 以意图驱动。</sub>
</p>
