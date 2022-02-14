UsEac3To v1.3.2 2021-10-31
==========================
(Sorry for my english).
I make this GUI for me to test eac3to, maybe can be useful also for you.
You can write the command line parameters with some help for filenames
and syntax remember.

There are also some Auxiliary tools and samples to automate jobs.
The included source is in Autoit3 and can be easy changed to accomplish
your need.

Install
-------
Decompress at any folder. Maybe with eac3to or in a subfolder.
To avoid UAC problems is recommended use a folder created by the user
for instance: C:\Portable\eac3to\UsEac3to

Of course need 'eac3to.exe' and, at first run, ask for it if isn't at same
folder or at the parent folder. Visit:
            http://forum.doom9.org/showthread.php?t=125966
to obtain a recent version. Now is supported eac3to v3.34
There are others links to needed soft like:

haali:      http://haali.su/mkv/
mkvtoolnix: http://www.bunkus.org/videotools/mkvtoolnix
ffmpeg      https://www.gyan.dev/ffmpeg/builds/ or https://github.com/BtbN/FFmpeg-Builds/releases
NeroAacEnc: https://www.videohelp.com/software/Nero-AAC-Codec

And, maybe, others like:
TsMuxer:    https://github.com/justdan96/tsMuxer    https://dl.bintray.com/justdan96/tsMuxer/
DelayCut:   http://madshi.net/delaycut.rar
Lame:       http://www.rarewares.org/
Oggenc2:    http://www.rarewares.org/ obsoleto usar mejor opus
Oggdec::    http://www.rarewares.org/ obsoleto usar mejor opus
Faad:       http://www.rarewares.org/ obsoleto usar mejor otro
opusenc:    http://www.rarewares.org/ http://forum.doom9.org/showthread.php?t=168270
wma2wav:    http://forum.doom9.org/showthread.php?p=1169827#post1169827
ffdcaenc:   http://forum.doom9.org/showthread.php?p=1688150#post1688150 (1)
qaac:       http://sites.google.com/site/qaacpage/home  http://forum.doom9.org/showthread.php?t=154233
fhgaacenc:  http://github.com/tmkk/fhgaacenc/downloads  http://forum.doom9.org/showthread.php?t=161806
SoundStretch: https://www.surina.net/soundtouch/download.html
mlp:        https://github.com/domyd/mlp/actions/runs/120022192  (2)
Sox:        https://sourceforge.net/projects/sox/files/sox/
BeSplit:    http://forum.doom9.org/showthread.php?p=609216#post609216
wavfix      http://forum.doom9.org/showthread.php?p=1520399#post1520399
avs4x26x-x64: https://forum.doom9.org/showthread.php?p=1529305#post1529305
x264        https://forum.doom9.org/showthread.php?p=610495#post610495
x265        http://msystem.waw.pl/x265/
(TwoLame:   deprecated, now use ffmpeg to encode MP2 in v1.2.7)
(aften:      http://code.google.com/p/wavtoac3encoder/downloads/list)
Deprecated aften.exe in v1.2.0
(1) Better than ffmpeg because: https://forum.doom9.org/showthread.php?p=1917913#post1917913
(2) This mlp-windows version can select streams.

Some options in UsEac3to can't work without them.

Working
-------
The first time ask for eac3to, but also you can go to 'Settings' to inform
about:

- MkvMerge (not needed if installed in default path)

- TsMuxer (not needed if installed in a eac3to subfolder)

- Folder with de/encoders: when the soft need a de/encoder search at UsEac3to
  folder, after in the folder indicated here and, at last, in the ec3to folder.
  (if NeroAacEnc is at eac3to folder can be used directly by eac3to)

- Output file folder: the converted files are stored, by default, at input
  file folder, unless you select 'Output Folder' -> 'User defined'.

This info is stored in a file: 'UsEac3to.ini'

When open ('File' -> 'Open...', 'Input File' or Drag&Drop) a multimedia file
is analyzed, and the eac3to 'log' is show in a edit window. The edited log
can be saved to document any trouble.

We can open also folder structure (BD o HDDVD) and a pop-up window let you
select the desired 'Feature'.
With v1.2.7 and eac3to v3.32 there are support for UHD BD's and HEVC video.

'+ Sources' add files with same extension and correlatives.
For .vob, .ts and .m2ts

Global Parameters
-----------------
This parameters can be 'RUN' without more info.
When 'Output Folder' -> 'User defined' is selected the -demux option is
replaced by a "Output folder\filename.*".

Track Input and Output format
-----------------------------
When we need convert/extract one (or more) track we need select the pair
'Track Input' and the 'Output format' desired. When a format have the '-ext'
sufix, for instance 'mp3-ext', means than we need a external encoder
'lame.exe' in this case.

Clicking 'Add' we include in the command line parameters like:
2: %_eng2.ac3
and means than the track 2 must be extracted/converted to ac3 format with the
name of the source file (represented by the '%' char, at input folder or in
'User defined' folder) with the sufix '_eng2' to point the source track.
Language sufix added in v0.9.2

Now we see the command line parameters more clear without big filenames.

Parameters
----------
Now we can 'Add' all desired parameters from 'Frequent parameters' and 'More
parameters' or typed directly (more of them need a retype like bitrates or
delays). I think than make list and boxes for all possible parameters and
values is a bad idea and can change in next eac3to version.

