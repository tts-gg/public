## Intro
Here is a brief guide to human voice transcription based on the knowledge I have gained from working on a tts project.
This guide is split in 4 parts, and will focus on types of transcribing, tools, tips and general things to keep in mind when transcribing.
This guide is primarily aimed at using audacity, but can be adapted for other tools.

##Part zero - General audacity help

To work on audacity labeling project, you will need audacity and 2 files: the audio in wav 16 - bit format and a labels file in txt format.
I suggest organizing these files into a folder for each labelling task you do.

#For the audio wav files:
Step zero: Get audio in some format that you aim to label (mp3,mp4,wav,ogg, etc)
Step one: Open that audio file in audacity by opening audacity and pressing file->open and selecting the audio file( you might to install ffmpeg as an addon to audacity to open mp3s or mp4s  - https://manual.audacityteam.org/man/installing_ffmpeg_for_windows.html )
Step two(not necessary if the source is already in .wav format): Export the audio file by pressing file->export->export as wav and select 16 bit.

#For the .txt files:
Step zero: Create a .txt file by right clicking and selecting new text file, and place that in your labelling task folder.

#For the labelling project - getting started:
Step zero: Open up the .wav file by using file->open and selecting .wav file of the audio. 
Step one: Import the empty labels .txt file by selecting file->import->labels. A new track should appear below the audio track

#Labelling process itself in audacity:
Firstly, I suggest just zooming in to have about 20 seconds worth of audio data present at all times. Use the horizontal scrollbar at the bottom to go forwards and backwards.
Next, click where you want to play on the audio track. This will create a black line in the audio track. 
Now whenever you press the green play button it will start playing from the black line. Press the square to stop playback.
To listen to a section of audio, click and hold where you want to start the audio, and drag the mouse to the end.
Now when you press play, it will play just until the the end of the selected audio.
To create a label, the quickest way is to use ctrl+B, which will create an label around the selection or starting at black bar in the labels track.
Click on the label box in the track to type in the label text, and the arrows at each side to position the start and end of the label.

Once you are finished with the labels track, click file->export->export labels and select where you want to save the new labels file.
To check your work, you can open up the labels file in notepad or notepad++ and you should see a format like this, each on a new line for a new label:
<starting position in seconds> <end position in seconds> <label text>


## Part one - Types of transcription tasks

There are 3 broad categories of transcriptions based on the amount initial data presented with. They are ranked
according descending in terms of the time/difficulty to complete:

- zero data transcriptions:	these transcriptions come with no labels and is up to the transcriber to create all of 
				the data, based on the audio file alone. 
				These are usually done when only the audio file is availiable from a specific source
				or when the transcriptions from a source are very poor in quality and can cause the 
				process to take longer than writing all of it from scratch

- google/youtube data     :	these transcriptions come with a label file auto-generated, usually from youtube, 
  transcriptions		and are usually for the most part pretty accurate. The main issues with these data
				sources is the labels given starting and ending at illogical and unnatural places in 
				speech, and mislabels due to jargon or peculiar accents displayed by the speaker.
				These datasets can be quite time consuming to fix, as one must be on high alert to
				pick up and correct any errors that google didn't, specifically to do with prior issues
				mentioned.

- book/script data	  :	these transcriptions are the gold standard and are by far the easiest to work on,
  transcriptions		and are usually sourced directly from the person who's voice is being recreated. 
				The issues with these datasets usually come down to small issues of correcting 
				or dumping places where the speaker mis-speaks and ensuring that labels are positioned
				correctly, also cutting out any non-speaking sounds such as breathing, coughing etc

Additionally as an added layer of complexity, one can also categorize different variants of a speakers voice to create specific 
voices. This is done by placing an additional label over the transcribed text in audacity with the text as '[voice-type]'. 
In the tts project the variant speaking is still in experimental stages but it is believed that this is how the 'forsenSWA' 
voice was created in 'notastreamers' tts project for forsen.

## Part two - tools used

The first tool used in transcription is obviously audacity as mentioned earlier. One simply needs to open audacity, import the desired
audio file, import the label file(create one if doing zero data transcriptions) and start transcribing. Generally however here are a few
extra things I would recommend:

1) Create a folder system, using the following hierarchy: 
   tts_data_files -> speaker_name (inside of which all data for that speaker) -> data_file_name 
