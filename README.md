# Video to audio synthesis - software instruments

### Table of contents

* [Objectives](#objectives)
* [instrument-1](#instrument-1)
* [instrument-2](#instrument-2)
* [How to use the instrument](#how_to)
* [Known issues](#issues)
* [Downloads](#downloads)
* [Sources](#Sources)

<a name="objectives"></a>
## Objectives
The primary goal of this work was to develop a software instrument, which takes video data as input and is able to synthesize audio from that input. In case of the first instrument, an external MIDI device can be connected to play the instrument. The second instrument works as a sampler. 

The main challenge was to choose a right way to extract the data from the video along with the right way to synthesize or modulate the audio, in order to achieve something that sounds interesting in the musical context.


<a name="instrument-1"></a>
## instrument-1


![instrument-1](https://codeberg.org/davidhro/video-to-audio-synthesis-instrument-1/raw/branch/main/documentation/pictures/instrument-1.png)



The data, extracted from the video, are in this case coordinates of boundaries around objects in the image, found by a simple computer vision algorithm. This algorithm converts video to greyscale, then to binary (controlled by a threshold). The threshold at which a pixel is classified either as black or white can be set manually. The boundaries are then drawn around a continuous group of white pixels, which are not separated by any black pixels.

The modulated audio data are the amplitudes and panning of 64 sine wave oscillators. The first oscillator is the root note (frequency of the MIDI note, which is currently played), the rest of the oscillators are harmonics (root note frequency multiplied by *n*, where *n* is a number from 2 to 64). A granulator, which can only be modified by the video data, samples the synthesized data from the oscillator and processes them. The granulator sound can be then mixed with the original signal to further modify the output audio signal.

ADSR control unit is also present (and modifiable by the video data) to further shape the sound. The instrument also consists of an effects unit and a step sequencer. Both the effects unit and the sequencer can be, with exceptions (Res and Type parametrs of the filter effect), configured to take the data, extracted from the video, to modulate the effects. Frequency shifter, waveshaper, chorus, delay, reverb and filter were picked due to a wide range of sound modifications, that can be achieved by combination of these effects. Output unit allows for audio driver settings, recording of the outgoing sound and gain, panning adjustments.


<a name="instrument-2"></a>
## instrument-2

![instrument-2](https://codeberg.org/davidhro/video-to-audio-synthesis-instrument-1/raw/branch/main/documentation/pictures/instrument-2.png)


Video data is acquired either as a webcam feed or a video that can be dragged and dropped into the corresponding section. The data are pixel values of one of the three planes (red, green or blue) of the video on the input. The pixels can be scrolled through by the XY axis slider. 

The audio is in this case imported as a .wav file (other file extensions not tested but might be possible to use). These audio files are played by turning on the transport toggle on the sequencer and toggling on any step in the corresponding row of the step sequencer. Parameters such as sample start, playback speed, panning, effects dry/wet setting and number of sequencer step can be automated by the video data. Tempo of the sequencer can be entered manually or controlled by the video data.

Similar to instrument-1, this instrument also allows to control the effects by the video data (apart from the Res and Type filter effect parameters). Output unit works the same as in case of instrument-1.


<a name="how_to"></a>
## How to use the instruments

### Setup

#### Option 1
Download the .zip file which contains the instrument. Each .zip file contains the .exe file and dependecies needed to run it (link in the [Downloads](#downloads) section).

#### Option 2
Download the folder which corresponds to the instrument, then open the .maxproj file in Max 8 or higher.


### Documentation
Detailed description of both instruments with a brief manual on their initial setup is available in the [Documentation](https://codeberg.org/davidhro/video-to-audio-synthesis-instruments/src/branch/main/documentation) folder.

<a name="issues"></a>
## Known issues
* While being run on Linux (Mint) with Bottles, it is not possible to use camera to acquire the video data. Therefore it is needed to use a video file as an input in this configuration. Also the program was unable to detect an external MIDI device, which makes it practically unusable on Linux (with the tested configuration).

* The sequencer steps on instrument-1 doesn't work as intended when it comes to the ON/OFF buttons on each step. The buttons tend to be ON most of the time even when they are turned OFF.


<a name="downloads"></a>
## Downloads


* Full text of the thesis (in Czech language): [Bachelor thesis](http://hdl.handle.net/11012/210871)
* Executable (.exe) files with resources needed to run them can be downloaded as a .zip file from these links: [instrument-1.zip](https://drive.google.com/file/d/1lqDwZQ3CtoBVO8veQoWEQ5xt-jy_xjvu/view?usp=drive_link), [instrument-2.zip](https://drive.google.com/file/d/1l4vRzr397L26udH7BqvDsOe21kkAZbYE/view?usp=drive_link)

<a name="Sources"></a>
## Sources

The main resources, which directly influenced the software are shown here. All other resources (literature and so on) used to complete this instrument are cited in the full text of this thesis, available from the link in the [Downloads](#downloads) section. Licenses for the external libraries used in this code are available in the [THIRD PARTY LICENSES ](https://codeberg.org/davidhro/video-to-audio-synthesis-instruments/src/branch/main/THIRD%20PARTY%20LICENSES) folder.

* [cv.jit Max Package](https://github.com/Cycling74/cv.jit)
* [LowkeyNW Max Package](https://github.com/nwolek/LowkeyNW)
* [Max/MSP Tutorial | A granular synthesiser built with codebox in gen~](https://www.youtube.com/watch?v=VU2TQmxte9A)
* [RTC-lib Max Package](https://www.essl.at/works/rtc.html)


