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
➜  gitleaks-issues git:(main) ✗ gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose

DEBU[2020-11-30T12:20:25+01:00] allowlisted file found, skipping scan of file: gitleaks-config.toml 
DEBU[2020-11-30T12:20:25+01:00] -------------------------                    
DEBU[2020-11-30T12:20:25+01:00] | Times and Commit Counts|                   
DEBU[2020-11-30T12:20:25+01:00] -------------------------                    
totalScanTime:  0 seconds
totalPatchTime:  0 seconds
totalCloneTime:  0 seconds
totalCommits:  1
DEBU[2020-11-30T12:20:25+01:00] --------------------------                   
DEBU[2020-11-30T12:20:25+01:00] | Individual Regexes Times |                 
DEBU[2020-11-30T12:20:25+01:00] --------------------------                   
-----BEGIN RSA PRIVATE KEY-----......269 microseconds
{
	"line": "-----BEGIN RSA PRIVATE KEY-----",
	"lineNumber": 1,
	"offender": "-----BEGIN RSA PRIVATE KEY-----",
	"commit": "c36b126d0114ee6693f547d6082d320c1767a608",
	"repo": ".",
	"rule": "RSA",
	"commitMessage": "added .gitignore\n",
	"author": "Masalski, Andrei",
	"email": "andrei.masalski@wolterskluwer.com",
	"file": "src/readme.md",
	"date": "2020-11-30T12:16:51+01:00",
	"tags": "",
	"operation": "addition"
}
WARN[2020-11-30T12:20:25+01:00] 1 leaks detected. 1 commits scanned in 0 seconds 
➜  gitleaks-issues git:(main) ✗ 
```
