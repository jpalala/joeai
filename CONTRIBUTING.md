
# Contributing to JoeAI - Agent Skills Registry for Frontend

A curated ecosystem of MCP-compatible Agent Skills for AI coding assistants. We index both remote skill repositories and skill servers that implement our System Capabilities API specification (`search_skills`, `get_skill`, etc.).

## Adding a Skill or Source

### Entry Format

Add your skill entry to the relevant section in `README.md`:

```markdown
- **[author/skill-name](https://github.com/author/repo/path)** - Short description of capabilities (10 words max)

```

For custom MCP skill registries or sources implementing `list_sources`:

```markdown
- **[org/source-name](https://github.com/org/source-repo)** - [MCP Server] Short description of hosted skill endpoints

```

### Categorization Guidelines

Organize your submission by capability or target framework:

* **Official Engineering Team Skills**: If your engineering org has an established section (e.g., "Vercel Engineering", "Figma Design-to-Code"), append to that section.
* **Frontend Framework Skills**: Add to the matching subcategory under "Frontend Skills" (`React`, `Vue`, `Svelte`, `Next.js`, `Tailwind CSS`, `State Management`, `Accessibility & i18n`, or `UI Components`).
* **System & Workflow Skills**: Add under "Context & Testing" (Design Tokens, Unit Testing, E2E, Component Storybooks, or Performance Optimization).
* **Uncategorized**: If no existing category fits, place your entry under "Other".

---

## Technical & Quality Requirements

Every submission must meet the following baseline requirements:

1. **API & Schema Compliance**:
* Skills MUST include a valid `SKILL.md` or OpenAPI/MCP tool definition compatible with our System Capabilities API (`get_skill`, `get_skill_reference`).
* Supporting documentation, design tokens, and asset schemas must be accessible via `get_skill_reference` or a clear path in the repo.


2. **Public Availability**: The host repository must be public, version-controlled, and accessible without unauthenticated rate-limiting.
3. **Naming Convention**: Use the `author/skill-name` or `org/skill-name` format.
4. **Concise Description**: Descriptions must be **10 words or fewer**. Keep it focused on the functional capability (e.g., *"Generates accessible Tailwind components from Figma node tokens"*).
5. **Maturity & Community Adoption**: We prioritize battle-tested, community-adopted skills. Brand-new or untested experimental repositories will be deferred until they show production usage.

---

## Pull Request Guidelines

* **PR Title**: `Add skill: author/skill-name` or `Add source: org/source-name`
* **Validation**: Run the internal validator before opening your PR:
```bash
npm run validate -- --url=https://github.com/author/skill-repo

```



---

## System Capabilities API Integration

If you are deploying a custom MCP server that serves skills dynamically:

* Ensure your server exposes the core capabilities:
* `search_skills`
* `list_skills`
* `get_skill`
* `get_skill_reference`
* `recommend_skills`
* `list_sources`


* Submit your server endpoint via the **Skill Registries & MCP Sources** section in `README.md`.

---

## Help & Support
- Review existing open [Issues](https://github.com/jpalala/joeai/issues) and [Pull Requests](https://github.com/jpalala/joeai/pulls) before submitting.
- Open a new issue for questions regarding category placement or API schema updates.
* Open a new issue for questions regarding category placement or API schema updates.
* For skill-specific bugs, open an issue directly in the skill's host repository.
