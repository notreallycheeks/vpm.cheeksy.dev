# Claude Instructions for vpm.cheeksy.dev

## Identity
This repository belongs to the **cheeks** anonymous identity. Do not include any real name references.

## Git Commit Rules

**CRITICAL: Do NOT include any of the following in commits:**
- Co-Authored-By lines mentioning Claude, Anthropic, or any AI
- Commit messages mentioning Claude, AI assistance, or Anthropic
- Any attribution to AI tools in commit messages or bodies

**Commit style:**
- Keep commit messages concise and descriptive
- Focus on what changed, not how it was made
- Use conventional commit style when appropriate

## SSH Configuration
Use the cheeks SSH key for git operations:
- Remote should use `github.com-cheeks` host
- Example: `git@github.com-cheeks:notreallycheeks/vpm.cheeksy.dev.git`

## VPM Repository Structure
- `index.json` - VPM manifest listing all packages
- `index.html` - Landing page for browser visitors
- `CNAME` - GitHub Pages custom domain configuration

**This repo is the canonical listing** (`https://vpm.cheeksy.dev/index.json`).
A byte-identical copy of `index.json` is kept at
`notreallycheeks.github.io/vpm/index.json` because `https://cheeksy.dev/vpm/index.json`
has also been live and may be in someone's VCC — keep the two files in sync whenever
this one changes. The human-facing landing page is `cheeksy.dev/vpm/` in the
`notreallycheeks.github.io` repo; update its package list too.

## Adding New Packages / Versions
1. In the package's repo, commit the package folder (the directory containing
   `package.json`, with all `.meta` files), then build the zip from the committed
   tree so nothing stray gets in:
   `git archive --format=zip -o dev.cheeksy.PKG-X.Y.Z.zip HEAD:path/to/PackageFolder`
   (package.json must end up at the ZIP ROOT.)
2. `sha256sum` the zip.
3. `gh release create vX.Y.Z <zip>` on that repo (gh active account must be
   `notreallycheeks` — check `gh auth status`).
4. Add the version entry to `index.json` here: `url` = the release asset's
   `releases/download/vX.Y.Z/<file>.zip` URL, `zipSHA256` = the hash (lowercase hex).
5. Update `index.html` here, mirror `index.json` to the site copy, and update the
   package list in `notreallycheeks.github.io/vpm/index.html`.
6. Commit + push both repos (GitHub Pages redeploys automatically).
