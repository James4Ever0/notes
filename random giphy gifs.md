---
title: random giphy gifs
created: '2022-09-11T04:28:27.713Z'
modified: '2022-09-11T07:23:51.941Z'
---

# random giphy gifs

## gif ratings

[official doc](https://support.giphy.com/hc/en-us/articles/360058840971-Content-Rating)

vulgar rate:

r > pg-13 > pg > g

while 'y' means accepting all shits, not 'youth' nor 'young'

## implementation

giphy has many extensible apis. i guess most media platforms are all the same (complex enough), but we have to start somewhere though...

giphy has 'clips' now. clips are gifs with sound, just like short videos.

beta key limitations:

1000 requests per day, 42 requests per hour

~~or just use the public beta key? does that subject to the rate limit?~~

this public beta key is trashed.

```javascript
var PUBLIC_BETA_API_KEY = 'dc6zaTOxFJmzC';
```

is this public api key? maybe it is both api and sdk key.
Gc7131jiJuvI7IdN0HZ1D7nh0ow5BU6g

api keys:
IoJVsWoxDPKBr6gOcCgOPWAB25773hqP
lTRWAEGHjB1AkfO0sk2XTdujaPB5aH7X

sdk keys:
6esYBEm9OG3wAifbBFZ2mA0Ml6Ic0rvy
sXpGFDGZs0Dv1mmNFvYaGUvYwKX0PWIh

to use api:
https://github.com/austinkelleher/giphy-api

to use sdk:
https://github.com/Giphy/giphy-js/blob/master/packages/fetch-api/README.md


find public api keys inside html:
```javascript
          window.GIPHY_FE_MOBILE_API_KEY = "L8eXbxrbPETZxlvgXN9kIEzQ55Df04v0"
          window.GIPHY_FE_WEB_API_KEY = "Gc7131jiJuvI7IdN0HZ1D7nh0ow5BU6g"
          window.GIPHY_FE_FOUR_O_FOUR_API_KEY = "MRwXFtxAnaHo3EUMrSefHWmI0eYz5aGe"
          window.GIPHY_FE_STORIES_AND_GIPHY_TV_API_KEY = "3eFQvabDx69SMoOemSPiYfh9FY0nzO9x"
          window.GIPHY_FE_DEFAULT_API_SERVICE_KEY = "5nt3fDeGakBKzV6lHtRM1zmEBAs6dsIc"
          window.GIPHY_FE_GET_POST_HEADERS_KEY = "e0771ed7b244ec9c942bea646ad08e6bf514f51a"
          window.GIPHY_FE_MEDIUM_BLOG_API_KEY = "i3dev0tcpgvcuaocfmdslony2q9er7tvfndxcszm"
          window.GIPHY_FE_EMBED_KEY = "eDs1NYmCVgdHvI1x0nitWd5ClhDWMpRE"
```

search for 'ear flops' to locate the tags in 'samoyed.html'
