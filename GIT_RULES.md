# Git Rules and Commit Standards

## Pre-commit Requirements

### 1. Git Add Confirmation Rule
**MANDATORY**: Before executing `git add`, must ask user for confirmation:
- List all modified files to be staged
- Ask user to confirm which files should be included
- Never automatically add all files without explicit user approval

```bash
# BAD: Never do this without asking
git add .
git add -A

# GOOD: Ask user first
echo "Modified files:"
git status --porcelain
echo "Which files should be staged? (Confirm before proceeding)"
```

### 2. One-Line Commit Rule
**MANDATORY**: All commits must use single-line format only:
```bash
# GOOD: Simple one-line commits
git commit -m "feat(auth): add JWT validation"
git commit -m "fix(api): resolve null pointer exception"
git commit -m "docs(readme): update installation guide"

# BAD: Multi-line commits not allowed
git commit -m "feat(auth): add JWT validation

This commit adds comprehensive JWT token validation
with proper error handling and security measures."
```

### 3. User Configuration Check
**MANDATORY**: Before first commit, verify Git user configuration:
```bash
# Check current configuration
git config --global user.name
git config --global user.email

# If not set, configure before any commits
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --list | grep user
```

### 4. Branch Naming Format
**MANDATORY**: All branches must follow `**/**` pattern:
```bash
# REQUIRED FORMAT: category/description
feature/user-authentication
fix/login-validation-error
hotfix/security-vulnerability
docs/api-documentation
refactor/database-optimization
test/unit-test-coverage

# BAD: Single word branches not allowed
authentication
bugfix
documentation
```

## Commit Message Convention

### Standard Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Commit Types
- **feat**: New feature for the user
- **fix**: Bug fix for the user
- **docs**: Documentation changes
- **style**: Code formatting, missing semicolons, etc (no code change)
- **refactor**: Code refactoring (no functional changes)
- **perf**: Performance improvements
- **test**: Adding or updating tests
- **chore**: Build process, auxiliary tools, libraries
- **ci**: CI/CD configuration changes
- **build**: Build system or external dependencies
- **revert**: Reverting previous commits

### Scope Examples
- **api**: API related changes
- **ui**: User interface changes
- **auth**: Authentication related
- **db**: Database changes
- **config**: Configuration changes
- **deps**: Dependencies updates

### Subject Guidelines
- Use imperative mood ("add" not "added" or "adds")
- Don't capitalize first letter
- No period at the end
- Maximum 50 characters
- Be concise but descriptive

### Body Guidelines
- Wrap at 72 characters
- Explain what and why, not how
- Use imperative mood
- Separate from subject with blank line

### Footer Guidelines
- Reference issues: "Closes #123", "Fixes #456"
- Breaking changes: "BREAKING CHANGE: description"
- Co-authored commits: "Co-authored-by: Name <email>"

## Commit Message Examples

### Good Examples
```bash
# Simple feature
feat(auth): add JWT token validation

# Bug fix with details
fix(api): resolve null pointer exception in user service

Handle case where user profile is not initialized before
accessing user properties. Add null checks and default
values to prevent application crashes.

Fixes #234

# Breaking change
feat(api): change user authentication flow

BREAKING CHANGE: Authentication now requires email verification
before account activation. Update client applications to handle
the new verification step.

# Documentation update
docs(readme): update installation instructions

Add Docker setup instructions and troubleshooting section
for common installation issues.

# Refactoring
refactor(utils): extract validation logic to separate module

Move email and phone validation functions to utils/validation.js
to improve code reusability and maintainability.
```

### Bad Examples
```bash
# Too vague
fix: bug fix

# Wrong tense
feat: added new feature

# Too long subject
feat(auth): implement comprehensive user authentication system with JWT tokens and refresh mechanism

# Missing type
update user profile component

# Unclear scope
fix(stuff): fix things
```

## Branch Naming Convention

### Mandatory Format: `**/**`
All branches MUST follow the double-star pattern with category and description:

### Branch Categories
- **feature/**: New features and enhancements
- **fix/**: Bug fixes and issue resolutions
- **hotfix/**: Critical production fixes
- **release/**: Release preparation branches
- **docs/**: Documentation updates and improvements
- **refactor/**: Code refactoring without functional changes
- **test/**: Test additions, updates, or improvements
- **chore/**: Maintenance tasks and tooling updates

### Naming Rules
- Use lowercase letters only
- Separate words with hyphens (kebab-case)
- Be descriptive but concise
- Include ticket ID when available

### Branch Name Examples
```bash
# CORRECT: Following **/** pattern
feature/user-profile-management
feature/PROJ-123-payment-integration
fix/login-validation-error
fix/PROJ-456-memory-leak-issue
hotfix/security-vulnerability-patch
docs/api-endpoint-documentation
refactor/database-query-optimization
test/unit-test-user-service
chore/update-dependencies

