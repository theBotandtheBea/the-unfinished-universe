# Pilot 001 — Session isolation check

**Status:** Inconclusive at setup, 17 November 2026. Zero of four comparison sessions started. Zero independent reviews performed.

## Observations

- The existing Codex conversation retrieved the GitHub record during the earlier access preflight. This conversation has also seen the research history and pilot rubric, so it cannot be used as a comparison session.
- Fresh background agents can start without the parent conversation. The available launch interface does not expose controls to remove GitHub and search tools from the control sessions or restrict the memory sessions to the frozen revision. Prompt instructions alone do not verify those boundaries.
- The local Codex CLI is present and reports an authenticated session. Its help shows options for fresh ephemeral runs and sandbox selection. Those options alone do not demonstrate that all retrieval paths are isolated. The two tested OS-level network isolation routes, `bwrap --unshare-net` and `unshare --net`, both failed with permission errors. No other way to enforce the required boundaries in two configurations was verified.

## Interpretation

This is a setup limitation of the environment used for the attempt. It provides no comparison between research with and without shared memory. No participant briefs, scores, contradictions, or reviewer judgments were generated. The earlier retrieval check remains the only observed research-memory outcome.

## Next check

Use a runner with explicit tool allowlists and no shared session history or personalization. Give control sessions only the frozen evidence packet. Give memory sessions the same packet and a read-only retrieval interface restricted to the chosen commit. Before collecting answers, verify in both configurations that a control cannot retrieve a repository file, a memory session can retrieve a file at the frozen revision, and that neither can retrieve the scoring key, a later revision, web sources outside the packet, or earlier outputs. Save the positive and negative access checks. Freeze the task, checked evidence packet, and scoring key before collecting any answers. Keep this setup record and add future runs and reviews as separate records.
