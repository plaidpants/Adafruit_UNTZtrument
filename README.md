Adafruit_UNTZtrument
====================

This demo step sequencer contains modifications from the original provided by AdaFruit. It also uses 4 encoders with push switches for additional input.

![untz step sequencer](/../master/basic.gif?raw=true)

Improvements include:
1. implements up to 16 beats on the grid with only an 8x8 untz using one of the encoders for scrolling left and right
2. the number of beats on the grid is adjustable up to 16
3. implements up to 8 layers outputing notes on different channels at the same time
4. implements up to 8 sets of sequence grid sets with 8 layers each that can be swiched
5. can change to and instruments (press button for first set 1-64, press again for second set 65-127)
6. has embedded notes scales (major, minor, chromatic, etc)
7. can adjust tempo and volume using 2 of the encoders
8. can adjust position on the scale with the last encoder
9. saves current state of the sequencer in EEPROM when button is held down for 10 seconds

The sequencer works by storing notes on a grid. Pressing a lighted button will toggle the lights on or off and the corresponding notes on or off in this grid layer.

A vertical bar moves across the notes on the grid playing all the notes in the column. More than one note can play at the same time.

A grid set has mutliple layers which can be used to play different instruments. As the vertical bar moves across the grid it will play all the notes on all the layers in a grid set. You can switch between layers and grid sets to make more complex musical sequences.

![untz step sequencer](/../master/button1.gif?raw=true)

Press button 1 to select the scale, press button 1 again to select the midi channel, press it again to return to normal. The value is indicated by the location of the intersection of the displayed horizontal and vertical line counting left to right and down. The value is changed by selecting a new value while the current value is being displayed. 

![untz step sequencer](/../master/individual.gif?raw=true) ![untz step sequencer](/../master/wholenote.gif?raw=true)

Selection of the same scale will alternate between notes being held for a duration or playing the note for each sequence light that is lit. See below for the list of scales embedded in the code.

All layers in a grid set default to the major scale with notes being held. All grid sets have the same scales.
Layers default to midi channels 3, 4, 5, 6, 7, 8, 9 (drum kit), 2 (performance layer). All grid sets have the same midi channels.

Hold button 1 for five seconds to erase everything in volitale memory.

![untz step sequencer](/../master/rotate1.gif?raw=true)

Rotate button 1 up and down to adjust note pitch range (notes are lost when they scroll off the top or bottom, this can be used to quickly erase a single grid layer).

All layers on all grid sets default to the middle of the scale. Each layer on each grid set can be set indivudually.

Press button 2 to select the layer, press button 2 again to select the grid set, press it again to return to normal. The value is indicated by the position of the horizontal or vertical line on the grid counting from the top or the left. The botton layer (layer 8) is the performance layer (see below). The currently playing grid set will not switch to a newly selected grid set until it has finished playing the current one.

Rotate button 2 up and down to adjust tempo up or down.

All grid sets defaults to 240 bpm. Individual layers in a grid set cannot have different tempos.

Press button 3 to select a midi instrument between 1-64, press button 3 again to select a midi instrument between 65-128, press it again to return to normal. The value is indicated by the location of the intersection of the displayed horizontal and vertical line counting left to right and down. The value is changed by selecting a new value while the current value is being displayed.

All layers default to midi instrument 0. All grid sets have the same midi instruments. The midi channel 9 (drum kit) set above will typically overide this setting and use the drum kit instrument instead. 

Rotate button 3 to adjust note sequence measure view left or right. You can have up to 16 note beats per measure.

Press button 4 to select the measure size, press it again to return to normal. The value is indicated by the location of the intersection of the displayed horizontal and vertical line counting from 1 left to right and down. The value is changed by selecting a new value while the current value is being displayed.

All grid sets default to 16 beats per measure. All layers in a grid set have the same beats per measure.

Hold button 4 for ten seconds to store everything in volatile mememory into non-volitale memory.

Rotate button 4 up and down to adjust volume up or down.

All layers in a grid set default to the middle volume value. All grid sets have the same volumes.

Note: Depending on how you wire the buttons and encoders you may find these functions located on different buttons or encoders.

Note: The performance layer is available on each grid set as layer 8 and is not used for storage of note sequences. Selecting this layer will change the meaning of all the grid buttons on the device. The right most column of buttons display the currently playing grid set and can be used to select which grid set will play next. The rest of the buttons are layed out in rows of octives. The rows are indivudal octive scales and have the lowest key on the left and the highest key on the right based on the currently selected scale. Scales that have more or less then seven notes will not be so well organized. Each octive row are stacked so the highest octives are on top and the lowest are on the bottom. You can use this mode to play along with the sequences you have stored by pressing the lighted buttons to play the select instrument. Notes that are playing on the other layers on the grid set will light up the corresponding buttons.

Scales:
majorScale = 0
minorScale = 1
chromaticScale = 2
bluesScale = 3
bluesDiminishedScale = 4
fullMinorScale = 5
harmonicMajorScale = 6
harmonicMinorScale = 7
jazzMinorScale = 8
hawaiianScale = 9
orientalScale = 10
majorMinorScale = 11
genusChromaticum = 12
dorian = 13
indian = 14
locrian = 15
lydian = 16
melodicMinor = 17
mixolydian = 18
pentatonic = 19
phrygian = 20
turkish = 21
wholeHalf = 22
wholeTone = 23
spanish = 24
pelog = 25
kumoi = 26
iwato = 27
inSen = 28
hirojoshi = 29
hungarianMinor = 30
bhairav = 31
superLocrian = 32
minorPentatonic = 33

