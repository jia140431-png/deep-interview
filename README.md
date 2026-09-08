# Deep Interview

> 先别告诉我答案。先通过访谈，帮我把真正的问题看清楚。

Deep Interview 是一个适用于 ChatGPT 和 Codex 的动态深度访谈 Skill。它不会一次抛出一套固定题目，而是根据用户刚刚给出的回答，选择下一条最有信息量的问题。

它适合这些场景：

- 有一件事想不明白，希望先把问题说清楚；
- 正在做重要选择，但怀疑表面问题不是真正的问题；
- 反复遇到相似困扰，想寻找其中的模式与例外；
- 希望梳理价值、需求、冲突、代价与边界；
- 想把一段访谈整理成可修正的认知地图。

## 它如何工作

- 一次只问一个主要问题；
- 根据回答动态选择下一问，不执行固定题库；
- 在具体事件、意义、价值、冲突、模式与代价之间往返；
- 区分“已确认、暂定、未知、已否定”，避免把 AI 猜测写成结论；
- 支持阶段检查、方向纠正、当前认知地图和跨会话 Resume Card。

核心原则是：**AI 负责发现可能的结构，用户负责确认意义。**

## 安装

### 使用 Skill Installer

在 Codex 中调用 `$skill-installer`，并告诉它：

```text
从 https://github.com/jia140431-png/deep-interview 安装 deep-interview。
```

### 手动安装

```bash
git clone https://github.com/jia140431-png/deep-interview.git "$HOME/.agents/skills/deep-interview"
```

Codex 通常会自动发现新安装的 Skill；如果没有出现，请重启 Codex。

## 使用

在 Codex CLI 或 IDE 扩展中显式调用：

```text
使用 $deep-interview 对我做一次深度访谈。
```

也可以直接用自然语言开始：

```text
这件事我想不明白，先别给建议，采访我。
```

```text
我最近总想辞职，但不知道真正不满的是什么。帮我做一次深度访谈。
```

在支持 Skill 选择器的 ChatGPT 客户端中，可以通过 `@` 选择 Deep Interview。

## 访谈中的控制语句

不需要记忆严格命令，直接表达下面这些意思即可：

- 开始访谈
- 继续往下
- 这个方向不对
- 换个问题
- 生成当前地图
- 先到这里
- 结束访谈
- 继续上次访谈

结束时生成的 Interview Resume Card 可以复制到新的会话或其他支持该 Skill 的模型中继续使用。

## 文件结构

```text
deep-interview/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── artifacts.md
```

- `SKILL.md`：访谈行为、提问策略、工作地图和安全边界；
- `references/artifacts.md`：阶段检查、认知地图和 Resume Card 的输出规范；
- `agents/openai.yaml`：Skill 的名称、说明和默认启动提示。

## 边界

Deep Interview 是澄清与反思工具，不是心理诊断、治疗或人格测评。它不会替用户做决定，也不应替代医疗、法律、财务等专业意见。

## License

[MIT](LICENSE)
