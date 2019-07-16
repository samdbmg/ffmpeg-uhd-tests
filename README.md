# Generate a per-pixel test pattern

Based on a silly idea: https://twitter.com/mikechislett/status/1150861136239239168

But unlike that tweet, this flashes each pixel for one frame, and repeats every 100 lines (or other configured value)

## To build it:
- Be on Linux
- Install CMake and a compiler (`sudo apt install cmake build-essential`)
- Install FFmpeg (`sudo apt install ffmpeg libavcodec-dev libavformat-dev libavutil-dev libswscale-dev`)
- `(mkdir build && cd build && cmake .. && make)`

## To run it:
Something like:
```
build/ffmpeg-uhd-test hd-flash.mp4 1920 1080 100
```

## Can I see the output files?
Yes! https://www.dropbox.com/sh/euny7f5ffpog6m2/AACTXWU0bW2LjnmQ5MfGQcyUa?dl=0

## Why is the file called muxing.c?
It started life as the [FFmpeg muxing example](https://ffmpeg.org/doxygen/4.1/muxing_8c_source.html)

I just changed the pattern and took all the audio bits out.
