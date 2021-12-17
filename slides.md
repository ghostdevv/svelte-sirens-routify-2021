---
background: '/routify-logo-bg.png'

fonts:
  - "Inter"
  - "Overpass"
---

# Routify & Svelte Kit

Exploring Routify inside of Svelte Kit

---

# What is Routify?

Routify is a router! It's based on your filesystem, which you'll be familiar with if you've used Kit.

---

# Why Routify & Svelte Kit

Combining the two systems brings the benefits of both worlds, for example:

## Svelte Kit

- The Svelte Community
- The Adapter Ecosystem
- Builtin backend
- SSR / SSG

## Routify

<!-- - Simplified SSR with `$ready` (get rid of the `if browser` hell!) -->
- Exposed Node Tree - For generated navigation, inlined page, etc.
- Metadata - Provides builtin/custom logic, data fetching, persistent, codesplitting
- Multiple router instances - For side by side navigation, widgets etc.
- Decorators - For transitions and logic that applies to all nested modules/pages
---

# Getting Started

---

#### 1. Install Routify in your Kit project

```html
npm install @roxi/routify@next
```

<br>

#### 2. Add Routify to `svelte.config.js`

```javascript {2|7,8,9}
// svelte.config.js
import routify from '@roxi/routify/vite-plugin'

const config = {
    kit: {
        vite: {
            plugins: [
              routify({ routesDir: 'src/pages' })
            ],
            ...
```


---

#### 3. Create an `[...index].svelte` to catch all traffic.
```html {2,10|3|4|6|9|12}
<!-- src/routes/[...index].svelte -->
<script context="module">
    import { Router, createRouter } from '@roxi/routify'
    import routes from '../../.routify/routes.default.js'
    
    const router = createRouter({ routes })

    // for SSR we need to tell Kit to wait for Routify to finish loading its components
    export const load = ({ page }) => router.url.replace(page.path)
</script>

<Router {router} />
```

---

#### 4. Create some pages in `src/pages`

Just like you would in `src/routes`.

---

# Thank You For Watching

## CLI:

```bash
npm init routify project-name
```

## Links:

https://v3.routify.dev

## GHOST
https://ghostdev.xyz/