# gitleaks-issues
demo repo to reproduce gitleaks issues

command to run scan:
```
gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose
```

command for pre-commit hook:
```
gitleaks --uncommitted --verbose --redact --pretty
```
