# OSS PR Workflow

通用高质量开源 PR 工作流，一份中文 Codex skill。OSS 是 Open Source Software（开源软件）的缩写。

用于在不同开源项目中发现、验证和修复有实际价值的问题，准备 issue 和 PR，并跟进评审。目标是可信的贡献，不是 PR 数量或修改行数。

## 工作原则

- 简短核对已有记录后，以真实使用流程和代码审查中的自主发现为主要选题方式；已有同题 issue 就复用。
- 核验问题的真实性、合理预期和实际价值，不把代码异味或环境错误直接当作 bug。
- 检查 open、closed、merged PR、关联讨论及当前实现，避免重复修复。
- 缺陷修复先用回归测试证明修复前失败，再验证修复后通过，并完成项目要求的检查。
- 如实记录失败、跳过和环境限制，披露实际 AI 参与，不虚构本人审阅。
- 默认由使用者亲自创建 issue、创建 PR（包括草稿）及点击 Ready for review；skill 本身不授予 GitHub 写权限。

后端优先是可调整的偏好，不排除其他模块。目标项目的贡献指南、安全政策和 AI 政策始终需要单独核验。工作流不保证测试全绿、评审通过或最终合并。

## 安装与使用

将本仓库作为一个完整的 skill 文件夹放入 Codex 的 skills 目录。默认位置下可运行：

```sh
git clone https://github.com/haotianqi666/oss-pr-workflow.git "${CODEX_HOME:-$HOME/.codex}/skills/oss-pr-workflow"
```

如果同名目录已存在，先检查已有内容，不要覆盖本地修改。

调用示例：

```text
使用 $oss-pr-workflow，在 <仓库链接或本地路径> 检查真实、有实际价值且没有重复修复的问题，按项目规范完成测试并准备 issue 和 PR，最后由我自己提交。
```

## 文件说明

- [SKILL.md](SKILL.md)：工作流入口、质量门槛和操作边界。
- [agents/openai.yaml](agents/openai.yaml)：Codex 展示名称和调用提示词。
- [references/evidence-and-handoff.md](references/evidence-and-handoff.md)：验证证据、发布交接和 CI 状态解释。
- [references/casebook.md](references/casebook.md)：截至文中记录日期的贡献复盘，不是实时 PR 状态看板，也不是可直接复用的代码方案。

## AI Assistance

这份 skill 及仓库说明由使用者提出要求，并由 Codex 辅助整理、编写和校验。
