# instrument-1

### Table of contents

* [Objectives](#objectives)
* [Description](#description)
* [Resources](#resources)

<a name="objectives"></a>
## Objectives
The primary goal of this work was to develop a software instrument, which takes video data as input and is able to synthesize audio from that input. In case of this instrument, an external MIDI device can be connected to play the instrument. The main challenge is to choose a right way to extract the data from the video along with the right way to synthesize or modulate the audio, in order to achieve something that sound interesting in the musical context.


<a name="description"></a>
## Description




The instrument also consists of an effects unit and a step sequencer. The effects unit can be configured to take the data, extracted from the video, to modulate the effects. Frequency shifter, waveshaper, chorus, delay, reverb and filter were picked due to a wide range of sound modifications, that can be achieved by combination of these effects. 

Manual on the use of this instruments is available in the documentation folder.

### Known issues
* While being run on Linux (Mint) with Bottles, it is not possible to use camera to acquire the video data. Therefore it is needed to use a video file as an input in this configuration. Also the program was unable to detect an external MIDI device, which makes it practically unusable on Linux (with the tested configuration).


<a name="resources"></a>
## Resources

* Full text of the thesis (in Czech language): [Bachelor thesis](http://hdl.handle.net/11012/210871)
* Executable (.exe) file with resources can be downloaded as a .zip file from this link: [instrument-1.zip](https://drive.google.com/file/d/1lqDwZQ3CtoBVO8veQoWEQ5xt-jy_xjvu/view?usp=drive_link)