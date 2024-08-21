---
created: 2024-08-21T17:40:58+08:00
modified: 2024-08-21T17:43:30+08:00
---

# Fix language stats in Github

[reference](https://dev.to/katkelly/changing-your-repo-s-language-in-github-5gjo)

You need to create a file `.gitattributes`  under the project root folder:

```
# for example, ignore javascript, html, jupyter notebooks

*.html linguist-detectable=false
*.js linguist-detectable=false
*.ipynb linguist-detectable=false
```
