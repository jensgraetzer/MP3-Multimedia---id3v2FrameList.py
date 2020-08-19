# MP3-Multimedia
MP3 files store audio data. Most MP3 files have an ID3v2 tag. In an ID3v2 there is other data stored - text, images and time stamp information. Combining this different data types in a smart way makes it possible to store a multimedial experience in a MP3 file.

This project presents some MP3 files, containing an ID3v2 tag, that creates a multimedial experience. 

Multimedia experiences can be stored in different ways - see (1).

In summer 2020 no mulimedia MP3 players exist. So the multimedia MP3 samples of this project together with the ID3v2 standards - see (2), (3) and (4) - may help to build the first players and editors of multimedia MP3 files.

# About the frames of a ID3v2 tag
This table shows some frames of an ID3v2.3 or ID3v2.4 tag. There are a lot more frames. For more information - see the ID3v2 standards (2), (3) and (4).

| Frame | Known as                               |
|:-----:|:-------------------------------------- |
| TCON  | Genre                                  |
| TALB  | Album                                  |
| TIT2  | Title                                  |
| TRCK  | Track Nr.                              |
| TPE1  | Interpret                              |
| COMM  | Comment                                |
| TDRC  | Date of recording (at least the year)  |
| APIC  | Image                                  |
| SYLT  | Text and synchronising timestamps      |

In the multimedia MP3 files of this project the content of the TCON frame is "Multimedia".

Multimedia MP3 files contain images and text, that is synchronised with the audio by timestamps. So the frames APIC and SYLT are very important. The ID3v2 standard allows experimental frames. The XSRT frame of the second example is an example of an experimental frame. 

Every image is stored in a APIC frame. In the first example, the name of the image file is given in the frame field "description".

The SYLT frame contains timestamps. Each timestamp has got some text. So this text can be displayed synchron to the audio. In this example, the text of a certain timestamp may contain the name of a picture file. This way, also pictures can appear synchron to the audio. The name of a picture is embedded in the text this way:

... text &lt;img src="image.jpg"&gt; text ...

In a multimedia MP3 file may be more than one picture, e.g. more than one APIC frame. In the multimedia MP3 files of this project the first APIC frame contains the cover image. The size of the cover image is 600 by 600 pixels. The cover image is sort of an icon of the MP3 file.

# id3v2FrameList.py
This Python script lists the frame names, found in the ID3v2.3 or ID3v2.4 tag of a MP3 file.

# mm01_presentation.mp3
This is the first example of a MP3 multimedia file. It contains audio data, a cover image, 4 more images in the format 16x9 and text. The appearance of the text and the images is syncronised with the audio. Therefore the timestamps given in the SYLT frame were used.

# mm02_543210.mp3
This is the second example of a MP3 multimedia file. It contains audio data, a cover image and text. The appearance of the text is syncronised with the audio. Therefore an experimental frame, called XSRT, has been invented and used. This XSRT frame has a structure similar to the USLT frame, but contains the text in the SubRip format for subtitles (5).

# References
1. J. Grätzer, Multimedia Data Categories, 2020
https://github.com/jensgraetzer/MP3-Pictures-Exporter/blob/master/Multimedia-Data-Categories.pdf (last visited 2020-06-11)
2. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Main Structure, 2000,
https://id3.org/id3v2.4.0-structure (last visited 2020-06-11)
3. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Native Frames, 2000,
https://id3.org/id3v2.4.0-frames (last visited 2020-06-11) 
4. M. Nilsson, Informal Standard: ID3 tag version 2.3.0, 1999,
https://id3.org/id3v2.3.0 (last visited 2020-06-11) 
5. wikipedia.de, SubRip
https://en.wikipedia.org/wiki/SubRip (last visited 2020-06-11)

