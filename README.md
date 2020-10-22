# urlzap

This Github Action will automatically generate your static URLs using `urlzap`. Paired with Github Page actions, you can automate your whole `urlzap` pipeline 🤖

## Usage:

To use it, call `brunoluiz/urlzap-github-action@v1` on your Github Action workflow. The example below:

1. Generates the static URL files 
2. Deploy to Github Pages, under `gh-pages` branch [(using this action)](https://github.com/marketplace/actions/deploy-to-github-pages).

```
name: urlzap
on: [push]

jobs:
  deploy:
    runs-on: ubuntu-latest
    name: Generate & Deploy
    steps:
    # Checkout your repo locally
    - uses: actions/checkout@v2

    # Generate files using this action
    - name: Generate
      uses: brunoluiz/urlzap-github-action@v1

    # Deplloy in Github Pages (you can use others)
    - name: Deploy
      uses: JamesIves/github-pages-deploy-action@3.7.1
      with:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        BRANCH: gh-pages
        FOLDER: .
```

A project using the above config is [brunoluiz/_](https://www.youtube.com/channel/UCCYzx5UEwMxFSQAQwi8f_Mg). An example output is [https://brunoluiz.net/_/yt](https://brunoluiz.net/_/yt).

## Configuration:

The `with` portion of the workflow can be configured with the following params.

Key | Required | Default | Description
--- | --- | --- | ---
`version` | **No** | **latest** | Defines which `urlzap` version to use
