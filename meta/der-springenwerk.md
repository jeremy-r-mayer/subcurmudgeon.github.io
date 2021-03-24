---
title: Der Springenwerk
subtitle: Relaxen, und watschen der blinkenlichten.
---

# Writing
The content of this site is written in [Markdown](https://daringfireball.net/projects/markdown/), which is a type of [markup language](https://en.wikipedia.org/wiki/Markup_language). The advantage of writing in Markdown is that it's easily readable, as if it were plain-text, but also convertable into other more visually-appealing formats such as [HTML](https://en.wikipedia.org/wiki/HTML) and [PDF](https://en.wikipedia.org/wiki/PDF). All you need to start writing in Markdown is a simple text editor, and there are a lot of free, open source tools available for converting Markdown documents into other formats. The tool I use for this site is called [Pandoc](https://pandoc.org).

# Publishing
Typically pandoc is used to output a single document from a single or multiple source documents. Because a website usually consists of many documents, I've written a [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) script [wrapper](https://en.wikipedia.org/wiki/Wrapper_function) for pandoc, which I've creatively named *[publi.sh](https://github.com/jeremy-rm/publi-sh)*. Publi.sh allows the user to convert all the files in an input directory and output them into a matching output directory, with some added features specific to generating a static website.

# Hosting
