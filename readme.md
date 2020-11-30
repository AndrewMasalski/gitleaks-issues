# gitleaks-issues
demo repo to reproduce gitleaks issues

command to run scan:
```
gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose
```
*expected result*:
no leaks should be found, since 'src/readme.md' file should be ignored by paths config 

*actual result*:
file is not ignored by path
```
➜  gitleaks-issues git:(main) gitleaks --version                                                                                      
6.2.0
➜  gitleaks-issues git:(main) ✗ gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose --redact

```
