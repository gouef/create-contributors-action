<img align=right width="168" src="docs/gouef_logo.png">

# Create contributors action
Github action for Create / Generate contributors list to your (README)

[![GitHub stars](https://img.shields.io/github/stars/gouef/create-contributors-action?style=social)](https://github.com/gouef/create-contributors-action/stargazers)
![Usages](https://img.shields.io/endpoint?url=https://github-repo-usages.vercel.app/api/getAction.go?repository=gouef/create-contributors-action)

## Versions
![Stable Version](https://img.shields.io/github/v/release/gouef/create-contributors-action?label=Stable&labelColor=green)
![GitHub Release](https://img.shields.io/github/v/release/gouef/create-contributors-action?label=RC&include_prereleases&filter=*rc*&logoSize=diago)
![GitHub Release](https://img.shields.io/github/v/release/gouef/create-contributors-action?label=Beta&include_prereleases&filter=*beta*&logoSize=diago)

## Introduction

Create contributors list. SVGs will in separate branch 

## Example

```yaml
name: Generate contributors

on:
  schedule:
    - cron: '0 0 * * 1'
  pull_request:
    types: [ opened, synchronize, edited ]
  push:
    branches:
      - master
      - main
      - develop
      - feature/**
      - release/**
      - test/**
      - bugfix/**

jobs:
  generate-contributors:
    runs-on: ubuntu-latest
    steps:
      - name: Generate contributors
        uses: gouef/create-contributors-action@main
        with:
          excludeBot: false
          notGenerateContributorsMd: false
          commitMessageBot: "[Update] Automate update contributors"
          svgBranch: "contributors-svg"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Action inputs

| Input                       | Default                                 | Required | Description                                  |
|-----------------------------|-----------------------------------------|----------|----------------------------------------------|
| `branch`                    | `main`                                  | `false`  | Branch                                       |
| `excludeBot`                | `false`                                 | `true`   | Exclude actions@github.com from contributors |
| `botName`                   | `GitHub Actions`                        | `false`  | Set bot name for contributors                |
| `botEmail`                  | `actions@github.com`                    | `false`  | Set bot email address for contributors       |
| `notGenerateContributorsMd` | `false`                                 | `true`   | Not commit generated CONTRIBUTORS.md ?       |
| `commitMessageBot`          | `[Update] Automate update contributors` | `true`   | Commit message which bot will do             |
| `svgBranch`                 | `contributors-svg`                      | `true`   | Branch where will save svgs of contributors  |

## Contributors

<div>
<span>
  <a href="https://github.com/actions-user"><img src="https://raw.githubusercontent.com/gouef/create-contributors-action/refs/heads/contributors-svg/.github/contributors/actions-user.svg" alt="actions-user" /></a>
</span>
<span>
  <a href="https://github.com/JanGalek"><img src="https://raw.githubusercontent.com/gouef/create-contributors-action/refs/heads/contributors-svg/.github/contributors/JanGalek.svg" alt="JanGalek" /></a>
</span>
</div>

