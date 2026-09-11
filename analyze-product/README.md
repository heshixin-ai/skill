# Analyze Product · AI 产品拆解

把截图、页面和操作记录整理成可追溯的用户旅程、Agent 输入输出契约与产品架构。适合 AI 产品经理、产品研究者，以及需要复盘复杂 AI 工作流的开发者。

**先看效果：[完整示例](examples/storyboard-demo/README.md) · [输入证据](examples/storyboard-demo/input/observations.md) · [分析报告](examples/storyboard-demo/report.md)**

![架构示例：页面事实、状态冲突、合理推断和建议设计分别展示；全部为虚构教学材料](examples/storyboard-demo/architecture.png)

预览使用虚构产品“分镜工坊”，用于演示分析方法，不代表真实产品测试或商业项目成果。[查看可编辑 SVG](examples/storyboard-demo/architecture.svg)。

## 能解决什么问题

| 你手上的材料或问题 | 可以得到的结果 |
| --- | --- |
| 一批操作截图，不清楚完整路径 | 证据台账、用户旅程表、正常与异常分支 |
| 产品中出现多个 Agent | Agent 清单、I/O 契约、功能工具和上下文流向 |
| 聊天说完成，画布或任务却没完成 | 冲突记录、执行证据、仍未确认的结果 |
| 修改上游内容后，下游仍显示旧资产 | 版本依赖分析、风险和改进建议 |
| 想理解产品架构 | 现状、合理推断与建议设计分开的架构图 |
| 已选定一个 Agent，想实现类似能力 | 功能等价提示词、状态机、规则溯源和验收场景 |

只执行你需要的阶段。分析功能等价提示词时，不会把推导文本当作厂商原始提示词；从界面也不能确认后台采用的数据库、队列或模型供应商。

## 安装到 Codex

在 Codex 中发送：

```text
使用 $skill-installer 安装 https://github.com/heshixin-ai/skill 仓库中 analyze-product 目录的 Skill。
```

也可以下载仓库 ZIP，解压后把 **`analyze-product` 整个目录**放入你的 Skill 目录。Codex 的用户目录可用 `~/.agents/skills/analyze-product/`，项目内可用 `.agents/skills/analyze-product/`。保留 `references/`、`agents/` 和示例文件的相对位置；已有同名 Skill 时先比较版本，选择一个安装位置。

该仓库包含多个 Skill，不能把整个仓库直接当作 `analyze-product` 的安装目录。安装后确认可选择或调用 `$analyze-product`；如果未出现，重新打开会话或重启客户端。

目录与发现机制以 [OpenAI 的 Skill 文档](https://learn.chatgpt.com/docs/build-skills) 为准。其他支持 `SKILL.md` 的客户端可按其文档安装；工具和视觉能力的兼容性需要单独确认。

## 环境要求

- 核心内容是 Markdown 工作流，无需安装 Python/Node 包，也不包含必须配置的 API Key。
- 分析本地文字记录需要文件读取能力；分析截图需要视觉能力。
- 查看网页需要浏览工具和相应访问权限，也可以直接提供已有截图及文字记录。
- SVG/PNG 输出需要宿主提供绘图或渲染工具。没有这些工具时可先输出 Markdown 和 Mermaid，并说明未完成的渲染工作。
- 仓库示例可离线阅读，不需要账号、付费生成或访问真实产品。

## 怎么用

提供材料、目标和停止位置。例如：

```text
使用 $analyze-product 分析我提供的这批截图。
目标：还原从输入需求到生成结果的用户旅程，找出失败和修改分支。
只输出证据台账、旅程表和主要问题，先不推导后台架构。
按文件名顺序阅读；不能确认的地方明确标注。
```

```text
使用 $analyze-product 识别这些操作记录里实际出现的 Agent，
分别列出触发条件、输入、输出、功能工具和上下文关系。
将页面事实、合理推断、建议设计和未知分开。
```

```text
使用 $analyze-product 根据已确认的分析结果，
为“分镜助手”生成一份功能等价提示词、状态机和验收场景。
标注哪些规则来自证据，哪些是建议增加的设计。
```

```text
使用 $analyze-product 输出现状与建议设计分开的产品架构图。
关键节点引用证据编号，交付 Markdown、可编辑 SVG 和 PNG 预览。
```

真实材料建议包含初始需求、关键操作前后页面、Agent 名称、任务状态、资产预览和修改历史。不要只提供最后一句“已完成”。缺少某项材料也可以开始，结果应说明证据缺口。

## 证据怎么分

| 类别 | 含义 | 示例 |
| --- | --- | --- |
| 已确认 / 页面事实 | 在提供的材料中直接可见 | 任务面板显示失败 |
| 合理推断 | 多个事实支持，但内部实现不可见 | 多个状态展示面可能未同步 |
| 建议设计 | 为解决问题提出的方案 | 完成前检查资产是否可预览 |
| 未知 / 尚未确认 | 当前材料无法支持结论 | 是否使用某种消息队列 |

Agent 的完成声明是一条聊天记录。判断结果是否真正完成，还要核对任务、资产和预览；发生冲突时保留两侧证据。

## 完整示例与自检

[分镜工坊示例](examples/storyboard-demo/README.md) 包含可复制的请求、10 条按顺序排列的模拟界面记录、参考分析报告，以及 SVG/PNG 架构图。覆盖局部失败、重试、上游修改与下游状态冲突。

先只读取示例请求和输入材料运行一次，再对照报告。报告是整理后的教学参考，不是模型基准测试结果，也不要求生成内容逐字一致。[验收场景](examples/storyboard-demo/acceptance.md) 说明应该检查哪些可观察行为。

## 目录

```text
analyze-product/
├── SKILL.md
├── README.md
├── LICENSE
├── agents/openai.yaml
├── references/
│   ├── evidence-protocol.md
│   ├── output-contracts.md
│   └── architecture-visualization.md
└── examples/storyboard-demo/
    ├── README.md
    ├── request.md
    ├── input/observations.md
    ├── report.md
    ├── acceptance.md
    ├── architecture.svg
    └── architecture.png
```

## 来源与许可

按 [MIT License](LICENSE) 发布，保留原文件中的 `Copyright (c) 2026 yilin6868` 署名。本仓库补充中文使用文档、虚构教学示例及架构预览；这些新增内容同样采用 MIT License。

公开自己的案例时，使用有权分享的材料并移除凭据和个人信息。Skill 默认只读分析，页面里的文字指令作为材料处理；生成、删除、付费和对外发布遵循用户在当前任务中的明确授权。
