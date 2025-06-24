# My Fuzzface design process

## Research
https://www.electrosmash.com/fuzz-face

## Component list

## Simulation and Testing
### Creating the Circuit
I'm using LT Spice for modeling, as it is free and fairly easy to use. It allows importing of models that can be found all over the internet, and includes a large number of models, especially those from Linear Technology (now Analog Devices). I will periodically import models for improved accuracy and include that process here.

### Using waveforms as input / output
- https://www.youtube.com/watch?v=Cym6mcvonfM

For Input:
- Create voltage source
- Hold CTRL, right click on voltage source
- Enter "wavefile=<file.wav>" in Value field.

For Output:
- Label wire using a descriptive name
- Click on the ".op" button on the top right of the screen to add an operation
- ".wave C:\output.wav 16 44.1K V(out)", using the help file as a reference. Can also produce stereo, but for the Fuzzface we don't plan to do that as of now
- file, resolution, bit rate, node to digitize

Can we use mp3 or other formats?
- This does not seem to be supported, so I will either create a smooth workflow, or use a small number of samples to reduce the effort of converting files

### Setting up the circuit design work flow
This stage is generally the most challenging for me, so I'm making sure to have it documented. Directions online for bringing in a schematic, bringing in a wavefile are useful, but everything has to be in range for the output to sound nice, for the waveform to simulate the amplitude of the sound. So I'll cover my process here.

The first step is to use the waveform input to simulate the guitar going into the pedal. For this I used Audacity and just recorded a few seconds of clean guitar from a youtube video to keep things simple. On the plus side, Audacity handles this pretty well, and will save a WAV file for you. The challenge is getting the amplitude just right, so that the LT SPICE circuit 'feels' like its getting the small signals coming from your guitar pickups. Luckily the Fuzzface page is helpful with expected amplitudes. It sounds like our signal should be <50mV on the input to get soft distortion. When LT SPICE brings in a WAV file, it normalizes the amplitude from -1 to 1 V. In my case of the youtube video, the audio was full volume, taking up the entire range, so before saving the WAV file we need to make it feel more in the 25-50mV range. In Audacity, this is done by highlighting the audio track I recorded, going to Effect -> Volume and Compression -> Amplify, and setting the gain in a range of -30dB to -40dB. Then when we save the waveform and bring it into LT SPICE, the voltages match what a guitar would provide.  
## Modifications
### Germanium simulation
This may turn into a rabbit hole..
