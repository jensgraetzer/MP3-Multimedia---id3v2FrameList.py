# MP3-Multimedia
MP3 files store audio data. Most MP3 files have a ID3v2 tag. In a ID3v2 there is other data stored - text, images and time stamp information. Combining this different data types in a smart war makes it possible to store multimedial user experiances in MP3 files.

This section presents MP3 samples, containing a ID3v2 tag, that build a multimedial user experiance.

# Some frames of a ID3v2 tag and their name

| Frame | Known as                           |
|:----- |:---------------------------------- |
| TCON  | Genre                              |
| TALB  | Album                              |
| TIT2  | Title                              |
| TRCK  | Track Nr.                          |
| TPE1  | Interpret                          |
| COMM  | Comment                            |
| TDRC  | Date of Recording (at least Year)  |
| APIC  | Image                              |
| SYLT  | Text and synchronising timestamps  |

# id3v2FrameList.py
This Python script lists the frame names, found in the ID3v2.3 or ID3v2.4 tag of a MP3 file.

# mm01_presentation.mp3
Example of a MP3 multimedia file. It contains audio data, a cover image, 4 more images in the format 16x9 and text. The appearance of the text and the images is syncronised with the audio. Therefore the timestamps given in the SYLT frame were used.

Every image is stored in a APIC frame. In this example, the name of the image file is given in the frame field "description".

The SYLT frame contains timestamps. Each timestamp has got some text. So this text can be displayed synchron to the audio. In this example, the text of a certain timestamp may contain the name of a picture file. This way, also pictures can appear synchron to the audio. The name of a picture is embedded in the text this way:

<img src="image.jpg">

# mm02_543210.mp3
Example of a MP3 multimedia file. It contains audio data, a cover image and text. The appearance of the text is syncronised with the audio. Therefore an experimental frame, called XSRT, is invented and used. This XSRT frame has a structure similar to the USLT frame. It contains the text in SRT format.

# References
1. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Main Structure, 2000,
https://id3.org/id3v2.4.0-structure (last visited 2020-06-11)
2. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Native Frames, 2000,
https://id3.org/id3v2.4.0-frames (last visited 2020-06-11) 
3. M. Nilsson, Informal Standard: ID3 tag version 2.3.0, 1999,
https://id3.org/id3v2.3.0 (last visited 2020-06-11) 
4. J. Grätzer, Multimedia Data Categories, 2020
https://github.com/jensgraetzer/MP3-Pictures-Exporter/blob/master/Multimedia-Data-Categories.pdf (last visited 2020-06-11)
