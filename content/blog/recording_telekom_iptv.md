---
title:       "Recording from Telekom IPTV to DVD"
type:        blog
date:        2010-01-02
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/270 ]
blog categories: [ "linux", "os x", "ubuntu" ]
flattr username: [ "nesono" ]

---

<!--more-->
Some days ago, my father asked me if I could record TROY for him, which was broadcasted around Christmas 2009 by a public TV station.
As I am a customer of T-Entertainment (the IPTV solution from Deutsche Telekom) I suffer from getting my recordings out of my media receiver box onto a shared medium. 
Anyhow, I heard from a colleague of mine that you can watch IPTV using the [VLC][1] player - as long as you are a customer of T-Entertainemt of course ;)
Additionally, the public TV stations had an HDTV showcase during Christmas and years eve and so I thought I should give it a try and record the stream in HDTV.

So I started searching for the multicast address of the HDTV stream and found it somewhere in the [web][2].
I started VLC and opened `File` -> `Network` and entered the multicast RTP information using 'Open RTP/UDP Stream'.
After this, I started the `Streaming/Exporting Wizard` and select the currently active stream as the source.
By that, I simply dumped the MPEG-TS stream onto my local hard drive.

After the movie has ended, I could open the transport stream with VLC.
The next step now was to convert the HDTV MPEG-TS stream, which contained H.264 video and MPEG Layer 2 audio to a DVD compatible format.
I tried several tools, e.g. Toast 10 Titanium, Movie Gate 2, ffmpegX, mencoder and transcode, but none of them produced a satisfying output.
The final choice was so simple, that it is almost embarrassing to note.
But so what, it was the reason that I started this blog entry and so here it is:

```bash
ffmpeg -i troja.ts -target pal-dvd troja.mpg
```

After that, I still had to re-quantize the video stream, but anyhow - it worked at least :)

That's it and cheers,  
iss

[1]: http://www.videolan.org "VideoLAN home page"
[2]: http://forum.digitalfernsehen.de/forum/t-home/236555-neuer-hd-showcase-ard-zdf-2.html
