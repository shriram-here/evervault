# Vault — Distributed Object Storage Research Console

This bundle contains the Vault full-stack demo source, its source-linked research brief, and the original user-provided background video.

## Contents

- `source/` — React + Tailwind frontend, tRPC/Express backend, Drizzle schema and migrations, and Vitest tests.
- `research/Vault-Distributed-Object-Storage-Research.md` — design principles, quorum/consistency comparisons, recovery risks, references, and prototype scope.
- `media/Data_network_explosion_and_debris_20260926030803.mp4` — the original clip supplied for the hero background.

## Development

Use Node.js 22 and pnpm. From `source/`:

```bash
pnpm install
pnpm check
pnpm test
pnpm build
pnpm dev
```

The project template supports a MySQL/TiDB database using `DATABASE_URL`; without a database, the demo API uses an in-memory fallback. Database migrations are in `source/drizzle/migrations/`.

## Video asset note

The website's hero currently references the managed WebDev asset path `/manus-storage/vault-network-bg_18794812.mp4`. The original source clip is included in `media/`. For another host, upload that file to its media/CDN storage and update `VIDEO_SRC` in `source/client/src/pages/Home.tsx` to that host's asset URL. Large media should not be placed into the app's public source folder when using the managed WebDev workflow.

## Scope

This is an interactive architecture and reliability **simulator**, not a production object-storage engine. It stores demo policy state and a bounded operation history; it does not store or replicate customer object bytes, coordinate real storage nodes, provide an SLO, or guarantee durability. The node/capacity values shown in the UI are illustrative. Production deployment needs an explicit consistency contract, consensus/fencing, failure-domain-aware placement, validated repair and integrity machinery, fault-injection tests, and workload-specific capacity planning.
