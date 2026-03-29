# AGENTS.md

本文件是仓库内的唯一入口。规则看这里，流程、状态和选题分别跳到对应笔记，不在多个文档里重复维护。

## 项目概述

**Ray** 是分布式 AI / Python 应用框架，当前贡献重点集中在 `python/ray/data`、`python/ray/serve`、`python/ray/llm`。

## 快速命令

```bash
bazel build //python/ray/...               # 构建
bazel test //python/ray/...                # 构建测试
pytest python/ray/llm/tests/... -v         # LLM 模块测试
uvx ruff check python/ray/llm/             # lint
pre-commit run --all-files                 # 提交前检查
```

## 核心规则

- 所有 commit 必须使用 `git commit -s`
- PR 标题格式必须是 `[Module] Short description`
- PR 必须附带测试
- 提交前必须跑 `pre-commit run --all-files`
- 使用 `git worktree` 隔离并行任务
- Python 依赖安装优先使用 `uv`

```bash
uv pip install -r python/deplocks/llm/rayllm_test_py311_cpu.lock --index-strategy unsafe-best-match
```

## 文档职责

- 流程手册：`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/CONTRIBUTING.md`
- 全局状态与下一步动作：`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/PROGRESS.md`
- 选题策略与复盘：`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/RESEARCH.md`
- 单个 Issue / PR 作战卡：`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/Issues/*.md`
- 架构补充资料：`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/ray-llm-research.md`、`/mnt/c/Users/admin/Documents/ob_notes/Ray开源贡献/dev-docs/ray-architecture.md`

## 使用约定

- 动态状态只写在 `PROGRESS.md` 和对应 `Issues/*.md`
- 选题结论、模块判断、maintainer 模式只写在 `RESEARCH.md`
- `CONTRIBUTING.md` 只讲怎么做，不重复实时进度
- 如果多个文档冲突，以 `PROGRESS.md` 的状态和对应 issue 作战卡为准
- 仓库根目录长期停在 `local/master`，用于跟踪你本地的 `AGENTS.md` 和个人工作流
- 所有 PR worktree 一律从 `upstream/master` 拉出，不从 `local/master` 拉

## 执行顺序

`RESEARCH.md` 选题 → `CONTRIBUTING.md` 执行 → `PROGRESS.md` 调度 → `Issues/*.md` 跟进 review 和 blocker
