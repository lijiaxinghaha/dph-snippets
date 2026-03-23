# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**dph-snippets** is a VS Code extension that provides code snippets for Vue 3, TypeScript, and JSON development. The extension is published as a `.vsix` package.

## Architecture

The extension follows the standard VS Code extension structure:

- **package.json** - Extension manifest. The `contributes.snippets` section defines which snippet files are loaded for each language.
- **snippets/** - Contains JSON files with snippet definitions:
  - `vue.json` - Vue 3 Composition API snippets
  - `typescript.json` - TypeScript/TSX snippets (shared between `typescript` and `typescriptreact` languages)
  - `json.json` - JSON snippets

Snippets use VS Code's standard JSON snippet format with `prefix`, `body`, and `description` fields. The `body` can be a string or array of strings. Placeholders use `$1`, `$2`, etc. for tab stops and `$0` for final cursor position.

## Development

**Testing snippets locally:**
1. Open the project root in VS Code
2. Press `Ctrl+F5` (or `Cmd+Shift+D`) to launch the Extension Development Host
3. Open a file with the relevant language (`.vue`, `.ts`, `.tsx`, `.json`)
4. Type a snippet prefix to verify it's working

**Adding new snippets:**
1. Edit the appropriate JSON file in `snippets/`
2. Follow the existing format: `{ "Snippet Name": { "prefix": "...", "body": [...], "description": "..." } }`
3. Test in the Extension Development Host
4. Commit changes

**Publishing:**
Run `pnpm vsce publish` to package and publish to the VS Code Marketplace (requires authentication).

## Key Files

- `package.json` - Defines extension metadata and snippet contributions
- `.vscodeignore` - Files to exclude from the `.vsix` package (avoids shipping test files, node_modules, etc.)
