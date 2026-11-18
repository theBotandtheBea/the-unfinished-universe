# Pilot 001 — Isolation follow-up, 18 November 2026

The [first documented experimental limitation](preflight-isolation.md) remains part of the record. No comparison sessions or independent reviews were run for this follow-up.

## Simplest test: frozen packets and fresh model requests

Use the same task, scientific evidence and settings in both conditions. A coordinator exports the curated historical files from a pinned GitHub commit, records file paths and SHA-256 hashes, and adds that packet only to the memory requests. Keep the scoring key, prior answers, assignment log and newer files entirely outside the participant runner. Keep a distinct request for each run with no shared conversation identifiers, history, templates, or personalization. Expose no search, file, shell, connector, tool discovery, or delegated agent capabilities. For the OpenAI Responses API, configure an empty tools list, no conversation or previous-response ID, and store:false. Validate the complete outgoing request against a strict allowlist and record its hash, model and settings before any live call. This verifies what the coordinator sends and which tool paths it grants; it cannot establish what a model knew before the experiment or audit provider internals. API response storage settings are separate from isolation.

This would be a protocol amendment. It measures the effect of receiving a GitHub-derived archive, including the effects of curation, order and extra context length. It does not measure live repository discovery, autonomous selection of files, or Codex Work's normal behavior. Two model configurations using this method can test the archive effect, but an API model does not make a run a Codex Work session. If on-demand retrieval matters, the next step is a single read-only lookup over an in-memory map of approved paths at the frozen commit. Give only the memory arm that lookup and reject every other path, ref and URL.

## If Codex itself must participate

Use two clean disposable environments with identically pinned Codex versions and configurations. Stage only the assigned packets read-only, with no shared workspace, home, repository checkout, prior transcripts or grading key. Disable web search and connectors and verify the effective tool inventory. Enforce outbound restrictions outside Codex so the client can reach only its model service and agent tools cannot use the connection to reach arbitrary resources. Prove the restrictions with direct environment probes. A fresh chat or an instruction to avoid GitHub supplies no equivalent proof. The prior network isolation attempts failed here and this alternative remains unverified.

## Observations and launch checks

- Successfully retrieved the corrections file by the previously recorded commit reference.
- Local offline smoke test: a synthetic builder emitted two payloads with identical common input. A synthetic archive marker appeared only in the memory payload. Synthetic scoring-key, prior-output and later-revision markers appeared in neither payload. Both had empty tools and no conversation references. No provider was contacted. This tested the payload shape only, not a production harness or live isolation.
- Before launch, freeze the amended protocol and file manifests. Validate actual request traces in both model configurations. Use fresh randomly generated markers in separate setup probes. For file or lookup runners, directly exercise permitted reads and rejected reads for the other arm, later commits, prior outputs, and grader files. Investigate any unexpected access before enrolling runs. Keep probe sessions separate from scored sessions.
- Running a new paid API or hosted environment needs budget authorization and a provisioned account. The offline check required neither. Keep grades and outputs sealed until collection ends, then preserve originals, contradictions and independent reviews as separate entries.

Related Future Farm research can proceed under its own evidence and contribution protocol. Keep new work outside the frozen pilot packet unless a new revision is deliberately selected before preregistration.

## Sources

- OpenAI, [Using tools](https://developers.openai.com/api/docs/guides/tools) and [Conversation state](https://developers.openai.com/api/docs/guides/conversation-state).
- ChatGPT Learn, [Codex configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference).
