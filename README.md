# Semantic Release Demo

## Steps to set up Semantic Release on your GitHub repo

- [ ] Only allow squash merging of pull requests
- [ ] Install https://github.com/apps/semantic-pull-requests
- [ ] Add release workflow file to `.github/workflows/release.yml`
- [ ] `npm i -D semantic-release`
- [ ] Use semantic commit messages
- [ ] Create a pull request

## Example Workflow

```yml
name: Release npm package

on:
  push:
    branches:
      - main

jobs:
  release:
    name: Release
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: "12.x"
      - run: npm ci
      - run: npm run build --if-present
      - run: npx semantic-release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
