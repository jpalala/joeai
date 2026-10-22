## Technical Merge Documentation Request

### Skill Definition

**Name:** `technical-merge-documentation-request`

**Purpose:** Generate structured technical documentation for merge requests, capturing component/API characteristics, review fixes, test coverage, story examples, and design decisions in a standardized format suitable for commit messages, changers, and technical documentation.

---

### Usage Pattern

When you need to document a merge or commit, provide:

1. **Component/Feature Name**
2. **Key Characteristics** (props, states, behavior, architecture principles)
3. **Review Fixes** (what changed during review)
4. **Tests** (coverage details, assertion strategies, edge cases)
5. **Stories/Examples** (documentation/demo updates)
6. **Shared Changes** (impact on other modules)
7. **Design Decisions** (trade-offs, intentional limitations, open questions)

---

### Output Template

```
### Key Characteristics
- **Interface:** Props, config options, or parameters accepted.
- **States:** Behavioral states and their rendering logic.
- **Architecture:** Stateless/stateful, side effects, dependencies, coupling.
- **Interaction:** User or system interaction patterns.
- **Impact:** Scope of change (new, modified, deprecated, removed).
- **Release Strategy:** Versioning, bundling, or rollout approach.

---

## Review Fixes Included

1. **[Category]:** Description of issue → Resolution.
2. ...

---

## Tests

- Assertion strategies and refactoring notes.
- Edge cases and boundary conditions covered.
- Accessibility or integration coverage.

---

## Documentation/Examples

- Demo updates, story additions, or usage examples.
- Assertion or validation strategies for examples.

---

## Shared/External Changes

- Modifications outside the primary scope (exports, dependencies, configs).
- Version bumps and changelog updates.

---

## Design Decisions for Review

- Intentional limitations or non-goals.
- Trade-offs made (performance, flexibility, consistency).
- Open questions or future extension points.
```

---

### Example Application (Avatar Initials Component)

```
### Key Characteristics
- **Interface:** `firstName` (string), `lastName` (string), `size?` ("sm" | "md" | "lg"), `className?`.
- **States:** Renders 1-2 uppercase initials; empty names render as "?" fallback.
- **Architecture:** Pure function; no state, effects, or dependencies; deterministic output.
- **Interaction:** Static display; no hover, click, or focus behavior.
- **Impact:** New component; zero breaking changes.
- **Release Strategy:** Bundled into upcoming 2.1.0 design system release.

---

## Review Fixes Included

1. **Empty String Handling:** Previously crashed on empty strings → now renders "?" fallback.
2. **Whitespace Trimming:** Leading/trailing spaces included in initials → now trimmed.
3. **Single Name Support:** Required both first and last name → now optional; uses available name.
4. **Color Contrast:** Random background colors could fail WCAG → constrained to approved palette.

---

## Tests

- Replaced snapshot tests with explicit text assertions.
- Added coverage for non-Latin characters and diacritics.
- Edge cases: empty strings, whitespace-only, single character names, very long names.
- Added visual regression test for all three size variants.

---

## Stories (Storybook)

- Added `Default`, `SingleName`, `NonLatin`, `EmptyFallback`.
- Removed `RandomColors` story (no longer supported).
- All stories include accessibility checks via storybook-addon-a11y.

---

## Shared Component Changes

- Added `AvatarInitials` export to `src/index.js`.
- Updated `SIZE_TOKENS` constant in theme package to include "lg".
- Changelog entry under "Unreleased".

---

## Design Decisions for Review

- **No image fallback:** Intentionally text-only; image avatar is a separate component.
- **Fixed sizes only:** No custom size prop to maintain design system consistency.
- **No tooltip:** Callers wrap in tooltip if needed; keeps component simple.
- **Palette constraint:** 8 approved colors only; no arbitrary hex values accepted.
```

---

### Commit Message Format (Conventional Commits)

```
feat(avatar-initials): add text-only avatar component

- Renders 1-2 uppercase initials from first/last name
- Supports sm/md/lg sizes via design system tokens
- Fallback to "?" for empty or invalid names

Review fixes:
- Handle empty strings without crashing
- Trim whitespace from name inputs
- Support single name input (first or last optional)
- Constrain background colors to WCAG-compliant palette

Test coverage: non-Latin chars, edge cases, size variants
Stories: Default, SingleName, NonLatin, EmptyFallback

Release: 2.1.0
```

---

### When to Use This Skill

| Scenario | Apply Template To |
|----------|-----------------|
| New component/module | All sections |
| Bug fix with test additions | Review Fixes, Tests, Shared Changes |
| API change | Key Characteristics, Design Decisions |
| Refactoring | Review Fixes, Tests, Shared Changes |
| Documentation-only | Documentation/Examples |

Want me to adjust the template for backend services, CLI tools, or data pipelines?