Also we can use external encoders (the name is also symbolic and is replaced
by the full path when is executed) with many possible parameters.
You must know and type them, this is how work UsEac3to.
In v0.7 a eac3to Help show info about parameters.

With v0.6 we can use more than one external programs with 'pipe'.
Example for a simple stereo downmix:
 stdout.wav | Sox --ignore-length - -t wav - remix -m 1v0.3694,3v0.2612,5v0.3694 2v0.3694,3v0.2612,6v0.3694 norm | Lame -b 128 - %_.mp3

In v1.3.0 I make a way to store complex commands like above to easy recover
them. In 'More parameters' selecct 'F-FFMPEG' and 'Add', a new window is open
and you can select ffmpeg functions or complex command stored in the file
'Vid_Enc.par'. See A/V Recode 2.1.2 y 2.2 to know more about this.
There ara also some tools to calculate times and gains.

More than one track
-------------------
You can extract/convert many tracks at time, but there are a limit.
You can convert only one with a external encoder and must be the last:

 4: %_4.ac3 3: stdout.wav -down2 | OggEnc2 -q 3 --ignorelength -o %_3.ogg -

The track 4 is extracted/converted to ac3 and the track 3 is converted to
stereo and codified to ogg.

RUN Command Line
----------------
When you have the desired command line (remember you can Edit/Copy/Paste/Type
anything in the window) click at 'RUN Command Line'. A DOS window is oppened
with the job progress, at end all the info is transferred to the eac3to info
window to analyze, type and save the log if you want document a problem.

Queue system
------------
Added a simple Queue system in v0.9.2

Using the new button 'EnQueue' instead 'RUN CL' the job is stored in a file
(...\UsEac3to\zzJob_1.cmd) pending of execution.
If the Command Line Parameters is empty only list stored job's.

When push 'Run Que.' the job's are executed in the order 1..9,A..Z
We can edit, delete or renumber the job files before the execution.

There are also the option of shutdown the system when queue finish.
To enable use 'Settings' -> 'Shutdown at finish' -> 'Enabled'.
Work also with 'RUN CL', but queue and shutdown don't work with 'Auxiliary Tools'

Auxiliary Tools
===============
There are here some complementary tools to eac3to, maybe someone can be
implemented in next versions (Ogg Vorbis, Subtitles, ...) but can be useful
at this moment.

1) MkvExtract/INF
-----------------
Modified in v1.2.8 to suport MkvToolNix v17.0.0

1.1) If the input file is a mkv work like a MkvExtractGUI:

Allow extract Tracks, TimeStamps, Chapters and Attachements in one job.

Complement eac3to extraction of tracks not supported (Xvid and other
videos, Vorbis and other audios, VobSub and other subs).
Or with troubles with actual eac3to version (h265, EAC3, SUP).

Use 'Add' to include any option in the job before 'Run/EnQueue'.
To cancel kill the window and reopen if needed.
Show a info (don't edit) to remind options selected.
With te info empty we can obtain a mkv Inform (tags).

Some updates in v1.2.0, now we can select all ATT or SUP in a unique 'Add'.

1.2) If the input file is a mpls and you have mpl.exe (and dll's) in one of
the UsEac3To folders you can extract TrueHD tracks. New in 1.3.0

In a new window you can select the desired stream TrueHD (if exist).
If there are angles or you want select segments the parameters must be filled
in the Comman Line Parameters window.

1.3) With other input file make a ffmpeg report to show the tracks:
New in v1.2.5

