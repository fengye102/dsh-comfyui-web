# Repository rules

## Purpose

This repository provides a dsh plugin that embeds ComfyUI and exposes the current workflow through MCP. Keep changes scoped to that integration.

## Structure and naming

- Root `client.js`, `bridge.js`, `comfy-extension.js`, and `mcp-stdio.mjs` are integration entry points. Put reusable runtime logic in `lib/` and executable checks in `scripts/`.
- Keep automated Node.js tests in `test/`, named `<area>.test.mjs`. Put user-facing documentation in `README.md` and `README.en.md`; keep the two languages in sync when changing shared facts.
- Keep static documentation assets in `docs/`. Do not commit generated output, dependency directories, temporary logs, or local ComfyUI/dsh configuration. Remove temporary verification files when done.

## Change process

- Investigate the root cause and add a failing regression test before changing runtime behavior. Prefer the smallest fix that addresses the cause.
- Keep dsh compatibility declarations in `package.json` aligned with versions actually exercised by tests. Update both README files when the supported dsh version changes.
- Run `npm test` before claiming a code change is complete; report any tests blocked by missing dependencies or environment.
