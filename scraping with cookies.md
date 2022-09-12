---
title: 'elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies'
created: 2022-09-12T15:24:30+08:00
modified: 2022-09-12T16:27:52+08:00
---

# elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies

first of all, set it up with a **normal** user agent

even better, we can chain it with some customized headless puppeteer/phantomjs (do not load video data), dump the dom when ready, and use elinks/lynx to analyze the dom tree.

to test if the recommendation bar shows up:
`https://v.qq.com/x/page/m0847y71q98.html`

to make web page more readable:
https://github.com/luin/readability

load webpage headlessly:
https://github.com/jsdom/jsdom
https://github.com/ryanpetrello/python-zombie
