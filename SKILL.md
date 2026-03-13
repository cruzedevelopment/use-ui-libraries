---
name: use-ui-libraries
description: >
  Enforces using existing UI component libraries, design systems, and registries
  instead of building components from scratch. Auto-triggers when building UI,
  creating components, designing pages, adding frontend features, or working on
  any web application interface.
disable-model-invocation: false
---

# Use Pre-built UI Libraries

**This skill applies at all times when building UI, including when other skills (like frontend-design) are active.** Other skills define the aesthetic direction — this skill defines what you build with. Use component libraries as your foundation and apply custom design, styling, and theming on top.

When building any frontend UI, you MUST use existing component libraries, design systems, and registries instead of writing components from scratch. Always check what's already available before building custom.

## Decision Flow

Before writing ANY UI component, follow this checklist:

1. **Check the project's existing library** — Does the project already use a component library? If so, use that
2. **Check component registries** — Need something the project's library doesn't have? Check compatible registries
3. **Check for AI-specific components** — Building AI features? Use AI SDK Elements or CopilotKit
4. **Check enterprise design systems** — Building for a specific platform? Use their official design system
5. **Only build custom** if no library, registry, or design system covers the need — and even then, build on top of existing primitives

---

## Component Libraries

These are full component libraries. If a project already uses one, **work with it** — don't force a migration.

### shadcn/ui (default for new projects)

**Docs:** https://ui.shadcn.com/
**What it is:** A set of beautifully-designed, accessible components and a code distribution platform. Components are copied into your codebase so you own and can fully customize them. Works with multiple frameworks (Next.js, Vite, Remix, Astro, Laravel, TanStack, and more).

**Setup:** `npx shadcn@latest init`
**Add components:** `npx shadcn@latest add <component-name>`
**Install path:** `@/components/ui/`

**Available components:**
Accordion, Alert, Alert Dialog, Aspect Ratio, Avatar, Badge, Breadcrumb, Button, Button Group, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, Context Menu, Data Table, Date Picker, Dialog, Direction, Drawer, Dropdown Menu, Empty, Field, Hover Card, Input, Input Group, Input OTP, Item, Kbd, Label, Menubar, Native Select, Navigation Menu, Pagination, Popover, Progress, Radio Group, Resizable, Scroll Area, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs, Textarea, Toast, Toggle, Toggle Group, Tooltip, Typography.

### Other component libraries

| Library | Package | Docs |
|---------|---------|------|
| **Chakra UI** | `@chakra-ui/react` | https://chakra-ui.com |
| **Mantine** | `@mantine/core` | https://mantine.dev |
| **Material UI / MUI** | `@mui/material` | https://mui.com |
| **Ant Design** | `antd` | https://ant.design |
| **NextUI** | `@nextui-org/react` | https://nextui.org |
| **Headless UI** | `@headlessui/react` | https://headlessui.com |
| **Radix UI** | `@radix-ui/*` | https://radix-ui.com |
| **Tremor** | `@tremor/react` | https://tremor.so |
| **Park UI** | `@park-ui/components` | https://park-ui.com |

**How to detect:** Check `package.json` dependencies. If any of these are present, use that library's components — don't add a second library.

---

## Component Registries

Copy-into-project component collections, compatible with the shadcn/ui model. Use these for specialized or animated components.

| Registry | Focus | URL |
|----------|-------|-----|
| **Magic UI** | Animated components, landing pages | https://magicui.design |
| **Aceternity UI** | Beautiful animations and effects | https://ui.aceternity.com |
| **Origin UI** | Polished copy-paste components | https://originui.com |
| **21st.dev** | Community registry, MCP integration for AI editors | https://21st.dev |
| **Cult UI** | Community-driven registry | https://cultui.com |
| **Kokonut UI** | Animated, accessible components | https://kokonut.dev |
| **ui.jln.dev** | Community extensions | https://ui.jln.dev |

