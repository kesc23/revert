# GitHub Action to revert a commit via a comment

After installation, comment `/revert <commit_sha>` to trigger the action.

![revert](https://user-images.githubusercontent.com/2181356/52225171-027d0100-2867-11e9-90a5-84073c790f0b.gif)

## Installation

```yaml
name: Automatic Revert

on:
  push:

jobs:
  revert-commit:

    runs-on: ubuntu-latest

    if: contains( ${{ github.event.comment.body }}, '/revert')

    steps:
      - name: Checkout latest code
        uses: actions/checkout@v3
      - name: Automatic Revert
        uses: kesc23/revert@v1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
 ```

This Action is heavily inspired by [rebase](https://github.com/cirrus-actions/rebase).
