# Pre-commit Hooks Configuration

This document provides an overview of the pre-commit hooks configured in the `.pre-commit-config.yaml` file.

## Repositories and Hooks

### pre-commit-hooks (out-of-the-box hooks for pre-commit)

- **trailing-whitespace**: Trims trailing whitespace.
- **end-of-file-fixer**: Ensures files end in a newline and only a newline.
- **double-quote-string-fixer**: Converts single-quoted strings to double-quoted strings.
- **debug-statements**: Removes debug statements from code.
- **name-tests-test**: Ensures test files are named correctly.
- **requirements-txt-fixer**: Fixes requirements.txt file format.
- **check-added-large-files**: Prevents large files from being added to the repository.
- **check-ast**: Checks Python files for syntax errors.
- **check-builtin-literals**: Checks for the use of builtin literals.
- **check-xml**: Validates XML files.
- **check-yaml**: Validates YAML files.
- **pretty-format-json**: Formats JSON files.
- **check-json**: Validates JSON files.
- **check-merge-conflict**: Detects merge conflict markers.
- **check-vcs-permalinks**: Ensures VCS permalinks are used.
- **forbid-new-submodules**: Prevents new submodules from being added.
- **no-commit-to-branch**: Prevents commits to the specified branch.
- **check-executables-have-shebangs**: Ensures executable files have shebangs.
- **mixed-line-ending**: Fixes mixed line endings.

### pre-commit-hooks (Lucas-C - useful git hooks)

- **forbid-crlf**: Forbids CRLF line breaks.
- **remove-crlf**: Removes CRLF line breaks.
- **forbid-tabs**: Forbids the use of tabs.
- **remove-tabs**: Removes tabs and replaces them with spaces.

### setup-cfg-fmt (apply a consistent format to setup.cfg files)

- **setup-cfg-fmt**: Formats setup.cfg files.

### typos (Finds and corrects spelling mistakes)

- **typos**: Finds and corrects spelling mistakes.

### yamlfix (fixes YAML formatting issues)

- **yamlfix**: Fixes YAML formatting issues.

### yamllint (linter for YAML files)

- **yamllint**: Lints YAML files.

### jenkinslint (basic Jenkinsfile linter)

- **jenkinslint**: Lints Jenkinsfiles.

### pygrep-hooks (collection of fast, cheap, regex based pre-commit hooks)

- **python-no-log-warn**: Ensures no use of `log.warn`.
- **python-no-eval**: Prevents the use of `eval`.
- **rst-backticks**: Checks for correct use of backticks in reStructuredText.
- **rst-directive-colons**: Ensures directives in reStructuredText end with colons.
- **rst-inline-touching-normal**: Ensures inline markup in reStructuredText is correctly formatted.
- **text-unicode-replacement-char**: Detects Unicode replacement characters.

### local hooks

- **python-safety-dependencies-check**: Checks Python dependencies for security issues using Safety.

### flake8 (Flake8 is a wrapper around these tools PyFlakes, pycodestyle, McCabe script)

- **flake8**: Lints Python code.

### bandit (security linter from PyCQA)

- **bandit**: Performs security analysis on Python code.

### prospector (Style Guide Enforcement)

- **prospector**: Enforces style guide rules.

### reorder-python-imports (Tool for automatically reordering python imports)

- **reorder-python-imports**: Reorders Python imports.

### skjold (Security audit python project dependencies against several security advisory databases)

- **skjold**: Audits Python project dependencies for security issues.

### autopep8 (Style Guide Enforcement)

- **autopep8**: Formats Python code according to PEP 8.

### dockerfilelint-precommit-hooks (Useful pre-commit hooks for checking Dockerfiles)

- **dockerfilelint**: Lints Dockerfiles.

### detect-secrets (module for detecting secrets)

- **detect-secrets**: Detects secrets in code.

### gitleaks (for detecting and preventing hardcoded secrets)

- **gitleaks**: Detects hardcoded secrets.

### talisman (scans git to ensure that potential secrets or sensitive information)

- **talisman-commit**: Scans for potential secrets or sensitive information.

### shfmt (format shell scripts)

- **shfmt**: Formats shell scripts.

### shellcheck (linter for shell scripts)

- **shellcheck**: Lints shell scripts.

### hadolint (Lint Dockerfiles)

- **hadolint**: Lints Dockerfiles.

### prettier (code formatter)

- **prettier**: Formats code according to Prettier rules.

### terraform-docs (generate documentation for Terraform modules)

- **terraform-docs-go**: Generates documentation for Terraform modules.

### pre-commit-terraform (Terraform hooks)

- **terraform_fmt**: Formats Terraform files.
- **terraform_tflint**: Lints Terraform files.
- **terraform_validate**: Validates Terraform files.
- **terraform_trivy**: Scans Terraform files for vulnerabilities.
- **terraform_providers_lock**: Locks Terraform providers.
- **terraform_checkov**: Scans Terraform files with Checkov.
- **terraform_docs**: Generates Terraform documentation.

### pre-commit-k8s (Kubernetes hooks)

- **pre-commit-k8s**: Runs pre-commit hooks for Kubernetes files.

### kube-linter (static analysis tool for Kubernetes YAML files)

- **kube-linter**: Lints Kubernetes YAML files.

```

```
