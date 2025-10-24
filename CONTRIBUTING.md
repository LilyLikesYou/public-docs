# Contributing Guide

Thank you for considering contributing to our project! This guide will help you understand how to contribute effectively.

## Ways to Contribute

There are many ways you can contribute:

- **Bug Reports**: Found a bug? Let us know!
- **Feature Requests**: Have an idea? Share it!
- **Documentation**: Improve or add to the docs
- **Code**: Fix bugs or implement features
- **Examples**: Create example projects
- **Community**: Help others in discussions

## Getting Started

### 1. Find Something to Work On

- Check the [issue tracker](https://github.com/your-org/your-software/issues)
- Look for issues labeled `good first issue` or `help wanted`
- Review the [project roadmap](https://github.com/your-org/your-software/projects)
- Or propose something new!

### 2. Set Up Your Development Environment

```bash
# Fork the repository on GitHub
# Clone your fork
git clone https://github.com/YOUR-USERNAME/your-software.git
cd your-software

# Add upstream remote
git remote add upstream https://github.com/your-org/your-software.git

# Install dependencies
npm install
# or
pip install -r requirements.txt

# Run tests to ensure everything works
npm test
# or
pytest
```

### 3. Create a Branch

Always create a new branch for your work:

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

Use clear, descriptive branch names:
- `feature/add-authentication`
- `fix/login-redirect-bug`
- `docs/update-api-reference`

## Making Changes

### Code Style

We follow standard coding conventions:

**For Python:**
- Follow PEP 8
- Use type hints
- Write docstrings for functions/classes
- Maximum line length: 88 characters

**For JavaScript/TypeScript:**
- Use ESLint with our config
- Use Prettier for formatting
- Write JSDoc comments
- Use TypeScript when possible

**For All Languages:**
- Write clear, self-documenting code
- Add comments for complex logic
- Keep functions small and focused
- Use meaningful variable names

### Writing Tests

All new features and bug fixes should include tests:

```python
# Python example
def test_new_feature():
    result = new_feature(input_data)
    assert result == expected_output
```

```javascript
// JavaScript example
describe('newFeature', () => {
  it('should return expected output', () => {
    const result = newFeature(inputData);
    expect(result).toBe(expectedOutput);
  });
});
```

### Documentation

Update documentation when you:
- Add a new feature
- Change existing behavior
- Fix a bug that was incorrectly documented

Documentation files are in Markdown format. Follow these guidelines:
- Use clear, concise language
- Include code examples
- Add screenshots when helpful
- Link to related pages

### Commit Messages

Write clear, meaningful commit messages:

```
Add user authentication feature

- Implement JWT token generation
- Add login and logout endpoints
- Include tests for auth flow
- Update API documentation

Fixes #123
```

Follow these rules:
- First line: Brief summary (50 chars or less)
- Blank line
- Detailed explanation if needed
- Reference related issues

## Submitting Changes

### 1. Push Your Changes

```bash
git push origin feature/your-feature-name
```

### 2. Open a Pull Request

1. Go to GitHub and open a pull request
2. Fill out the PR template completely
3. Link related issues (e.g., "Fixes #123")
4. Provide clear description of changes
5. Add screenshots for UI changes

### 3. Code Review

- Respond to review comments promptly
- Make requested changes in new commits
- Push updates to your branch
- Re-request review when ready

### 4. After Merge

```bash
# Update your local main branch
git checkout main
git pull upstream main

# Delete your feature branch
git branch -d feature/your-feature-name
```

## Pull Request Guidelines

A good pull request:

- **Solves one problem**: Don't combine multiple unrelated changes
- **Includes tests**: All new code should be tested
- **Updates documentation**: Keep docs in sync with code
- **Follows style guide**: Consistent with existing code
- **Has clear commits**: Logical, well-described commits
- **Passes CI checks**: All automated tests pass

## Reporting Bugs

### Before Reporting

1. Search existing issues to avoid duplicates
2. Try to reproduce on the latest version
3. Check if it's already fixed in `main` branch

### Creating a Bug Report

Include:

- **Clear title**: Describe the bug concisely
- **Description**: What happened vs. what you expected
- **Steps to reproduce**: Minimal steps to see the bug
- **Environment**: OS, version, browser, etc.
- **Screenshots**: If applicable
- **Error messages**: Copy full error messages
- **Code samples**: Minimal code to reproduce

Example:

```markdown
## Bug Description
Login fails with "Invalid credentials" even with correct password

## Steps to Reproduce
1. Go to login page
2. Enter email: user@example.com
3. Enter correct password
4. Click "Login"
5. See error message

## Expected Behavior
User should be logged in and redirected to dashboard

## Actual Behavior
Error message "Invalid credentials" appears

## Environment
- OS: macOS 12.0
- Browser: Chrome 96.0
- App Version: 1.2.3

## Error Logs
```
[ERROR] Authentication failed: user not found
```
```

## Proposing Features

### Before Proposing

1. Check if feature already exists or is planned
2. Search existing feature requests
3. Consider if it fits project goals

### Creating a Feature Request

Include:

- **Use case**: Why do you need this?
- **Description**: What should it do?
- **Examples**: Show how it would work
- **Alternatives**: Other solutions you considered
- **Willingness to help**: Can you implement it?

## Code Review Process

### For Contributors

- Be patient; reviews take time
- Respond constructively to feedback
- Don't take criticism personally
- Ask questions if unclear

### For Reviewers

- Be respectful and constructive
- Explain reasoning behind suggestions
- Acknowledge good work
- Focus on code, not the person

## Community Guidelines

We are committed to providing a welcoming and inclusive environment:

- **Be respectful**: Treat everyone with respect
- **Be constructive**: Provide helpful feedback
- **Be patient**: Remember everyone was a beginner once
- **Be open**: Consider different perspectives
- **Be collaborative**: Work together towards common goals

## Questions?

- **Chat**: Join our [Discord/Slack](https://chat.yourcompany.com)
- **Discussions**: Use [GitHub Discussions](https://github.com/your-org/your-software/discussions)
- **Email**: contribute@yourcompany.com

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.

---

Thank you for contributing! 🎉
