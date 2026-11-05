- Reproduce the bug end to end, as the user would hit it, before touching the code.
- Form several hypotheses and eliminate them with runtime evidence from the real running system, ideally one fact that can't be argued; ship only what the surviving cause justifies.
- Name the invariant a failure breaks, not just the instance: one root class (e.g. "an attempted action is treated as completed") explains and fixes many symptoms at once.
- Before judging a system, confirm the thing you are judging is the thing that runs: the running process, binary, config and session match the release you think you fixed.
- Don't ask a broken tool to repair itself: fix it from outside, coordinating with whoever owns it, then hand control back.
- Reproduce the bug first. What proves it works are the tests a human names or the end-to-end tests of the real path, never the ones the agent writes for itself.
- Inspect the blast radius outside the diff, and prove the fact the change is safe because of.
- Compare 2–3 alternatives before choosing one when there's no established pattern.
- Capture the real product before and after, and show that evidence instead of claiming it works.
- Turn every correction into structure: architecture first, then a lint or test, then a skill or rule.
- When making technical decisions, do not give much weight to development cost. Instead, prefer quality, simplicity, robustness, scalability, and long term maintainability.
- For one-off or infrequent operational work, start with the simplest direct end-to-end path. Do not build wrappers, control planes, policy layers, custom verifiers, or automation unless the direct path exposes a concrete blocker or repeated need that justifies the added machinery.
- When end-to-end testing a product, be picky about the UI you see and be obsessed with pixel perfection. If something clearly looks off, even if it is not directly related to what you are doing, try to get it fixed along the way.
- Apply that same high standard to engineering excellence: lint, test failures, and test flakiness. If you see one, even if it is not caused by what you are working on right now, still get it fixed.
- Use early returns so the code is more readable.
- Tautological tests considered harmful.
- A change that touches several files or will outlast one session goes through `research-plan-implement` skill; a diff that fits in one sentence does not.
- Cut taglines, helper text and secondary labels. If a screen needs them to make sense, fix the layout.
- Make the best decision that will elevate all three: the user experience (UX), developer experience (DX), and agent experience (AX) always, without breaking anything.
- Before adding complexity for a speculative or vanishingly unlikely race or security edge case, explain the concrete failure mode, likelihood, and complexity cost to the user and get their buy-in. Do not silently expand scope for theoretical robustness.

<!-- CODEGRAPH_START -->
## CodeGraph

In repositories indexed by CodeGraph (a `.codegraph/` directory exists at the repo root), reach for it BEFORE grep/find or reading files when you need to understand or locate code:

- **MCP tool** (when available): `codegraph_explore` answers most code questions in one call — the relevant symbols' verbatim source plus the call paths between them, including dynamic-dispatch hops grep can't follow. Name a file or symbol in the query to read its current line-numbered source. If it's listed but deferred, load it by name via tool search.
- **Shell** (always works): `codegraph explore "<symbol names or question>"` prints the same output.

If there is no `.codegraph/` directory, skip CodeGraph entirely — indexing is the user's decision.
<!-- CODEGRAPH_END -->

## Maintaining this file

Keep this file for knowledge useful to almost every future agent session in this project.
Do not repeat what the codebase already shows; point to the authoritative file or command instead.
Prefer rewriting or pruning existing entries over appending new ones.
When updating this file, preserve this bar for all agents and keep entries concise.
