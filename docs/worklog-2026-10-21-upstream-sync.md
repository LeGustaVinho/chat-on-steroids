# Upstream sync — 2026-10-21

Integrated `totec448-spec/chat-on-steroids` `main` at `072f70fc` into the fork's `main` at `5d8532cf`.

The two merge conflicts were in `src/main/config.ts` and `src/main/session/input.ts`. The resolved defaults retain the fork's stealth settings and include the upstream's opt-in `rotateStopFallback`. Recovery messages retain the fork's delayed `dueAt` and include the upstream's configurable Continue text. The merged tree also retains the fork's connector branding and browser behavior. Removed one upstream trailing blank line in `test/input-delivery-integration.test.ts` for `git diff --check`.

Validation: `git diff --cached --check` passed. `npm run verify` passed the ripgrep staging, public-history privacy, third-party notices and TypeScript typecheck stages. The broad Vitest stage failed in suites including `test/update.test.ts`, `test/plugins-ui.test.ts`, `test/mcp.test.ts`, `test/bridge.test.ts` and `test/input-delivery-integration.test.ts`; the run was stopped before completion. A targeted rerun of the first input-delivery failure showed the existing fork stealth delay keeps a recovery row from being pending immediately, while that test expects immediate pickup. The fork's connector-name changes likewise conflict with upstream tests that expect the original branding. No package, install or live browser validation was performed.

## Follow-up sync

GitHub showed the fork 8 commits ahead and 24 behind after upstream advanced from `072f70fc` to `b07cb541`. The local checkout had only `origin`, so the remote `upstream` was configured to `https://github.com/totec448-spec/chat-on-steroids.git` and fetched. Merging `upstream/main` into the fork's `main` required no manual conflict resolution. `git diff --cached --check`, `npm run typecheck`, and the targeted bookmark, Goal, Session finish and renderer CSP suites passed (209 tests across four files). The earlier broad-suite failures remain unaddressed. No package, install or live app validation was performed.

`npm run build` passed. `npm run verify:ui` passed the bookmark list, chat, settings and other checks it reached, but failed `verify-cos-sign-in.cjs` because OpenSSL could not create its fixture certificate and `verify-pet-performance.cjs` because the app raised `b.releaseFocus is not a function`. `verify-setup-guide.cjs` then stopped making progress and the run was interrupted. The overall UI gate did not pass. The GitHub page was checked in Chrome before this second merge; the post-push comparison must be checked separately.
