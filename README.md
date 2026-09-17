# Marketing Plan Generator

An agent-guided framework for building a paid-advertising and organic-social marketing plan for a new niche. It contains methods and templates only; generated plans, PRDs, research inputs, and local agent settings stay out of Git.

## Start

```sh
git clone https://github.com/<owner>/marketing-plan-generator-public.git
cd marketing-plan-generator-public
```

Open this folder in Claude Code or another coding agent and paste:

> Read `CLAUDE.md` and `GENERATOR.md`, ask me for my niche PRD, and walk me through the full generator including the intake, avatar confirmation, paid plan, organic plan, QA, and handoff. Executive briefs are optional.

The agent should ask for the PRD if it is missing, batch the questions in `INTAKE-QUESTIONNAIRE.md`, research the market on the web, and stop for avatar confirmation before drafting downstream documents. If its environment has no `AskUserQuestion` tool, it should ask the same questions in normal conversation.

Generated results belong at `niches/<niche-slug>/marketing-plan/`, which is ignored. The PRD and private materials belong under `inputs/`, which is also ignored. The source project is read-only: do not write into it.

## What an agent needs

- Web research access for reviews, communities, competitor ads, and current platform guidance.
- Local read access to the PRD and any user-provided materials.
- Optional PDF rendering tools if executive briefs are requested.

This framework guides planning; it does not deploy ads or replace required human decisions, research, or domain/compliance review.
