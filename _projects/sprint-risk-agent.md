---
title: Sprint Risk Agent
summary: A tool-using agent that flags GitHub issues quietly going sideways, scored against a hand-labeled set and a rule-based baseline.
learning_path: 2
tech:
  - Claude
  - Tool use
  - Python
  - GitHub API
link: https://github.com/DaleShockley/sprint-risk-agent
---

**Step 2 of my AI learning path: build an agent and measure it against a baseline.**

Every TPM spends hours a week scanning a backlog for issues that are silently rotting. This agent does the first pass. It calls tools to pull each issue's labels, assignee, dates and comment thread, decides what to look at next, and writes the status digest a human would send, with every verdict validated against a typed schema.

I scored it against 8 hand-labeled issues, including two traps: an issue still labeled "blocked" that the comments show was resolved, and an assignee who said they'd be out for three weeks. A rule-based baseline that never reads comments gets both wrong.

| Approach | Accuracy |
|---|---|
| Rule-based baseline | 6/8 |
| Claude agent, 3 runs | 6/8, 7/8, 6/8 |

The headline number barely moved, but the mistakes did. The agent caught the resolved-"blocked" trap every run. It missed the out-of-office assignee every run, and that was the prompt's fault, not the model's: it defined "unowned" as "no assignee", and the agent followed that exactly.

Running it for real also found two bugs the mocked tests couldn't: the agent was never told today's date, so "14 days idle" was a guess, and Claude often wrapped its JSON in extra text. Both are fixed and covered by tests.
