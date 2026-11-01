# Repository Guidelines

## Project Structure & Content Organization

This repository is an Obsidian knowledge vault. The root `index.md` is the landing note. Keep notes in the topic directory that best fits their subject, such as `AWS/`, `Devops/`, `Linux/`, `System Design/`, `SRE/`, `Unity/`, `AI/`, and `Programming/`. Store Excalidraw-backed diagrams only in `Excalidraw/` as `*.excalidraw.md` files. The `.obsidian/` directory contains vault and plugin settings; do not change it unless the task specifically concerns Obsidian configuration.

## Development & Validation

There is no application build, package manager, or automated test suite. Review Markdown changes in Obsidian (or a Markdown preview) before committing: verify headings render correctly, internal links resolve, and code blocks are readable. For a quick repository check, use:

```sh
git status --short
git diff --check
```

`git diff --check` catches whitespace errors. The GitHub Actions workflow in `.github/workflows/update-vault-submodule.yml` updates the vault reference in the companion blog after pushes to `main`; contributors should not run it locally.

## Writing Style & Naming

Use Markdown with concise headings, short explanatory paragraphs, and numbered lists for sequences. Preserve existing YAML front matter when editing a note. Prefer descriptive, title-cased filenames that match nearby notes, for example `AWS/EC2/EC2 Basics.md` or `System Design/Shorten URL.md`. Keep related material in the existing note when it is a small addition; create a new note for a distinct concept. Use fenced code blocks with a language label when known.

## Review Checklist

Check factual accuracy, spelling, and link targets. Keep diagrams editable in their Excalidraw note rather than replacing them with exported images. Avoid committing incidental workspace changes under `.obsidian/`, such as `workspace.json`, `workspace-mobile.json`, file-recovery data, or personal plugin state.

## Commits & Pull Requests

Recent history uses short, plain-language messages, often prefixed `vault backup:` and followed by a brief summary (for example, `vault backup: update docs`). Use an imperative, scoped summary for intentional changes, such as `docs: expand EC2 storage notes`. Keep commits focused on one topic. Pull requests should state the notes changed, summarize substantive additions or corrections, link an issue when applicable, and include a screenshot only when a diagram or rendered layout changed.
