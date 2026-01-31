# Conventional Commit

## Description
Creates conventional commit messages and commits changes to git. Use when committing code changes, following conventional commit standards, or preparing commits with proper formatting.

## When to Use This Skill
- User asks to commit changes
- When preparing a commit with proper conventional format
- For projects requiring standardized commit messages
- When the user mentions "commit", "conventional commits", or "git commit"
- When the user says "let's commit this" or "merge this"

## Prerequisites
- Git repository initialized
- Changes staged or ready to commit
- Understanding of conventional commit types (feat, fix, docs, etc.)

## Conventional Commit Format
```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

## Commit Types
- **feat**: A new feature (correlates with MINOR in semver)
- **fix**: A bug fix (correlates with PATCH in semver)
- **docs**: Documentation only changes
- **style**: Changes that do not affect the meaning of the code
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **perf**: A code change that improves performance
- **test**: Adding missing tests or correcting existing tests
- **chore**: Changes to the build process or auxiliary tools
- **ci**: Changes to CI configuration files and scripts
- **build**: Changes that affect the build system or external dependencies

## Breaking Changes
- Add `!` after the type/scope: `feat!: breaking change`
- Or add `BREAKING CHANGE:` in the footer
- Breaking changes correlate with MAJOR in semver

## Step-by-Step Workflow

1. **Analyze Changes**: Review staged/unstaged changes using `git status` and `git diff`

2. **Determine Commit Type**: Based on the changes, select the appropriate type:
   - New functionality → `feat`
   - Bug fix → `fix`
   - Documentation → `docs`
   - Code cleanup → `refactor`
   - etc.

3. **Identify Scope** (optional): Determine the area of the codebase affected (e.g., `auth`, `ui`, `api`)

4. **Write Description**: Create a concise, imperative description (e.g., "add login button" not "added login button")

5. **Stage Changes**: 
   ```bash
   git add <files>
   # or
   git add .
   ```

6. **Create Commit**:
   ```bash
   git commit -m "<type>(<scope>): <description>"
   ```

## Examples

### Feature commit
```bash
git commit -m "feat(ui): add dark mode toggle to settings"
```

### Bug fix commit
```bash
git commit -m "fix(auth): resolve token expiration issue"
```

### Documentation commit
```bash
git commit -m "docs: update README with installation instructions"
```

### Breaking change commit
```bash
git commit -m "feat(api)!: change authentication endpoint response format

BREAKING CHANGE: The /auth/login endpoint now returns a different JSON structure"
```

## Validation Rules
- Type must be lowercase
- Description must not end with a period
- Description should be imperative mood ("add" not "added")
- First line should be under 72 characters

## References
- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Angular Commit Guidelines](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#commit)

