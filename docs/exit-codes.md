# Exit Codes

| Exit Code	| Default | Description |
| --------- | ------- | ----------- |
| 0 | N/A | OK. Some emails were found that matched. |
| 1 | N/A | Command line arguments error. |
| 2 | N/A | General error. |
| User-defined | 0 | No matching emails were found. <br></br><br></br> - Note: Users who have already modified their job failure criteria to allow exit code 3 will not need to modify their jobs. Those users who want the job to fail when no matching emails are found will want to modify this setting to some non-zero value. New users and those upgrading SMArt Email will not need to modify the INI configuration file and can choose the default during install. |