Now we can extract audio tracks with a "-acodec copy" of ffmpeg.
With other tracks can work of not. Maybe changing the output extension
or replacing "-acodec copy" with other parameters.


2) A/V Recode
------------
If we open a file not supported by eac3to, for instance a .avs, send the message:
"The format of the source file could not be detected.  <ERROR>"
Now 'Output format' show 'A.Tools' and, maybe, there are a Auxiliay Tool that can do
some job over this file.

Clicking 'A/V Recode' with a .avs open a window 'Video Recode', with other file open
the 'Audio recode' window.

2.1) Audio Recode

The behaviour of this tool was changed with v1.2.1, v1.2.3, ... until v1.3.0
Is designed to complement eac3to with external programs.
UsEac3to search that external decoders/encoders in folders defined in Working.

2.1.1) Merge wavs

New in v1.2.4: If the input file is a wav with the name finished with 'L', for instance
"xL.wav", search in same folder others xR.wav, xC.wav, xLFE.wav, etc.
(the same sufix than eac3to make: R|C|LFE|BL|BR|LC|RC|BC|SL|SR).
If there are at least two, offer the option to use the mono-channels merge like input
for all next options.

2.1.2) Force FFMPEG

After v1.2.9 we can force always use ffmpeg like encoder.
For that select any map:X greater than 0.
1 for a standalone audio or the first audio of a container.
Other value if it is not the first audio (MkvExtract/INF can help).

When let map:X = 0 UsEac3to search for specific decoders for each format.
The available decoders are:

INPUT    DECODER     default PARAMETERS
-------  ----------  --------------------------
ogg      oggdec      -b 3
wma|wmv  wma2wav
mp2|mp3  lame        --decode
opus     opusdec
m4a|mp4  NeroAacDec
aac|m4a  qaac        -D -b 24
aac|m4a  faad        -b 2
other    ffmpeg      -vn|-map 0:MAP

Notes:
- Of course parameters for INPUT and OUTPUT or STDOUT are added automatically
- Parameters try to output 24 bits int, can be changed with 'Add to DEC' or 'ReplaceDEC'
- If container input decode first audio or the selected in ffmpeg map.

2.1.3) Use Command Line parameters

There are many parameters from de/coders/filters/ffmpeg and we can't put all of them
in a GUI, but we can use the edit window 'Command Line parameters' to write anything
BEFORE click in 'A/V Recode' and after selecy 'Add to DEC'/'Replace DEC' to madify
the default parameters showed in the table above.

If we select 'Add to ENC'/'Replace ENC' we can modify the default parameters of
decoders in the next table:

OUTPUT    ENCODER      default PARAMETERS
--------  -----------  ---------------------------------------------------------
 wav/w64  ffmpeg       -acodec pcm_s24le
 flac     ffmpeg       -acodec flac
 thd/...  ffmpeg       -strict -2 -acodec truehd/mlp/wavpack/alac/tta/aiff
 ac3      ffmpeg       -acodec ac3 -center_mixlev 0.707 -ab CBRk
 eac3     ffmpeg       -acodec eac3 -center_mixlev 0.707 -ab CBRk
 mp2      ffmpeg       -acodec mp2 -ab CBRk
 aac      ffmpeg       -acodec aac -ab CVBRk|-aq QUA
 aac      qaac         -V TVBR|-v CVBR --ignorelength --adts --no-delay
 mp3      Lame         -b CBR|-V QUA
 opus     opusenc      --bitrate CVBR --ignorelength
 ogg      OggEnc2      -q QUA --ignorelength
 m4a      NeroAacEnc   -q QUA -ignorelength
 m4a      fhgaacenc    --vbr QUA|--cbr CBR --ignorelength
 dts      ffdcaenc     -l -b CBR

Notes:
- Of course parameters for OUTPUT and INPUT or STDIN are added automatically
- Parameters options (separated by '|') and CBR,QUA,VBR selected in dialog.
- For wav/w64 if we know the input bitdeph we put the correct.
  For instance for a DTS-MA 16 bits we use pcm_s16le
- From 1.3.0 if don't found Lame, opusenc, OggEnc2 o ffdcaenc we recode with
  ffmpeg the mp3, opus, ogg y dts, we don't need here other external encoders.

2.1.4) Select ENCODER

