# GitHub Action: Workflow Run Wait

If the same workflow is already running from a previous commit, wait for it to finish

[![license][license-img]][license-url]
[![release][release-img]][release-url]
[![super linter][super-linter-img]][super-linter-url]
[![test][test-img]][test-url]
[![semantic][semantic-img]][semantic-url]

<details>
  <summary><strong>Why?</strong></summary>

Workflows run on every commit asynchronously, this is fine for most cases, however, you might want to wait for a previous commit workflow to finish before running another one, some example use-cases:

-   Deployment workflows
-   Terraform workflows
-   Database Migrations

</details>

## Usage

###### `.github/workflows/my-workflow.yml`

``` yaml
jobs:
  xyz:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: keylogic1/action-workflow-queue@v1

      # only runs additional steps if there is no other instance of `my-workflow.yml` currently running
```

### Inputs

| input          | required | default        | description                                     |
|----------------|----------|----------------|-------------------------------------------------|
| `github-token` | ❌        | `github.token` | The GitHub token used to call the GitHub API    |
| `timeout`      | ❌        | `600000`       | timeout before we stop trying (in milliseconds) |
| `delay`        | ❌        | `10000`        | delay between status checks (in milliseconds)   |

----
> Author: [Ahmad Nassri](https://www.ahmadnassri.com/) &bull;
> Twitter: [@AhmadNassri](https://twitter.com/AhmadNassri)

[license-url]: LICENSE
[license-img]: https://badgen.net/github/license/keylogic1/action-workflow-queue

[release-url]: https://github.com/keylogic1/action-workflow-queue/releases
[release-img]: https://badgen.net/github/release/keylogic1/action-workflow-queue

[super-linter-url]: https://github.com/keylogic1/action-workflow-queue/actions?query=workflow%3Asuper-linter
[super-linter-img]: https://github.com/keylogic1/action-workflow-queue/workflows/super-linter/badge.svg

[test-url]: https://github.com/keylogic1/action-workflow-queue/actions?query=workflow%3Atest
[test-img]: https://github.com/keylogic1/action-workflow-queue/workflows/test/badge.svg

[semantic-url]: https://github.com/keylogic1/action-workflow-queue/actions?query=workflow%3Arelease
[semantic-img]: https://badgen.net/badge/📦/semantically%20released/blue
