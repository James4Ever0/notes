---
title: download/collect info of hack tools
created: '2022-12-12T14:35:02.642Z'
modified: '2022-12-13T10:05:36.428Z'
---

# download/collect info of hack tools

## general introduction

given the name of the hack tool, you may not be able to tell what the tool is (written in python? hosted on github? online tool?) and you want to use search engine to find possible entries. you may take snapshots on these pages and index them.

if the hack tool is linked to some website/manual, you can index the website. if you find it inside some package index or package manager, you will know how to install the package.

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

kali tool list pages

```bash
curl https://en.kali.tools/all/ > kali_tools_all.html # more tags, more categories, the same as blackarch?
curl https://www.kali.org/tools/ > kali_official.html
curl https://en.kali.tools/ > pentest_tools_with_name.html
```

[kali meta page on web](https://www.kali.org/tools/kali-meta/)

[kali meta page on package index](http://pkg.kali.org/pkg/kali-meta)

[kali package index](https://pkg.kali.org/)

notice kali official "offsec" provides training courses and materials as apt packages. the list:
```
offsec-awae/kali-rolling 2021.1.2 amd64
  Resources for OffSec's AWAE/WEB-300

offsec-awae-python2/kali-rolling 2021.1.2 amd64
  Python 2 resources for OffSec's AWAE/WEB-300

offsec-exp301/kali-rolling 2021.1.2 amd64
  Resources for OffSec's WUMED/EXP-301

offsec-pen300/kali-rolling 2021.1.2 amd64
  Resources for OffSec's ETBD/PEN-300

offsec-pwk/kali-rolling 2021.1.2 amd64
  Resources for OffSec's PWK2/PEN-200
```

these two OSes are for pentesting, using `apt` as package manager. but parrot does not provide tool introductions.


get all package names:
```bash
apt list
```
you can retrieve package information in apt command, like:
```bash
apt show <package_name>
```
you will get homepage link and package description
if you want package dependencies you will also have it.

using `apt` one can retrieve package infos with simple command. find main metapackages like `parrot-tools-full` (parrot) and `kali-linux-everything` (kali) first, then retrieve dependency trees.

parrotos has [index.db](https://mirrors.tuna.tsinghua.edu.cn/parrot/index.db) which you can retrieve info from there. 

### blackarch

blackarch is based on archlinux, which has both official repo and user provided packages repo (AUR). the syntax is almost the same for `pacman` and `yaourt` to retrieve all available info of packages.


maybe you want to retrieve package information with pacman.

list all package information just like apt, description, dependencies, homepage and more.
```bash
pacman -Si
```
use some parser?

for aur repos, use yay or yaourt.
```bash
yaourt -Si
```
you may use dependencies to deduce relationship between packages, use description, man pages, wiki, manual and tutorials to understand the usage of packages.

download main blackarch tool list:
```bash
curl https://www.blackarch.org/tools.html > tools.html
```

### alpine


alpine linux is able to [download man page alone without installing package](https://georgegarside.com/blog/technology/alpine-linux-install-all-man-pages/)
```bash
apk list -I | sed -rn '/-doc/! s/([a-z-]+[a-z]).*/\1/p' | awk '{ print system("apk info \""$1"-doc\" > /dev/null") == 0 ? $ "-doc" : "" }' | xargs apk add
``````

### nuget

we can search in cli tool (not `dotnet nuget` (installed with dotnet sdk) but `nuget` ([installation guide](https://learn.microsoft.com/en-us/nuget/reference/nuget-exe-cli-reference))) and [web interface](https://www.nuget.org/).

the web interface seems allowing us to do some traversal on the parameter: `https://www.nuget.org/packages?page=<pagenum>&sortBy=relevance`

keep in mind the pagenum cannot be too big (like 2000).

### maven

there are tools for interacting with maven search api.

you can retrieve "pom.xml" to get package info like homepage and description.

maven central has [archtype-catalog](https://repo1.maven.org/maven2/archetype-catalog.xml) for retrieving all avaliable artifact names

maven search tools:

[mvn-search](https://github.com/erosb/mvn-search)

[mcs](https://github.com/mthmulders/mcs)

### npm

there's a [repo](https://github.com/nice-registry/all-the-package-names) storing up-to-date package names on github. after that, use [npm-description](https://www.npmjs.com/package/npm-description) to download description for every package.

### gem

change gem sources first:
```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

`gem list -r` really works. you just have to wait.

`gem info -r` list all remote gem infos, but too slow and not working, use only one package at a time.

### manpages

location of locally installed man pages: `/usr/share/man`

### vscode plugin

[web interface](https://marketplace.visualstudio.com/VSCode) for searching

