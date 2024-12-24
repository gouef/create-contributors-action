<img align=right width="168" src="docs/gouef_logo.png">

# Create contributors action
Github action for create contributors list

[![GitHub stars](https://img.shields.io/github/stars/gouef/create-contributors-action?style=social)](https://github.com/gouef/create-contributors-action/stargazers)
[![Go Report Card](https://goreportcard.com/badge/github.com/gouef/create-contributors-action)](https://goreportcard.com/report/github.com/gouef/create-contributors-action)

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
  workflow_dispatch:
    inputs:
      excludeBot:
        description: "Exclude actions@github.com from contributors"
        required: false
        type: boolean
        default: false
      notGenerateContributorsMd:
        required: false
        type: boolean
        default: false
        description: "Not commit CONTRIBUTORS.md ?"
      commitMessageBot:
        required: true
        type: string
        default: "[Update] Automate update contributors"
        description: "Commit message which bot will do"
      svgBranch:
        required: true
        default: "contributors-svg"
        description: "Branch where will save svgs of contributors"

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
          excludeBot: ${{ inputs.excludeBot || false}}
          notGenerateContributorsMd: ${{ inputs.notGenerateContributorsMd || false }}
          commitMessageBot: ${{ inputs.commitMessageBot || "[Update] Automate update contributors" }}
          svgBranch:  ${{ inputs.svgBranch || "contributors-svg" }}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
