# Simple Screen Capture

A script using ffmpeg to do screen capture in 3 simple audio settings: monitor
audio only, audio input only or both. This script will ease the task of
recording videos and also live streaming to RTMP streams

## Available options

```
    -h|--help
        Print this help.
    -s|--no-sound source
        Disables the sound capture for {source}.
    --rtmp
        The output is rtmp stream.
    -o|--out {destination}
        The destination to output the video to (file, rtmp url, etc.).
    -a|--audio-device {device}
        The audio device.
    -v|--video_size {geometry}
        Video geometry (format: WxH). This is passed to ffmpeg's -s
        argument.
    -f|--offset {offset}
        Video offset of the display origin point (format: W,H).
```

## Example usage

There are two simple use cases: video record and RTMP stream.

### Video recording

One can simply call `ssc` which will capture the screen with the detected video
size, the audio from both default microphone and audio monitor stream, and output
a file in the file `out.mkv`.

```sh
$ ssc
```

If one wants to record his 1920x1080 screen on the right of his main monitor and
output a `ogv` file, he can do as follows:

```sh
$ ssc -f 1920,0 -o my_awesome_video.ogv
```

### YouTube streaming

Go on Youtube and recover your stream key `${STREAM_KEY}` and issue the
following command:

```sh
$ ssc --rtmp -o "rtmp://a.rtmp.youtube.com/live2/${STREAM_KEY}"
```

The stream will contain audio from both monitor and input device mixed together
with video.

## Author

Simon Désaulniers <sim.desaulniers@gmail.com>

