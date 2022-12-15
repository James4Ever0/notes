---
title: download/collect info of hack tools
created: '2022-12-12T14:35:02.642Z'
modified: '2022-12-15T00:53:23.604Z'
---

# download/collect info of hack tools

what to do when chatgpt is not for everyone?

## general introduction

this is about **information gathering**, so you might learn how to scrape AI models, AI notebooks, tutorials, code snippets from websites/search engines/social media as well.

given the name of the hack tool, you may not be able to tell what the tool is (written in python? hosted on github? online tool?) and you want to use search engine to find possible entries. you may take snapshots on these pages and index them.

if the hack tool is linked to some website/manual, you can index the website. if you find it inside some package index or package manager, you will know how to install the package.

you may miss the wiki, forum, tutorials. you know where to get them.

here are few sources where you can learn things from:

[darknet.org.uk](https://www.darknet.org.uk/) where you learn hacking and [hack tools](https://www.darknet.org.uk/category/hacking-tools/)

[null byte](https://null-byte.wonderhowto.com/) in [wonderhowto](https://www.wonderhowto.com/)

you also have `brew` `sdkman` `macport` `pkgsrc` `chocolatey` `scoop` `winget`  `snap` `portage` `conda` `flatpak` `rpm` `urpm` `yum` `cargo` `dnf` indexes and more to scrape. maybe it is time to improve your searching skill? (**select few web domains you want to learn things from, then perform the query, still you have to deal with keywords generation and site selection**)

[cyborg hawx linux](https://launchpad.net/~cyborg-hawk/+archive/ubuntu/stable), backtrack linux may join the parade.

for language specific package indexs, we have `hackage` `CPAN` `CRAN` `crates.io` and more (where are package indexes for `C` `C++` `Pascal` `BASIC` `assembly` `lisp` `prolog` `lua` and more? visit [awesomeopensource](https://awesomeopensource.com/) then use combined topics to find [package managers for c](https://awesomeopensource.com/projects/c/package-manager) and more. you also have [libraries.io](https://libraries.io/) to monitor libraries across all package managers). just check [tuna mirror site](https://mirrors.tuna.tsinghua.edu.cn/) and get a view on that. you may want a network directory traversal tool akin to `find` in local filesystem, without downloading anything "binary" but just logging all possible urls for you to inspect. (with file size)

after all these information collecting, you must categorize them (topic modelling), retrieve info when needed (semantic searching? recommendation? dialog based GPT?). you may find many things not obviously a hack tool but in general fit well into specific needs.

with all packages being scraped, you need to deduplicate it a little bit, either by name or homepage.

## case specific

### github

repo named with "awesome" means this is a collection of handpicked resources

you will find github links on web, social media, instant messaging and forums

[Scraper](https://github.com/henson/Scraper) scrape popular github repositories every day

[gitsuggest](https://github.com/csurfer/gitsuggest) recommend github repos

[How to Use the GitHub API to List Repositories](https://fusebit.io/blog/github-api-list-repositories/?utm_source=cn.bing.com&utm_medium=referral&utm_campaign=none)

[PyGithub](https://pygithub.readthedocs.io/en/latest/introduction.html) use python to automate github api v3

if you want all README pages on github, you first need to collect all github repo urls. you may also collect info on github repos (OSINT). you can retrieve all repos link to given user with github api (quota limited). you can search github on github or search engine with some juicy/promising keywords then collect repo name, username, keywords, repeat the search.

there are few github repo archives avaliable for download. the github archive program packed many repos to arctic, the list is called [Greatest Hits](https://archiveprogram.github.com/assets/img/archive-repos.txt)

[gharchive](https://www.gharchive.org/) provides many websites for monitoring github repos, though stopped archiving since 2016

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

parrotos has [index.db](https://mirrors.tuna.tsinghua.edu.cn/parrot/index.db) which you can retrieve info from there, or "Packages" for general debian package index, or anything you think is metadata.

### chocolatey

note: deprecated since v2.0, can only be used to list local packages
```bash
choco list
```

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
```

### pypi/pip

i remember you have scraped tsinghua pypi index, containing many python tools.

retrieve python package info as json:
`https://pypi.org/pypi/<package-name>/json`

visit [pypi simple index](https://pypi.tuna.tsinghua.edu.cn/simple/) to get all package names. but the info is clearly on the other page. you retrieve this from pypi. use the below commandline tool?

`pypi [information|description] <package_name>`

documentation url is provided separately from mainpage.

[commandline tool for searching in pypi](https://pypi.org/project/pypi-command-line/)

install it, then run:
```bash
pypi search <query>
```

it also provides "read-the-docs" to search in documentation of a package, detailed info

### nuget

we can search in cli tool (not `dotnet nuget` (installed with dotnet sdk) but `nuget` ([installation guide](https://learn.microsoft.com/en-us/nuget/reference/nuget-exe-cli-reference))) and [web interface](https://www.nuget.org/).

list all packages:
```bash
nuget list
```

get package information:
```
nuget list <packageName> -Verbosity detailed
```

[query all package information without nuget](https://learn.microsoft.com/en-us/nuget/guides/api/query-for-all-published-packages)

the web interface seems allowing us to do some traversal on the parameter: `https://www.nuget.org/packages?page=<pagenum>&sortBy=relevance`

keep in mind the pagenum cannot be too big (like 2000).

### maven

there are tools for interacting with maven search api.

you can retrieve "pom.xml" to get package info like homepage and description.

maven central has [archtype-catalog](https://repo1.maven.org/maven2/archetype-catalog.xml) for retrieving all avaliable artifact names

maven search tools:

[mvn-search](https://github.com/erosb/mvn-search)

[mcs](https://github.com/mthmulders/mcs)

### homebrew

reading the source code and according to [brew api docs](https://formulae.brew.sh/docs/api/) i found [this url](https://formulae.brew.sh/api/formula.json) is for retrieving all formula info on brew index, and [this](https://formulae.brew.sh/api/cask.json) for casks.

also run this command for showing local cached package infos:
```bash
brew info --json --all
```

### npm

there's a [repo](https://github.com/nice-registry/all-the-package-names) storing up-to-date package names on github. after that, use [npm-description](https://www.npmjs.com/package/npm-description) to download description for every package.

[all-the-package-repos](https://github.com/nice-registry/all-the-package-repos) contains repo information (github, gitlab) of every npm package

### gem

change gem sources first:
```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

`gem list -r` really works. you just have to wait.

`gem info -r` list all remote gem infos, but too slow and not working, use only one package at a time.

### manpages

you can download man pages before installing package

use "dman" by bikeshed (not avaliable on kali, maybe on ubuntu?)

```bash
apt-get install bikeshed
```

or browse manpages on web, [tutorials on linux and languages](https://linux.die.net)

[man pages with different sections (categories)](https://linux.die.net/man/)

[hierachical manpages of ubuntu](https://manpages.ubuntu.com/manpages)

[dman for ubuntu man pages](https://manpages.ubuntu.com/dman)

location of locally installed man pages: `/usr/share/man`

### vscode plugin

[web interface](https://marketplace.visualstudio.com/VSCode) for searching

