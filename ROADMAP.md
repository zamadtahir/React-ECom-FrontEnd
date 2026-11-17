# ShopLab — React + TypeScript Pro Roadmap

You build a real e-commerce front end, one task at a time.
After each task, tell Claude **"Task X.Y done"**. Claude reviews your code; you fix what comes up; then you get the next task.

**Data source:** [DummyJSON](https://dummyjson.com/docs/products) — a free fake API for products, users, login and carts. You don't need to build a backend.

**Ground rules (pro habits from day one)**
- TypeScript `strict` mode. No `any` unless you write a comment saying why.
- One commit per task, with a clear message (`feat: add product card`).
- Write it yourself before you ask for help. If you're stuck for 30+ minutes, ask for a hint, not the answer.
- Each task has **Learn** (concepts), **Build** (what to make), **Done when** (acceptance criteria) and sometimes **Stretch** (optional extras).

## How every feature is taught: Old → New → Optimised
For each feature, you learn the same thing three ways:

1. **🕰️ Old way.** How React apps did it before (class components, lifecycle methods, HOCs, `connect()`…). You'll meet this in legacy codebases and interviews. Usually you **read** it or write a small throwaway version.
2. **✨ Modern way.** Today's idiomatic React: function components, hooks, and React 19 APIs. This is what goes into the app.
3. **🚀 Optimised / pro way.** The production-grade version: the right library, performance tuning, edge cases and trade-offs.

Each lesson ends with **"Why did it change?"**: the problem the old way had and how the new way solves it. If you understand that, you understand React.

---

## Phase 1 — Foundations & tooling
| # | Task | Key concepts |
|---|------|--------------|
| 1.1 | Project setup | Vite, React 19, TS strict, ESLint, Prettier, git, folder structure |
| 1.2 | Model the domain in TypeScript | `type` vs `interface`, unions, optional fields, `as const`, utility types |
| 1.3 | Static product card and grid | JSX, components, typed props, `children`, lists & `key`, module CSS / Tailwind |

## Phase 2 — State & interactivity
| # | Task | Key concepts |
|---|------|--------------|
| 2.1 | Search, filter, sort (local mock data) | `useState`, controlled inputs, derived state (don't store what you can compute), typed events |
| 2.2 | Reusable UI kit: Button, Input, Badge, Rating | Extending native props (`ComponentProps<'button'>`), variants with unions, composition |

## Phase 3 — Routing
| # | Task | Key concepts |
|---|------|--------------|
| 3.1 | Pages: Home, Products, Product detail, Cart, 404 | React Router, layouts, `<Outlet>`, URL params |
| 3.2 | Filters live in the URL | `useSearchParams`, shareable URLs, URL as state |

## Phase 4 — Talking to an API
| # | Task | Key concepts |
|---|------|--------------|
| 4.1 | Fetch products by hand | `useEffect`, async/await, loading/error states, `AbortController`, race conditions |
| 4.2 | Write a generic `useFetch<T>` hook | Custom hooks, generics, typed API layer, runtime validation with Zod |
| 4.3 | Move to TanStack Query | Caching, query keys, pagination, prefetching, why server state ≠ client state |

## Phase 5 — Global state: the cart
| # | Task | Key concepts |
|---|------|--------------|
| 5.1 | Cart with Context + `useReducer` | Discriminated union actions, exhaustive `switch` with `never`, typed context |
| 5.2 | Persist the cart | `localStorage`, lazy initial state, syncing across tabs |
| 5.3 | Rewrite the cart with Zustand (or Redux Toolkit) | Comparing approaches, selectors, avoiding re-renders |

## Phase 6 — Forms & auth
| # | Task | Key concepts |
|---|------|--------------|
| 6.1 | Multi-step checkout form | React Hook Form + Zod, `z.infer`, field errors, accessibility of forms |
| 6.2 | Login & protected routes | DummyJSON auth, token storage trade-offs, route guards, redirect back after login |

## Phase 7 — Performance & polish
| # | Task | Key concepts |
|---|------|--------------|
| 7.1 | Measure, then optimise | React DevTools Profiler, `memo`, `useMemo`, `useCallback` (and when *not* to use them) |
| 7.2 | Code-splitting & UX | `lazy` + `Suspense`, error boundaries, skeleton loaders, debounced search |
| 7.3 | Accessibility & responsive design | Semantic HTML, keyboard navigation, focus management, ARIA basics |

## Phase 8 — Testing
| # | Task | Key concepts |
|---|------|--------------|
| 8.1 | Unit tests | Vitest, testing reducers and utility functions |
| 8.2 | Component tests | React Testing Library, user-event, testing behaviour not implementation |
| 8.3 | Mock the API | MSW (Mock Service Worker) |

## Phase 9 — Advanced TypeScript & architecture
| # | Task | Key concepts |
|---|------|--------------|
| 9.1 | Type-level refactor | Generics with constraints, mapped & conditional types, type guards, `satisfies` |
| 9.2 | Feature-based folder structure | Colocation, barrel files trade-offs, absolute imports |

## Phase 10 — Ship it
| # | Task | Key concepts |
|---|------|--------------|
| 10.1 | CI pipeline | GitHub Actions: typecheck, lint, test on every push |
| 10.2 | Deploy | Vercel or Netlify, environment variables, production build |

## Phase 11 — Bonus: full-stack React
| # | Task | Key concepts |
|---|------|--------------|
| 11.1 | Port a page to Next.js App Router | Server Components vs Client Components, `"use client"`, streaming SSR |
| 11.2 | Server Actions | `"use server"`, forms that work without JS, revalidation |

---

## React concept coverage map (where you learn each concept)
| Concept | 🕰️ Old way | ✨ Modern way | 🚀 Optimised / pro | Task |
|---|---|---|---|---|
| Project tooling | Create React App, Webpack config | Vite | Framework (Next.js / React Router framework mode) | 1.1 |
| Components | `class extends React.Component`, `React.createElement` | Function components + JSX | Composition, small focused components | 1.3 |
| Prop types | `PropTypes`, `defaultProps` | TS types, default parameters | Discriminated-union props, `ComponentProps<>` | 1.2, 1.3, 2.2 |
| Local state | `this.state` / `this.setState` | `useState`, functional updates | Derived state, automatic batching (React 18+) | 2.1 |
| Expensive updates | — | `useState` | `useTransition`, `useDeferredValue` | 2.1, 7.2 |
| Refs | String refs, `createRef` | `useRef` | `useImperativeHandle`, callback refs | 2.2 |
| Forwarding refs | `forwardRef` | `ref` as a regular prop (React 19) | — | 2.2 |
| Logic reuse | Mixins → HOCs → render props | Custom hooks | Compound components, headless UI | 2.2, 4.2 |
| Side effects / lifecycle | `componentDidMount/DidUpdate/WillUnmount` | `useEffect`, cleanup, StrictMode double-run | `useLayoutEffect`, `useEffectEvent`, "you might not need an effect" | 4.1 |
| Data fetching | Fetch in `componentDidMount` | `useEffect` + `AbortController` | TanStack Query; `use()` + Suspense; router loaders | 4.1–4.3 |
| Routing | React Router v5 (`<Switch>`, `withRouter`) | v6/v7 `<Routes>`, hooks, `<Outlet>` | Data routers, loaders/actions, lazy routes | 3.1, 3.2 |
| Context | `<Consumer>` render prop, `static contextType` | `useContext`, `<Context>` as provider (React 19) | `use(Context)`, split contexts, memoised values | 5.1 |
| Complex state | `setState` callbacks | `useReducer` + typed actions | — | 5.1 |
| Global state | Redux + `connect`, `mapStateToProps` | Redux Toolkit hooks / Zustand | Selectors, `useSyncExternalStore` | 5.3 |
| Forms | Class-controlled inputs, uncontrolled + refs | Controlled with hooks, React Hook Form + Zod | Form Actions, `useActionState`, `useFormStatus`, `useOptimistic` | 6.1 |
| Re-render control | `shouldComponentUpdate`, `PureComponent` | `memo`, `useMemo`, `useCallback` | React Compiler (automatic memoisation) | 7.1 |
| Code splitting | Webpack `import()` + loadable libs | `lazy` + `Suspense` | Route-level splitting, prefetching | 7.2 |
| Error handling | `componentDidCatch` (still class-only!) | `getDerivedStateFromError` boundary | `react-error-boundary`, Query error resets | 7.2 |
| Hidden UI / tabs | Unmount and lose state | CSS hiding | `<Activity>` (React 19.2) | 7.2 |
| Modals & IDs | Manual DOM, random ids | `createPortal`, `useId` | Focus traps, native `<dialog>` | 7.3 |
| Head / SEO | `react-helmet` | `<title>` / `<meta>` in components (React 19) | — | 7.3 |
| Lists | `.map` everything | Stable `key`s | Virtualisation (TanStack Virtual) | 1.3, 7.1 |
| Rendering model | Client-only SPA | SSR + hydration | Server Components, streaming, Server Actions | 11.1, 11.2 |

---

## Progress log
| Task | Status | Review notes |
|------|--------|--------------|
| 1.1 | 🔁 Changes requested (review 1) | Vite + React 19 + TS 6 scaffold works; lint and build pass. Missing: explicit `strict` + `noUncheckedIndexedAccess`, Prettier, `format`/`typecheck` scripts, demo cleanup, folder structure, git commit, written answers. |
