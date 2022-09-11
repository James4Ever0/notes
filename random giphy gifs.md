---
title: random giphy gifs
created: '2022-09-11T04:28:27.713Z'
modified: '2022-09-11T05:14:03.252Z'
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

api keys:
IoJVsWoxDPKBr6gOcCgOPWAB25773hqP
lTRWAEGHjB1AkfO0sk2XTdujaPB5aH7X

sdk keys:
6esYBEm9OG3wAifbBFZ2mA0Ml6Ic0rvy

to use api:
https://github.com/austinkelleher/giphy-api

to use sdk:
https://github.com/Giphy/giphy-js/blob/master/packages/fetch-api/README.md
