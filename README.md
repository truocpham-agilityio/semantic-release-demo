# Semantic Release Demo

## Steps to set up Semantic Release on your GitHub repo

- [ ] Only allow squash merging of pull requests
- [ ] Install https://github.com/apps/semantic-pull-requests
- [ ] Add release workflow file to `.github/workflows/release.yml`
- [ ] `npm i semantic-release`
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
      - uses: actions/checkout@main
      - uses: actions/setup-node@v1
        with:
          node-version: "12.x"
      - run: npm ci
      - run: npm run build --if-present
      - run: npx semantic-release
        env:
          PERSONAL_ACCESS_TOKEN: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
```