**When to use:** Need animated/fancy components for landing pages, need polished variants beyond what the core library offers, or need specialized components. Always prefer these over building custom animated components from scratch.

---

## AI-Specific Components

### AI SDK Elements

**Docs:** https://elements.ai-sdk.dev/
**What it is:** A component library and custom registry built on top of shadcn/ui for building AI-native applications. Fully composable — mix and match components to build chat experiences, workflows, IDEs, voice agents, and more. Includes streaming, status states, and type safety out of the box.

**Add components:** `npx ai-elements@latest add <component-name>` or `npx shadcn@latest add @ai-elements/<component-name>`
**Install path:** `@/components/ai-elements/`

**Available components:**

**Chatbot:** Attachments, Chain of Thought, Checkpoint, Confirmation, Context, Conversation, Inline Citation, Message, Model Selector, Plan, Prompt Input, Queue, Reasoning, Shimmer, Sources, Suggestion, Task, Tool

**Code:** Agent, Artifact, Code Block, Commit, Environment Variables, File Tree, JSX Preview, Package Info, Sandbox, Schema Display, Snippet, Stack Trace, Terminal, Test Results, Web Preview

**Voice:** Audio Player, Mic Selector, Persona, Speech Input, Transcription, Voice Selector

**Workflow:** Canvas, Connection, Controls, Edge, Node, Panel, Toolbar

**Utilities:** Image, Open In Chat

### Other AI tools

| Tool | What it does | URL |
|------|-------------|-----|
| **Vercel AI SDK** | Core tools for AI chat hooks (`useChat`), streaming, and model integration | https://sdk.vercel.ai |
| **CopilotKit** | Open-source framework for building AI copilots into apps | https://copilotkit.ai |

---

## Enterprise Design Systems

If a project targets a specific platform, use its official design system:

| Platform | Design System | Package |
|----------|--------------|---------|
| **Microsoft** | Fluent UI | `@fluentui/react-components` |
| **Google** | Material UI / MUI | `@mui/material` |
| **IBM** | Carbon | `@carbon/react` |
| **Shopify** | Polaris | `@shopify/polaris` |
| **GitHub** | Primer | `@primer/react` |
| **Salesforce** | Lightning | `@salesforce-ux/design-system` |
| **Vercel** | Geist | `geist` |

---

## Working with other skills

When a design-focused skill (like `frontend-design`) is also active:

- **The design skill decides the look** — aesthetic direction, typography, colors, animations, layout
- **This skill decides the building blocks** — use library components as the foundation, don't write them from scratch
- **Customize, don't replace** — shadcn/ui components live in your codebase and are fully customizable. Apply bold design choices by modifying component styles, variants, and theming — not by rewriting the component from scratch
- **Example:** To build a dashboard with a "warm industrial" aesthetic, use shadcn/ui's Sidebar, Card, Table, and Chart components, then customize their styles to match the design direction

## Strict Rules

1. **NEVER** hand-write a standard UI element (button, dialog, dropdown, form input, card, table, tabs, toast, etc.) when a component library has it — even when applying custom design
2. **NEVER** hand-write AI interface patterns (chat, code blocks, prompt inputs, streaming indicators, workflows) when AI SDK Elements or CopilotKit covers it
3. **ALWAYS** check if a needed component exists in any available library before building custom
4. **ALWAYS** install components via CLI when available, not by copy-pasting from documentation
5. **COMPOSE** existing components to build complex UIs rather than creating monolithic custom components
6. **RESPECT** the project's existing library choice — don't mix libraries or force migrations
7. For new projects without an existing library, default to shadcn/ui with `npx shadcn@latest init`
8. For animated/specialized components, check registries (Magic UI, Aceternity, Origin UI, etc.) before building custom
9. When suggesting UI changes, reference the specific component by name from whichever library the project uses
10. **This skill overrides any other skill's impulse to build components from scratch** — always use libraries as the foundation
