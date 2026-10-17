# Direction Check

<p align="center">
  <strong>English</strong> · <a href="README.zh-CN.md">中文</a>
</p>

Have you ever started discussing a research idea with an LLM and ended up working on a question so narrow you barely remembered why it mattered?

Or followed its advice through one experiment after another, changing models, datasets, and parameters, until nothing worked and you gave up?

At some point, the useful question may have changed from “What should we try next?” to “What are these results telling us?” A negative result might challenge an assumption, suggest a different research direction, or give you enough evidence to stop. But the conversation keeps moving toward another experiment.

Direction Check is a small skill that asks the agent to reconsider the path before adding more work. It checks whether the next step serves your goal, whether recent attempts taught you anything, and whether the requirements have grown beyond what you asked for.

When there is a reason to continue, the agent keeps working. When the evidence calls for a change, it explains why and recommends a concrete next step.

## What it asks the agent to do

- Check before adding experiments, prerequisites, or retries. Routine execution stays routine.
- Trace added requirements back to the agreed deliverable, including who introduced them.
- Separate execution failures, inconclusive evidence, and negative evidence.
- Reconsider the approach after two unsuccessful attempts testing the same hypothesis with no new information.
- Keep working when there is a reason to continue. Explain a proposed change without making the user read a reflection essay.

The two-attempt rule is a practical default, not a validated threshold. There is no numeric risk score.

## Use it

The same files can be used in Codex and Claude Code. No separate edition is needed; the installation path and invocation differ.

### Codex

Copy this folder into your project's `.agents/skills/` directory:

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

Then invoke it explicitly:

```text
Use $direction-check before we decide what to try next.
```

Codex can also select skills from their descriptions. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills) for installation and discovery details.

### Claude Code

Copy this folder to `.claude/skills/direction-check/` in your project, so the instructions are at `.claude/skills/direction-check/SKILL.md`. Then invoke:

```text
/direction-check
```

See the [Claude Code skill documentation](https://code.claude.com/docs/en/skills) for details.

### Make the trigger easier to notice

A skill cannot check anything if the agent never loads it. For ongoing work, you can add this short rule to your project's `AGENTS.md` for Codex or `CLAUDE.md` for Claude Code:

```text
Before adding a new experiment, prerequisite, or retry, use the installed
direction-check skill to check its connection to the latest agreed goal.
If the skill is unavailable, check that connection directly. Continue justified,
authorized work without asking again. Raise scope changes before expanding work.
```

This remains a prompt instruction. The package does not include a hook or enforce a spending limit.

## Examples

The first scenario is adapted from a real conversation that prompted this project, before the skill existed. Its example response has been rewritten. The other scenarios are illustrative. None is a measured result of using the skill.

**A small release becomes a research project.** The user wants to publish a skill. The assistant proposes experiments, finds the results hard to score, then proposes collecting a more difficult dataset.

> Publishing the skill does not require a claim that it improves performance. A new dataset would help answer that separate research question. I recommend releasing the documented draft and describing the limits of the evidence we have.

**Two runs produce no useful comparison.** Both runs finish, but the metric cannot distinguish the outputs. The next suggestion is to change the model again.

> The last two runs did not tell us whether the method helps. Changing models would leave the measurement problem unresolved. I recommend checking a few raw outputs against the metric before launching another batch.

**Debugging is making progress.** One check rules out the input parser. Another narrows the failure to cache invalidation. The agent continues with the targeted cache check. Two attempts have produced new information, so the skill should not interrupt them merely because the bug remains.

## Status

This is an initial release. It has not been evaluated against a short prompt or in a controlled study. The examples describe intended behavior. Automatic triggering, interpretation of prior decisions, and adherence depend on the agent and its available context. The skill cannot enforce a budget or override the host's instructions.

## Sources and license

The workflow draws on two MIT-licensed skills:

- [Reflect](https://github.com/alirezarezvani/claude-skills/blob/main/productivity/reflect/skills/reflect/SKILL.md), by Alireza Rezvani, for reassessing direction during a conversation.
- [Systematic Debugging](https://github.com/obra/superpowers/blob/main/skills/systematic-debugging/SKILL.md), from Jesse Vincent's Superpowers, for questioning an approach after repeated unsuccessful fixes.

Direction Check brings these ideas into experiment planning and scope decisions. Its specific rules cover assistant-added prerequisites, negative research results, and the boundary between an authorized batch and unplanned follow-up work. Reassessment itself is not a new idea.

Released under the [MIT License](LICENSE). Upstream copyright notices are retained there.
