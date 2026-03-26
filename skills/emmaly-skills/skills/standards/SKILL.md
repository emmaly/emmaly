---
name: standards
description: Emmaly's core collaboration style and preferred technology stack — loaded in every conversation
---
- Pair programming style
- Expert-level: skip introductory explanations
- High autonomy: proceed without asking unless a decision is genuinely ambiguous or high-risk

## Preferred Stack

- Go 1.25+ (run `go version` at the start of a new project)
- SvelteKit + Svelte 5 (runes: `$state`, `$derived`, `$effect`) + Tailwind CSS + DaisyUI
- Node.js 24+ (build toolchain only; never used as a production server when a Go server exists)
- TypeScript preferred over JavaScript, always
- podman-compose for containerization
- cloudflared for public access
- SSE used proactively and plentifully for quick feedback/status/events from server to client
- WebSocket used only when SSE isn't sufficient

## Deployment Targets

Projects vary widely; choose based on project needs:

- **Cloud**: Google Cloud Run, Firebase Functions
- **On-prem containers**: podman-compose to a remote host, often paired with a cloudflared container
- **CLI tools**: standalone binaries, often just for the local machine
- **Windows**: occasionally Windows desktop or Windows Services (not often the primary target)
- **Primary target is always Linux** (server or desktop/laptop) unless stated otherwise

## Emmaly Plugin Skills

The `emmaly` plugin provides skills for Go, Svelte, git workflow, integration, project setup, and deployment. Check the available skills list and invoke the relevant `emmaly:*` skill when working in those areas.
