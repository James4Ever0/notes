---
title: 'elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies'
created: '2022-09-12T07:24:30.355Z'
modified: '2022-09-12T07:35:05.332Z'
---

# elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies

first of all, set it up with a **normal** user agent

even better, we can chain it with some customized headless puppeteer/phantomjs (do not load video data), dump the dom when ready, and use elinks/lynx to analyze the dom tree.

to test if the recommendation bar shows up:
`https://v.qq.com/x/page/m0847y71q98.html`
