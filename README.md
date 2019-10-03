# conventional-pr-action

GitHub Action that validates the PR title and commits against a
[Conventional Commits](https://www.conventionalcommits.org) preset.

## Setup

Create a `.github/workflows/pr.yml` file in your repository, with the following contents. Requires
the `GITHUB_TOKEN` to be passed.

```yaml
name: PR
on: pull_request
jobs:
  conventional:
    name: Conventional PR
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - uses: beemojs/conventional-pr-action@v1
        with:
          config-preset: 'beemo'
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Supports the following input options:

- `config-preset` - The conventional changelog config preset. Defaults to the
  [Beemo preset](https://github.com/beemojs/conventional-changelog-beemo).
- `require-multiple-commits` - Validates the commits for use within squash merging. Defaults to
  `true`.