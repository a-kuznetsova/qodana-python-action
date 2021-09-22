## Qodana Python

[![official project](https://jb.gg/badges/official.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)

![Qodana EAP version alert](resources/eap-alert.png)

**Qodana** is a code quality monitoring platform that allows you to evaluate the integrity of code you own, contract, or purchase. It brings into your CI/CD pipelines all the smart features you love in the JetBrains IDEs plus continues adding project-level checks like clone detection and license audit.

Qodana Python is based on PyCharm Professional and provides static analysis for Python projects.

**Table of Contents**

<!-- toc -->

- [Qodana Python](#qodana-python)
- [Usage](#usage)
- [License Summary](#license-summary)

<!-- tocstop -->


## Usage

* `project-dir` - Project folder to inspect (default `${{ github.workspace }}`)
* `results-dir` - Save results to folder (default `${{ github.workspace }}/qodana`)
* `cache-dir` - Save cache to folder (default `/home/runner/work/_temp/_github_home/qodana-cache`)
* `inspected-dir` - Directory to be inspected. If not specified, the whole project is inspected by default
* `baseline` - Run in baseline mode. Provide the path to an exisitng SARIF report to be used in the baseline state calculation
* `baseline-include-absent` - Include in the output report the results from the baseline run that are absent in the current run (default `false`)
* `fail-threshold` - Set the number of problems that will serve as a quality gate. If this number is reached, the inspection run is terminated
* `save-html-report` - Generate HTML report (default `false`)
* `profile-name` - Name of a profile defined in project
* `profile-path` - Absolute path to the profile file
* `additional-volumes` - Additional volumes to mount to qodana docker image
* `additional-env-variables` - Additional environment variables to pass to qodana docker image

```yaml
- uses: JetBrains/qodana-python-action@v1.1.1
```

All action's inputs are optional. 
```yaml
- uses: JetBrains/qodana-python-action@v1.1.1
  with:
      fail-threshold: 10
      additional-env-variables: |
            IDE_PROPERTIES_PROPERTY='-Didea.headless.enable.statistics=false;-Didea.required.plugins.id=JavaScript,org.intellij.grails'
```

<!-- #TODO: update output results and License Summary -->

<!-- ## Output Results

An example of the Qodana command-line summary output:
```
---- Qodana - Code Inspection ----

2 problem(s) with Critical severity
 - Category(ies): General

1 problem(s) with Moderate severity
 - Category(ies): Code style

---- Problems reported: 3 ----
```

Full Qodana results are available in the file `results-allProblems.json` located in the `results-dir` folder. -->

## License Summary

By using Qodana, you agree to the [JetBrains EAP user agreement](https://www.jetbrains.com/legal/agreements/user_eap.html) and [JetBrains privacy policy](https://www.jetbrains.com/company/privacy.html).
