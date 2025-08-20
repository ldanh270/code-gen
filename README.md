# Code Generator — VS Code Extension

Developer docs. Build, test, ship.

## 1. Requirements

-   Node.js 18+
-   VS Code 1.92+
-   `vsce` via `npx`

## 2. Repo structure

```
.
├─ package.json
├─ README.md
├─ CHANGELOG.md
├─ LICENSE
├─ .vscodeignore
└─ snippets/
   ├─ js.json
   ├─ ts.json
   ├─ react.json
   ├─ react-ts.json
   ├─ c.json
   └─ cpp.json
```

## 3. Minimal `package.json`

```json
{
	"name": "code-gen",
	"displayName": "Code Generator",
	"publisher": "your-publisher-id",
	"version": "1.0.0",
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
	},
	"scripts": {
		"dev": "code --extensionDevelopmentPath=$(pwd)",
		"package": "npx @vscode/vsce package",
		"package:pre": "npx @vscode/vsce package --pre-release",
		"publish": "npx @vscode/vsce publish",
		"publish:pre": "npx @vscode/vsce publish --pre-release",
		"lint": "node ./scripts/validate-snippets.mjs"
	}
}
```

## 4. `.vscodeignore`

```
**/.git/**
**/.github/**
**/node_modules/**
**/.husky/**
**/*.test.*
**/tests/**
.vscode/
.DS_Store
scripts/
```

## 5. Snippet conventions

-   Prefix: short and consistent (`rfc`, `rhook`, `bs-grid`, `dsa-ll`).
-   Scope: bind to exact languages.
-   Placeholders: `${1:name}`, `${2:type}`; choices when needed.
-   Descriptions: concise. Avoid unused imports.

Example:

```json
{
	"React Function Component": {
		"scope": "typescriptreact, javascriptreact",
		"prefix": "rfc",
		"body": [
			"import React from 'react';",
			"",
			"type ${1:Props} = {",
			"  ${2:// props}",
			"};",
			"",
			"export default function ${3:Component}(${4:props}: ${1:Props}) {",
			"  return (",
			"    <div>${5}</div>",
			"  );",
			"}"
		],
		"description": "React function component (TS/JS)"
	}
}
```

## 6. Run in Extension Development Host

-   Open folder in VS Code.
-   Press `F5`.
-   Create `.js/.ts/.tsx/.c/.cpp` file and test prefixes.

## 7. Build a `.vsix`

```bash
npx @vscode/vsce package
# pre-release
npx @vscode/vsce package --pre-release
```

Output: `code-gen-1.0.0.vsix`.

## 8. Install the `.vsix`

```bash
code --install-extension code-gen-1.0.0.vsix
```

Or: Extensions panel → `…` → Install from VSIX.

## 9. Publish to Marketplace (optional)

```bash
npx @vscode/vsce create-publisher your-publisher-id   # once
npx @vscode/vsce login your-publisher-id              # Azure DevOps PAT
npx @vscode/vsce publish                              # stable
npx @vscode/vsce publish --pre-release                # pre
```

## 10. PR workflow

1. Branch: `feat/<slug>` or `fix/<slug>`.
2. Add snippet + description.
3. `npm run lint`.
4. Test with F5.
5. Update `CHANGELOG.md`.
6. Open PR with GIF or screenshot.

## 11. Versioning

-   `MAJOR.MINOR.PATCH`
-   New snippets → MINOR
-   Fixes → PATCH
-   Prefix changes → MAJOR

## 12. Release notes

### 1.0.0

-   Graduation to stable.
-   Documentation and packaging clarified.
-   VSIX build and install steps added to README.

_(Add concrete Added/Changed/Removed/Breaking bullets here as applicable.)_

## 13. Troubleshooting

-   Install fails → check `engines.vscode`.
-   Snippet missing → verify `scope` and file extension.
-   Large VSIX → tighten `.vscodeignore`.

## 14. License

MIT. See `LICENSE`.

## 15. Author

Le Duc Anh.
