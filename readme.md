# gitleaks-issues
demo repo to reproduce gitleaks issues

command to run scan:
```
gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose
```
*expected result*:
no leaks should be found, since 'src/readme.md' file should be ignored by paths config 

*actual result*:
file with the leak isn't ignored by path
```
➜  gitleaks-issues git:(main) gitleaks --version                                                                                      
6.2.0
➜  gitleaks-issues git:(main) ✗ gitleaks --repo-path=. --config=gitleaks-config.toml --files-at-commit=latest --pretty --debug --verbose --redact
DEBU[2020-11-30T12:51:06+01:00] allowlisted file found, skipping scan of file: gitleaks-config.toml 
DEBU[2020-11-30T12:51:06+01:00] -------------------------                    
DEBU[2020-11-30T12:51:06+01:00] | Times and Commit Counts|                   
DEBU[2020-11-30T12:51:06+01:00] -------------------------                    
totalScanTime:  0 seconds
totalPatchTime:  0 seconds
{
	"line": "REDACTED",
	"lineNumber": 1,
	"offender": "REDACTED",
	"commit": "847fd468aed2a5bb7e1838aab2ec0da9ffef0f9a",
	"repo": ".",
	"rule": "RSA",
	"commitMessage": "removed leak from root readme.md\n",
	"author": "Masalski, Andrei",
	"email": "andrei.masalski@wolterskluwer.com",
	"file": "src/readme.md",
	"date": "2020-11-30T12:50:04+01:00",
	"tags": "",
	"operation": "addition"
}
totalCloneTime:  0 seconds
totalCommits:  1
DEBU[2020-11-30T12:51:06+01:00] --------------------------                   
DEBU[2020-11-30T12:51:06+01:00] | Individual Regexes Times |                 
DEBU[2020-11-30T12:51:06+01:00] --------------------------                   
WARN[2020-11-30T12:51:06+01:00] 1 leaks detected. 1 commits scanned in 0 seconds 
```
