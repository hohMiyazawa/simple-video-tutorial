# 1. Container formats

When you're encountering a video file, you're usually not looking directly at the real thing. Instead, what you have is probably a **container format**.

- .mkv
- .webm
- .mp4
- .avi

Any of those extensions looking familiar? They are all container formats.
They consist of "video and other stuff". Actually, many aren't even required to contain video, so the more accurate description is "they contain stuff".

Imagine if you had to press "play" for both a video file and an audio play at the same time in order to watch an episode of something. Not very convenient. Instead, the video and audio are stuffed inside a container so they can be experienced together. Even if they are completely unrelated things.
Subtitles can be put inside many containers too (even if not all containers want them). Sure more convenient than manually adding a subtitle file every time you want to watch something.

Containers have rules for what they can contain. If they didn't, you would never be able to be sure that you could play them.
Matroska (.mkv) allows a whole lot of whacky stuff, so to fully support it, you need a media player than can deal with a wide range of video and audio.
WebM is the opposite, video in WebM must be VP8, VP9 or AV1, and audio must be Vorbis or Opus. No subtitles allowed. These limits are to make sure than most browsers can play WebM files, making it suitable for internet usage. (fun fact: WebM is the exact same thing as Matroska, just with extra limits).

Images also have container formats. The images you usually deal with (PNG, JPEG, WebP), *are* container formats. But since you usually don't need access to the raw image data, you don't really have to think much about it and let your image viewer deal with it.

Stuffing things into containers is called **muxing**.

Separating containers into "stuff" again ("stuff" is usually called "streams" or "bitstreams") is called **demuxing**.

Muxing and demuxing is *fast*. Nothing is changed about the video or audio, it's just copied from one place to another.
There's no quality loss.
But if you need to change the video to a different format so it fits in the container you are trying to stuff it into, *then* things get slow. And lossy.

When your video player starts playing a file, it begins by running the container through a **demuxer**, to get access to the video and audio streams.
