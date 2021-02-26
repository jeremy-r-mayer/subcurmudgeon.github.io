---
title: Publi.sh
---

***[Publi.sh](/publi.sh)*** is a [bash](https://www.gnu.org/software/bash/) wrapper for [pandoc](https://pandoc.org) that can simplify the process of publishing markdown documents on the web.

## Usage
`./publi.sh [options] <input directory> <output directory>`

## Options

| Flag                | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| `-d`, `-v`          | display verbose debugging output                             |
| `-h`                | display help                                                 |
| `-i <glob pattern>` | rename all input files matching glob pattern to `index.html` |
| `-o`                | confirm overwrite of output directory                        |
| `-p <args>`         | pass additional arguments to pandoc                          |

## Example
This is the command used by the Github Action that builds this page:

```
publi.sh \
-i README.md \
-p "--css=https://cdn.jsdelivr.net/npm/@exampledev/new.css@1/new.min.css" \
-v \
. \
.site
```

- `-i README.md` renames the output of `README.md` to `index.html`, not `README.html`.
- `-p "--css=https://cdn.jsdelivr.net/npm/@exampledev/new.css@1/new.min.css"` sets the `--css` option in pandoc.
- `-v` enables verbose output for troubleshooting purposes.
- `. .site` tells publi.sh to use the current directory as input and `.site` as output.

This is the Github Action:

```yaml
name: Publi.sh

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Preflight
        run: |
          sudo apt-get install pandoc
          mkdir .site
      - name: Publi.sh
        run: |
          curl -L -s https://raw.githubusercontent.com/jeremy-r-mayer/publi.sh/main/publi.sh | bash -s -- \
          -i README.md \
          -p "--css=https://cdn.jsdelivr.net/npm/@exampledev/new.css@1/new.min.css" \
          -v \
          . \
          .site
      - name: Deploy to GitHub Pages
        if: success()
        uses: crazy-max/ghaction-github-pages@v2
        with:
          build_dir: .site
          fqdn: www.01001010.net
          jekyll: false
          target_branch: gh-pages
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
