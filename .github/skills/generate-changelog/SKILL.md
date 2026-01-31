# Generate Changelog

## Description
Generates a changelog based on conventional commits. Analyzes git history to create or update CHANGELOG.md with categorized changes.

## When to Use This Skill
- Before deployment to update changelog
- When user asks to generate or update changelog
- Called by the deploy skill before releasing
- When preparing a new version release

## Prerequisites
- Git repository with conventional commits
- VERSION.txt file with current version
- Existing CHANGELOG.md (or will create one)

## Changelog Format
```markdown
# Changelog

## [X.Y.Z] - YYYY-MM-DD

### Features
- feat descriptions

### Bug Fixes  
- fix descriptions

### Documentation
- docs descriptions

### Other Changes
- other commit descriptions
```

## Step-by-Step Workflow

1. **Read Current Version**: Get version from VERSION.txt

2. **Get Recent Commits**: Fetch commits since last version tag (or all if no tags)
   ```bash
   git log --oneline
   ```

3. **Parse Commits**: Categorize by conventional commit type:
   - `feat` → Features
   - `fix` → Bug Fixes
   - `docs` → Documentation
   - `refactor`, `style`, `chore`, `perf`, `test`, `ci`, `build` → Other Changes

4. **Generate Entry**: Create markdown section for new version

5. **Update CHANGELOG.md**: Prepend new entry after the header

## Example Output

```markdown
# Changelog

## [1.1.0] - 2026-01-31

### Features
- Add dark mode toggle to settings
- Implement user profile page

### Bug Fixes
- Fix navigation menu on mobile
- Resolve authentication timeout

### Documentation
- Update README with new features
```

## Commit Parsing Rules

| Commit Type | Changelog Section |
|-------------|-------------------|
| feat | Features |
| fix | Bug Fixes |
| docs | Documentation |
| perf | Performance |
| refactor, style, chore, test, ci, build | Other Changes |

## Script Reference
The `scripts/generate-changelog.sh` script automates this process:
```bash
./scripts/generate-changelog.sh <new_version>
```

## References
- [Keep a Changelog](https://keepachangelog.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)

