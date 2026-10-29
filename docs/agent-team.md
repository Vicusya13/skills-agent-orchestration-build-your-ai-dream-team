# Project Pulse agent team

The Project Pulse dashboard is built by a team of custom agents defined in `.github/agents` and run from GitHub Copilot CLI.

| Agent | File | Model | Responsibility |
|---|---|---|---|
| Orchestrator | `.github/agents/orchestrator.agent.md` | Claude Opus 5.5 | Coordinates the team: delegates to the Planner, Designer and Coder, tracks progress and runs final validation |
| Planner | `.github/agents/planner.agent.md` | Claude Opus 5.5 | Researches the brief and codebase and produces the implementation plan with phases, dependencies and file ownership |
| Designer | `.github/agents/designer.agent.md` | Gemini 3.7 Flash | Owns layout, information hierarchy, accessibility and visual design of the dashboard |
| Coder | `.github/agents/coder.agent.md` | GPT-5.5 | Implements the static dashboard files and the VS Code launch configuration |

## How the team works together

1. **Orchestrator** receives the Project Pulse brief and asks the **Planner** for a plan.
2. **Planner** splits the work into phases, lists dependencies and assigns file ownership.
3. **Designer** and **Coder** work in parallel on their own files where there are no dependencies.
4. **Orchestrator** validates the result against the brief and prepares the final handoff.

## Why different models

Each role uses the model that best fits the task: a strong reasoning model (Opus 5.5) for orchestration and planning, a coding-focused model (GPT-5.5) for implementation, and a fast model (Gemini 3.7 Flash) for quick design iterations.
