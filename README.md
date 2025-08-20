# Code Generator — VS Code Extension

Useful code snippets for JavaScript, TypeScript, React, Bootstrap, and Data Structures & Algorithms.

## Features

-   **JavaScript/TypeScript**

    -   Modern JS utilities
    -   React components and hooks
    -   TS types and interfaces

-   **Bootstrap**

    -   Common components
    -   Layout utilities
    -   Init templates

-   **DSA**

    -   C and C++ implementations
    -   Core data structures and algorithms

## Installation

### From Marketplace

1. Open VS Code.
2. `Ctrl+P` / `Cmd+P` → `ext install code-gen`.

### From a local `.vsix`

See **Build & Install from VSIX** below.

## Usage

1. Open a supported file: `.js`, `.ts`, `.jsx`, `.tsx`, `.c`, `.cpp`.
2. Start typing a snippet prefix.
3. Pick from IntelliSense.

## Available Snippets

### JavaScript/TypeScript

-   React function components
-   Custom hooks
-   Utilities
-   TS types and interfaces

### Bootstrap

-   Grid layouts
-   Components
-   Utilities
-   Responsive patterns

### DSA

-   LinkedList, Stack, Queue, …
-   Sorting and searching
-   Trees

## Build & Install from VSIX

### Prerequisites

-   Node.js 18+ and npm
-   A valid `package.json` with:

    -   `"name"`, `"displayName"`, `"version"`
    -   `"publisher"` (any string you own; required even for local packaging)
    -   `"engines": { "vscode": "^1.xx.0" }`
    -   `"categories": ["Snippets"]`
    -   `"contributes.snippets"` pointing to your snippet files

Example:

```json
{
	"name": "code-gen",
	"displayName": "Code Generator",
	"publisher": "your-publisher-id",
	"version": "0.0.1",
	"engines": { "vscode": "^1.92.0" },
	"categories": ["Snippets"],
	"contributes": {
		"snippets": [
			{ "language": "javascript", "path": "./snippets/js.json" },
			{ "language": "typescript", "path": "./snippets/ts.json" },
			{ "language": "javascriptreact", "path": "./snippets/react.json" },
			{ "language": "typescriptreact", "path": "./snippets/react-ts.json" },
			{ "language": "c", "path": "./snippets/c.json" },
			{ "language": "cpp", "path": "./snippets/cpp.json" }
		]
	}
}
```

Optional `.vscodeignore` to shrink the package:

```
**/.git/**
**/.github/**
**/node_modules/**
**/.husky/**
**/*.test.*
**/tests/**
.vscode/
.vscode/**
.DS_Store
```

### Package

Use `vsce` (official packager):

```bash
# One-off without global install
npx @vscode/vsce package

# or install globally
npm i -g @vscode/vsce
vsce package

# optional pre-release
vsce package --pre-release
```

This generates `code-gen-0.0.1.vsix` in the project root.

### Install the VSIX

```bash
# Using VS Code CLI
code --install-extension code-gen-0.0.1.vsix

# Or via UI: Extensions panel → … menu → Install from VSIX…
```

### Publish to Marketplace (optional)

```bash
# Create a publisher once
npx @vscode/vsce create-publisher your-publisher-id

# Acquire a Personal Access Token (Azure DevOps)
# Then:
npx @vscode/vsce login your-publisher-id
npx @vscode/vsce publish
# or pre-release
npx @vscode/vsce publish --pre-release
```

## Contributing

1. Fork the repo.
2. Create a branch: `git checkout -b feat/amazing-feature`.
3. Commit: `git commit -m "feat: add amazing feature"`.
4. Push: `git push origin feat/amazing-feature`.
5. Open a Pull Request.

## Release Notes

### 0.0.1

-   Initial snippets for JS, TS, React, Bootstrap, and DSA.

## License

MIT. See [LICENSE](LICENSE).

## Author

Lê Đức Anh - ldanh270
