---
title: 'song recognition, music recognition api'
created: '2022-09-12T15:40:57.656Z'
modified: '2022-09-12T16:44:17.219Z'
---

# song recognition, music recognition api

## self-hosted

[shazam](https://github.com/bmoquist/Shazam) algorithm

## audiotag.info

[portify](https://github.com/adbcode/portify) recognize local music and add them to spotify playlist

[wav_to_info.py](https://github.com/whuds/song-classifier/blob/7c6771312e45a0f72f966a77506317d5cc98212a/metadata/code/wav_to_info.py)

[audio identifier](https://github.com/jndrf/audioidentifier/tree/b110ff7ce25b1a2d758b1b9baac2d809ae928e4e)

[nowspinning](https://github.com/ChristopherCarignan/NowSpinning/blob/master/NowSpinning.py) get song info and cover art

## shazam

[shazamio](https://github.com/dotX12/ShazamIO) reverse engineered shazam api with many supported functions

[audiorec](https://github.com/marin-m/SongRec) shazam client for linux, with cli support

## midomi houndify soundhound

to get track info from soundhound (no cookie):
https://www.midomi.com/api/track?trackID=100282107076607645

the houndify music recognition api:
wss://houndify.midomi.com/

some lib for midomi found over [here](https://github.com/Azarattum/AmadeusCore/blob/3bbb39e4d92508f036dd7be68b66681013866cba/src/components/app/models/recognizers/midomi.recognizer.ts)
it can also bridge yandex music recognition api

houndify also have api for that, but requires credit

free credits per day: 100

[soundhound now](https://docs.houndify.com/reference/SoundHoundNowCommand#field_SingleTrackResult) requires 1 credit

[soundhound python sdk](https://pypi.org/project/Houndify)
