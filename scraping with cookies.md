---
title: 'elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies'
created: '2022-09-12T07:24:30.000Z'
modified: '2022-10-19T09:54:08.811Z'
---

# elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies

[general news extractor](https://github.com/GeneralNewsExtractor/GeneralNewsExtractor/) for extracting main content of news, articles

first of all, set it up with a **normal** user agent

even better, we can chain it with some customized headless puppeteer/phantomjs (do not load video data), dump the dom when ready, and use elinks/lynx to analyze the dom tree.

to test if the recommendation bar shows up:
`https://v.qq.com/x/page/m0847y71q98.html`

to make web page more readable:
https://github.com/luin/readability

load webpage headlessly:
https://github.com/jsdom/jsdom
https://github.com/ryanpetrello/python-zombie
