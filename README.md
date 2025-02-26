# rye-easy

Rye Easy is a tool to help you manage your Python projects with Rye.

## Installation

```bash
pip install rye-easy
```

## Usage

Rye Easy provides simple commands to build and publish your Python packages managed with Rye.

### Command Line Interface

#### Build Command

```bash
python -m rye_easy build
```

When you run the build command, the following operations are performed:
1. Cleans the `dist` directory to remove any previous build artifacts
2. Bumps the patch version of your package using `rye version --bump patch`
3. Builds the package using `rye build`
4. Installs the newly built wheel package locally using pip

This is useful for testing your package locally before publishing.

#### Publish Command

```bash
python -m rye_easy publish
```

When you run the publish command, the following operations are performed:
1. Bumps the patch version of your package using `rye version --bump patch`
2. Adds the updated `pyproject.toml` to git staging
3. Commits the changes with the message "update version"
4. Creates a git tag with the new version (prefixed with 'v')
5. Pushes the commit to the remote repository
6. Pushes the tags to the remote repository

This command automates the entire release process in one step.

### As a Python Module

```python
from rye_easy import build, publish

# Build your package
build()

# Publish your package
publish()
```

### Functions

- `build()`: Bumps patch version, builds the package, and installs it locally
- `publish()`: Bumps patch version, commits changes, creates a git tag, and pushes to remote
- `clean_dist()`: Cleans the dist directory
- `get_version()`: Gets the current version from Rye

## TODO 
- [ ] pyproject.toml hatching 버젼 수정하여 build 잘 되게 하기
- [ ] github action 에서 배포가 잘될 수 있게 .github\workflows\python-publish.yml을 복사할 수 있게 하기 
