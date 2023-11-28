# Snyk Results Action

A [GitHub Action](https://github.com/features/actions) to read [Snyk](https://snyk.io) JSON output file and structure the results in variables to be used in other actions.

This action was validate with:
- Terraform Files

You can use the Action as follows:

```yaml
name: Example workflow for Snyk Results Action
on: [pull_request]
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Get Snyk results
        id: snyk_results
        continue-on-error: true
        uses: shoootyou/actions/snyk_results@prod
        with:
          file_name: snyk.json
```

The Snyk Results Action has properties which are passed to the underlying image. These are
passed to the action using `with`.

| Property  | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| file_name | snyk.json | The JSON file of Snyk results |

This action has the following outputs:

| Output                | Content                                                                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| list_critical_issues  | The list of all critical issues founded on the JSON file. If none critical issues was found, it's returns `No critical issues found.`               |
| list_high_issues      | The list of all high issues founded on the JSON file. If none critical issues was found, it's returns `No high issues found.`                       |
| list_low_issues       | The list of all low issues founded on the JSON file. If none critical issues was found, it's returns `No low issues found.`                         |
| list_medium_issues    | The list of all medium issues founded on the JSON file. If none critical issues was found, it's returns `No medium issues found.`                   |
| total_critical_issues | Number of all the critical issues found                                                                                                             |
| total_high_issues     | Number of all the high issues found                                                                                                                 |
| total_low_issues      | Number of all the low issues found                                                                                                                  |
| total_medium_issues   | Number of all the medium issues found                                                                                                               |
| total_issues          | Number of all issues found                                                                                                                          |
| total_scanned_files   | Number of all the scanned files                                                                                                                     |
| list_files            | The list of all scanned files.                                                                                                                      |
| status                | Status of the Snyk scan. `failure` if any critical or high issues found, `warning` if any medium or low issues found, `success` if no issues founds |

---
## Disclaimer
- You can find anything from Snyk [here](https://snyk.io)