# Thoughtfully Designed Agent Skills & Workflows

Reusable skills, prompts, and workflow blueprints for your AI agent. Opinionated about useful behavior, configurable to your preferences, and designed to adapt to your agent or harness rather than fighting it. Small ones live here; larger projects have their own repositories. 

The goal is to do each job well with sound, proportionate design: use existing capabilities, avoid reinventing the wheel, and add only the structure the task needs.

I continually refine them as AI capabilities evolve, aiming for no more and no less than agents can reliably handle. That includes simplifying or removing structure when it stops being useful. When a skill becomes redundant, I'll mark it as superseded and explain what I replaced it with in my own workflows.


## In this repo

### [agent-pager](agent-pager/)

**Your agent “calls” you when something is urgent.**

Maturity: **Testing** · Lifecycle: **Active**

Guides you through setting up ntfy so your agent can get your attention on your phone, including persistent ringing on Android, only for situations you choose. Adapts to your existing notification channels and agent setup.

## Larger projects

### [agent-research-digest](https://github.com/arjver/agent-research-digest)

**Your agent keeps you up to date on what you care about, without fluff or repeated info.**

Maturity: **Refined** · Lifecycle: **Active**

A blueprint for recurring, sourced research digests around your interests. Covers topic discovery, source watchlists, duplicate-story handling, meaningful follow-ups, scheduling, and delivery using your agent's available capabilities.

### [auto-architect-skills](https://github.com/arjver/auto-architect-skills)

**Your agent plans software work (collaboratively) and coordinates implementation + verification (autonomously).**

Maturity: **Varies by skill — refactor: Refined** · Lifecycle: **Active**

Skills for building and maintaining software projects using an architect/executor workflow, including collaborative planning, delegated implementation with subagents, verification, and handoffs:
- `auto-architect-refactor`: large refactors and migrations (includes autonomous and HITL versions)
- `auto-architect-initialize`: coming soon -- starting and defining architecture for a new project
- `auto-architect-greenfield`: coming soon -- building and verifying new features

## Status labels

**Maturity:** New — recently introduced; Testing — being tested and refined; Refined — improved through repeated use, and I think it's solid.

**Lifecycle:** Active — I use it regularly; Maintenance only — limited updates; Superseded — replaced, with explanation of what I use instead or what built-in agent capability became common that makes it redundant.

Labels reflect my experience, not a guarantee across every agent or setup.

## Getting started

Open a project's README for its quick-start prompt, setup instructions, and requirements. For agents: read the linked skill or blueprint in full before using it; follow its setup flow and verify what your environment supports. These are instructions, not a hosted service or agent runtime.

## License

[MIT](LICENSE). Separately linked projects have their own licenses and terms.

## Disclaimer

**Use at your own risk.** These prompts, skills, examples, and instructions are provided **“AS IS” and “AS AVAILABLE,” without warranties of any kind**. You are responsible for reviewing them, protecting credentials and data, testing behavior, and deciding whether they are suitable for your use. AI agents can make mistakes, and third-party software and services can change or fail. Accuracy, reliability, security, compatibility, and continued availability are not guaranteed.

To the maximum extent permitted by applicable law, the authors and contributors disclaim liability for claims, damages, losses, or other liability arising from use of, or inability to use, this project.
