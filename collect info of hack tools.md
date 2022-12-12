---
title: download/collect info of hack tools
created: '2022-12-12T14:35:02.642Z'
modified: '2022-12-12T16:52:11.949Z'
---

# download/collect info of hack tools

## general introduction

given the name of the hack tool, you may not be able to tell what the tool is (written in python? hosted on github? online tool?) and you want to use search engine to find possible entries. you may take snapshots on these pages and index them.

if the hack tool is linked to some website, you can index the website. if you find it inside some package index or package manager, you will know how to install the package.

## case specific

### github

you will find github links on web, social media, instant messaging and forums

[Scraper](https://github.com/henson/Scraper) scrape popular github repositories every day

[gitsuggest](https://github.com/csurfer/gitsuggest) recommend github repos

[How to Use the GitHub API to List Repositories](https://fusebit.io/blog/github-api-list-repositories/?utm_source=cn.bing.com&utm_medium=referral&utm_campaign=none)

[PyGithub](https://pygithub.readthedocs.io/en/latest/introduction.html) use python to automate github api v3

if you want all README pages on github, you first need to collect all github repo urls. you may also collect info on github repos (OSINT). you can retrieve all repos link to given user with github api (quota limited). you can search github on github or search engine with some juicy/promising keywords then collect repo name, username, keywords, repeat the search.

there are few github repo archives avaliable for download. the github archive program packed many repos to arctic, the list is called [Greatest Hits](https://archiveprogram.github.com/assets/img/archive-repos.txt)

[gharchive](https://www.gharchive.org/) provides many websites for monitoring github repos

### kali, parrot

these two are for pentesting, using `apt` as package manager. but parrot does not provide tool introductions.

using `apt` one can retrieve package infos with simple command. find main metapackages first, then retrieve dependency trees.

parrotos has [index.db](https://mirrors.tuna.tsinghua.edu.cn/parrot/index.db) which you can retrieve info from there. 


