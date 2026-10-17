---
name: direction-check
description: Check direction before proposing another experiment, adding a prerequisite, or retrying an unsuccessful approach. Use during research, debugging, and planning, or when the user asks whether to continue. Reassess the next decision without interrupting routine execution.
license: MIT
---

# Direction Check

Keep the next action connected to the user's latest agreed goal. A working script, another experiment, or a longer plan does not by itself mean the task is closer to done.

## When to check

Make a brief check before adding an experiment, introducing a prerequisite, or repeating an unsuccessful approach. Reassess immediately when the user questions the cost or direction. Routine reads, edits, and runs within an agreed batch do not need separate checks.

Use the available conversation and task notes. Do not reconstruct missing history as fact or search unrelated conversations. A user-approved change of goal is the new reference point.

## Check the next action

Establish the current deliverable, its completion criteria, and any known budget. Separate the user's requirements from conditions you introduced. Unknown limits are not evidence that a task costs too much.

Ask what the proposed action will contribute:

- Which decision could its result change?
- What uncertainty will it reduce?
- Is it required to deliver or verify what the user requested?

If none applies, leave it out. Required validation can be worthwhile even when it is unlikely to change the plan. Past effort alone is not a reason to continue; reusable results can still have value.

Use the relevant branch below. Do not turn every checkpoint into a report.

### Work keeps expanding

Trace the proposed prerequisite back to the agreed deliverable. If the chain contains two or more requirements you introduced, inspect whether each is necessary. This is a review trigger, not proof of drift.

Distinguish a real dependency from a higher standard you invented. Permission to run one experiment does not make a positive result a permanent condition for finishing the project. Remove optional prerequisites from the completion criteria. Do not remove requirements the user explicitly chose.

### Attempts keep failing

Before a new experiment or batch, briefly state its question, what would count as informative evidence, and what the main outcomes would imply. Keep this in the existing plan or update; do not require a separate document. Reuse an agreed plan rather than restating it for every run.

Once the result is verified, follow the course of action you stated for that outcome. If you need to change it, identify the new evidence that makes the earlier judgment no longer apply before starting further work.

After an unsuccessful attempt, distinguish:

- **Execution failure:** the intended check did not run correctly.
- **Inconclusive evidence:** the check ran but cannot answer the question.
- **Negative evidence:** the check was valid and did not support the hypothesis within its tested scope.

A negative result can complete a research task. Do not treat it as an implementation bug or keep changing the success criterion to obtain a positive result. If new evidence warrants a revised criterion, explain the change before the next run.

After two unsuccessful attempts testing the same hypothesis without reducing uncertainty, compare alternatives before a third. Merely changing the model, dataset, or parameters does not make it a new path, even if the failures look different. If a new setting tests a distinct explanation, state that distinction before proceeding. Attempts that rule out explanations are progress, even if they do not yet solve the problem.

You need not know the cause before proposing a diagnostic experiment. You must explain which plausible explanations it could distinguish.

## Choose what happens next

Compare the current path with at most two materially different alternatives. Consider inspecting an assumption, narrowing scope, using an existing solution, or reporting the current result. Recommend one next action.

If the path remains justified, continue authorized work without a reflection announcement. In an advice-only conversation, give the next recommendation without starting execution.

If a change is warranted, give one short paragraph: the concrete signal, its effect on the goal, and the recommended action. Show evidence and a decision, not a numeric risk score. Ask only when a missing preference or authorization matters. Propose changes to the user's goal or completion criteria; do not silently make them.

When unattended, follow the agreed batch, budget, and stop conditions. If further work would exceed that scope or requires a user decision, preserve results and leave the decision note. Do not launch an unplanned branch. Do not interrupt a valid authorized batch merely because a checkpoint fired.

After the user chooses a direction with the tradeoff understood, proceed. Reopen the issue only when new evidence or constraints matter. Do not create another research task to justify this check.
