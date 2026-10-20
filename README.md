# joeai

A README helps humans understand the project, decide whether to use it, and get started quickly. My primary skill though is fullstack, but I'd like to catalog the frontend skills I gained through the years. From UX design to some frontend css. 

Frontend Skills Registry

A searchable registry of skills for React, frontend design, and design-system utilities — built for AI coding agents.

Frontend Skills Registry helps AI coding agents discover and retrieve reusable skills that improve how they design, build, and maintain frontend applications.

It brings together skills for UI design, React development, component architecture, design systems, accessibility, responsive layouts, and frontend engineering into one discoverable registry.

Instead of manually searching repositories for the right SKILL.md, agents can search the registry, inspect available skills, and fetch relevant instructions when needed through a Model Context Protocol (MCP) server.

What Is This?

Frontend Skills Registry is a registry and discovery layer for frontend-related AI agent skills.

It is designed to make existing frontend knowledge easier to find, reuse, and integrate into AI-assisted development workflows.

The registry can index skills from curated repositories and other compatible sources, providing a consistent way to discover skills regardless of where they originate.

The goal is simple: help AI agents build better frontend interfaces by giving them access to the right skills at the right time.

What Can You Find Here?

- React Development
- React components, hooks, and composition patterns
- Component architecture and reusable abstractions
- State management and data-fetching patterns
- Next.js and modern React application development
- TypeScript conventions for frontend applications
- Frontend Design
- UI composition, visual hierarchy, and layout
- Typography, color, spacing, and visual consistency
- Landing pages, dashboards, forms, and application interfaces
- Responsive design and mobile-first development
- Interaction design, loading states, and empty states
- Design Systems
- Design tokens and theming
- Component libraries and reusable UI primitives
- Consistent spacing, typography, and color scales
- Design-system documentation and maintenance
- Integration with systems such as Tailwind CSS and component libraries
- Frontend Quality
- Accessibility and semantic HTML
- Responsive behavior and cross-browser considerations
- Frontend performance and rendering optimization
- UI testing and visual regression testing
- Code quality and maintainability

Curated from https://awesomeskill.ai/

## How It Works

1. D for Discover — Find frontend skills using keywords, categories, frameworks, and tags.
2. I for Inspect — Review a skill's description, source repository, license, and supported use cases.
3. F for Fetch — Retrieve the skill instructions and relevant supporting files.
4. A for Apply — Let the AI coding agent use those instructions while working on the frontend project.

The registry focuses on discovery and retrieval. Skills remain independently maintained at their original sources where possible.

MCP Integration

The registry is designed to expose skills through a Model Context Protocol (MCP) server so compatible AI coding agents can discover and retrieve them.

Planned capabilities include:

search_skills — Search for relevant frontend skills.
list_skills — Browse available skills by category or framework.
get_skill — Retrieve a skill's full instructions.
get_skill_reference — Retrieve supporting documentation and examples.
recommend_skills — Find suitable skills for a frontend task.
list_sources — Inspect registered repositories and skill sources.
Existing Projects Worth Studying

This project builds on the broader ecosystem of agent skills and MCP tooling rather than attempting to reinvent existing skill formats.

1. Anthropic Skills

github.com/anthropics/skills

A useful reference for the structure and organization of reusable agent skills, including the SKILL.md format.

2. Model Context Protocol

modelcontextprotocol.io

The protocol that enables AI applications to discover and use tools and resources exposed by external servers.

3. Skills CLI

github.com/vercel-labs/skills

A useful reference for discovering, managing, and installing agent skills across coding environments.

These projects provide useful foundations for understanding skill formats, distribution, and interoperability. Frontend Skills Registry focuses specifically on organizing and discovering skills for React, frontend design, and design-system workflows.

Design Principles
Discoverability first: Make relevant skills easy to find.
Framework-aware: Support React and related frontend ecosystems without limiting the registry to one framework.
Source transparency: Preserve original source information, licensing, and attribution.
On-demand retrieval: Fetch detailed instructions only when they are needed.
Composable skills: Allow agents to combine design, implementation, accessibility, and testing guidance.
Open ecosystem: Make it possible to add new repositories and skill categories over time.
Project Status

This project is in early development.

The initial focus is on establishing the registry, defining a consistent skill metadata model, integrating skill sources, and exposing discovery and retrieval through MCP.

Planned future work includes richer search, skill recommendations, source synchronization, and additional frontend ecosystem integrations.

Contributing

Contributions are welcome, especially:

Frontend and React skill sources
Design-system utilities and component development skills
Registry integrations and source adapters
Search and recommendation improvements
Documentation, examples, and tests

See CONTRIBUTING.md for contribution guidelines.

License

See LICENSE for the project's license.

Third-party skills may have their own licenses and attribution requirements. Each source should retain its original licensing information.
