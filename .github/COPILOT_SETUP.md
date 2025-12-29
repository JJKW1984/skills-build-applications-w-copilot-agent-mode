# GitHub Copilot Coding Agent Setup

This repository is configured to work optimally with GitHub Copilot coding agent following the best practices outlined in [Best practices for Copilot coding agent in your repository](https://docs.github.com/en/copilot/tutorials/coding-agent).

## Instruction Files

This repository uses custom instructions to guide GitHub Copilot coding agent when making changes to the codebase. Instructions are organized in a hierarchical structure:

### Main Instructions File

**`.github/copilot-instructions.md`**
- Provides general repository-wide guidance
- Contains project overview, architecture, and development guidelines
- Applies to all files in the repository
- Should be read first by Copilot when starting work

### Specialized Instruction Files

Located in `.github/instructions/`, these files provide context-specific guidance:

#### **`octofit_tracker_setup_project.instructions.md`**
- **Applies to:** All files (`applyTo: "**"`)
- **Purpose:** Overall project setup, structure, and environment configuration
- **Key topics:**
  - Project goals and features
  - Directory structure
  - Python virtual environment setup
  - MongoDB configuration
  - Port forwarding rules

#### **`octofit_tracker_django_backend.instructions.md`**
- **Applies to:** `octofit-tracker/backend/**`
- **Purpose:** Django backend-specific guidelines
- **Key topics:**
  - Django settings configuration
  - Serializer patterns (ObjectId to string conversion)
  - URL configuration for Codespaces
  - REST API testing approaches

#### **`octofit_tracker_react_frontend.instructions.md`**
- **Applies to:** `octofit-tracker/frontend/**`
- **Purpose:** React frontend-specific guidelines
- **Key topics:**
  - React app structure
  - Bootstrap integration
  - React Router setup
  - Image asset locations

## How Instructions Work

1. **YAML Frontmatter**: Each `.instructions.md` file starts with YAML frontmatter containing an `applyTo` field that specifies which files the instructions apply to:
   ```yaml
   ---
   applyTo: "octofit-tracker/backend/**"
   ---
   ```

2. **Pattern Matching**: The `applyTo` field uses glob patterns:
   - `**` matches all files
   - `octofit-tracker/backend/**` matches all files in the backend directory
   - `octofit-tracker/frontend/**` matches all files in the frontend directory

3. **Hierarchical Application**: When working on a file, Copilot considers:
   - The main `.github/copilot-instructions.md` (always)
   - Any matching `.instructions.md` files based on file path
   - More specific instructions take precedence over general ones

## Prompt Files

The `.github/prompts/` directory contains example prompts used in different stages of the exercise:

- **`create-django-project.prompt.md`**: Initial Django project setup
- **`init-populate-octofit_db.prompt.md`**: Database initialization and population

These files serve as templates and examples for interacting with Copilot during development.

## Best Practices for Using These Instructions

### For Repository Maintainers

1. **Keep Instructions Updated**: Update instruction files when architectural decisions or coding standards change
2. **Be Specific**: Provide concrete examples and patterns rather than vague guidelines
3. **Scope Appropriately**: Use `applyTo` patterns to target instructions to relevant files
4. **Avoid Duplication**: Don't repeat information that's in the main `copilot-instructions.md`

### For Copilot Coding Agent

When working on this repository:

1. **Read Instructions First**: Always review relevant instruction files before making changes
2. **Follow Patterns**: Respect the architectural patterns and conventions outlined in the instructions
3. **Respect Constraints**: Adhere to specific rules like "never change directories" or port restrictions
4. **Test Changes**: Follow the testing guidelines in the instructions
5. **Ask for Clarification**: If instructions are unclear or conflicting, ask the user before proceeding

### For Developers

1. **Understand the Structure**: Familiarize yourself with the instruction hierarchy
2. **Reference in PRs**: Mention which instructions guided your changes
3. **Suggest Improvements**: If you notice gaps or issues in the instructions, suggest updates
4. **Use as Onboarding**: New team members should read these files to understand project conventions

## Validating Instructions

To ensure instructions are properly formatted and accessible:

```bash
# Check that files exist
ls -la .github/copilot-instructions.md
ls -la .github/instructions/*.instructions.md

# Verify YAML frontmatter
head -5 .github/instructions/*.instructions.md

# Check for syntax issues
grep -n "applyTo:" .github/instructions/*.instructions.md
```

## Additional Resources

- [GitHub Copilot Coding Agent Documentation](https://docs.github.com/en/copilot/tutorials/coding-agent)
- [VS Code Copilot Customization](https://code.visualstudio.com/docs/copilot/customization/overview)
- [Best practices for Copilot coding agent](https://docs.github.com/en/copilot/tutorials/coding-agent/get-the-best-results)

## Feedback and Improvements

This instruction setup is part of the learning exercise and can be improved. If you have suggestions:

1. Open an issue describing the improvement
2. Submit a PR with proposed changes to instruction files
3. Share feedback about what worked well or what was confusing

---

*These instructions follow the best practices documented at [gh.io/copilot-coding-agent-tips](https://gh.io/copilot-coding-agent-tips)*
