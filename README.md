# OSS PR Workflow

通用高质量开源 PR 工作流，一份面向支持 Agent Skills 的 AI 工具的中文 skill。

用于在不同开源项目中发现、验证和修复有实际价值的问题，准备 issue 和 PR，并跟进评审。目标是可信的贡献，不是 PR 数量或修改行数。

## 工作原则

- 简短核对已有记录后，以真实使用流程和代码审查中的自主发现为主要选题方式；已有同题 issue 就复用。
- 核验问题的真实性、合理预期和实际价值，不把代码异味或环境错误直接当作 bug。
- 检查 open、closed、merged PR、关联讨论及当前实现，避免重复修复。
- 缺陷修复先用回归测试证明修复前失败，再验证修复后通过，并完成项目要求的检查。
- 如实记录失败、跳过和环境限制，披露实际 AI 参与，不虚构本人审阅。
- 默认由使用者亲自创建 issue、创建 PR（包括草稿）及点击 Ready for review；skill 本身不授予 GitHub 写权限。

后端优先是可调整的偏好，不排除其他模块。目标项目的贡献指南、安全政策和 AI 政策始终需要单独核验。工作流不保证测试全绿、评审通过或最终合并。

## 平台兼容性

核心内容是 [Agent Skills 开放格式](https://agentskills.io/specification) 的 `SKILL.md` 和相对路径引用的 `references/`，工作流不依赖某一家模型或服务商。

- 支持 Agent Skills 的工具：按该工具的安装规则加载整个 skill 文件夹；安装目录和调用方式以对应工具文档为准。
- 不支持自动加载 skill 的助手：也可以将这些 Markdown 文件作为工作流参考，但这不等同于原生 skill 支持。
- `agents/openai.yaml` 只提供 Codex 专用的展示和调用元数据，不是核心流程的运行依赖；其他工具是否读取它由各自实现决定。

完整执行需要宿主工具具备相应的文件、Git、测试命令及网页/API 操作能力和授权。没有这些能力时，只能完成可支持的阶段，不能宣称已验证或已提交。本仓库尚未逐一在其他客户端实测，不承诺所有平台开箱即用。

## 安装与使用

先获取完整文件夹：

```sh
git clone https://github.com/haotianqi666/oss-pr-workflow.git
```

然后按所用工具的文档，将 `oss-pr-workflow` 文件夹安装或注册为 skill。保留 `SKILL.md`、`references/` 的目录关系。如果同名目录已存在，先检查已有内容，不要覆盖本地修改。

通用任务描述示例（具体调用语法按平台调整）：

```text
请使用 oss-pr-workflow 工作流，在 <仓库链接或本地路径> 检查真实、有实际价值且没有重复修复的问题，按项目规范完成测试并准备 issue 和 PR，最后由我自己提交。
```

<details>
<summary>Codex 安装示例</summary>

使用 Codex 时，可以直接克隆到其 skills 目录：

```sh
git clone https://github.com/haotianqi666/oss-pr-workflow.git "${CODEX_HOME:-$HOME/.codex}/skills/oss-pr-workflow"
```

调用时可使用 `$oss-pr-workflow`：

```text
使用 $oss-pr-workflow，在 <仓库链接或本地路径> 检查真实、有实际价值且没有重复修复的问题，按项目规范完成测试并准备 issue 和 PR，最后由我自己提交。
```

</details>

## 文件说明

- [SKILL.md](SKILL.md)：工作流入口、质量门槛和操作边界。
- [agents/openai.yaml](agents/openai.yaml)：可选的 Codex 专用展示名称和调用提示词。
- [references/evidence-and-handoff.md](references/evidence-and-handoff.md)：验证证据、发布交接和 CI 状态解释。
- [references/casebook.md](references/casebook.md)：截至文中记录日期的贡献复盘，不是实时 PR 状态看板，也不是可直接复用的代码方案。

## AI Assistance

这份 skill 及仓库说明由使用者提出要求，并由 Codex 辅助整理、编写和校验。这是编写过程的说明，不代表只能使用 Codex 运行。
