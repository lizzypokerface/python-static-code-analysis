# Python Static Code Analysis

Static tests using pre-commit for Python projects

## Context
Pre-commit is a tool used by developers to ensure code quality by running checks on code before it is committed to the repository. This tool relies on a configuration file that lists hooks which execute scripts or commands to check the code. If the code fails the checks, the commit is rejected, and the developer is asked to fix the issues.

Pre-commit can be used to enforce consistent code style, catch syntax errors, and identify security vulnerabilities. It also supports plugins that can extend its functionality and integrate with other tools like linters, formatters, and static analysis tools.

## Objective
Set up a basic Python project with static analysis tools using pre-commit hooks.

**Note:** In this project, Pre-commit is added as a development dependency:

```toml
[tool.poetry.group.dev.dependencies]
pre-commit = "^3.7.1"
```

The pre-commit hooks are configured in a `.pre-commit-config.yaml` file in the project root. The pre-commit hooks will run automatically before a commit is created.

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.6.0
    hooks:
      - id: trailing-whitespace
        args:
        - --markdown-linebreak-ext=md
      - id: end-of-file-fixer
      - id: check-yaml
  - repo: https://github.com/psf/black
    rev: 24.4.2
    hooks:
      - id: black
  - repo: https://github.com/PyCQA/flake8
    rev: 7.0.0
    hooks:
      - id: flake8
        args:
          - --exclude=venv
          - --max-line-length=79
          - --ignore=E203,E501,W503
```

## Up and Running

This project requires Python 3.10 or higher.

### Setup

1. **Create a virtual environment in the root directory:**

    ```sh
    python3 -m venv env
    source env/bin/activate
    ```

2. **Install [Poetry](https://python-poetry.org/docs/cli/) for dependency management:**

    ```sh
    env/bin/pip install -U pip setuptools
    env/bin/pip install poetry
    ```

3. **Install project dependencies:**

    ```sh
    poetry install
    ```

4. **Install pre-commit:**

    ```sh
    poetry run pre-commit install
    ```

5. **Update pre-commit hooks:**

    It's crucial to keep the pre-commit configuration up to date and test the hooks regularly to catch any issues before they affect the codebase.

    ```sh
    poetry run pre-commit autoupdate
    ```

### Running Pre-Commit

1. **Run pre-commit on all files:**

    Pre-commit will check all staged files before committing. You can also run it manually on your codebase.

    ```sh
    poetry run pre-commit run --all-files
    ```

    **Output:**

    ```sh
    % poetry run pre-commit run --all-files
    trim trailing whitespace.................................................Passed
    fix end of files.........................................................Passed
    check yaml...............................................................Passed
    black....................................................................Passed
    flake8...................................................................Passed
    ```

## Benefits of Pre-Commit in Python

**Improved Code Quality:** Pre-commit improves the overall quality of your code by ensuring consistency, readability, and adherence to best practices. It checks for syntax errors, enforces code formatting standards, and detects potential bugs or security vulnerabilities.

**Reduced Time and Effort:** Pre-commit automates several aspects of code testing, reducing the time and effort required to manually check code for errors. It runs all checks in a single command, saving developers valuable time.

**Easy to Use:** Pre-commit is easy to set up and use in your Python project. The configuration file can be easily customized to meet the specific needs of your project. Pre-commit supports a wide range of hooks and linters, making it versatile enough for almost any project.

**Improved Collaboration:** Pre-commit helps improve collaboration among team members. By running checks before pushing changes to the repository, everyone can be confident that the code follows the same standards and conventions, making it easier for new team members to get up to speed and maintain consistency throughout the project.

## Common Mistakes to Avoid

- **Specifying the Correct Version of a Dependency:** Ensure compatibility by defining the correct versions of all packages used in your pre-commit hooks.
- **Updating Pre-Commit Configuration:** Keep the configuration up to date and test the hooks regularly to catch any issues before they affect the codebase.

## Integrate Pre-Commit with CI Workflow

Integrating pre-commit with your CI workflow can further improve code quality by catching issues before they make it to production. When integrated with a CI tool like Jenkins or Travis CI, the hooks are automatically run on every code change, ensuring that all code meets the same quality standards.

## Best Practices for Pre-Commit in Python

- **Use pre-commit.ci:** A service that runs pre-commit hooks on your codebase and provides feedback on code quality. It can be integrated with your CI workflow for consistent code quality.
- **Use a Virtual Environment:** Ensures that the hooks are run in a consistent environment, reducing the chances of version conflicts.
- **Configure Hooks for the Right Files:** Reduces build times and speeds up the development process by configuring hooks to run on the right files.

## Conclusion

Pre-commit is a powerful tool for improving code quality and consistency in Python projects. By setting up custom hooks and integrating it with your CI workflow, you can catch errors and warnings before they are committed, streamlining your development process. With proper configuration and best practices, Pre-commit can significantly reduce bugs, save time, and enhance the overall quality of your codebase.

By following the steps outlined in this guide, you can easily get started with Pre-commit and take your Python development to the next level.

## Reference Material

- [Pre-Commit Documentation](https://pre-commit.com)
- [The Power of Pre-Commit for Python Developers: Tips and Best Practices](https://dev.to/techishdeep/maximize-your-python-efficiency-with-pre-commit-a-complete-but-concise-guide-39a5)
