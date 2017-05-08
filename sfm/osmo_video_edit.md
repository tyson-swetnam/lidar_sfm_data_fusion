# DJI Osmo videos 

Concurrent to the DJI Phantom 3/4 flights I walked along each transect of the study area taking 4k videos using a gimbal stabilized DJI Osmo.

The Osmo was held in near nadir and up to 4 oblique angles to simulate the same collection pattern as the DJI Phantom.

The elevation of the Osmo was ~ 2.5 - 3.5 meters above ground level.

## Video decomposition

I used `ffmpeg` to convert the .mp4 and .avi files to JPEG images

```
ffmpeg -i myvideo.avi -qscale:v 2 -vf fps=3 img%03d.jpg
```

where `fps=3` creates an image rate of 3 frames a second (we shot our 4k video at 24 and 30 fps).

We do not need to extract all 24 frames per second of film. 

I use `%03d` to add the number of images, here I am trying to keep my images under 1,000 per video.
