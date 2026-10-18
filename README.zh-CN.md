# Direction Check

![Codex](https://img.shields.io/badge/Codex-Skill-blue)
![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-orange)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)
![Research Workflow](https://img.shields.io/badge/Research-Workflow-purple)

<p align="center">
  <a href="README.md">English</a> · <strong>中文</strong>
</p>

你有没有过这样的经历：和 LLM 讨论一个idea时，聊着聊着，最后窄到几乎变成了一个“人造问题”？

或者在验证idea时，照着它的建议，一个实验接一个实验地做，换模型、换数据集、换参数，直到结果都不 work，你只好放弃？

或许在某时，真正有用的问题已经从“下一步该试什么？”变成了“这些结果在告诉我们什么？”。一个负结果可能在反驳某个前提假设，可能指向另一个研究方向，亦可能已经给了你足够的证据，可以停下来了。但对话还是一直朝着下一个实验走。

Direction Check 是一个小 skill，让 agent 在追加工作之前重新检查方向：下一步是否服务于你的目标，最近的尝试有没有带来新信息，任务是否已经超出了约定的范围。

当围绕同一个假设的两次尝试都没有成功，也没有带来新信息时，它要求 agent 横向考虑其他路径：检查前提是否成立、回到数据和错误样本寻找线索，或接受当前结果并收尾。仅仅换一个模型、数据集或参数，不算换了思路。若新证据指向另一条研究路线，agent 应把它提出来，而不是继续沿原路追加实验。

有理由继续时，agent 就继续工作。证据表明需要改变时，它会解释原因，并推荐一个具体的下一步。

## 它要求 agent 做什么

- 在增加实验、前置条件或重试之前检查。常规执行照常进行。
- 把新增的要求追溯到约定的交付物，包括这些要求是谁提出的。
- 区分执行失败、证据不足和负面证据。
- 针对同一个假设的两次尝试都失败、也没有带来新信息时，重新考虑方法。
- 有理由继续时就继续。提议改变时说明理由，但不让用户读一篇反思长文。

“两次尝试”规则是一个实用的默认值，不是经过验证的阈值。没有数值风险评分。

## 使用方法

同一套文件可以用在 Codex 和 Claude Code 里，不需要分开的版本，只是安装路径和调用方式不同。

### Codex

把这个文件夹复制到你项目的 `.agents/skills/` 目录：

```text
your-project/
└── .agents/
    └── skills/
        └── direction-check/
            ├── SKILL.md
            ├── README.md
            ├── README.zh-CN.md
            └── LICENSE
```

然后显式调用：

```text
Use $direction-check before we decide what to try next.
```

（在我们决定下一步尝试什么之前，使用 $direction-check。）

Codex 也可以根据 skill 的描述自动选用。安装和发现机制的细节，见[官方 skill 文档](https://learn.chatgpt.com/docs/build-skills)。

### Claude Code

把这个文件夹复制到项目里的 `.claude/skills/direction-check/`，让指令文件位于 `.claude/skills/direction-check/SKILL.md`。然后调用：

```text
/direction-check
```

详见 [Claude Code skill 文档](https://code.claude.com/docs/en/skills)。

### 让触发更容易发生

如果 agent 从不加载这个 skill，它就什么也检查不了。对于持续进行的工作，你可以把下面这条简短规则加到项目的 `AGENTS.md`（Codex）或 `CLAUDE.md`（Claude Code）里：

```text
Before adding a new experiment, prerequisite, or retry, use the installed
direction-check skill to check its connection to the latest agreed goal.
If the skill is unavailable, check that connection directly. Continue justified,
authorized work without asking again. Raise scope changes before expanding work.
```

（在增加新的实验、前置条件或重试之前，用已安装的 direction-check skill 检查它和最新约定目标之间的联系。如果这个 skill 不可用，就直接检查这种联系。合理且已授权的工作直接继续，不用再问。要扩大工作范围，先提出来。）

这仍然只是一条 prompt 指令。这个包不包含 hook，也不会强制执行花费上限。


## 来源与许可

这个工作流借鉴了两个 MIT 许可的 skill：

- [Reflect](https://github.com/alirezarezvani/claude-skills/blob/main/productivity/reflect/skills/reflect/SKILL.md)，作者 Alireza Rezvani，用于在对话中重新评估方向。
- [Systematic Debugging](https://github.com/obra/superpowers/blob/main/skills/systematic-debugging/SKILL.md)，来自 Jesse Vincent 的 Superpowers，用于在反复修复失败后质疑当前的方法。

以 [MIT 许可证](LICENSE)发布。上游的版权声明保留在 LICENSE 里。
