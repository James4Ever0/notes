---
title: generate docx document from python docstring
created: '2023-02-19T03:08:01.292Z'
modified: '2023-02-19T06:22:02.456Z'
---

# generate docx document from python docstring

install and use `pdoc3`

```bash
pip install pdoc3
pdoc --html [-o <output_dir>] <python_script_or_module_path> # default output directory of "html" is `./html`
```

install and use `pandoc`, on its [homepage](https://pandoc.org/) we find some slideshow backends like [reveal.js](https://revealjs.com/), [dzslides](https://github.com/paulrouget/dzslides), [s5](https://meyerweb.com/eric/tools/s5/), [slideous](https://goessner.net/articles/slideous/) and [slidy](https://www.w3.org/Talks/Tools/Slidy) (alternative to microsoft powerpoint, may help rendering video, or let's use libreoffice instead? or some dedicated video editing library like moviepy)

```bash
# let's convert the html version of 
pandoc -o <output_docx_filename> <input_html_path>
```

remove unwanted parts from html (`beautifulsoup`), and split index from main content (split and concat with [docxcompose](https://github.com/4teamwork/docxcompose))

for composing docx from hand, use [python-docx](https://python-docx.readthedocs.io/en/latest/index.html). for template based docx generating, use [docxtpl](https://docxtpl.readthedocs.io/en/latest/)

to insert page break into converted docx, there are two ways (maybe):

1. [change css](https://www.techjunkie.com/how-to-use-page-breaks-in-html) in the original html code
2. [insert page break](https://github.com/4teamwork/docxcompose/issues/89) while concatenating
