---
created: 2022-07-09T02:17:05+08:00
modified: 2022-07-09T02:31:53+08:00
---

# Cut Music Scenes With Lyrics and BPM

def compare(a,b,reverse=False):


seg_low, seg_high = get_allowed_segments(bpm, low, high, tolerance=0.8) # the tolerance is compared with a common function called compare. it can be customized to output only value >=1 or vice versa.
candidates = sorted_lyrics_nearby_bpm_candidates + sorted_remained_bpm_candidates # priortize lyrics candidates.
