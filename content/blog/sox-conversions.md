---
title:       "SOX Conversions, Raw Files, Splitting And Merging Channels"
type:        blog
date:        2010-01-21
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/275 ]
blog categories: [ "bash", "music", "operating systems", "linux", "os x", "ubuntu", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today the command line audio utility sox gave me some head aches while I was working on some sample files for a listening test I prepare for my current research.
I actually just needed to convert a stereo 44.1kHz floating point WAV file to 48kHz, split it into single mono files (one for each channel), convert the mono files to raw PCM, process some filter on the raw files, convert them back to mono WAVs, merge the mono files back to stereo again and convert back to 44.1kHz.
To accomplish this, I used these commands, which were neither well documented, nor correctly referred to by most of the blogs I've read today.

The following command simply converts the samplerate to 48kHz (nothing special):

```bash
sox infile.wav -r 48k outfile.wav
```

These commands split the stereo file into two mono files (left and right channel):

```bash
sox infile.wav outfile.l.wav remix 1
sox infile.wav outfile.r.wav remix 2
```

The following commands create a mono mix-down of a stereo file

```bash
sox infile.wav outfile.wav remix 1,2
sox infile.wav outfile.wav remix 1-2
```

The following command converts a wav file to a raw 16-bit signed integer mono file with 48kHz:

```bash
sox infile.wav -b 16 -s -c 1 -r 48k -t raw outfile.raw
```

The following command converts a raw file back to WAV (option -t raw is mandatory!):

```bash
sox -b 16 -s -c 1 -r 48k -t raw infile.wav outfile.wav
```

The following command merges the two mono files into one stereo WAV file (order: left, right):

```bash
sox -M input.l.wav input.r.wav output.wav
```

This command converts the 48kHz back to 44.1kHz:

```bash
sox input.wav -r 44100 output.wav
```

Another nice command, not too intrusively documented is the following:

```bash
sox audiofile.wav -n stat
```

which allows scripts to read audio signal attributes like overall gain, mean values etc. from audio files and use them afterward e.g. for normalization, dc-offset compensation, etc.

Another command for acquiring signal information is soxi:

```bash
soxi audiofile.wav
```

The main problem for me today was the flag '-t raw', which is not stated as mandatory in the sox manpage for raw file, but it actually is! Anyhow, the remaining part is pretty straight forward :)  

Cheers,  
is
