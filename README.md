# GitHub Action Reusable Workflows

[![Tag](https://img.shields.io/github/tag/Flaconi/github-reusable-workflow.svg)](https://github.com/Flaconi/github-reusable-workflow/releases)
[![License](https://img.shields.io/badge/license-MIT-%233DA639.svg)](https://opensource.org/licenses/MIT)

## :computer: A Reusable workflow to backup GitHub repository to S3 bucket

To trigger the flow, add the following to your respective repository you want to backup.

```
name: Backup Respository

# -------------------------------------------------------------------------------------------------
# When to run
# -------------------------------------------------------------------------------------------------

on:
  push:
    branches:
      - master

jobs:
  backup:
    uses: Flaconi/github-reusable-workflow/.github/workflows/backups.yml@v1
    with:
      enabled: true
      region: eu-central-1
    secrets:
      iam_role_arn: ${{ secrets.BACKUP_REPO_IAM_ROLE }}
      bucket_name: ${{ secrets.BACKUP_REPO_BUCKET }}
```


## :exclamation: Keep up-to-date with GitHub Dependabot


| :warning: UPDATE    |
|:--------------------|
| The following is not yet available as part of Dependabots package ecosystem.<br/>https://github.com/community/community/discussions/8088 |


Since [Dependabot](https://docs.github.com/en/github/administering-a-repository/keeping-your-actions-up-to-date-with-github-dependabot) has [native GitHub Actions support](https://docs.github.com/en/github/administering-a-repository/configuration-options-for-dependency-updates#package-ecosystem), to enable it on your GitHub repo all you need to do is add the `.github/dependabot.yml` file:

```yml
version: 2
updates:
  # Maintain dependencies for GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"
```

Then Dependabot will PR you version updates as soon as this repository gets updated.


## :page_facing_up: License

**[MIT License](LICENSE)**

Copyright (c) 2022 [Flaconi GmbH](https://github.com/Flaconi)
