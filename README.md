# Team Identity Layer Template (TILT)

Use this repository as the starter Team Identity Layer. Identity Layers are Markdown bundles that define the AI’s persona, guardrails, and default context. This Team Identity Layer stands on its own as a deployable agent identity and can also be combined with a Personal Identity Layer to form a blended identity.

## Structure

| Index | File | Purpose |
|-------|------|---------|
| 00 | 00_CORE_{TILname}.md | Central system prompt: the non-negotiable instructions, values, and operating intent for this Team Identity Layer. |
| 01 | 01_INDEX_{TILname}.md | Routing table that explains when to load each identity file and what requirements gate it. |
| 02 | 02_TASKS_{TILname}.md | Repeatable procedures the team relies on; run them verbatim when triggers fire. |
| 03 | 03_SOURCES_{TILname}.md | Registry of preferred references and the allowed / disallowed lists to obey before researching. |
| 04-08 | None | Reserved for future templates. |
| 09 | 09_MEMORY.md | Optional shared memory log the AI creates when durable recall is needed. |
| 10 | 10_USER_{TILname}.md | User identification protocols and recognition cues when the user’s identity is uncertain. |
| 11 | 11_PEOPLE_{TILname}.md | Context profiles for users and any other relevant people. |
| 12 | 12_ORGANIZATION_{TILname}.md | Mission, values, and structure of the host organization. |
| 13 | 13_ENVIRONMENT_{TILname}.md | Tooling, communication channels, workflows, and constraints. |
| 14-18 | None | Reserved for future templates. |
| 19 | 19_GLOSSARY_{TILname}.md | Canonical definitions for team-specific language. |

## For Identity Maintainers

1. Fork or clone this repository and rename it for your team identity (for example `Jarvis`).
2. Replace `{TILname}` across filenames and file contents, then tailor every document to fit your team. Each heading or field is only a prompt, so reshape or delete anything that doesn’t serve you, and decide which identity files belong in this Team Identity Layer.
3. Keep all identity files directed at the AI and remove unused placeholders. Use this README for any human-facing notes.
4. Provide either an Allowed list or a Disallowed list in `03_SOURCES_{TILname}.md`; omit the unused section to avoid conflicts.
5. Slots 20–99 are available for additional identity files. For compatibility, avoid adding or renaming files in the 00–19 range.
6. Whenever you add, rename, retire, or relocate any identity file, whether in the core slots (00-19) or custom extensions (20-99), update `01_INDEX_{TILname}.md`, keep this README’s structure table in sync with the index, and ensure any cross-references in other files stay aligned.
7. Test the identity in your target interface(s) and iterate until the persona, tone, and guardrails behave as intended.
8. Version this Team Identity Layer (tags or branches) so composite identities can pull updates confidently.

## For Operators and End Users

1. Deploy this Team Identity Layer by placing `00_CORE_{TILname}.md` in the system prompt (or equivalent) and staging the supporting files wherever your interface expects them: file upload dialog, `.github/identity`, shared drive, etc.
2. Pair this team layer with a personal layer by appending the personal `00_CORE` file after the team `00_CORE` and staging all identity files from both layers.
3. For durable recall, ensure the deployment environment allows the AI to create `09_MEMORY.md`; the agent will generate and update the file when necessary.
