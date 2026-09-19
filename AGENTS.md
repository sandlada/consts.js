# AGENTS.md

Personal-use URL/metadata constants package (`@sandlada/consts.js`). Public repo, but data is Sandlada-specific — don't generalize it.

- Sole source: `src/index.ts` exports `Consts as const` (`Domain`, `Member`, `Repo`, `Social`). Single-file lib, ESM-only (`"type": "module"`).
- Keep `as const` on the export; consumers rely on literal types.
- Match existing data style: backtick strings, grouped objects per site/member/repo. Static readonly fields use leading-capital names (`Author`, `GitHubLink`, `NpmLink`); `Domain` computed `['...']` keys stay as-is.

## Commands

- `npm run build` — `tsdown`, outputs `dist/index.mjs` + `index.d.mts` (dts via `tsgo`).
- `npm run dev` — `tsdown --watch`.
- `npm run typecheck` — `tsc --noEmit` (strict, `noUnusedLocals`, `verbatimModuleSyntax`).
- No tests, lint, or CI. Verify with `npm run typecheck && npm run build`.

## Publish

- `prepublishOnly` rebuilds `dist/`; `dist/` is gitignored and the only published dir (`files: ["dist"]`, export `.` → `./dist/index.mjs`).
- Never edit `dist/` by hand; never commit it.
