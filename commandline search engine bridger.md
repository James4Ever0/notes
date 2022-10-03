---
title: commandline search engine bridger
created: '2022-09-26T15:04:21.000Z'
modified: '2022-10-03T10:20:41.749Z'
---

# commandline search engine bridger

## nosql/nosqlite key-value json like document store databases

[this guy](https://github.com/coleifer/) makes database related libraries.

[lsm-db](https://lsm-db.readthedocs.io/en/latest/) fast key-value store using sqlite 4

[unqlite](https://github.com/coleifer/unqlite-python) Python bindings for the UnQLite embedded NoSQL database

[tinydb](https://github.com/msiemens/tinydb) json-oriented, mongo alike database

## reason to develop this

you are short of brain power. short of time to perspect and investigate.

many platforms now have recommendation engines, but they do not have powerful semantic search tools. what a pity. maybe i am interested in some 'unseen' stuff, but i want to get the thing that i currently need! fail to do so will limit my productivity.

## sentence embeddings

difference between 'symmetric' and 'asymmetric' retrieval questions from sbert.net:

symmetric means similar, asymmetric usually means question to answer.

[top 4 sentence embedding techniques using python](https://www.analyticsvidhya.com/blog/2020/08/top-4-sentence-embedding-techniques-using-python/)

[sentence to vector](https://github.com/prabha88978/Sentence-To-Vector)

tutorial: [sentence vector word2vec](https://www.baeldung.com/cs/sentence-vectors-word2vec)

[sentence2vec based on word2vec](https://github.com/stanleyfok/sentence2vec)

## similarity search and clustering

facebook [faiss](https://github.com/facebookresearch/faiss/watchers)

[hnswlib](https://github.com/nmslib/hnswlib) Header-only C++/python library for fast approximate nearest neighbors

spotify [annoy](https://github.com/spotify/annoy) Approximate Nearest Neighbors in C++/Python optimized for memory usage and loading/saving to disk

## problems

- [ ] enable copy/pasting/selection in console

- [ ] make reversible/auto-cleanup feature when copy and pasting

- [x] reverse stemming and keywords highlighting

- [ ] memory efficient embedding querying/storage via sql or binary format

txtai store to sqlite: [Build an Embeddings index from a data source](https://github.com/neuml/txtai/blob/master/examples/03_Build_an_Embeddings_index_from_a_data_source.ipynb)

- [ ] make "complete" excerpt by looking ahead and backward to find the closest sentence start/stop and/or use gpt completion method instead? still need punctual or sentence start/stop index identification.

## offline

### terminal interface builder

[rich](https://pypi.org/project/rich/) and [tutorial](https://python.plainenglish.io/build-your-own-search-engine-in-python-part-1-2-the-engine-3b060e49eb84)

[textual](https://github.com/Textualize/textual)

[urwid](https://github.com/urwid/urwid)

[plie](https://plie.readthedocs.io/en/master/renderer.html)

### ai assisted search engine libraries

[jina-ai](https://github.com/jina-ai/jina) and docarray

[txtai](https://github.com/neuml/txtai)

[typesense](https://github.com/typesense/typesense)

[zinc](https://github.com/zinclabs/zinc) search

[fuzzy search](https://pypi.org/project/fuzzy-search/)

[fuzzy](https://pypi.org/project/Fuzzy/) phonic toolkit

### traditional search engine libraries

[pythonql](https://github.com/pythonql/pythonql) as extension of python syntax, able to search data in python data structure.

[jq](https://github.com/stedolan/jq) and [pyjq](https://pypi.org/project/pyjq/) as json search engine, [jqterm](https://jqterm.com/?query=.) as jq repl

[a curated search engine list](https://medevel.com/os-fulltext-search-solutions/)

[scout](https://scout.readthedocs.io/en/latest/server.html) sqlite based full text search

[whoosh](https://pypi.org/project/Whoosh/) with bm25 support

[python-searchengine](https://github.com/bartdegoede/python-searchengine) and [the tutorial](https://bart.degoe.de/building-a-full-text-search-engine-150-lines-of-code/)

## online
[surfraw](https://github.com/kisom/surfraw), or just [s](https://github.com/zquestz/s), is for some common parameter prefixes for searching on common websites. will open GUI browser or cli browser if configured with one.

surfraw supported:

```
W               -- Activate Surfraw defined web-browser
acronym         -- Look for acronyms definitions (www.acronymfinder.com)
ads             -- Search SAO/NASA Astrophysics Data System
alioth          -- Search Alioth (alioth.debian.org)
amazon          -- Search the amazon.com bookstore
archpkg         -- Search Arch Linux Packages (www.archlinux.org/packages/)
archwiki        -- Search the Arch Linux Wiki
arxiv           -- Search arXiv E-Print Archive for articles
ask             -- Question the web using Ask Jeeves (www.ask.com)
aur             -- Search aur.archlinux.org for PKGBUILDs
austlii         -- Search Australian Law docs (www.austlii.edu.au)
bbcnews         -- Search BBC News (news.bbc.co.uk)
bing            -- Search the web using Microsoft's Bing (www.bing.com)
bookfinder      -- Search for books using www.bookfinder.com
bugmenot        -- Bypass compulsory web registration with bugmenot.com
bugzilla        -- Search for bugs on Bugzilla bugtrackers
cablesearch     -- search for leaked diplomatic communications
cia             -- Search CIA documents at www.cia.gov
cisco           -- Search Cisco documentation (www.cisco.com)
cite            -- Search computer science papers (citeseerx.ist.psu.edu)
cliki           -- Search the common lisp wiki
cnn             -- Search on CNN (cnn.com)
comlaw          -- Search Australian Law using Comlaw (www.comlaw.gov.au)
commandlinefu   -- Search on www.commandlinefu.com
ctan            -- Search the Comprehensive TeX Archive Network (ctan.org)
currency        -- Convert currencies with the Universal Currency Converter (www.xe.net/ucc)
cve             -- Search for CAN assignments in CVE
debbugs         -- Search the debian BTS (bugs.debian.org)
debcodesearch   -- Search debian source code
debcontents     -- Search contents of debian/ubuntu packages (packages.debian.org/packages.ubuntu.com)
deblists        -- Search debian mailing lists (lists.debian.org/search.html)
deblogs         -- Show changelogs for a package in Debian main (changelogs.debian.net)
debpackages     -- Search debian/ubuntu packages (packages.debian.org/packages.ubuntu.com)
debpkghome      -- Visit the home page for a Debian package
debpts          -- Search the Debian Package Tracking System (packages.qa.debian.org)
debsec          -- Search the Debian Security Tracker for CVE ids or package names
debvcsbrowse    -- Browse the VCS repository for a Debian package
debwiki         -- Search the Debian Wikis (wiki.debian.org & women.debian.org/wiki)
deja            -- Search usenet using Google Groups (groups.google.com)
deli            -- Search Delicious bookmarks
discogs         -- Search the Discogs database of music information (www.discogs.com)
dmoz            -- Search the Open Directory Project web directory (dmoz.org)
duckduckgo      -- Securely search the web using duckduckgo (www.duckduckgo.com)
ebay            -- Search the Ebay auction site
etym            -- Look up word origins at www.etymonline.com
excite          -- Search on Excite (www.excite.com)
f5              -- Search F5 related information (www.f5.com)
finkpkg         -- Search Fink packages (pdb.finkproject.org)
foldoc          -- The Free On-Line Dictionary Of Computing (foldoc.org)
freebsd         -- Search FreeBSD related information (www.freebsd.org)
freedb          -- Search for cd track listings in FreeDB (www.freedb.org)
freshmeat       -- Search Freshmeat (www.freshmeat.net)
fsfdir          -- Search the FSF/UNESCO Free Software Directory (directory.fsf.org)
gcache          -- Search the web using Google cache (www.google.com)
genbugs         -- Search the Gentoo bug tracker (bugs.gentoo.org)
genportage      -- Search gentoo-portage.com for packages
github          -- Search GitHub (https://github.com)
gmane           -- Search mailing list with gmane (gmane.org)
google          -- Search the web using Google (www.google.com)
gutenberg       -- Search for books on Project Gutenberg (gutenberg.org)
imdb            -- Search the Internet Movie Database (www.imdb.com)
ixquick         -- Search the web using ixquick [HTTPS] (www.ixquick.com)
jamendo         -- Search Jamendo: free music with Creative Commons licenses (www.jamendo.com)
javasun         -- Search Java API docs (java.sun.com)
jquery          -- Search the jQuery documentation (api.jquery.com)
l1sp            -- Search lisp documentation
lastfm          -- Search last.fm
leodict         -- Search Leo's German <-> English dictionary (dict.leo.org)
lsm             -- Search the Linux Software Map
macports        -- Search macports packages (macports.org)
mathworld       -- Search Wolfram MathWorld
mdn             -- Search the mozilla developer network (developer.mozilla.org)
mininova        -- Search the mininova bittorent source.
musicbrainz     -- Search MusicBrainz (musicbrainz.org)
mysqldoc        -- Search mysql documentation (dev.mysql.com)
netbsd          -- Search NetBSD related information (www.netbsd.org)
nlab            -- Search the nLab wiki (http://ncatlab.org)
ntrs            -- Search the NASA Technical Report Server
openbsd         -- Search OpenBSD related information (www.openbsd.org)
openports       -- search openports for OpenBSD packages
opensearch      -- Search an OpenSearch-enabled website
oraclesearch    -- Search an OpenSearch-enabled website
pasearch        -- Search the unofficial Penny Arcade archives (pipefour.org/pa)
pgdoc           -- Search postgres documentation (www.pgdoc.com)
pgpkeys         -- Search the PGP key database
phpdoc          -- Search php documentation (php.net)
pin             -- Search Pinboard bookmarks (http://pinboard.in)
piratebay       -- Search The Pirate Bay (http://thepiratebay.org)
priberam        -- Look up word in Priberam online dictionary (www.priberam.pt/dlpo)
pubmed          -- Search medical/molbio databases (www.ncbi.nlm.nih.gov)
rae             -- Busca en el diccionario de la Real Academia de la Lengua Española (Spanish Dictionary)
rfc             -- Search RFCs (internet standards documents)
rhyme           -- Search for rhymes et al using Lycos Rhyme (rhyme.lycos.com)
rpmsearch       -- Search for RPMs in various distros
scholar         -- Search Google Scholar (scholar.google.com)
scicom          -- Search Scientific Commons
scirus          -- Search for science using Scirus (scirus.com)
scpan           -- Search the Comprehensive Perl Archive Network (search.cpan.org)
searx           -- Search using searx metasearch engine instances (searx.me)
slashdot        -- Search stories on Slashdot (www.slashdot.org)
slinuxdoc       -- Search entries in LDP (www.linuxdoc.org)
sourceforge     -- Search SourceForge (www.sourceforge.net)
springer        -- Search Springer for Books and Articles
stack           -- Search Stack Overflow
stockquote      -- Get a single stock quote (multiple providers)
thesaurus       -- Look up word in Merriam-Webster's Thesaurus (www.m-w.com)
translate       -- Translate human languages
urban           -- Search urbandictionary.com for a definition
w3css           -- Validate a CSS URL with the w3c CSS validator (jigsaw.w3.org/css-validator)
w3html          -- Validate a web page URL with the w3c validator (validator.w3.org)
w3link          -- Check web page links with the w3c linkchecker (validator.w3.org/checklink)
w3rdf           -- Validate a RDF URL with the w3c RDF validator (validator.w3.org)
wayback         -- Search The Internet Archive's Wayback Machine for a URL (archive.org)
webster         -- Look up word in Merriam-Webster's Dictionary (www.m-w.com)
wetandwild      -- Real time weather information (many sources)
wikipedia       -- Search the free encyclopedia wikipedia
woffle          -- Search the web using Woffle (localhost:8080)
wolfram         -- Ask questions of the computational knowledge engine
worldwidescience -- Search for science with www.worldwidescience.org
yacy            -- Search YaCy P2P search, including ScienceNet
yahoo           -- Search Yahoo categories (www.yahoo.com)
yandex          -- Search the web using Yandex (yandex.ru)
youtube         -- Search YouTube (www.youtube.com)
yubnub          -- Use the social command-line for the web (yubnub.org)
```

S supported:
```
    500px
    8tracks
    aliexpress
    allocine
    amazon
    archpkg
    archwiki
    ardmediathek
    arstechnica
    arxiv
    atmospherejs
    aur
    baidu
    bandcamp
    bgr
    bigbasket
    bing
    brave
    buzzfeed
    cnn
    codepen
    coursera
    cplusplus
    cppreference
    crates
    crunchyroll
    debianpkg
    dict
    digg
    diigo
    dockerhub
    dribbble
    duckduckgo
    dumpert
    ecosia
    engadget
    explainshell
    facebook
    flickr
    flipkart
    foursquare
    freebsdman
    freshports
    gibiru
    giphy
    gist
    github
    gmail
    go
    godoc
    goodreads
    google
    googledocs
    googleplus
    hackernews
    idealo
    ietf
    ifttt
    imdb
    imgur
    inbox
    instagram
    kaufda
    kickasstorrents
    libgen
    linkedin
    lmgtfy
    macports
    magnetdl
    mdn
    medium
    metacpan
    msdn
    naver
    netflix
    nhaccuatui
    npm
    npmsearch
    npr
    nvd
    openbsdman
    overstock
    packagist
    presearch
    phandroid
    php
    pinterest
    postgresql
    python
    quora
    qwant
    reddit
    regex
    rottentomatoes
    rubygems
    shodan
    soundcloud
    spotify
    stackoverflow
    steam
    taobao
    thepiratebay
    theregister
    torrentz
    twitchtv
    twitter
    ultimateguitar
    unity3d
    upcloud
    vimeo
    wikipedia
    wolframalpha
    yahoo
    yandex
    youtube
    zdf
    zhihu

```
