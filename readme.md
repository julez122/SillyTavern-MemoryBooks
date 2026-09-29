

# 📕 Memory Books

Memory Books is a SillyTavern extension for creating and managing long-term chat memory. It turns completed scenes or automatically selected portions of a chat into structured, editable lorebook entries that preserve important events, decisions, relationships, discoveries, promises, and unresolved threads.

As your chat grows, older messages can be hidden from the active context while their important information remains available through the Memory Book. You keep a durable record of what actually happened without carrying the entire raw conversation inside every new request.

Use Memory Books manually when you want precise control over scene boundaries, or automate the process and let it create memories as the chat continues.

## Local modification: neutral relationship reports

This copy modifies upstream 9.2.3's **Status** Side Prompt. It describes any relationship using established facts, each participant's perspective, changes and evidence, trust/boundaries/communication, goals, and unresolved questions. It has no attraction factors or numerical relationship ladder, and does not suggest future plot developments. Romance or sexuality is included only when established in the supplied story. Other Memory Books features are unchanged.

Both **Prompt** and **Response Format** are updated, including the translated defaults and downloadable Side Prompt packs. Existing saved copies of recognized upstream wording are migrated without resetting their names, enabled state, triggers, profiles, lorebook settings, or set references. Exact known sections can be replaced within a customized format. Unrecognized legacy wording is preserved and marked **Review relationship instructions** in the tracker list and editor; inspect both fields before using such a custom tracker.

Before migrating saved wording, the extension saves a complete recovery copy to your SillyTavern user files as `stmb-side-prompts-before-neutral-status-<timestamp>-<id>.json`. Backup filenames appear under `relationshipPromptBackups` in a Side Prompts JSON export. If backup or save fails, migration stops; it does not reset your prompts. These copies contain your saved prompt configuration and should be kept private. To recover custom text, copy the relevant original fields from the backup into the editor. Importing a backup is additive and runs migration again; it is not a rollback command.

Install the patched extension files, including **index.build.js**, then reload SillyTavern. Keep a copy of this modified folder; an upstream extension update may overwrite the local patch. Do not use **Recreate Built-in Side Prompts** for this update, because it resets every built-in tracker's settings. Stop old pending jobs and start a new run: queued requests retain their original assembled prompt, including on retry. Existing reports and regeneration/rollback history are preserved. The new instructions correct unsupported interpretations during future updates, but cannot automatically repair every inaccurate claim already saved in a lorebook; review old reports and regenerate from the relevant original scene where needed.

Developer commands (from this folder): `node bin/update-relationship-prompts.js` synchronizes neutral translations/packs and the legacy recognition hashes; `node --experimental-vm-modules --test` runs tests; `bun run build.ts` rebuilds the files loaded by SillyTavern. Historical wording exists only in migration recognition and regression fixtures, not in active generation defaults. See [CONTEXT.md](CONTEXT.md) for patch architecture and verification status.

> **Not sure how AI memory actually works?**
> Read [How Memory Works in SillyTavern](https://www.hanasaki.ai/ref/stmemory.html) for a plain-language explanation of chat history, summaries, lorebooks, vector retrieval, trackers, and where Memory Books fits.

## 📖 Learn Memory Books

STMB has a lot of features, and its documentation became too large to navigate comfortably as a traditional README. Choose whichever guide option works best for you. 

### Quickstart

Just want to get STMB up and running? [Start here.](./Start_Here.md)

### AI Reference Manual

Download the [Memory Books AI Reference Manual](userguides/1%20Memory_Books_AI_Reference_Manual.md), upload it to your preferred assistant, and ask it questions about Memory Books.

## Copyright and License

SillyTavern Memory Books is Copyright © 2024–2026 Aiko Hanasaki.

The original code in this repository is licensed under the GNU Affero General Public License v3.0. Modified versions and forks must preserve applicable copyright and license notices, identify their modifications, and comply with the AGPL's source-availability requirements. 

See [LICENSE](./LICENSE).
