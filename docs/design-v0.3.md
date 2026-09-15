# v0.3：双语触发与 Agent 中立

## 目标与范围

解决 v0.2 的两个使用限制：入口只有中文，英文请求难以触发；安装与分享说明按 Codex 写，读起来像只能在 Codex 使用。

本次不改访谈方法、覆盖框架、证据状态和交付格式，v0.2 的需求卡与续访卡保持兼容。

## 具体变化

| 项 | v0.2 | v0.3 |
| --- | --- | --- |
| `SKILL.md` description | 仅中文触发语 | 中英双语，英文侧补 `interview me`、`ask me questions first`、`generate a requirements card`、`resume our last interview` 等表达，并保留双语的不触发条件 |
| `SKILL.md` 正文 | 中文 | 每节中英并列，含新增的「语言 / Language」节：跟随用户当前语言提问与交付，用户中途换语言就跟着换 |
| `references/` | 中文 | 保持中文；每个文件加一行英文用途说明，便于英文 Agent 判断何时加载 |
| 安装说明 | Codex 路径与 `$skill-installer` | 先给通用原则（整个目录放进 Agent 的 skills 位置），再按 Claude Code / Claude 桌面端、Codex、其他 Skill 目录、无 Skill 机制分列 |
| 启动示例 | `$deep-interview` | 改为不依赖某个客户端前缀的自然语言，并补英文示例 |
| `agents/openai.yaml` | 未标注归属 | 文件头注明是 Codex 专用可选元数据，其他 Agent 忽略，删除不影响使用 |
| `SKILL.md` 执行边界 | 不自带调度/发送/抓取 | 明确补一句不绑定任何特定 Agent、模型、客户端或调度平台，实施时以当前环境工具的返回结果为准 |

## 取舍

- 双语只做到 `SKILL.md`：入口决定触发与整体行为，收益最大；`references/` 按模式加载，全量翻译会显著增加体积与后续维护时的漂移风险。英文用途说明行足以让 Agent 判断是否加载。
- 保留 `agents/openai.yaml` 而不是删除：Codex 用户仍需要它，加注释说明归属比移除更少破坏。
- 不引入语言开关字段：语言由用户的实际用词决定，多一个需要配置的字段反而增加门槛。

## 未验证范围

英文访谈的多轮稳定性、各 Agent 的实际安装与加载行为、双语 description 在不同客户端下的触发准确率，均未在本次纳入验证。
