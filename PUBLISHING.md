# GitHub preparation

Upload the contents of this folder as your repository root. The original working folder has not been changed. No Git repository was initialized and nothing was pushed by this preparation.

## Included

- Application source, static image/SVG assets, and project configuration.
- `package.json` and `package-lock.json` for dependency installation.
- A credential-free `.env.example` and a `.gitignore`.
- English documentation, synthetic GeoJSON, and the optional CSV converter.

The npm package name was normalized to `histori-banjir`, and the lint command was changed to `eslint src` to use the existing ESLint configuration directly.

## Excluded

- `.env` and any actual tokens or local credentials.
- `node_modules`, `.next`, build output, caches, and logs.
- The original `.git` directory, including its remote, commit history, and author metadata.
- Raw datasets, original processed datasets with undocumented redistribution permission, and duplicate outputs.
- The old standalone HTML prototype, which embeds a Mapbox token.
- The old top-level lockfile and `to_csv.py`, whose required input file was not supplied.

The original standalone prototype contains a public Mapbox token. Check ownership and restrictions before reusing it; this package does not copy that value. Never publish private/secret tokens.

## Before a public upload

1. Read README.md and DATA_NOTES.md; keep the synthetic data unless you have permission to publish real data.
2. Confirm attribution and permission for the inherited application code and static assets. Do not add a license on behalf of another author.
3. Configure your own public Mapbox token in `.env.local` for local use.
4. Install dependencies, run lint/build, address reported problems, and review dependency security before deployment.
5. Inspect exactly what Git will publish.

```bash
git init
git add .
git status --short
git diff --cached --stat
git diff --cached
```

Confirm that no real `.env` files, credentials, private data, dependency directories, build output, or unintended dataset replacements are staged. Then create the initial commit and connect your own GitHub repository:

```bash
git commit -m "Prepare flood history map project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

Choose private repository visibility while provenance or publication permission remains unresolved. Keep `.gitignore`, `.env.example`, and the other dotfiles when uploading through the GitHub website.

## Preparation checks

- 46 packaged files, approximately 4.7 MB, before this validation note.
- All packaged JSON and GeoJSON parsed successfully.
- Common Mapbox/GitHub/AWS token patterns and private-key headers were scanned; no matches were found. This is a limited pattern scan, not proof that every possible sensitive value is absent.
- No original `.git`, `.env`, `node_modules`, or `.next` directory was copied.
- ESLint was run against the original source using its installed dependencies. The copied `src` files are unchanged: **10 errors and 9 warnings** remain, including explicit `any` types, `prefer-const`, an unused expression, hook dependency warnings, and image-element warnings.
- A production build and browser interaction were not tested. This preparation is a repository packaging task, not a repair or deployment of the application.