# INCORRECT: Single word or wrong format
authentication          # Missing category
user-profile            # Missing category
feature-auth            # Wrong separator
Feature/Auth            # Wrong case
feature/Auth_System     # Wrong case and separator
```

## Git Workflow Standards

### Pre-Development Setup (First Time Only)
```bash
# 1. MANDATORY: Verify user configuration
git config --global user.name
git config --global user.email

# 2. If not configured, set up user info
git config --global user.name "Your Full Name"
git config --global user.email "your.email@company.com"

# 3. Verify configuration is correct
git config --list | grep user
```

### Feature Development Flow
```bash
# 1. Create and switch to feature branch (MUST follow **/** pattern)
git checkout -b feature/user-profile-management

# 2. Make changes and check status
git status

# 3. MANDATORY: Ask user before staging files
echo "Modified files to be staged:"
git status --porcelain
echo "Confirm: Stage these files? (y/n)"
# Wait for user confirmation before proceeding

# 4. Stage confirmed files only
git add src/components/UserProfile.js
git add src/styles/profile.css

# 5. MANDATORY: One-line commit only
git commit -m "feat(profile): add user profile management interface"

# 6. Keep branch updated with main
git fetch origin
git rebase origin/main

# 7. Push feature branch
git push origin feature/user-profile-management

# 8. Create pull request
```

### Hotfix Flow
```bash
# 1. Verify user configuration first
git config --list | grep user

# 2. Create hotfix branch from main (MUST follow **/** pattern)
git checkout main
git pull origin main
git checkout -b hotfix/critical-security-patch

# 3. Make minimal fix and check status
git status

# 4. MANDATORY: Confirm files to stage
echo "Files to be staged for hotfix:"
git status --porcelain
echo "Confirm staging? (y/n)"

# 5. Stage confirmed files
git add src/security/validation.js

# 6. MANDATORY: One-line commit
git commit -m "fix(security): patch XSS vulnerability in user input"

# 7. Push and create urgent PR
git push origin hotfix/critical-security-patch
```

## Commit Best Practices

### Mandatory Pre-Commit Checklist
1. **User Configuration**: Verify `user.name` and `user.email` are set
2. **File Confirmation**: Ask user which files to stage before `git add`
3. **One-Line Commit**: Use only single-line commit messages
4. **Branch Format**: Ensure branch follows `**/**` pattern

### Atomic Commits with Confirmation
```bash
# 1. Check what files are modified
git status

# 2. MANDATORY: List and confirm files to stage
echo "Modified files:"
git diff --name-only
echo "Which files should be staged? Please confirm:"

# 3. Stage only confirmed files (never use git add .)
git add src/components/UserProfile.js
git add src/utils/validation.js

# 4. Review staged changes
git diff --staged

# 5. MANDATORY: One-line commit only
git commit -m "feat(profile): add user profile validation logic"

# FORBIDDEN: Multi-line commits
# git commit -m "feat(profile): add user profile validation
# 
# This commit adds comprehensive validation
# for user profile forms with error handling"
```

### File Staging Rules
```bash
# GOOD: Selective staging with user confirmation
git status
# Ask user: "Stage src/components/Header.js? (y/n)"
git add src/components/Header.js

# Ask user: "Stage src/styles/main.css? (y/n)"  
git add src/styles/main.css

# FORBIDDEN: Automatic staging without confirmation
git add .
git add -A
git add --all
```

### Commit Message Rules
```bash
# MANDATORY: Single line format only
git commit -m "type(scope): brief description"

# Examples of CORRECT one-line commits:
git commit -m "feat(auth): implement JWT token validation"
git commit -m "fix(api): resolve database connection timeout"
git commit -m "docs(readme): update installation instructions"
git commit -m "refactor(utils): optimize string manipulation functions"
git commit -m "test(user): add unit tests for user service"

# FORBIDDEN: Multi-line commits
git commit -m "feat(auth): implement authentication

This commit adds JWT token validation with proper
error handling and security measures."
```

## Git Hooks and Automation

### Pre-commit Hook with User Confirmation
```bash
#!/bin/sh
# .git/hooks/pre-commit

# 1. MANDATORY: Check user configuration
USER_NAME=$(git config user.name)
USER_EMAIL=$(git config user.email)

if [ -z "$USER_NAME" ] || [ -z "$USER_EMAIL" ]; then
  echo "ERROR: Git user configuration missing!"
  echo "Please set user.name and user.email:"
  echo "  git config --global user.name 'Your Name'"
  echo "  git config --global user.email 'your.email@example.com'"
  exit 1
fi

# 2. Check branch naming format (**/**)
BRANCH_NAME=$(git rev-parse --abbrev-ref HEAD)
if [ "$BRANCH_NAME" != "main" ] && [ "$BRANCH_NAME" != "master" ]; then
  if ! echo "$BRANCH_NAME" | grep -qE '^[a-z]+/[a-z0-9-]+$'; then
    echo "ERROR: Branch name must follow **/** pattern (e.g., feature/user-auth)"
    echo "Current branch: $BRANCH_NAME"
    exit 1
  fi
