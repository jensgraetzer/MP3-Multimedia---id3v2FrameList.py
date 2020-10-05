# MP3-Multimedia
MP3 files store audio data. Most MP3 files have an ID3v2 tag. In an ID3v2 there is other data stored - text, images and time stamp information. Combining this different data types in a smart way makes it possible to store a multimedial experience in a MP3 file.

This project presents some MP3 files, containing an ID3v2 tag, that creates a multimedial experience. 

Multimedia experiences can be stored in different ways - see (1).

Today (in summer 2020) only one multimedia MP3 player application exists - see (2). So the multimedia MP3 samples of this project together with the ID3v2 standards - see (3), (4) and (5) - may help to build more player applications of multimedia MP3 files, and editor applications as well.

# ID3v2 frames of a multimedia MP3 file
This table shows some frames of an ID3v2.3 or ID3v2.4 tag. There are a lot more frames. For more information - see the ID3v2 standards (3), (4) and (5).

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

## Additional requirements
This text defines the way, how to use the ID3v2 tag for the purpose of multimedia MP3 files. A multimedia MP3 file should meet these additional requirements:

1. In multimedia MP3 files only the ID3v2.4 version tag should be used. Using only that tag version, but not the ID3v2.3 tag version, makes the player development less complicated.
2. In multimedia MP3 files the  ID3v2.4 version tag should be at the beginning of the MP3 file only, not at the end.
3. There should not be an extended ID3v2 tag header.
4. Within the SYLT frame the time format is milliseconds only, not MPEG frames.
5. In all multimedia MP3 files the content of the TCON frame always should be "Multimedia". 
6. In APIC frames of an multimedia MP3 file the "description" field contains the picture file name.
7. Recommended image size of the image in the first APIC frame (this will be the cover image of the MP3 file) is 600 by 600 pixels. 

## Showing images at times, defined by a SYLT frame

Multimedia MP3 files contain images and text, synchronized with the audio by timestamps. Images can be stored in APIC frames. Timing information can be stored in a SYLT frame. There are two possible ways:

1. There are several images, each in a separate APIC frame. Each APIC frame has the filename of the image stored in the field “description”. The SYLT frame has content type 8. The text of every timestamp of the SYLT frame stores one single filename of an image.

2. There are several images, each in a separate APIC frame. Each APIC frame has the filename of the image stored in the field “description”. The SYLT frame has a content type smaller than 7. In this case the text of a SYLT frame time stamp is subtitle text. It is allowed to embed an imagefile name into the subtitle text. This can be done by writing the image file name in a HTML like image tag. So it looks like &lt;img src="image file name"&gt;. Additionally, some other HTML like tags are allowed. This is these tags: &lt;b&gt;...&lt;/b&gt;, &lt;i&gt;...&lt;/i&gt;, &lt;u&gt;...&lt;/u&gt; and &lt;font color="color name"&gt;...&lt;/font&gt;. Other than these HTML tags are not allowed.

## The new XSRT frame

The ID3v2 standard allows experimental frames. The XSRT frame is an experimental frame, invented for multimedia MP3 files. It presents a third way for showing text and images, synchronized with the audio by timestamps.

An XSRT frame has a structure similar to the USLT frame, but contains subtitle text in the SubRip format (6). So, audiosynchron subtitle text can be displayed. Additionally, some HTML like tags are allowed. These tags are allowed by the SRT standard and subsequently are allowed in the XSRT frame too: &lt;b&gt;...&lt;/b&gt;, &lt;i&gt;...&lt;/i&gt;, &lt;u&gt;...&lt;/u&gt;, &lt;font color="color name"&gt;...&lt;/font&gt;. Additionally a image tag is allowd - &lt;img src="image file name"&gt;. The image frame indicates, that an image appeares at the screen at the start time of that certain title. There is no more than one image tag in a certain SRT text title. The image doesn't disappeare at the end time of this title. The image only can be replaced by an other image, defined by in a title of an other start time.

## APIC frames

An APIC frame stores an image. A multimedia MP3 file may contain more than one image. Thus, there may be more than one APIC frame. In multimedia MP3 files, the frame field "description" contains the image file name.

The first APIC frame of a multimedia MP3 file will be used as the cover image. A cover image is sort of an icon of the MP3 file, that is shown by the file picker of the player. It is recommended the image to be a quadrat of 600 by 600 pixels. 

## Multipe SYLT and XSRT frames

There can be more than one SYLT or XSRT frame. It is strongly recommended, that the timing of the images is done by only one of these frames. So, the other SYLT or XSRT frames contain text only, perhaps text translations into other languages.

If there is more than one SYLT or XSRT frame, the timing of the images should be done by a SYLT frame with content type 8. HTML image tags in a SYLT or XSRT frame should be used only in the case, if there is only one SYLT or XSRT frame within the ID3 tag.

There may be more than one SYLT or XSRT frames in a tag, but only one with the same language and content descriptor. The content descriptor should be the whole string language name, e.g. "Français" (for French) or "Русский" (for Russian).

# Files of this repository

## id3v2FrameList.py
This Python script lists the frame names, found in the ID3v2.3 or ID3v2.4 tag of a MP3 file.

## mm01_presentation.mp3
This is the first example of a MP3 multimedia file. It contains audio data, a cover image, 4 more images in the format 16x9 and text. The appearance of the text and the images is syncronised with the audio. The synchronisation is done by a SYLT frame with content type other than 8.

## mm02_543210.mp3
This is the second example of a MP3 multimedia file. It contains audio data, a cover image and text. The appearance of the text is syncronised with the audio. Therefore an experimental frame, called XSRT, has been invented and used. This XSRT frame has a structure similar to the USLT frame, but contains subtitle text in the SubRip format (6).

## mm03_briefmark.mp3
This example contains 3 APIC frames. The synchronisation of the images is done by a SYLT frame with content type 8. So the SYLT frame contains only image file names. Additionally, this example contains a USLT frame.

# References
1. J. Grätzer, Multimedia Data Categories, 2020
https://github.com/jensgraetzer/MP3-Pictures-Exporter/blob/master/Multimedia-Data-Categories.pdf (last visited 2020-06-11)
2. J. Grätzer, MP3 Multimedia Player app at the Microsoft Store,
https://www.microsoft.com/de-de/p/mp3-multimedia/9nt7d443vx86 (last visited 2020-08-16)
3. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Main Structure, 2000,
https://id3.org/id3v2.4.0-structure (last visited 2020-06-11)
4. M. Nilsson, Informal Standard: ID3 tag version 2.4.0 - Native Frames, 2000,
https://id3.org/id3v2.4.0-frames (last visited 2020-06-11) 
5. M. Nilsson, Informal Standard: ID3 tag version 2.3.0, 1999,
https://id3.org/id3v2.3.0 (last visited 2020-06-11) 
6. wikipedia.de, SubRip
https://en.wikipedia.org/wiki/SubRip (last visited 2020-06-11)

