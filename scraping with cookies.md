---
title: 'elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies'
created: '2022-09-12T07:24:30.000Z'
modified: '2022-10-27T12:24:22.233Z'
---

# elinks/lynx with python: how to speed up headless website browsing/parsing/scraping with cookies

[newscrawl](https://github.com/casual-silva/NewsCrawl) 狠心开源企业级舆情新闻爬虫项目：支持任意数量爬虫一键运行、爬虫定时任务、爬虫批量删除；爬虫一键部署；爬虫监控可视化; 配置集群爬虫分配策略；👉 现成的docker一键部署文档已为大家踩坑

[general news extractor](https://github.com/GeneralNewsExtractor/GeneralNewsExtractor/) for extracting main content of news, articles

```bash
pip3 install gne
```

first of all, set it up with a **normal** user agent

even better, we can chain it with some customized headless puppeteer/phantomjs (do not load video data), dump the dom when ready, and use elinks/lynx to analyze the dom tree.

to test if the recommendation bar shows up:
`https://v.qq.com/x/page/m0847y71q98.html`

to make web page more readable:
https://github.com/luin/readability

load webpage headlessly:
https://github.com/jsdom/jsdom
https://github.com/ryanpetrello/python-zombie
