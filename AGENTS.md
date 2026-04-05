# Repository Guidelines

## Project Structure & Module Organization
This repository stores source prompts and generated Anki card exports for Go study materials. Keep artifacts small and traceable.

- `LLM/`: prompt and workflow documents used to generate cards, such as `chatgpt-project-sources-2-cards.md`.
- `go/`: exported card decks in tab-separated format, currently `anki_go_cards.tsv`.
- `QWEN.md`: project context in Russian; update when the repository structure or workflow changes.
- `README.md`: minimal project entry point.

When adding a new subject, follow the existing pattern: create a subject folder like `python/` or `rust/` and store the deck export there.

## Build, Test, and Development Commands
There is no compiled application in this repository. Contributors mainly edit Markdown prompts and TSV exports.

- `git status`: check pending changes before editing.
- `sed -n '1,20p' go/anki_go_cards.tsv`: preview TSV structure and field order.
- `wc -l go/anki_go_cards.tsv`: count cards quickly.
- `rg -n "level_" go/anki_go_cards.tsv`: inspect tag consistency.

Use Anki's import UI to validate deck imports locally: separator `Tab`, fields `Front`, `Back`, `Tags`.

## Coding Style & Naming Conventions
Use Markdown for documentation and TSV for exports.

- Prefer concise, instructional prose.
- Keep filenames lowercase with hyphens or underscores, for example `anki_go_cards.tsv`.
- Preserve UTF-8 text when working with Russian content.
- In TSV files, keep the header row as `Front<TAB>Back<TAB>Tags`.
- Use normalized tags such as `go`, `anki_cards`, and `level_*`.

## Testing Guidelines
No automated test suite is configured. Validate contributions by checking:

- TSV opens cleanly and remains tab-delimited.
- Each card contains one idea and traceable source metadata.
- Tags are consistent across the deck.
- Imports succeed in Anki without field misalignment.

## Commit & Pull Request Guidelines
Recent history uses short, direct commit messages, often describing prompt revisions, for example `Add QWEN.md project context` or `FINAL PROMPT v10`.

- Write commit messages in the imperative mood and keep them specific.
- Group related prompt and deck changes in the same commit.
- In pull requests, include: purpose, affected files, whether card exports changed, and a short sample of added or modified cards.
- Add screenshots only when documenting Anki import behavior or formatting issues.
