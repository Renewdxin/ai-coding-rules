# Contributing to AI Coding Rules

Thank you for your interest in contributing to the AI Coding Rules project! This document will guide you on how to contribute to the project.

## 🚀 Getting Started

### 1. Fork the Repository
Click the "Fork" button in the top right corner of the GitHub page to fork the repository to your account.

### 2. Clone the Repository
```bash
git clone git@github.com:your-username/ai-coding-rules.git
cd ai-coding-rules
```

### 3. Create a Branch
```bash
# Must follow **/** format
git checkout -b feature/your-feature-name
git checkout -b fix/bug-description
git checkout -b docs/documentation-update
```

## 📋 Types of Contributions

### Rule Improvements
- Enhance descriptions and examples of existing rules
- Add new programming standards and best practices
- Fix errors or inaccuracies in rules

### New Rule Additions
- Add specialized rules for specific tech stacks
- Introduce new development scenario standards
- Supplement missing tools and patterns

### Documentation Optimization
- Improve README and usage instructions
- Add more usage examples
- Enhance structure and formatting of rule documentation

### Bug Fixes
- Fix logical errors in rules
- Correct issues in code examples
- Improve readability and comprehension of rules

## 🔧 Development Standards

### Commit Standards
Strictly follow the project's Git rules:

```bash
# Verify user configuration before committing
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Branch naming must use **/** format
git checkout -b feature/add-react-rules

# Confirm files before staging
git status
# Ask user for confirmation before executing
git add specific-files

# One-line commits only
git commit -m "feat(rules): add React development guidelines"
```

### Code Quality
- All rule documentation written in English
- Maintain consistent document format and structure
- Provide clear code examples
- Ensure practicality and operability of rules

### Documentation Standards
- Use Markdown format
- Maintain clear hierarchical structure
- Add appropriate code blocks and examples
- Include necessary explanations and descriptions

## 📝 Pull Request Process

### 1. Create Pull Request
- Provide clear PR title and description
- Explain the reason and impact of changes
- List all modified files

### 2. PR Template
```markdown
## Description
Brief description of your changes

## Type of Change
- [ ] New rule addition
- [ ] Rule improvement
- [ ] Bug fix
- [ ] Documentation update

## Testing
- [ ] Verified rule practicality
- [ ] Checked document formatting
- [ ] Confirmed code examples are correct

## Checklist
- [ ] Follows project Git commit standards
- [ ] Consistent document formatting
- [ ] Accurate code examples
- [ ] No spelling or grammar errors
```

### 3. Code Review
- Respond to reviewer feedback
- Fix identified issues promptly
- Maintain friendly and professional communication

## 🎯 Rule Writing Guidelines

### Rule Structure
```markdown
# Rule Category

## Rule Name
Brief description of the rule

### Why This Rule
Explanation of the reasoning behind the rule

### How to Apply
Step-by-step implementation guide

### Examples
```javascript
// Good example
const goodCode = "example";

// Bad example
const badCode = "counter-example";
```

### Common Mistakes
List of common violations and how to avoid them
```

### Quality Standards
- **Clarity**: Rules should be easy to understand and implement
- **Practicality**: Rules should solve real development problems
- **Completeness**: Provide sufficient examples and explanations
- **Consistency**: Maintain consistency with overall project style

## 🐛 Issue Reporting

### Creating Issues
If you find problems or have improvement suggestions, please create an Issue:

1. Use clear title to describe the problem
2. Provide detailed problem description
3. Include reproduction steps (if applicable)
4. Suggest possible solutions

### Issue Template
```markdown
## Problem Description
Clearly describe the encountered problem

## Expected Behavior
Describe the expected correct behavior

## Actual Behavior
Describe what actually happened

## Reproduction Steps
1. Step one
2. Step two
3. Step three

## Suggested Solution
If you have ideas, please share your suggestions
```

## 📞 Contact

If you have any questions or need help, please contact us through:

- Create GitHub Issue
- Leave comments in Pull Request
- Communicate through project discussion area

## 🙏 Acknowledgments

Thanks to all developers who have contributed to the AI Coding Rules project! Your contributions make this project better.

---

Thank you again for your contribution! Let's build better AI-assisted development standards together.
