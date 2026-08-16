# VibeUnion Skills Guide / Skills 使用指南

[English](#english) | [中文](#中文)

---

<a id="english"></a>

## English

VibeUnion publishes [Codex skills](https://developers.openai.com/codex) that teach AI coding agents how to work with our projects effectively. Skills are reusable instruction sets that an agent loads on demand, so it follows project conventions instead of guessing.

### Available skills

| Skill | Project | What it does |
| --- | --- | --- |
| `supacloud-platform` | supacloud | Deploy, configure, and operate SupaCloud-hosted projects: project lifecycle, multi-tenant setup, Caddy gateway, Edge Functions, storage, and the Lite runtime. |
| `svadmin-admin-ui` | svadmin | Build admin/backoffice CRUD interfaces with svadmin: DataProvider/AuthProvider/LiveProvider wiring, resource definitions, RBAC, audit logging, and data provider adapters. |
| `postgres-database` | postgresx | Work with PostgreSQL-backed persistence, including the pgredis replacement toolkit, LISTEN/NOTIFY, advisory locks, and durable outbox patterns. |
| `supacloud-platform` | supauth | Configure enterprise IAM on SupaCloud: hosted login UI, organization/RBAC governance, audit logging, Supabase Auth compatibility, and admin console built on svadmin. |

### Install

Skills are installed into your Codex skills directory (`$CODEX_HOME/skills`). You can install them individually or from the repo.

```bash
# Install all VibeUnion skills
codex skill install --from github:vibeunion/.github

# Or install a single skill
codex skill install supacloud-platform
codex skill install svadmin-admin-ui
codex skill install postgres-database
```

After installation, restart Codex and the skills will be available automatically when relevant context is detected.

### Use

Skills activate contextually. When you ask Codex to deploy a SupaCloud project, build a svadmin dashboard, or replace Redis with pgredis, the matching skill loads its instructions and the agent follows project conventions.

You can also invoke a skill explicitly:

```
Use the supacloud-platform skill to deploy a new project with Caddy and Edge Functions.
```

### Project composition

Skills are designed to compose across projects:

1. **Host** your backend on **supacloud** (Postgres + Auth + Storage + Edge Functions).
2. **Add enterprise IAM** with **supauth** for hosted login UI, org/RBAC, and audit on top of Supabase Auth.
3. **Replace Redis** with **postgresx** if you need cache, queue, or realtime primitives without a separate Redis instance.
4. **Build** an admin dashboard with **svadmin**, using the `@svadmin/supabase` data provider to connect to your supacloud project.
5. **Ship a WeChat mini-program** with **supabase-mp-js** to connect the same Supabase backend into WeChat's runtime.

The skills carry these composition patterns, so an agent can wire the full stack without manual hand-holding.

---

<a id="中文"></a>

## 中文

VibeUnion 发布了 [Codex skills](https://developers.openai.com/codex)，教会 AI 编程 Agent 如何高效使用我们的项目。Skill 是可复用的指令集，Agent 按需加载，遵循项目约定而非靠猜。

### 可用 skills

| Skill | 项目 | 作用 |
| --- | --- | --- |
| `supacloud-platform` | supacloud | 部署、配置和运维 SupaCloud 托管项目：项目生命周期、多租户配置、Caddy 网关、Edge Functions、存储和 Lite 运行时。 |
| `svadmin-admin-ui` | svadmin | 用 svadmin 构建管理后台 CRUD 界面：DataProvider/AuthProvider/LiveProvider 接线、资源定义、RBAC 权限、审计日志和数据适配器。 |
| `postgres-database` | postgresx | 使用 PostgreSQL 持久化，包括 pgredis 替代工具包、LISTEN/NOTIFY、咨询锁和持久化发件箱模式。 |
| `supacloud-platform` | supauth | 在 SupaCloud 上配置企业 IAM：托管登录 UI、组织/RBAC 治理、审计日志、Supabase Auth 兼容性和基于 svadmin 的管理控制台。 |

### 安装

Skill 安装到你的 Codex skills 目录（`$CODEX_HOME/skills`），可单独安装或从仓库安装。

```bash
# 安装全部 VibeUnion skills
codex skill install --from github:vibeunion/.github

# 或安装单个 skill
codex skill install supacloud-platform
codex skill install svadmin-admin-ui
codex skill install postgres-database
```

安装后重启 Codex，skill 会在检测到相关上下文时自动加载。

### 使用

Skill 按上下文自动激活。当你让 Codex 部署 SupaCloud 项目、构建 svadmin 仪表盘、或用 pgredis 替代 Redis 时，对应的 skill 会加载指令，Agent 遵循项目约定。

你也可以显式调用：

```
使用 supacloud-platform skill 部署一个带 Caddy 和 Edge Functions 的新项目。
```

### 项目组合

Skill 设计为跨项目可组合：

1. 在 **supacloud** 上**托管**后端（Postgres + 认证 + 存储 + Edge Functions）。
2. 用 **supauth** **叠加企业 IAM**，在 Supabase Auth 之上提供托管登录 UI、组织/RBAC 和审计。
3. 如果需要缓存、队列或实时原语但不想单独部署 Redis，用 **postgresx** **替代 Redis**。
4. 用 **svadmin** **构建**管理仪表盘，通过 `@svadmin/supabase` 数据适配器连接你的 supacloud 项目。
5. 用 **supabase-mp-js** **发布微信小程序**，将同一个 Supabase 后端接入微信运行时。

Skill 内置了这些组合模式，Agent 可以无需手动引导就完成全栈接线。
