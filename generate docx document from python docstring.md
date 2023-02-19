---
title: generate docx document from python docstring
created: '2023-02-19T03:08:01.292Z'
modified: '2023-02-19T04:21:18.346Z'
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

remove unwanted parts from html (`beautifulsoup`), and split index from main content (split and concat with `` and ``), 
