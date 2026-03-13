# use-ui-libraries

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that makes Claude use existing UI component libraries, design systems, and registries instead of writing components from scratch.

## What it does

This skill auto-triggers when Claude Code detects you're building UI — creating components, designing pages, adding frontend features, or working on any web application interface. It ensures Claude always reaches for pre-built, battle-tested components before writing custom ones.

### Decision flow

1. **Check the project's existing library** — already using Chakra, MUI, Mantine, etc.? Use that
2. **Check component registries** — need animations or specialized components? Check compatible registries
3. **Check AI-specific components** — building AI features? Use AI SDK Elements or CopilotKit
4. **Check enterprise design systems** — building for Microsoft, Shopify, etc.? Use their system
5. **Only build custom** if nothing covers the need

## What it covers

### Component libraries

| Library | Docs |
|---------|------|
| **shadcn/ui** (default for new projects) | https://ui.shadcn.com |
| **Chakra UI** | https://chakra-ui.com |
| **Mantine** | https://mantine.dev |
| **Material UI / MUI** | https://mui.com |
| **Ant Design** | https://ant.design |
| **NextUI** | https://nextui.org |
| **Headless UI** | https://headlessui.com |
| **Radix UI** | https://radix-ui.com |
| **Tremor** | https://tremor.so |
| **Park UI** | https://park-ui.com |

### Component registries (shadcn-compatible)

| Registry | Focus |
|----------|-------|
| [**Magic UI**](https://magicui.design) | Animated components, landing pages |
| [**Aceternity UI**](https://ui.aceternity.com) | Beautiful animations and effects |
| [**Origin UI**](https://originui.com) | Polished copy-paste components |
| [**21st.dev**](https://21st.dev) | Community registry, MCP integration |
| [**Cult UI**](https://cultui.com) | Community-driven registry |
| [**Kokonut UI**](https://kokonut.dev) | Animated, accessible components |
| [**ui.jln.dev**](https://ui.jln.dev) | Community extensions |

### AI-specific

| Tool | What it does |
|------|-------------|
| [**AI SDK Elements**](https://elements.ai-sdk.dev) | Chat, code, voice, and workflow components built on shadcn/ui |
| [**Vercel AI SDK**](https://sdk.vercel.ai) | Core AI chat hooks, streaming, model integration |
| [**CopilotKit**](https://copilotkit.ai) | Framework for AI copilots in apps |

### Enterprise design systems

| Platform | Design System |
|----------|--------------|
| Microsoft | [Fluent UI](https://fluent2.microsoft.design) |
| Google | [Material UI](https://mui.com) |
| IBM | [Carbon](https://carbondesignsystem.com) |
| Shopify | [Polaris](https://polaris.shopify.com) |
| GitHub | [Primer](https://primer.style) |
| Salesforce | [Lightning](https://lightningdesignsystem.com) |
| Vercel | [Geist](https://vercel.com/geist) |

## Installation

### Personal skill (applies to all your projects)

```bash
git clone https://github.com/cruzedevelopment/use-ui-libraries.git ~/.claude/skills/use-ui-libraries
```

### Project skill (shared with your team)

```bash
# From your project root
mkdir -p .claude/skills/use-ui-libraries
curl -sL https://raw.githubusercontent.com/cruzedevelopment/use-ui-libraries/main/SKILL.md \
  -o .claude/skills/use-ui-libraries/SKILL.md
```

Then commit `.claude/skills/use-ui-libraries/SKILL.md` to your repo.

## Rules enforced

1. **Never** write custom components when a library already has them
2. **Respect** the project's existing library — don't mix or force migrations
3. **Always** check libraries and registries before building custom
4. **Compose** existing components to build complex UIs
5. For new projects, default to shadcn/ui
6. For animations, check registries before building custom
7. For AI features, check AI SDK Elements and CopilotKit before building custom

## License

MIT
