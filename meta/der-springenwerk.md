---
title: Der Springenwerk
subtitle: Relaxen, und watschen der blinkenlichten.
---

# Writing
Nerd-Level: 1

The contents of this site are written in [Markdown](https://daringfireball.net/projects/markdown/), which is a type of [markup language](https://en.wikipedia.org/wiki/Markup_language). The advantage of writing in Markdown is that it's easily readable, as if it were plain-text, but also convertable into other more visually-appealing formats such as [HTML](https://en.wikipedia.org/wiki/HTML) and [PDF](https://en.wikipedia.org/wiki/PDF).

All you need to start writing in Markdown is a basic text editor, and there are a lot of free, open source tools available for converting Markdown documents into other formats. The tool I use for this site is called [Pandoc](https://pandoc.org).

# Publishing
Nerd-Level: 2

Typically pandoc is used to output a single document from a single or multiple source documents. Because a published website usually consists of multiple documents, I've written a [wrapper](https://en.wikipedia.org/wiki/Wrapper_function) for pandoc in [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) script which I've creatively named *[publi.sh](https://github.com/jeremy-rm/publi-sh)*. Publi.sh allows the user to replicate an input directory structure containing Markdown files to a matching output directory structure containing HTML files, with some added features specific to static websites.

# Hosting
Nerd-Level: 3

All of the files which comprise this website are stored in a [Git](https://en.wikipedia.org/wiki/Git) repository which allows me to keep up-to-date copies of the site on multiple devices.

The primary repository is hosted at [Github](https://www.github.com/jeremy-rm/jeremy-rm.github.io), converted to a static website using a [Github Actions](https://docs.github.com/en/actions) workflow, and hosted via [Github Pages](https://pages.github.com/). All of this is controlled by a single configuration file, found [here](https://raw.githubusercontent.com/jeremy-rm/jeremy-rm.github.io/main/.github/workflows/github-ci.yml). All I need to do is push a change to the repository and the website is automatically rebuilt and available online within minutes.

This entire process is duplicated by [Gitlab](https://www.gitlab.com/jeremy-rm/jeremy-rm.gitlab.io) using [repository mirroring](https://docs.gitlab.com/ee/user/project/repository/repository_mirroring.html) and a configuration file for their own [CI/CD](https://docs.gitlab.com/ee/ci/) process, found [here](https://gitlab.com/jeremy-rm/jeremy-rm.gitlab.io/-/raw/main/.gitlab/workflows/gitlab-ci.yml).

A domain name record can easily be switched between the two services should one suddenly cease to exist.