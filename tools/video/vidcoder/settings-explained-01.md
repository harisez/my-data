https://digiex.net/threads/vidcoder-settings-tutorial-high-quality-h-264-x264-mkv-video-encoding.10725/

To Begin:

Choose your movie to encode on the main window and choose the [High Profile] preset to base your settings off of. It is important to first pick the [High Profile] preset and then go to the settings window to make your changes.

1-vidcoder-mainmenu.png 


Picture Tab:

- Keep the width the same as the original width (usually 720 for standard dvds) and make sure
"Keep Aspect Ratio" is checked.
- Anamorphic: Choose [Loose]. Don't worry if the display resolution says something different
than the storage resolution.
- Cropping: Choose [Automatic]

2-vidcoder-settings-picture-tab.png 


Video Filters Tab:

- Detelicine: Choose [Default], this setting is usually safe to keep at default.
- Decomb: Choose [Default], this setting is a smart deinterlacer. It will make sure to deinterlace
when needed...but if and only if when needed. It is therefore safe to leave on even if your source
is not interlaced.
- Deinterlace: [Off] No need for this since Decomb is smarter and will deinterlace if needed.
- Denoise: usually [Off]. However, if you have a very grainy, noisy source video, choose [Weak]
to smooth out some of the noise/grain. Choose [medium] only in very rare cases. Denoise
smooths out the picture, but it also eats away at detail. Therefore, I rarely use this setting. But if I
have a very noisy video and/or want to get the file size down a bit (denoise reduces detail, and
therefore also reduces the need for higher bitrate), I usually choose [weak].
- Deblock: [Off]

3-vidcoder-settings-video-filters-tab.png 


Video Tab:

- Video Codec: [H.264(x264)]
- Framerate (FPS): Depends. Usually [23.976]. If you know you have a constant framerate,
leave this at [Same as Source]. If you have a source with a variable framerate, you may have to
try encoding at both 23.976 and 29.97 to see what looks better. In most of my cases, 23.976 has
usually been the choice for sources with variable framerates. Note, Vidcoder may tell you (in the
blue box) that the input framerate is 29.97 when it may actually be variable. If you know or find
out that it is variable, and Vidcoder says input is 29.97, 23.976 may actually look better. So
bottom line, if you have a variable framerate source, choosing same as source will probably break
compatibility with various media streamers. Therefore you are forced to choose between 23.976
or 29.97. Although 9 times out of 10, I have gone with 23.976...you should still test encoding,
trying each one.
- Target Size: Depends. More on how to choose this later.
- 2-Pass Encoding: turned [on] if using Target Size
- Turbo First Pass: turned [off]

4-vidcoder-settings-video-tab.png 


Audio Tab:

