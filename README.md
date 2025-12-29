<div align="center">

<!-- Animated Typing Banner -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=2E9EF7&center=true&vCenter=true&multiline=true&repeat=true&width=600&height=100&lines=Sql+Assistant;7+Agents+%7C+7+Skills;Claude+Code+Plugin" alt="Sql Assistant" />

<br/>

<!-- Badge Row 1: Status Badges -->
[![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)](https://github.com/pluginagentmarketplace/custom-plugin-sql/releases)
[![License](https://img.shields.io/badge/License-Custom-yellow?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production-brightgreen?style=for-the-badge)](#)
[![SASMP](https://img.shields.io/badge/SASMP-v1.3.0-blueviolet?style=for-the-badge)](#)

<!-- Badge Row 2: Content Badges -->
[![Agents](https://img.shields.io/badge/Agents-7-orange?style=flat-square&logo=robot)](#-agents)
[![Skills](https://img.shields.io/badge/Skills-7-purple?style=flat-square&logo=lightning)](#-skills)
[![Commands](https://img.shields.io/badge/Commands-4-green?style=flat-square&logo=terminal)](#-commands)

<br/>

<!-- Quick CTA Row -->
[📦 **Install Now**](#-quick-start) · [🤖 **Explore Agents**](#-agents) · [📖 **Documentation**](#-documentation) · [⭐ **Star this repo**](https://github.com/pluginagentmarketplace/custom-plugin-sql)

---

### What is this?

> **Sql Assistant** is a Claude Code plugin with **7 agents** and **7 skills** for sql development.

</div>

---

## 📑 Table of Contents

<details>
<summary>Click to expand</summary>

- [Quick Start](#-quick-start)
- [Features](#-features)
- [Agents](#-agents)
- [Skills](#-skills)
- [Commands](#-commands)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

</details>

---

## 🚀 Quick Start

### Prerequisites

- Claude Code CLI v2.0.27+
- Active Claude subscription

### Installation (Choose One)

<details open>
<summary><strong>Option 1: From Marketplace (Recommended)</strong></summary>

```bash
# Step 1️⃣ Add the marketplace
/plugin add marketplace pluginagentmarketplace/custom-plugin-sql

# Step 2️⃣ Install the plugin
/plugin install custom-plugin-sql@pluginagentmarketplace-sql

# Step 3️⃣ Restart Claude Code
# Close and reopen your terminal/IDE
```

</details>

<details>
<summary><strong>Option 2: Local Installation</strong></summary>

```bash
# Clone the repository
git clone https://github.com/pluginagentmarketplace/custom-plugin-sql.git
cd custom-plugin-sql

# Load locally
/plugin load .

# Restart Claude Code
```

</details>

### ✅ Verify Installation

After restart, you should see these agents:

```
custom-plugin-sql:05-data-analyst
custom-plugin-sql:01-sql-fundamentals
custom-plugin-sql:03-mongodb
custom-plugin-sql:02-postgresql-dba
custom-plugin-sql:04-redis
... and 2 more
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **7 Agents** | Specialized AI agents for sql tasks |
| 🛠️ **7 Skills** | Reusable capabilities with Golden Format |
| ⌨️ **4 Commands** | Quick slash commands |
| 🔄 **SASMP v1.3.0** | Full protocol compliance |

---

## 🤖 Agents

### 7 Specialized Agents

| # | Agent | Purpose |
|---|-------|---------|
| 1 | **05-data-analyst** | Learn SQL for data analysis with comprehensive coverage of e |
| 2 | **01-sql-fundamentals** | Master SQL fundamentals including DDL, DML, joins, subquerie |
| 3 | **03-mongodb** | Master MongoDB and document-oriented database design with co |
| 4 | **02-postgresql-dba** | Become a PostgreSQL Database Administrator mastering install |
| 5 | **04-redis** | Master Redis for high-performance caching, real-time applica |
| 6 | **06-data-engineer** | Master data engineering with comprehensive coverage of datab |
| 7 | **07-bi-analyst** | Learn Business Intelligence with comprehensive coverage of S |

---

## 🛠️ Skills

### Available Skills

| Skill | Description | Invoke |
|-------|-------------|--------|
| `sql-fundamentals` | Master SQL fundamentals including SELECT, INSERT, UPDATE, DE | `Skill("custom-plugin-sql:sql-fundamentals")` |
| `redis` | Redis data structures and commands including strings, lists, | `Skill("custom-plugin-sql:redis")` |
| `data-analyst` | SQL for data analysis with exploratory analysis, advanced ag | `Skill("custom-plugin-sql:data-analyst")` |
| `bi-analyst` | BI fundamentals with metric definition, KPI calculation, dim | `Skill("custom-plugin-sql:bi-analyst")` |
| `postgresql-dba` | PostgreSQL administration and setup including installation,  | `Skill("custom-plugin-sql:postgresql-dba")` |
| `data-engineer` | Data warehouse design mastery with star schema, dimensional  | `Skill("custom-plugin-sql:data-engineer")` |
| `mongodb` | MongoDB fundamentals including document model, CRUD operatio | `Skill("custom-plugin-sql:mongodb")` |

---

## ⌨️ Commands

| Command | Description |
|---------|-------------|
| `/learn` | Learn SQL & Database Mastery |
| `/assess` | Knowledge Assessment |
| `/browse-agent` | Browse Database Agents |
| `/projects` | Hands-On Projects |

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |
| [LICENSE](LICENSE) | License information |

---

## 📁 Project Structure

<details>
<summary>Click to expand</summary>

```
custom-plugin-sql/
├── 📁 .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── 📁 agents/              # 7 agents
├── 📁 skills/              # 7 skills (Golden Format)
├── 📁 commands/            # 4 commands
├── 📁 hooks/
├── 📄 README.md
├── 📄 CHANGELOG.md
└── 📄 LICENSE
```

</details>

---

## 📅 Metadata

| Field | Value |
|-------|-------|
| **Version** | 1.0.0 |
| **Last Updated** | 2025-12-29 |
| **Status** | Production Ready |
| **SASMP** | v1.3.0 |
| **Agents** | 7 |
| **Skills** | 7 |
| **Commands** | 4 |

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md).

1. Fork the repository
2. Create your feature branch
3. Follow the Golden Format for new skills
4. Submit a pull request

---

## ⚠️ Security

> **Important:** This repository contains third-party code and dependencies.
>
> - ✅ Always review code before using in production
> - ✅ Check dependencies for known vulnerabilities
> - ✅ Follow security best practices
> - ✅ Report security issues privately via [Issues](../../issues)

---

## 📝 License

Copyright © 2025 **Dr. Umit Kacar** & **Muhsin Elcicek**

Custom License - See [LICENSE](LICENSE) for details.

---

## 👥 Contributors

<table>
<tr>
<td align="center">
<strong>Dr. Umit Kacar</strong><br/>
Senior AI Researcher & Engineer
</td>
<td align="center">
<strong>Muhsin Elcicek</strong><br/>
Senior Software Architect
</td>
</tr>
</table>

---

<div align="center">

**Made with ❤️ for the Claude Code Community**

[![GitHub](https://img.shields.io/badge/GitHub-pluginagentmarketplace-black?style=for-the-badge&logo=github)](https://github.com/pluginagentmarketplace)

</div>
