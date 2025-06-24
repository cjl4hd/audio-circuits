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
## Modifications
### Germanium simulation
This may turn into a rabbit hole..