fi

# 3. Check commit message format (one-line only)
COMMIT_MSG_FILE=".git/COMMIT_EDITMSG"
if [ -f "$COMMIT_MSG_FILE" ]; then
  COMMIT_MSG=$(head -n 1 "$COMMIT_MSG_FILE")
  LINE_COUNT=$(wc -l < "$COMMIT_MSG_FILE")
  
  if [ "$LINE_COUNT" -gt 1 ]; then
    echo "ERROR: Only one-line commit messages allowed!"
    echo "Use format: type(scope): description"
    exit 1
  fi
  
  if ! echo "$COMMIT_MSG" | grep -qE '^(feat|fix|docs|style|refactor|perf|test|chore|ci|build|revert)(\(.+\))?: .{1,50}$'; then
    echo "ERROR: Invalid commit message format!"
    echo "Use: type(scope): description (max 50 chars)"
    echo "Your message: $COMMIT_MSG"
    exit 1
  fi
fi

# 4. Run linting
npm run lint
if [ $? -ne 0 ]; then
  echo "ERROR: Linting failed. Please fix errors before committing."
  exit 1
fi

# 5. Run tests
npm test
if [ $? -ne 0 ]; then
  echo "ERROR: Tests failed. Please fix tests before committing."
  exit 1
fi

echo "✓ Pre-commit checks passed"
```

### Commit Message Template (One-Line Only)
```bash
# ~/.gitmessage
# type(scope): description (max 50 characters)
# 
# Types: feat, fix, docs, style, refactor, perf, test, chore, ci, build, revert
# Scope: api, ui, auth, db, config, deps, etc.
# 
# Examples:
# feat(auth): add JWT token validation
# fix(api): resolve database connection timeout
# docs(readme): update installation guide
```

### Configure Git Template and Hooks
```bash
# Set commit message template
git config --global commit.template ~/.gitmessage

# Make pre-commit hook executable
chmod +x .git/hooks/pre-commit

# Verify user configuration
git config --global user.name "Your Full Name"
git config --global user.email "your.email@company.com"
```

## Repository Management

### .gitignore Best Practices
- Include language-specific ignores
- Add IDE and OS specific files
- Ignore build artifacts and dependencies
- Never commit sensitive information

### Tag Management
```bash
# Semantic versioning tags
git tag -a v1.0.0 -m "Release version 1.0.0"
git tag -a v1.0.1 -m "Patch release 1.0.1"
git tag -a v1.1.0 -m "Minor release 1.1.0"

# Push tags
git push origin --tags

# List tags
git tag -l

# Delete tag
git tag -d v1.0.0
git push origin :refs/tags/v1.0.0
```

### Branch Protection Rules
- Require pull request reviews
- Require status checks to pass
- Require branches to be up to date
- Restrict pushes to main branch
- Require signed commits (optional)

## Troubleshooting Common Issues

### Fixing Commit Messages
```bash
# Fix last commit message (not pushed)
git commit --amend -m "correct message"

# Fix older commit messages
git rebase -i HEAD~n
# Change 'pick' to 'reword' for commits to edit
```

### Undoing Changes
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert specific commit
git revert <commit-hash>
```

### Resolving Merge Conflicts
```bash
# During merge conflict
git status
# Edit conflicted files
git add <resolved-files>
git commit -m "resolve merge conflict in user authentication"
```

## Code Review Integration

### Pull Request Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No breaking changes (or documented)
```

### Review Guidelines
- Review code, not the person
- Focus on logic, security, and maintainability
- Suggest improvements, don't just point out problems
- Approve only when confident in the changes
- Use conventional comments: "nit:", "suggestion:", "question:"
