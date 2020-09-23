Video is just a bunch of images ("frames") displayed very quickly.

Some simple video codecs, usually those aimed at being very very fast, will just store all the frames as individual images.
That is not very efficient for compression though. In actual video, most frames look very similar to the previous frame, so to save space, you can store only the *difference* from the previous frame.

That means video will have two types of frames:

1. I-frames ("Intra frames", "key frames"), which is a standalone image. These are needed every time the scene changes.
2. P-frames ("Inter frames"), which encodes a frame as the difference from the previous ones.

There's also a third kind, B-frames, which is kinda like a P-frame except it also looks at future frames. But that's not possible for things like streaming.

For the best possible compression, we only want I-frames when strictly necessary. But having a large distance between key frames also has some disadvantages:

- If you want to cut up compressed video into parts, this can only be done at key frames.
- When seeking, your video player has to decode all the way from the previous key frame. If this distance is large, it may take a while.
- When streaming video, if a keyframe is lost, all the following frames will be corrupted until a new keyframe arrives.
- Few key frames limits parallel video encoding. If every frame was a key frame, we could have one CPU core for each frame and compress the entire video in parallel.
