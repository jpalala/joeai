Here is the polished specification for your **Frontend Skills MCP Server** (or registry service), completed with the missing section for **Existing Projects Worth Studying**.

---

### **System Capabilities API Specification**

#### **Core Tool Methods**

1. **`search_skills`**
* **Goal:** Perform semantic or keyword searches across the registry for relevant frontend skills.
* **Parameters:** `query` (string), `framework` (optional string, e.g., `"react"`, `"vue"`), `limit` (optional integer).


2. **`list_skills`**
* **Goal:** Browse available skills categorized by domain, framework, or paradigm.
* **Parameters:** `category` (optional string, e.g., `"accessibility"`, `"state-management"`, `"ui-design"`), `page` (optional integer).


3. **`get_skill`**
* **Goal:** Retrieve a skill's full execution instructions (`SKILL.md` / workflow prompt).
* **Parameters:** `skill_id` or `skill_name` (string).


4. **`get_skill_reference`**
* **Goal:** Retrieve supporting documentation, design tokens, asset schemas, and code examples associated with a skill.
* **Parameters:** `skill_id` (string), `resource_path` (optional string).


5. **`recommend_skills`**
* **Goal:** Analyze a high-level task description or codebase context and suggest suitable frontend skills.
* **Parameters:** `task_description` (string), `context` (optional object containing dependencies, frameworks, etc.).


6. **`list_sources`**
* **Goal:** Inspect registered Git repositories, local directories, and upstream MCP skill sources.
* **Parameters:** None.



---

### **Existing Projects Worth Studying**

When building a skill registry or MCP skill-distribution server, analyze these existing open-source implementations for architectural inspiration:

#### 1. **`biocontext-ai/skill-to-mcp`**

* **Why study:** Converts standard `SKILL.md` directory structures into accessible MCP resources and tools over stdio/SSE.
* **Key feature:** Demonstrates clean separation between skill discovery (`SKILL.md` frontmatter parsing) and fetching supporting assets using file-path traversal guards.

#### 2. **`JayCheng113/skill-retrieval-mcp`**

* **Why study:** Implements a two-step retrieval pattern (`search_skills` $\rightarrow$ `get_skill`) for large skill libraries to avoid polluting context windows.
* **Key feature:** Features embedding-based semantic index search, deduplication across sources, and priority-weighted source overrides.

#### 3. **`figma/mcp-server-guide` (Skills Directory)**

* **Why study:** The reference standard for frontend design-to-code skills (e.g., `figma-generate-design`).
* **Key feature:** Shows how complex frontend skills manage multi-step dependencies, cross-referencing Figma tokens, local Code Connect files, and HTML-to-component mappings.

#### 4. **`openai/skills` & Anthropic Skill Spec**

* **Why study:** The canonical repository format for reusable agent skills (`SKILL.md` specification).
* **Key feature:** Illustrates how to format system prompts with YAML frontmatter, execution gates, and strict input/output deliverable constraints.

#### 5. **Microsoft Agent Framework (`AgentSkillsProvider`)**

* **Why study:** Enterprise-grade implementation supporting file-based, class-based, and remote MCP-based skill aggregation.
* **Key feature:** Features built-in tool approval rules, automatic caching, zip-archive skill fetching, and multi-source deduplication.