Here we select the encoder and the main parameter: the bitrate or quality
like we can see in the table above.
Only the first option 'Decode,Lossless,WavDts' need some explain:

wav/w64  only decode or format change to manage after.

thd/mlp  lossless encoders, thd and mlp are experimental only until 5.1
flac/wv  If the input is a TrueHD Atmos and with 'Replace ENC' we put:
tta/aif  -bsf:a truehd_core -c:a copy
alac     select the thd here make a TrueHD output without the Atmos metadata.
         With this 'Replace ENC' and selecting AC3 we obtain the embedded AC3.

dts      If we know the input is a dtswav we can convert to a standard DTS with
         BeSplit -core( -type dtswav -fix )    [if found BeSplit]
         But if the input is a DTS-HD and 'Replace ENC' to include:
         -bsf:a dca_core -c:a copy
         we extract the 'core' of the DTS-HD

null     Without output file. To test and emule Normalize.

2.1.5) eac3to versus ffmpeg

- With eac3to we can open a BD folder, select a .mpls and extract/recode
  some tracks. With ffmpeg we can't open, by now, a .mpls but, of course,
  can manage much more codecs of video, audio and subs.
  Here we talk only about audio.

- eac3to have some simple functions than not need decode the input,
  we can do delay's and edit's without lose quality recoding.
  ffmpeg, like AviSynth, only can apply the functions over decompressed audio
  We can obtain delay's and edit's with 'asplit', 'adelay', 'atrim' y 'concat',
  but at end we need recode to desired format.

- eac3to have a Normalize function, like AviSynth, than do 2 passes to avoid
  distortion or low volume. With ffmpeg we can use the 'volumedetect' function
  after a downmix over a null output to know for instance:
  "max_volume: -8.7 dB" (in my PC 19 sec. over an AC3 5.1 of 2 hours)
  And make the second pass with 'volume=2.7' (1m 53s encoding AAC with qacc)
  Is not easy but is fast.

- Other eac3to functions like resample, slowdown o speedup have 'aresample'
  and 'asetrate' to do the same job, also ffmpeg have 'atempo' to preserve
  the pitch.
  In my test over a sample of 1 hour the 'atempo' function have a error of 10 ms
  with 32 sec. of execution time, there are soundstretch.exe (example included
  in Vid_end.par) with less than 1ms/hour but 105 sec of execution time,
  I can't listen quality differences, let me know if you check it.
  I check rubberband, 137 sec. with a error of 11 ms but less quality in my
  opinion (https://breakfastquay.com/files/releases/)

- There are many other audio functions in ffmpeg, you can see the docs in:
  https://www.ffmpeg.org/ffmpeg-filters.html#Audio-Filters
  Seems the same functions included in Sox.exe but fast.
  I include a sox usage example if anybody want compare.

To finish a example with a simple process than eac3to can't do because can't
decode a EAC3 track:

You have a mkv with the second audio track:
3: EAC3, English, 5.1 channels, 48kHz, 678ms
and you want recode to AC3 and apply the delay

1) With 'More parameters: FFMPEG' and 'Add' include in CLP 'delayM':
 -af "adelay=delays=1600:all=1" (here the time go in ms)
2) Edit the delay to the desired 678 ms and click in 'A/V Recode'
3) Select the 'ffmpeg map' to 2 (in ffmpeg the video track is the 0)
4) Select 'Use Commad Line Parameters' to 'Add to DEC'
5) Select the AC3 desired bitrate
6) 'Run' or 'EnQueue' the job

If we want a AAC 2.0 you can use the Normalice procedure already explained
until obtain a CLP window with:
 -filter_complex "pan=stereo|FL=.3694FL+.2612FC+.3694BL|FR=.3694FR+.2612FC+.3694BR, volume=2.7, adelay=delays=678:all=1"
Maybe is not easy but you can learn to do many things.

2.2) Video Recode:

Because a user request I added a help to recode video (x264, XviD) by command line.
The method is not recommended for newbies.

In v1.1.4 added support for wavi.exe to encode audio with a audio .avs source.
In v1.2.4 added support to x265 with avs4x26x.exe or avs4x265.exe
See encoders samples and paths in the included Vid_enc.par (new in v1.3.0).

In the new window we can edit the .avs, select the encoder, output file and encoder
parameters. Also edit the Vid_enc.par file to add your preferences.
See the example included, here explai the different sections:

[Encoders]
List of video/audio encoders than support .avs like input

