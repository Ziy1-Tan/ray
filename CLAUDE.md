# CLAUDE.md

本文件为 Claude Code 提供项目指导。详细内容见文档索引。

## 项目概述

**Ray** 是分布式 AI/Python 应用框架：Ray Core + AI 库 + LLM 批处理

## 快速命令

```bash
bazel build //python/ray/...          # 构建
bazel test //python/ray/...           # 测试
pytest python/ray/llm/tests/... -v    # LLM 模块
uvx ruff check python/ray/llm/       # lint
```

## 核心规则（强制）

- **Sign-off**: 所有 commit 必须 `git commit -s`
- **PR 格式**: `[Module] Short description`
- **测试**: PR 必须包含测试，无测试不合并
- **Pre-commit**: 提交前必须 `pre-commit run --all-files`
- **Issue 评分**: Bugfix(+3) > Enhancement > Feature | 小规模(+2) | 独立模块(+2) | Good First Issue(+2)
- **Worktree 隔离**: 使用 `git worktree` 隔离多任务开发
- **Worktree 基准**: 所有 worktree 必须基于 `~/github/ray`（SSH 协议），而非 `~/.config/superpowers/worktrees/` 中的 fork/master
  - `~/.config/superpowers/worktrees/ray-project/` 下所有 worktree 必须来自 `~/github/ray` master 分支
  - 每次 `git worktree add` 前确认基准：`cd ~/github/ray && git worktree add ... master`

## 架构概览

- `python/ray/` - 核心 + AI 库
- `python/ray/llm/` - LLM 批处理（vLLM/SGLang）
- `src/ray/` - C++ 核心

## 文档索引

| 文档 | 内容 |
|------|------|
| `Ray开源贡献/CONTRIBUTING.md` | 完整贡献流程 |
| `Ray开源贡献/RESEARCH.md` | Issue分析、推荐列表 |
| `Ray开源贡献/dev-docs/ray-architecture.md` | 详细架构 |

## 开源贡献

详见 `Ray开源贡献/CONTRIBUTING.md`

核心流程：Pick Issue → Plan → Worktree → TDD → Review → Squash -s → PR
