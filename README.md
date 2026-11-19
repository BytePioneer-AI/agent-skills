# agent-skills

面向日常工程开发与多 Agent 协作的实用 Skill 集合，兼容 [`skills`](https://github.com/vercel-labs/skills)（`npx skills add`）以及 `~/.agents/skills`、`~/.codex/skills`、`~/.claude/skills` 目录约定。

> 本仓库只维护自研或深度泛化改写的通用 Skill；常用第三方 Skill 保留在下方「外部精选推荐」中直接指向原仓库，不拷贝上游代码。

## 快速安装

### 方式一：使用 `skills` CLI（推荐）

```bash
# 安装全部
npx skills add BytePioneer-AI/agent-skills

# 或按需安装单个 Skill
npx skills add BytePioneer-AI/agent-skills --skill trim-cot-leakage
npx skills add BytePioneer-AI/agent-skills --skill find-simplifications
npx skills add BytePioneer-AI/agent-skills --skill lead-delegation
```

### 方式二：手动克隆并链接到全局目录

```bash
git clone https://github.com/BytePioneer-AI/agent-skills.git
ln -s "$(pwd)/agent-skills/skills/trim-cot-leakage" ~/.agents/skills/trim-cot-leakage
ln -s "$(pwd)/agent-skills/skills/find-simplifications" ~/.agents/skills/find-simplifications
ln -s "$(pwd)/agent-skills/skills/lead-delegation" ~/.agents/skills/lead-delegation
```

如需在原生 Codex 或 Claude Code 中共享，可继续软链至 `~/.codex/skills/` 或 `~/.claude/skills/`。

---

## 本仓收录的 Skills

| Skill | 适用阶段 | 解决什么问题 | 入口 |
| --- | --- | --- | --- |
| **`trim-cot-leakage`** | 审查与清理、文档维护 | 审计并清理 AI 写完代码/PR 后残留在注释、JSDoc 和功能文档中的“推理过程泄漏”（如“本 PR 新增”“以前/不再”“失效草稿编号”“向评审者辩解”），保留真实不变量与实测边界。 | [SKILL.md](skills/trim-cot-leakage/SKILL.md) |
| **`find-simplifications`** | 审查与清理、架构减法 | 默认只读的过度设计审计：通过区分生产语料与测试/文档语料取证，找出无生产调用方的导出接口、镜像表示、空扩展点与可替换轮子，并强制写出“最强反对理由”与兼容风险。 | [SKILL.md](skills/find-simplifications/SKILL.md) |
| **`lead-delegation`** | 多 Agent 协作委派 | 以主导者身份拆解并委派开发/调研任务给其他 Agent（含任务文件模板与审查清单）：自己把模糊问题核实成事实、写清晰约束、严格审查与集成，让用户只做关键取舍。 | [SKILL.md](skills/lead-delegation/SKILL.md) · [任务模板](skills/lead-delegation/references/task-template.md) · [审查清单](skills/lead-delegation/references/review-checklist.md) |

---

## 外部精选 Skill 推荐

以下是日常高频搭配使用的优秀开源 Skill（直接指向官方上游仓库，随时安装/更新到最新版，不拷贝上游代码）：

### 工程研发

| 来源仓库 | 常用 Skill | 典型用途 | 获取最新版 |
| --- | --- | --- | --- |
| [mattpocock/skills](https://github.com/mattpocock/skills) | `grill-me`、`tdd`、`diagnosing-bugs`、`codebase-design`、`writing-for-agents`、`code-review`、`handoff`、`research` | 需求追问与方案打磨、TDD、复杂排障、深模块设计、撰写 Agent 规范 | `npx skills@latest add mattpocock/skills` |

### 前端与交互设计

| 来源仓库 | 常用 Skill | 典型用途 | 获取最新版 |
| --- | --- | --- | --- |
| [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | `impeccable` | 旗舰级前端设计/改版/评审工作流（`Persuade` / `Operate` / `Read` / `Experience` 四模式、`craft-floor` 反 AI 模板底线、20+ 细分设计命令） | `npx impeccable install` |
| [emilkowalski/skills](https://github.com/emilkowalski/skills) | `mobile-native`、`apple-design` | `mobile-native` 修复移动端 Web/PWA 平台层真机手感坑（`100dvh`、hover 卡死、iOS 输入框缩放、安全区等）；`apple-design` 翻译 Apple WWDC 弹簧物理与流体手势交互规范 | `npx skills@latest add emilkowalski/skills --skill mobile-native --skill apple-design` |
| [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/frontend-design/skills/frontend-design) | `frontend-design` | 轻量级视觉美学与排版指导，适合快速消除页面模板味 | 查看上游 [SKILL.md](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md) |
| [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | `vercel-react-best-practices`、`web-design-guidelines` | React / Next.js 性能优化与 Web UI 界面规范/可访问性审查 | `npx skills@latest add vercel-labs/agent-skills` |

---

## License

[MIT](LICENSE)
