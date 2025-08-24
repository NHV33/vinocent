# vinocent

ES5-compatible DOM & object utilities. Works in Node (CommonJS) and directly in the browser via a CDN script tag (attaches to `window.vinocent`). Published automatically with semantic-release.

## Install (Node)

```
npm install @vinocent/vinocent
```

```js
const { randInt, newElement } = require('@vinocent/vinocent');
console.log(randInt(1, 10));
```

## CDN (Browser Global)

Latest (not recommended for production pinning):
```html
<script src="https://unpkg.com/@vinocent/vinocent@latest/index.js"></script>
<script>
  const el = vinocent.newElement({ text: 'Hello', style: { color: 'red' } });
  console.log(vinocent.randInt(1, 5));
  document.body.append(el);
 </script>
```

Pinned version (recommended):
```html
<script src="https://cdn.jsdelivr.net/npm/@vinocent/vinocent@1.0.0/index.js"></script>
```

Global object: `window.vinocent`.

## Utilities (selection)
- DOM: `newElement`, `updateElement`, `toggleVisible`, `copyToClipboard`
- Objects/styles: `deepClone`, `updateObjProps`, `styleObjectToString`, `parseStyleString`
- Arrays/classes: `parseClassString`, `randItem`, `wrappedIndex`

## Semantic Release
Automated versioning & publishing based on Conventional Commits.

Conventional commit examples:
```
feat: add wrappedIndex helper
fix: handle empty style string in parseStyleString
chore: update README with CDN examples
```

Branch strategy:
- Stable releases from `main`
- Prereleases from `next` (tagged with prerelease identifiers)

### Releasing
1. Write commits using Conventional Commit messages.
2. Push to `main` (or open PR, merge).
3. GitHub Actions workflow runs semantic-release:
	- Determines new version.
	- Publishes to npm (requires `NPM_TOKEN` secret).
	- Creates GitHub release & changelog notes.

### Required Secrets
In the repository settings add:
- `NPM_TOKEN` (automation token with publish rights for the `@vinocent` scope)
(`GITHUB_TOKEN` is provided automatically by GitHub Actions.)

## Local Dry Run (optional)
```
npx semantic-release --dry-run
```
Requires setting env vars locally: `NPM_TOKEN` and `GITHUB_TOKEN` (a classic PAT with `repo` scope) for a full dry-run; otherwise it will warn.

## License
ISC