In this data_file_name, create two folders, one called source, the other output. Put the audio file and transcription and save 
the audacity project file in source, and once you are done with a transcription, generate the 16-bit wav file of the audio and 
export the labels file into the output folder. If you want to only finish part a transcription, remember the time stamp of the 
finished transcription and export only the selected audio to that point from audacity, and generate the labels file as before.

2) Download and install ffmpeg as an addon to audacity. This will allow you to view and export mp4 and mp3 files to wav.

The second broad tool I would recommend is youtube-dl. This is a command line youtube downloader with a lot of options, and allows 
you to source google/youtube data transcriptions very easily (and can even generate label files although I haven't used this feature 
myself).

The third tool I would use is some sort of hot key or macro script( I use autohotkey, my code for my transcriptions of 
a voice variants is at the bottom of the text file). This is useful first of all consistently mark garbage data as 
[unintelligible] and also to do voice variants as mentioned earlier. Since you will likely not use your number keys while
transcribing, I recommend using these as voice variants and macro keys.

Fourth and lastly, I would recommend espeak (https://github.com/espeak-ng/espeak-ng, run from command line as 
espeak-ng.exe "insert text here" default). This allows you to hear whata tts would do to text and thus what phonetic variations 
you can replace if a speaker misspeaks, or to check for prounciation differences between different variants of english (such as UK vs US). 


## Part three - General tips and tricks

- Firstly, as mentioned previously, you will not need number keys for transcriptions. Every date or number said should be typed out
in full as a word to ensure data integrity. 

- Secondly, try to use a variety of punctuation marks(it can be tempting to use ',' for all pauses, and use them appropriately. 
This allows the final tts to be more polished and predictable.

- Make sure to correctly mark down the start and end of a labelled section. This is critical

- If a speaker mis-speaks, you have two options; either mark down that section [unintelligible] if it is impossible to discern 
or type out what they said phonetically. Using espeak to check the phonetic tts is very helpful here.

- Make sure to splice out any coughing or deep in-breathing or generally any noisy action a speaker does between sentences. 

- Make sure to mark any data where the speaker in interrupted or a loud background sound is heard as [unintelligible]

- When in doubt, leave the data out. In most cases more good data can always be collected

- Learn a speakers voice patterns. This allows you to predict and more quickly identify a cough or deep breath, or 
stuttering they might perform that you can correct.

- Aim for an average of 4-8 second sections, and don't put any sections longer than 10s. This is easy to do as a speaker will almost always take 
a breath at least once every 10s

- Work on small files, and take breaks. It is exhausting and tiring working on long files, and you can miss important details.It is also far
easier to listen through a short file again to spot any mistakes. That being said, getting into a rythym is important to, and keep in mind that 
it will typically take far longer to transcribe than the actual length of the file, especially to do it meticously.

- Ask questions when you are unsure and work with the data engineers. They want good data just as much as you do, and will help you do improve the 
the data collection in general and your transcription skill.
  
- Lastly enjoy it. TTS is an awesome technology and although transcribing can seem tedious at times, the results it helps to create are amazing!




AutoHotKeyScript for labelling a voice

```
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
; #Warn  ; Enable warnings to assist with detecting common errors.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

#SingleInstance, Force 
CoordMode, ToolTip, Screen
ToolTip, Script is running!, A_ScreenWidth //2, 0
SendMode, Input

1::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_0]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return

2::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_1]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return


3::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_2]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return


4::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_3]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return


5::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_4]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return

6::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_5]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return

7::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[voice_variant_6]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return


`::
    a := ClipboardAll
    Clipboard := ""
    Clipboard := "[unintelligible]"
    ClipWait
    sleep, 100
    Send, {Ctrl Down}v{Ctrl Up}
    sleep, 100
    Clipboard := a
    a := ""
return



Esc::ExitApp

```
