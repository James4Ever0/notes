---
title: pyttsx3 cross platform tts generator
created: '2023-01-11T03:53:36.660Z'
modified: '2023-01-11T06:00:19.711Z'
---

# pyttsx3 cross platform tts generator

By looking into the [NaturalLanguage Framework](https://developer.apple.com/documentation/naturallanguage?preferredLanguage=occ) on macOS, I find text classifier and embeddings inside.

It will leverage default TTS engine on Windows and macOS, but for linux you must install espeak.

```python
import pyttsx3
engine = pyttsx3.init()

# dir(engine.getProperty("voices")[0]) -> ['age', 'gender', 'id', 'languages', 'name']

# The voices are related to languages. Set it properly.

# you want "en_US" and "zh_CN"
# [['en_US'], ['it_IT'], ['sv_SE'], ['fr_CA'], ['de_DE'], ['he_IL'], ['id_ID'], ['en_GB'], ['es_AR'], ['nl_BE'], ['en-scotland'], ['en_US'], ['ro_RO'], ['pt_PT'], ['es_ES'], ['es_MX'], ['th_TH'], ['en_AU'], ['ja_JP'], ['sk_SK'], ['hi_IN'], ['it_IT'], ['pt_BR'], ['ar_SA'], ['hu_HU'], ['zh_TW'], ['el_GR'], ['ru_RU'], ['en_IE'], ['es_ES'], ['nb_NO'], ['es_MX'], ['en_IN'], ['en_US'], ['da_DK'], ['fi_FI'], ['zh_HK'], ['en_ZA'], ['fr_FR'], ['zh_CN'], ['en_IN'], ['en_US'], ['nl_NL'], ['tr_TR'], ['ko_KR'], ['ru_RU'], ['pl_PL'], ['cs_CZ']]
engine.setProperty('voice', engine.getProperty("voices")[39].id)

engine.save_to_file("你好 世界", 'output.wav')
engine.runAndWait()

engine.setProperty('rate', 125) # setting up new voice rate

# The punctuals make the bot to pause for some time. Maybe you should control that yourself.
engine.save_to_file("你好，世界", 'output.wav')
engine.runAndWait()
```