[Extensions]
Any supported by the precedent encoders

[Text Editor]
Notepad.exe (by default) or include your preferred plain text editor

[Presets]
NAME_1|list of parameters of default (and next options) of your encoders

[FFMPEG]
NAME_2|list of options to include in the edit window CML (explained in 2.1.3)

[END]

3) SRT/.../TRIM
---------------
Beggining in v1.2.3 this tool add a new function.
With input text files work as before:

3.1) Text files SRT/SSA/ASS/TXT/XML/CUE

There are many free tools to convert subtitle formats here there are a simple
tool to delay and speedup/slowdown text subtitles: SRT, SSA and ASS
Since v0.3 also TXT files with chapters.
Since v0.6 also XML files with chapters and CUE files.
Since v1.2.3 we can add a offset to delay.

Remember than subtitle text files can be modified also with NotePad to change
the character map (UTF-8, ANSI, Unicode), source of problems for some players.

v1.1.9 Added option to process all files with the same extension in the folder.

3.2) Audio files AC3/DTS/MP3/MP2/WAV/AAC/M4A/FLAC/OPUS/OGG/W64

Now we can cut audio based in Trim inside a .avs.
Ask for a timecodes file for use instead the fps of the video if is VFR.

Make a .mka with the cutted audio.
The executed .bat is not deleted and remain like info about the cut's maked.

If a timecodes file is provided, make a new timecodes_Trim.txt to apply to
the output video.

3.3) Files AVS

Like before, but now only the info .bat is generated to be used for a manual
audio edition.
And make a new timecodes_Trim.txt if a timecode file is provided.

4) MkvMergeGUI
--------------
Is only a link to this program. We don't need replace here all the MkvMergeGUI
options, use it.
Since v1.1.8 mkvtoolnix-gui if exist, else mmg.

5) TsMuxerGUI
-------------
Same than for MkvMergeGUI.

6) DelayCut
-----------
Other link to repair audio tracks.

7) Run and MkvMux
-----------------
This last two tools are only samples to how automate the full process of
extract, convert and remux with only a click. The problem is than only work
for specific conversions. Let me show some samples:

We have a mkv input file with a video(1) track, audios (2,3,4,..) and
subtitles (7,8,9). We make a command line like:

 3: %_3.ac3 4: %_4.ac3 -448

and click at 'Run and MkvMux', we extract/convert the track 3 to ac3, and also
for track 4 converted to 448 Kb/s.
Now send the mkv source to MkvMerge for cancel all audios (subtitles remain)
and add the two converted audios.
Tipical track conversion from DTS/FLAC/... to standard AC3

With this command line:

 1: %_1.mkv -speedup 3: %_3.ac3 -speedup 4: %_4.ac3 -speedup -448

Now the video track is extracted and converted to 25 fps (from 23.976, for
instance), same process for the audios.
Now the mkv sended to MkvMerge only have the new video track (subtitles are
missing, and need SRT/SSA/ASS conversion).
Typical for fps conversion.

Only one/two audios are allowed. If you select 3 or more only the first and
last are sended to make the mkv final.

New in v0.7.41 audio without track compression
New in v0.7.42 all tracks without compression
New in v0.8.1 work now with m4a audio (is a container)
New in v0.9 the track order sended to mkvmerge is video,audio,subs like eac3to
show.
New in v1.2.0 option to add jobs to queue.

8) Run and TsMux
----------------
Like the precedent but with some differences:

- The output file is one or more .m2ts (option to split in 4GB fragments to
  accomplish FAT32)
- Only the first video from the mkv source is sended to TsMuxer (subtites
  always missing).

Typical to convert mkv to play in PS3 with external hard drive.

Changelog
=========
- v1.3.2 2021-10-31 Solved bug regresion in Merge Wav's function.
- v1.3.1 2021-05-26 Default flac compression level (5) instead 12.
                    Some ffmpeg improvements. AvsCutter function.
                    https://forum.doom9.org/showthread.php?p=1943641#post1943641
- v1.3.0 2020-08-03 Incluided mlp.exe (Extract TrueHD from .mlps, see 1.2).
                    Improved include of FFMPEG functions (see 2.1 y 2.2).
                    ffmpeg can now encode all audio formats.
