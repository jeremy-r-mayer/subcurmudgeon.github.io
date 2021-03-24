---
title: Der Springenwerk
subtitle: Relaxen, und watschen der blinkenlichten.
---

# Writing
Nerd-Level: 1

The contents of this site are written in [Markdown](https://daringfireball.net/projects/markdown/), which is a type of [markup language](https://en.wikipedia.org/wiki/Markup_language). The advantage of writing in Markdown is that it's easily readable, as if it were plain-text, but also convertable into other more visually-appealing formats such as [HTML](https://en.wikipedia.org/wiki/HTML) and [PDF](https://en.wikipedia.org/wiki/PDF).

All you need to start writing in Markdown is a basic text editor, and while there are a lot of free, open source editors available, pretty much every modern operating system has at least one installed by default. My favorite tool for writing Markdown on my desktop computer is [Sublime Text](https://www.sublimetext.com), and on my iOS devices I use [Working Copy](https://workingcopyapp.com/) which also serves as my [Git](https://en.wikipedia.org/wiki/Git) client - but more on that later.

# Publishing
Nerd-Level: 2

I find [Pandoc](https://pandoc.org) to be the tool of choice for converting a document from one format to another. Typically pandoc is used to output a single document from a single or multiple source documents. Because a published website can consist of many documents, I've written a [wrapper](https://en.wikipedia.org/wiki/Wrapper_function) for pandoc in [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) script which I've creatively named *[publi.sh](https://github.com/jeremy-rm/publi-sh)*. Publi.sh allows the user to replicate an input directory structure containing Markdown files to a matching output directory structure containing HTML files, and has some additional features specific to creating static websites.

Simply put, Markdown goes into the input folder and HTML comes out of the output folder, and anything not Markdown just gets passed along unchanged.

# Hosting
Nerd-Level: 3

All of the files which comprise this website are stored in a git repository which allows me to keep up-to-date copies of the site on multiple devices.

The primary repository is hosted at [Github](https://www.github.com/jeremy-rm/jeremy-rm.github.io), converted to static HTML using [publi.sh](https://github.com/jeremy-rm/publi-sh) via a [Github Actions](https://docs.github.com/en/actions) workflow, and the output is hosted at [Github Pages](https://pages.github.com/). All of this is controlled by a single configuration file, found [here](https://raw.githubusercontent.com/jeremy-rm/jeremy-rm.github.io/main/.github/workflows/github-ci.yml). All I need to do is push a change to the repository from anywhere and the website is automatically rebuilt and available online within minutes.

This entire process is duplicated by [Gitlab](https://www.gitlab.com/jeremy-rm/jeremy-rm.gitlab.io) using [repository mirroring](https://docs.gitlab.com/ee/user/project/repository/repository_mirroring.html) and a configuration file for their own [CI/CD](https://docs.gitlab.com/ee/ci/) process, found [here](https://gitlab.com/jeremy-rm/jeremy-rm.gitlab.io/-/raw/main/.gitlab/workflows/gitlab-ci.yml).

Also noteworthy is that domain name records can easily be switched between the two services should one suddenly and unexpectedly cease to exist.