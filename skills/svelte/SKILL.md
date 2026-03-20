---
name: svelte
description: SvelteKit + Svelte 5 conventions, Tailwind CSS, DaisyUI, TypeScript — use when working in frontend code
---

## Stack

- SvelteKit + Svelte 5 with runes (`$state`, `$derived`, `$effect`)
- Tailwind CSS + DaisyUI for styling
- TypeScript over JavaScript, always

## Conventions

- When paired with a Go backend, SvelteKit builds to static/SSR output served by the Go server — do not run a Node.js host in production
- SSE used plentifully for quick feedback/status/events from server to client
- WebSocket used only when SSE isn't sufficient

## Testing

- Use Vitest for SvelteKit
- Write tests when they provide real value, not for coverage metrics
- Focus on logic that is complex, error-prone, or critical