- v1.2.9 2018-06-12 Correct some bugs and improve A/V Recode.
- v1.2.8 2017-10-16 Support MkvToolNix v17.0.0. New MkvExtractGUI.
- v1.2.7 2017-10-12 Support eac3to v3.32 (UHD BD's y HEVC)
                    Force ANSI to read text files.
                    TwoLame replaced by ffmpeg to encode MP2.
- v1.2.6 2017-06-19 Bug fix: Autoit v3.3.14.2 write files by default like UTF-8
                             Before are writed like ANSI. Corrected.
- v1.2.5 2017-06-15 Audio recode: decoder admit parameters change (for ffmpeg).
                    INF: ffmpeg report of tracks in any container.
                    Can extract audio tracks.
- v1.2.4 2017-06-10 Video recode: x265 support using avs4x26x.exe
                    Audio recode: Decode to W64 (always ffmpeg) or WAV.
                    Encode to EAC3 (ffmpeg), bitrate with prefix 'E'
                    Merge mono-channels WAV with sufix L,R,C,LFE,...
- v1.2.3 2017-05-21 The exe (or link) support Drag & Drop.
                    Extract Info from mkv's.
                    Audio Recode use ffmpeg if don't found a proper decoder.
                    Audios cut with Trim's of .avs
                    Offset in Delays of srt's, ass, etc.
- v1.2.2 2016-10-02 Added -drc_scale 0 to ffmpeg (to decode AC3 or E-AC3)
- v1.2.1 2016-09-15 Improved 'A/V Recode':
                    Added ffmpeg MAP to select track in container.
                    Added option to override encoder parameters.
- v1.2.0 2016-08-05 Aften.exe deprecated by ffmpeg.exe. See Audio recode.
                    Added Opus encoder and BeSplit for dtswav.
                    Option to enqueue Run and MkvMux
                    Update MkvExtract options (all ATT or SUP)
- v1.1.9 2015-12-12 SRT/.../TXT Added option to process all files with
                    the same extension in the folder.
- v1.1.8 2015-11-02 Support for ffmpeg external encoder.
                    MkvToolNix-GUI instead MkvMergeGUI
                    Minor bug (features) and some defaults changed.
- v1.1.7 2015-06-02 MkvMux: if an audio is a thd+ac3 mux the two tracks.
                    Trim of timecodes.txt for VFR.
- v1.1.6 2015-03-31 Added parameters -dcadec, -arcsoft and OpusEnc
- v1.1.5 2015-03-10 Solved bug when press Cancel selecting feature
- v1.1.4 2014-11-09 Support for wavi.exe
- v1.1.2 2014-09-12 Now we can extrat attached files from mkv.
                    ffdcaenc replace to dcaenc.
                    Some minor bugs solved.
- v1.1.1 2013-12-13 Solved bug XviD -cq mode.
- v1.1.0 2013-12-08 Added Video Recode.
- v1.0.0 2013-01-05 Minor changes to support eac3to v3.26
- v0.9.2 2012-05-10 Added Queue system and Shutdown.
                    Sopport for dcaenc, qaac and fghaacenc.
                    Added language in track name and some minor improvements.
- v0.9.0 2011-10-18 'Decode Ogg/mpx' changed to 'Recode Audio'.
           Better control of track order in 'MkvExtract/Mux' and 'Run and MkvMux'
           The user must close the command windows to can see errors if any.
- v0.8.1 2011-04-27 MkvMux work now with m4a audio (is a container)
- v0.8  2010-11-29 Now 'Output format' only show allowed options for 'Track Input'
                   If show 'A.Tools' only 'Auxiliary Tools' can manage track/file.
                   Example: Xvid in mkv, Vobsub in mkv, files .ogg, .srt, ...
                   Better support for .mpls.
- v0.7.42 2010-07-28 Option to remux without compression
- v0.7.41 2010-07-28 Option to remux without audio compression
- v0.7  2010-05-25 eac3to Help, Track input filled with only audio, Settings improved.
- v0.6  2010-03-06 Improved command line parse (external programs 'pipe')
                   Decode with NeroAacDec and Lame
                   Time change also in XML and CUE
                   Workaround to change ANSI chars to OEM ASCII for cmd's
- v0.5e 2010-02-14 Options in MkvExtract and Run_and_TsMux
- v0.4  2009-10-12 less CPU use, -progressnumbers and 'User Defined' folder selected by default- v1.1.7 2015-06-02 MkvMux: si un audio es thd+ac3 se mezclan las dos pistas.
                    Trim de timecodes.txt para VFR.
