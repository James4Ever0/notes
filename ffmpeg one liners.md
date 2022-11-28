---
created: 2022-09-12T02:11:01+08:00
modified: 2022-11-28T22:08:36+08:00
---

# ffmpeg one liners

# For all snippets, check documentation for details and settings.

## speed up ffmpeg encoding

[ffmpeg speedup cli flags](https://blog.csdn.net/weixin_39981360/article/details/111807188)

`ffmpeg -threads 4 -crf 28 -preset ultrafast`

# encode video from a V4L2 device, using specified settings.
# x265 worked somewhat better here and produced less skips (although uses 10x CPU compared to x264)
ffmpeg -f video4linux2 -framerate 30 -input_format mjpeg -video_size 1920x1080 -i /dev/video6 -c:v libx265 -preset ultrafast -c:a none -crf 20 out.mp4

# Convert a raw YUYV422 frame from my USB "microscope" to PNG:
# other valid pixel formats are e.g. rgb24 or yuv420p
ffmpeg -f rawvideo -video_size 2592x1944 -pixel_format yuyv422 -i input_yuyv422_2592x1944.dat -f image2 output.png

# copy a portion of a video, copying and not recoding. Might need to use the same container as the input
ffmpeg -i $input -ss $seek_to_seconds -t $output_length -c:v copy -c:a copy $output

# Export and show h.264 MVs
ffplay -flags2 +export_mvs input.mkv -vf codecview=mv=pf+bf+bb

# Show motion vector estimate on any input:
ffplay $input -vf mestimate=epzs:mb_size=16:search_param=32,codecview=mv=pf+bf+bb

# Select one frame every 10, set presentation time stamp to 10x (0.1*PTS), deshake, do not copy audio
ffmpeg -i MOV_3147.mp4 -vf 'select=not(mod(n\,10))',setpts=0.1*PTS,deshake=edge=blank:rx=64:ry=64:blocksize=4:contrast=31 -tune grain -crf 17 -an wolken-2-deshake.mkv

# Extreme high quality deshake:
ffmpeg -i input.mkv -vf 'select=not(mod(n\,20))',setpts=0.05*PTS,mestimate=hexbs,vidstabdetect=shakiness=10:result=transforms.trf
ffmpeg -i input.mkv -vf 'select=not(mod(n\,20))',setpts=0.05*PTS,mestimate=hexbs,vidstabtransform=crop=black:smoothing=0:optzoom=0
# or for pass 2
ffmpeg -i MOV_3147.mp4 -vf 'select=not(mod(n\,20))',setpts=0.05*PTS,vidstabtransform=crop=black:smoothing=180:optzoom=0:interpol=bicubic -an -vcodec libx265 -crf 16 -tune grain wolken-2-deshake.mkv

# Tonemap a ITU.2020 (HDR, high gamut, ususally 4K) video to ITU.709 (1080p)
# Also see: https://stevens.li/guides/video/converting-hdr-to-sdr-with-ffmpeg/
ffmpeg -i file.mkv -vf zscale=t=linear:npl=100,format=gbrpf32le,zscale=p=bt709,tonemap=tonemap=hable,zscale=t=bt709:m=bt709:r=tv,format=yuv420p -crf 20 -acodec copy output.mkv

# Extract all frames as <pattern>.jpg
ffmpeg -r 1 -i file.mp4 -r 1 frames_%05d.jpg

# Create video from all the frames (missing any codec spec):
ffmpeg -r 30 -i frames_%05d.jpg output.mp4

### XXX the following where copied from
###     https://hbish.com/ffmpeg-one-liners/
# Get infomation for a audio/video
ffmpeg -i file.mp3

# Convert video into images
ffmpeg -i video.avi image_output%d.jpg

# Split audio files
# Generate a section of the audio from the 30 second mark (start) for 15 seconds (duration)
ffmpeg -f mp3 -i input.mp3 -t 00:00:30 -ss 00:00:15 output.mp3

# Covert avi to animated gif
ffmpeg -i video.avi output.gif

# Add audio to a video file
ffmpeg -i music.mp3 -i video.avi output.mpg

# Extract audio from video file"&gt;## Useful for extracting music from youtube videos
# avi to mp3
ffmpeg -i video.avi -vn -ar 44100 -ac 2 -ab 192k -f mp3 output.mp3

# flv to mp3
ffmpeg -i video.flv -ar 44100 -ac 2 -ab 192k -f mp3 output.mp3
