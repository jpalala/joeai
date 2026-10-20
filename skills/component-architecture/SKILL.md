---
name: component-architecture
description: Rules for building scalable React component architectures using core UX principles and reusable abstractions.
---

# Component Architecture & UX Principles

## 1. UX & Interaction Principles
- **Predictable Feedback States:** Every interactive element MUST explicitly handle default, hover, active, focus-visible, loading, and disabled states. Never leave a user guessing if an action registered.
- **Optimistic UI & Skeleton Loading:** Avoid layout shifts (CLS). Always use skeleton placeholders matching the layout dimensions during initial loads.
- **Keyboard & Screen Reader Accessibility:** 
  - Ensure custom interactive elements use semantic HTML (`<button>`, `<dialog>`) or explicit ARIA roles/attributes (`aria-expanded`, `aria-controls`).
  - Always manage focus trapped inside modals and dialogs, restoring focus on close.
- **Micro-Interactions:** Use spring-based or subtle transitions (150–250ms) for UI state changes. Avoid sudden jumps or slow layout animations (>400ms).

## 2. Reusable Component Abstractions
- **Compound Component Pattern:** For complex stateful UI (e.g., Accordions, Dropdowns, Tabs), expose subcomponents sharing implicit context rather than a monolithic prop-heavy API.
  ```tsx
  // PREFERRED: Compound composition
  <Select onChange="{setVal}" value="{val}">
    <Select.Trigger/>
    <Select.Content>
      <Select.Item value="1">Option 1</Select.Item>
    </Select.Content>
  </Select>
