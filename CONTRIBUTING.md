# Contributing to PromptTrace

Thank you for your interest in contributing to PromptTrace! We welcome contributions from security researchers, forensic analysts, and developers.

## Code of Conduct

- Be respectful and professional
- Provide constructive feedback
- Focus on improving the tool for DFIR community
- Respect privacy and legal boundaries

## How to Contribute

### Reporting Bugs

1. Check if bug already exists in Issues
2. Create new issue with:
   - Clear description
   - Steps to reproduce
   - Python version & OS
   - Expected vs actual behavior
   - Screenshots/logs if applicable

### Suggesting Features

1. Check existing issues/discussions
2. Describe the feature and why it's needed
3. Provide use case examples
4. Link to relevant research/documentation

### Submitting Code

1. Fork the repository
2. Create feature branch: `git checkout -b feature/your-feature`
3. Make changes with clear commits
4. Follow Python style (PEP 8)
5. Add comments for complex logic
6. Test thoroughly
7. Submit pull request with description

## Development Guidelines

### Code Style
- Follow PEP 8
- Use meaningful variable names
- Add docstrings to functions
- Keep functions focused and small
- Aim for < 100 lines per function

### Comments
```python
# Good - explains WHY
normalized = ' '.join(text.strip().lower().split())  # Normalize whitespace for consistent hashing

# Avoid - restates obvious
x = y + 1  # Add 1 to y
```

### Testing
- Test on Windows, Linux, macOS if possible
- Verify with different Python versions (3.7+)
- Test with various artifact types
- Check for false positives/negatives

### Security Considerations
- No hardcoded credentials
- Validate file paths
- Handle errors gracefully
- Don't modify user data unnecessarily
- Document any security assumptions

## Pull Request Process

1. Update README.md if needed
2. Update version number if applicable
3. Provide clear PR description:
   - What problem does it solve?
   - How does it work?
   - Any breaking changes?
   - Testing performed
4. Link related issues
5. Wait for review feedback
6. Address comments and re-request review

## Areas for Contribution

### High Priority
- [ ] Support for JetBrains IDEs
- [ ] Support for Visual Studio
- [ ] Cross-platform compatibility improvements
- [ ] Performance optimization
- [ ] Additional threat detection patterns

### Medium Priority
- [ ] Better error handling
- [ ] More export formats (CSV, HTML)
- [ ] Configuration file support
- [ ] Logging improvements
- [ ] Documentation expansion

### Documentation
- [ ] More examples
- [ ] Video tutorials
- [ ] Forensic methodology guide
- [ ] API documentation
- [ ] Case studies

## Questions?

- Open a Discussion on GitHub
- Tag maintainers in issues
- Check existing documentation
- Review closed issues for context

## Legal Notice

By contributing to PromptTrace, you agree that your contributions will be licensed under the same MIT License as the project. You also confirm that your contributions are your own work and don't infringe on others' rights.

---

**Thank you for making PromptTrace better!** 🚀

---

**Repository:** https://github.com/pbsecforge-lab/PromptTrace
**Issues:** https://github.com/pbsecforge-lab/PromptTrace/issues
**Discussions:** https://github.com/pbsecforge-lab/PromptTrace/discussions
