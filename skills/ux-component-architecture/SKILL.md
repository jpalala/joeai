# UX-Driven Component Architecture & Design System Rules

Apply these UX principles and component patterns whenever creating or modifying React/Next.js UI components.

## Core UX & Accessibility Principles

1. **Optimistic & Immediate Feedback:**
   - Always pair async actions with local state updates, pending states, or skeleton loaders.
   - Interactive elements (`button`, `a`, `input`) must explicitly define `:hover`, `:focus-visible`, and `:disabled` styles.
   - Ensure focus rings use high-contrast outline styles (`ring-2 ring-offset-2`).

2. **Accessible Semantics (A11y):**
   - Use standard HTML semantics over generic `<div>` wrappers wherever possible.
   - For custom interactive components, adhere strictly to WAI-ARIA authoring practices.
   - Decorative SVGs must include `aria-hidden="true"`.
   - Dynamic status messages or alerts must use `aria-live="polite"` or `role="status"`.

3. **Layout Stability & Content Jump Prevention:**
   - Prevent Cumulative Layout Shift (CLS) by giving images, avatars, and asynchronous content containers defined aspect ratios or fixed explicit dimensions during loading states.

---

## Component Abstraction Rules

1. **Compound Component Pattern for Complex UIs:**
   - Use Compound Components for modular design systems (e.g., `<Dialog>`, `<Dropdown>`, `<Accordion>`) to allow sub-component composition rather than massive prop interfaces.

```tsx
// Pattern Example:
export function Card({ children, className }: CardProps) {
  return <div className={cn("rounded-xl border bg-card p-6", className)}>{children}</div>;
}
Card.Header = function CardHeader({ children }: { children: React.ReactNode }) {
  return <div className="flex flex-col space-y-1.5 mb-4">{children}</div>;
};
Card.Body = function CardBody({ children }: { children: React.ReactNode }) {
  return <div className="text-sm text-muted-foreground">{children}</div>;
};
