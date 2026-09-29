# Repository Guidelines

## Project Structure & Module Organization

This repository is a Korean-language, browser-only task calendar. `index.html` contains all HTML, CSS, and JavaScript: calendar rendering, task management, persistence, and the fixed top-right theme toggle. `index.backup.html` is a historical backup; do not update it alongside ordinary feature changes. There are no separate source, asset, or test directories, package dependencies, or backend services.

The link to `../about/about.html` targets a sibling project outside this repository. Check its availability when deploying.

## Build, Test, and Development Commands

No build or dependency installation is required. Open `index.html` directly in a modern browser. Alternatively, with Python installed, run `python -m http.server 8000 --bind 127.0.0.1` from the repository and visit `http://localhost:8000`.

Use `git diff --check` to detect whitespace errors and `git diff -- index.html` to review application changes. There is no configured `npm test`, formatter, linter, or CI pipeline.

## Coding Style & Naming Conventions

Preserve UTF-8 encoding and Korean interface text. Use vanilla JavaScript, `const` or `let`, single-quoted strings, and semicolons. Prefer camelCase identifiers and descriptive lowercase hyphenated CSS names, such as `theme-toggle`. For new multiline code, use two-space indentation; avoid reformatting unrelated compact code.

Render user-entered task text with `textContent`. Preserve accessible labels, keyboard focus indicators, `aria-pressed`, and reduced-motion support.

## Testing Guidelines

No automated framework, coverage threshold, or test-file naming convention exists. Manually verify task creation with Enter and `+`, completion toggling, individual and monthly deletion, month navigation, and summary counts. Use disposable tasks for deletion checks.

Verify both themes, reload persistence, keyboard operation, Korean text composition, and narrow-screen horizontal scrolling. Check the browser console for errors. Report actual checks and any unverified behavior in the PR.

## Storage & Configuration

Keep `todo-calendar-v1` for task data and `todo-calendar-theme` for `dark` or `light`. Preserve existing data compatibility and storage-error handling. Browser storage is origin-specific; file and HTTP previews may show different data. Never commit credentials or personal task exports.

## Commit & Pull Request Guidelines

History uses concise descriptive messages in English and Korean, including `다크모드 업그레이드`; no mandatory prefix convention exists. Keep commits focused. PRs should explain behavior changes, list verification performed, link relevant issues, and include screenshots for visual changes. Preserve unrelated working-tree changes.
