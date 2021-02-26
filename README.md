---
title: Publi.sh
---

# publi.sh
Publi.sh is a [pandoc](https://pandoc.org) wrapper that can simplify the process of publishing markdown documents on the web.

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
publi.sh -i README.md -p "--css=https://cdn.jsdelivr.net/npm/@exampledev/new.css@1/new.min.css" -v . .site
```

- `-i README.md` renames the output of `README.md` to `index.html`, not `README.html`.
- `-p "--css=https://cdn.jsdelivr.net/npm/@exampledev/new.css@1/new.min.css"` sets the `--css` option in pandoc.
- `-v` enables verbose output for troubleshooting purposes.
- `. .site` tells publi.sh to use the current directory as input and `.site` as output.