- Choose your audio stream (usually first one...other streams may include commentary track,
other languages, etc.
- Choose [AC3/DTS Pass-through].
- AC3/DTS Pass-through "passes through" the audio. Meaning, the audio in your encoded file will
be the exact same quality audio track that's included with your source file. Anything besides
Pass-through will be lossy, meaning you will lose some quality. The only reason to "downmix" to
another codec such as AAC is if your target device doesn't support AC3.

5-vidcoder-settings-audio-tab.png 


Advanced Tab:

Encoding:
Reference Frames: 8
Maximum B-Frames: 8
CABAC: Checked (on)
8x8 Transform: Checked (on)
Weighted B-Frames: Checked (on)
Pyramidal B-Frames: [Normal (default)]

Psychovisual:
No DCT-Decimate: unchecked (off)

Analysis:
Adaptive B-Frames: [Optimal]
Adaptive Direct Mode: [Automatic]
Motion Estimation Method: [Uneven Multi-Hexagon]
Subpixel Motion Estimation: [10]
Motion Estimation Range: [32]
Adaptive Quantization Strength: left untouched (default)
Psychovisual Rate Distortion: left untouched (default)
Psychovisual Trellis: [0.10] (two notches up from the default which is 0)
Deblocking: [0, 0] (default)
Partition Type: [All]
Trellis: [Always]

Manual Adjustment to Options String:
On the Advanced tab, you will see a box for "Options String" at the bottom. Manually change rclookahead
from 50 to 100. There is no way to change this value from the gui, however, it can be
manually changed in the options string box.

Options String:
When you are done choosing all of your options, the Options String should look like this:
[rc-lookahead=100:ref=8:bframes=8:badapt=
2:Direct=auto:me=umh:Subme=10:merange=32:analyse=all:trellis=2:Psy-rd=1.0,0.10]


Preset:
- Click on "save as..." at the top of the settings window to save your settings for future use.

6-vidcoder-settings-advanced-tab.png 

Final Notes:
These settings require a lot of juice from your computer. I have an Intel i7 (quad core / hyperthreading / turbo boost) with 8gb of ddr3 ram. It really helps to have a powerful processor for encoding. With my system and these settings, I get an average encoding speed of about 12-15fps. A two-pass encode takes about 3 hours. It's lengthy. But to me it's worth it.

These settings create very high quality videos with an acceptable file size (higher settings = better picture and better compression). So my computer basically always has Vidcoder running. If these settings are just too much for your computer to handle, and you can't get a new computer : ), the first setting you may want to adjust down is the Motion Estimation Range. 32 is kind of overkill. Higher values are good for high action videos. But you can get away alright with the default which is 16. You will see an increase in speed if you lower this value.

Then I would next maybe drop Subpixel Motion Estimation from 10 to 9. If you still need to boost your speed, you could try lowering your Reference Frames and Maximum B-Frames from 8 to 6 or even lower. Just remember, you may then have to compensate for less compression and up your target size. You could also turn on [Turbo First-Pass]. You'll see almost no difference from regular 2-pass.


How to Choose your Target Size:

So how do we know what target size to use? After all, different video sources require different bitrates (thus different sizes) to achieve the same quality. An old grainy video may need a higher bitrate and require a larger size. Every video is a little different and we shouldn't take a "one-sizefits- all" approach. The standard of old was: 350mb for a 1 hour (actually around 45 min without commercials) show. And forget 5.1 audio...that took up too much space. It was 2-channel mp3
128 bitrate. I don't know how this precedent got started, but I could strangle whoever came up with this. 350mb is almost never enough to create a good looking video...even with the high compressing x264 codec. Perhaps it was because then you could fit two (blocky looking) episodes on one cd (700mb). Well, we no longer rely on cd's. We have hard drives and flash drives. Hard drive space is relatively cheap, so let's worry about quality over size. Especially if you plan on streaming your files to a TV.

x264 comes with a setting called "Constant Quality", often referred to as CRF. This is a great feature. Basically, you set it at a value, and then let the encoder figure out what bitrate/size is needed to attain that quality. There are a couple benefits. One is that you don't have to do 2-pass which takes longer. CRF does everything in 1 pass. Also, you don't have to guess the bitrate or target size. The encoder will figure that out and will smartly give you the desired quality every time. It is an amazing feature, and I have no idea how it works. But that's besides the point. I usually use CRF for my movies. I generally don't care how big the size is of my movie files. However I do care about the quality. So I pick my quality setting and let the encoder figure everything else out. However, for TV. shows, I generally like to predict my target size so I can be consistent with all episodes of every season across the board. And after all, generally t.v. episodes within a series require about the same bitrate to maintain the same quality, since the original sources are very similar.

Here's how I go about determining what target size to use:

With each new series, I begin with some lengthy experimenting. I try to take a random sample...a few episodes from different DVDs and from different seasons. I begin by encoding each episode 3 different times with CRF levels of 18.5, 19, and 19.5. These numbers should all give a pretty good acceptable quality. I always do 18.5 with my movies, but 19 is a pretty good rule for standard DVDs. (For Bluray, you can get away with higher CRF values like 22 or 23). Then I see what kind of sizes I get. You will see that they vary, but usually by not too much. Some episodes will need a lesser bitrate to attain the very same quality as an episode that may require 50-75 more mb's.

Examine the sizes of the resulting files and pick an average. You will get a feel for how large you should go. I usually find that it hovers any where from 450 - 600mb...sometimes more, especially if you include multiple audio tracks. And remember, a lot of the compression, and thus size, is based on your x264 settings. For example, say you use a Subpixel Motion Estimation of 8 for one encode and 10 for another...on the same episode/file, but you choose the same CRF value of 18.5 for both. The one where you set the SME at 8 will be a larger output file than the one you set at 10. Because the encoder was told to maintain the same quality. So at 10, it could keep the same quality with a lower bitrate because it had more compression. But an SME of 8 required a higher bitrate to maintain the same quality. I hope this makes sense. Basically. the better the x264 settings, the smaller file size you will need to maintain the same quality.

I think that about covers everything. If you want to add subtitles, I generally do this after the fact. I use Vsrip to create the individual episodes .idx/.sub files and then use Subrip to convert them to .srt. Then I mux them into the mkv file with mkvmerge gui.
Attached Files:
