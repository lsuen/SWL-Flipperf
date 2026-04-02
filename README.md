# SWL-Flipperf

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8.svg)](https://golang.org/)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-green.svg)](https://github.com/swl-flipperf/swl-flipperf)

> A skater's manifesto to passion and performance.
> 一名滑手对热爱与性能的宣言。

**Stay on board, stay sharp. Flip the pressure, flip the limit.**
**保持滑行，保持锋芒。翻转压力，突破界限。**

---

## What's SWL-Flipperf? / 什么是 SWL-Flipperf？

SWL-Flipperf is not just a tool — it's a **performance testing ecosystem** built around a microkernel core. Think of it like assembling your perfect setup: the deck is solid, but the trucks, wheels, and bearings make it yours.

SWL-Flipperf 不只是一个工具——是一个以微内核为核心的**性能测试生态系统**。就像组装一块滑板：主板很重要，但桥架、轮子和轴承才让它真正属于你。

---

## Projects / 项目

### Core / 核心

| Project | Description |
|---------|-------------|
| [**SWL-Flip**](https://github.com/swl-flipperf/swl-flip) | The **Deck** — Microkernel + CLI core, the foundation of everything |

> **Deck (主板)**: The core board. Everything mounts to it, everything depends on it.

### Plugins / 插件 (外挂)

| Plugin | Type | Description |
|--------|------|-------------|
| [**flip-plugin-ui**](https://github.com/swl-flipperf/flip-plugin-ui) | Web UI | **Griptape** — Interactive graphical interface |
| [**flip-plugin-tui**](https://github.com/swl-flipperf/flip-plugin-tui) | TUI | **Trucks** — Bridge between CLI and visual, Terminal UI |
| [**flip-plugin-gui**](https://github.com/swl-flipperf/flip-plugin-gui) | GUI | **Wheels** — Desktop native application |
| [**flip-plugin-report**](https://github.com/swl-flipperf/flip-plugin-report) | Reporter | **Bearings** — Report generation & export |
| [**flip-plugin-llm**](https://github.com/swl-flipperf/flip-plugin-llm) | AI | **Chip** — LLM-powered analysis & suggestions |

> **Griptape** (砂纸) · **Trucks** (桥架) · **Wheels** (轮子) · **Bearings** (轴承) · **Chip** (芯片)

Each plugin is independent, hot-swappable, and maintained in its own repository.

---

## Quick Start / 快速上手

```bash
# Install core
go install github.com/swl-flipperf/swl-flip/cmd/flip@latest

# Run a basic load test
flip run --target http://example.com --rps 1000 --duration 30s

# Enable AI-powered analysis (requires flip-plugin-llm)
flip run --target http://example.com --llm --analysis
```

---

## Architecture / 架构

```
┌─────────────────────────────────────────────────────────┐
│                      SWL-Flip (Deck)                     │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
│  │   Kernel    │  │   Engine    │  │     Plugin      │  │
│  │  (Runtime)  │  │  (Scheduler)│  │    Manager      │  │
│  └─────────────┘  └─────────────┘  └─────────────────┘  │
├─────────────────────────────────────────────────────────┤
│                      Plugins (外挂)                      │
│  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐ │
│  │  UI   │  │  TUI  │  │  GUI  │  │Report │  │  LLM  │ │
│  │(Grip) │  │(Truck)│  │(Wheel)│  │(Bearing)│ │ (Chip)│ │
│  └───────┘  └───────┘  └───────┘  └───────┘  └───────┘ │
└─────────────────────────────────────────────────────────┘
```

---

## Project Structure / 项目结构

```
swl-flip/
├── cmd/flip/                # CLI 入口
│   └── main.go
├── kernel/                  # 微内核核心
│   ├── kernel.go            # 内核启动与生命周期
│   ├── engine.go            # 多引擎抽象
│   └── plugin.go            # 插件注册与加载
├── engine/                  # 内置压测引擎
│   ├── http/
│   ├── grpc/
│   └── baseline/
├── extensions/              # 扩展插件 (内置)
│   ├── ui/
│   ├── report/
│   └── recorder/
├── interfaces/              # 插件接口定义
│   └── extension.go
├── llm/                     # LLM 能力模块
│   ├── client.go
│   ├── prompt.go
│   └── analysis.go
├── cli/                     # CLI 命令实现
│   ├── root.go
│   ├── run.go
│   ├── plan.go
│   └── report.go
├── metric/                  # 指标采集与计算
│   ├── stats.go
│   └── prom.go
├── internal/                # 内部工具
├── go.mod
├── go.sum
├── LICENSE
└── README.md
```

> **Note**: `extensions/` contains built-in plugins (ui, report, recorder). Future plugins like `web-server`, `file-upload` will also live here under subdirectories. External/third-party plugins use separate repositories under the SWL-Flipperf organization.

---

## Core Features / 核心特性

- **Microkernel Architecture** — Minimal core, maximum flexibility
- **Native CLI** — Zero-dependency terminal interface
- **Multiple Load Engines** — HTTP, gRPC, custom protocols
- **Plugin System** — Web UI / GUI / TUI are all optional plugins
- **LLM Integration** — AI-powered scenario generation & result analysis
- **Distributed Testing** — Scale from single instance to full-link pressure testing

---

## Tech Stack / 技术栈

| Layer | Technology |
|-------|------------|
| Language | Go |
| Core | CLI + Plugin System |
| Engines | fasthttp / gRPC |
| Metrics | Prometheus-compatible |
| LLM | OpenAPI-compatible |

---

## License

MIT

---

## Manifesto / 宣言

**Stay on board, stay sharp.**
**Flip the pressure, flip the limit.**
**保持滑行，保持锋芒。翻转压力，突破界限。**
