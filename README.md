# Python Static Code Analysis

Static tests using pre-commit for Python projects

## Context
As a software developer, ensuring high-quality and consistent code is vital for seamless operations. Pre-commit is a powerful tool that can assist in achieving this by automatically checking the code before it's committed. This repository demonstrates how to set up and use pre-commit with a Python project to enhance code quality and optimize the development process. For more information on pre-commit, refer to the documentation in the reference material section.

## Objective
This project aims to set up a basic Python project with static analysis tools using pre-commit hooks.

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

### Running Pre-Commit

1. **Run pre-commit on all files:**

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

2. **Update pre-commit hooks:**

    ```sh
    poetry run pre-commit autoupdate
    ```

    Pre-commit will check all staged files before committing.

## Reference Material

- [Pre-Commit Documentation](https://pre-commit.com)
- [The Power of Pre-Commit for Python Developers: Tips and Best Practices](https://dev.to/techishdeep/maximize-your-python-efficiency-with-pre-commit-a-complete-but-concise-guide-39a5)
