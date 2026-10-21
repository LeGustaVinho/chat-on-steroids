# Upstream sync — 2026-10-21

Integrated `totec448-spec/chat-on-steroids` `main` at `072f70fc` into the fork's `main` at `5d8532cf`.

The two merge conflicts were in `src/main/config.ts` and `src/main/session/input.ts`. The resolved defaults retain the fork's stealth settings and include the upstream's opt-in `rotateStopFallback`. Recovery messages retain the fork's delayed `dueAt` and include the upstream's configurable Continue text. The merged tree also retains the fork's connector branding and browser behavior. Removed one upstream trailing blank line in `test/input-delivery-integration.test.ts` for `git diff --check`.

Validation: `git diff --cached --check` passed. `npm run verify` passed the ripgrep staging, public-history privacy, third-party notices and TypeScript typecheck stages. The broad Vitest stage failed in suites including `test/update.test.ts`, `test/plugins-ui.test.ts`, `test/mcp.test.ts`, `test/bridge.test.ts` and `test/input-delivery-integration.test.ts`; the run was stopped before completion. A targeted rerun of the first input-delivery failure showed the existing fork stealth delay keeps a recovery row from being pending immediately, while that test expects immediate pickup. The fork's connector-name changes likewise conflict with upstream tests that expect the original branding. No package, install or live browser validation was performed.
