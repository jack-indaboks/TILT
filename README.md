# Team Identity Layer Template (TILT)

Use this repository as the starter Team Identity Layer. Identity Layers are Markdown bundles that define the AI’s persona, guardrails, and default context. This Team Identity Layer stands on its own as a deployable agent identity and can also be combined with a Personal Identity Layer to form a blended identity.

## Structure

| Range | Category | Purpose |
|-------|----------|---------|
| 00 | `00_CORE_{TILname}.md` | Central system prompt with the team’s non-negotiable instructions, values, and operating intent. |
| 01 | `01_INDEX_{TILname}.md` | Routing guide that tells the agent when to load each identity file and what prerequisites apply. |
| 02 | `02_TASKS_{TILname}.md` | Repeatable procedures the team relies on; the agent runs them verbatim when triggers fire. |
| 03 | `03_SOURCES_{TILname}.md` | Registry of preferred references plus the allowed and disallowed lists that govern research. |
| 04-08 | Reserved | Future core template slots shared across team identity layers. |
| 09 | `09_MEMORY.md` | Optional shared memory log the agent creates only when the deployment supports file writes. |
| 10 | `10_USER_{TILname}.md` | User identification protocols and recognition cues for ambiguous interactions. |
| 11 | `11_PEOPLE_{TILname}.md` | Context profiles for team members, stakeholders, and other relevant people. |
| 12 | `12_ORGANIZATION_{TILname}.md` | Mission, values, and structure of the host organization. |
| 13 | `13_ENVIRONMENT_{TILname}.md` | Tooling, communication channels, workflows, and operating constraints. |
| 14-18 | Reserved | Future shared template slots. |
| 19 | `19_GLOSSARY_{TILname}.md` | Canonical definitions for team-specific language and shorthand. |
| 20-99 | Custom extensions | Additional identity files your team creates to extend the layer. |

## For Identity Maintainers

1. Fork or clone this repository and rename it for your team identity (for example `Jarvis`).
2. Replace `{TILname}` across filenames and file contents, then tailor every document to fit your team. Each heading or field is only a prompt, so reshape or delete anything that doesn’t serve you, and decide which identity files belong in this Team Identity Layer.
3. Keep all identity files directed at the AI and remove unused placeholders. Use this README for any human-facing notes.
4. Provide either an Allowed list or a Disallowed list in `03_SOURCES_{TILname}.md`; omit the unused section to avoid conflicts.
5. Slots 20–99 are available for additional identity files. For compatibility, avoid adding or renaming files in the 00–19 range.
6. Name every file in the 20–99 range using `NN_{TILname}_FileName.md`; hyphens are allowed inside `FileName` as needed. Consider reserving each band’s `N0` slot, such as 20 or 30 or 40, for the overview or template governing that category.
7. Whenever you add, rename, retire, or relocate any identity file, whether in the core slots (00-19) or custom extensions (20-99), update `01_INDEX_{TILname}.md`, keep this README’s structure table in sync with the index, and ensure any cross-references in other files stay aligned.
8. Test the identity in your target interface(s) and iterate until the persona, tone, and guardrails behave as intended.
9. Version this Team Identity Layer (tags or branches) so composite identities can pull updates confidently.

## For Operators and End Users

1. Paste `00_CORE_{TILname}.md` at the top of the system prompt (or equivalent) so the team directives load first; if you are running a blended stack, paste the personal core immediately afterward.
2. Upload or stage the supporting identity files:
    - Simple file-upload interfaces (for example, ChatGPT or Anthropic Workbench): attach every remaining team identity file (include personal files when blending), treat the uploaded copies as read-only, re-uploading any modified files as they are changed in this source repository.
    - Directory-based workflows (for example, GitHub Copilot repositories): place the team bundle inside `.github/1_{TILname}/` and any paired personal layer inside `.github/2_{PILname}/`; keep Markdown links intact because the agent depends on them to traverse the identity files.
3. For durable and/or portable memory, ensure the deployment environment allows the AI to create `09_MEMORY.md`; the agent will generate and update the file when necessary.
