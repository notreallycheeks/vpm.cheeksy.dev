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

## Adding New Packages
When adding a new package to the VPM:
1. Create a release on the package's GitHub repo with a zip file
2. Add the package entry to `index.json` under `packages`
3. Update `index.html` to show the new package
