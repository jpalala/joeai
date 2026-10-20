# Next.js App Router Architecture & Server Actions Guide

Standardized guidelines for Next.js App Router applications, focusing on React Server Components (RSC) and performance optimization.

## React Server Components (RSC) Paradigm

1. **Server-First Boundary:**
   - Treat components as Server Components by default. Add `'use client'` only at the lowest leaf nodes requiring interactive hooks (`useState`, `useEffect`, event handlers).
   - Never import a Server Component into a Client Component directly; pass Server Components as `children` or JSX slots.

2. **Parallel & Streaming Data Fetching:**
   - Fetch data directly inside Server Components using async/await.
   - Avoid waterfalls by using `Promise.all()` for independent asynchronous data requests.

```tsx
// Preferred: Parallel fetching on the server
export default async function DashboardPage() {
  const [user, analytics] = await Promise.all([
    getUserProfile(),
    getAnalyticsData()
  ]);

  return (
    <main>
      <ProfileHeader user={user} />
      <AnalyticsGrid data={analytics} />
    </main>
  );
}
```

3. **Server Actions with Progressive Enhancement:**

Define Server Actions in isolated actions.ts files or marked inline with 'use server'.

Validate input parameters using a schema parser (e.g., zod) before running server-side logic.

Support progressive enhancement so forms remain functional prior to JavaScript hydration where applicable.

4. **Error & Loading UX Routing:**

Utilize granular `loading.tsx`, `error.tsx`, and `not-found.tsx` files within route segments to contain error boundaries locally without crashing adjacent layout regions.
