# Deploy

## Description
Deploys the site to GitHub Pages with automatic version calculation and changelog generation. Handles the complete release workflow.

## When to Use This Skill
- User says "deploy", "let's deploy", or "push to production"
- When releasing a new version
- After features are complete and ready for release

## Prerequisites
- All changes committed with conventional commits
- Clean working directory (no uncommitted changes)
- GitHub repository configured with Pages

## Version Calculation (Semantic Versioning)

Based on conventional commits since last version:
- **MAJOR** (X.0.0): Breaking changes (`feat!:`, `fix!:`, `BREAKING CHANGE:`)
- **MINOR** (x.Y.0): New features (`feat:`)
- **PATCH** (x.y.Z): Bug fixes, docs, refactors (`fix:`, `docs:`, `refactor:`, etc.)

## Step-by-Step Workflow

1. **Check Prerequisites**
   ```bash
   git status  # Ensure clean working directory
   ```

2. **Read Current Version**
   ```bash
   cat VERSION.txt
   ```

3. **Analyze Commits for Version Bump**
   ```bash
   git log --oneline  # Review commits since last version
   ```

4. **Calculate New Version**
   - Parse commit types
   - Determine version bump type (major/minor/patch)
   - Calculate new version number

5. **Update VERSION.txt**
   ```bash
   echo "X.Y.Z" > VERSION.txt
   ```

6. **Generate Changelog** (uses generate-changelog skill)
   - Parse commits
   - Update CHANGELOG.md with new version entry

7. **Commit Version Bump**
   ```bash
   git add VERSION.txt CHANGELOG.md
   git commit -m "chore(release): bump version to X.Y.Z"
   ```

8. **Push to Trigger Deployment**
   ```bash
   git push origin main
   ```

9. **Verify Deployment**
   - GitHub Actions will automatically deploy
   - Check https://sgoettschMSCS.github.io after a few minutes

## Version Bump Examples

| Commits Since Last Version | Version Change |
|---------------------------|----------------|
| `feat: add login` | 1.0.0 → 1.1.0 |
| `fix: resolve bug` | 1.0.0 → 1.0.1 |
| `feat!: breaking change` | 1.0.0 → 2.0.0 |
| `docs: update readme` | 1.0.0 → 1.0.1 |
| `feat: add login`, `fix: bug` | 1.0.0 → 1.1.0 |

## Deployment Verification Checklist
- [ ] VERSION.txt updated
- [ ] CHANGELOG.md updated
- [ ] Changes pushed to main
- [ ] GitHub Actions workflow completed
- [ ] Site accessible at GitHub Pages URL

## References
- [Semantic Versioning](https://semver.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

