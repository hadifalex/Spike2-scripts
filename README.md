# Spike2-scripts
Various scripts used for Spike2

# fileSplitter.s2s

## Intro

This is the most commonly used script for Spike2 that breaks down a standard .smrx file into many smaller .txt files.
The partitioning of the file is based on the file Markers within the file.

It is important to remember that .smrx files are a proprietary form of a standard binary file which means that when you convert to 
multiple .txt files you should expect heavier memory footprint. 

## Usage

### Selecting channel to "split"

While having the desired .smrx file selected, start the fileSplitter.s2s script to open the GUI.
From the drop-down menu select the channel you would like to break down based on Markers. 
In our lab, the Markers we use Channel 32 for our experimental markers and although they been hardcoded into the script,
they can easily be modified to any Marker channel of choice.

In a similar vein, we always "split" the original, raw channels of interest - Laser, Nerve, Signal and Stimulus.
We always work with the most raw format that Spike2 can generate as we currently do not exploit any post-processing capabilities of Spike2. 
As with the Markers, the channels can be modified to any name or number via the variable "chanNames" to include any post-processed channel we desire.

### Split file size
Once a channel has been selected, the user is asked to provide the exact time interval of each file relative to each time Marker from channel 32
and requires a starting point A and an ending time B given in [SECONDS].

For instance, assume that you have a marker at t = 128.3 s.
If you have selected A=0 and B=10, then that particular file will be the data of the selected channel for the duration 128.3-138.3 seconds.
This process will be repeated for all Markers in that file.


### Select ROI

Sometimes you do not want to extract all the data from the entire .smrx file.
You can limit the extraction temporal ROI through the last dialogue option where the script will only be applied for Markers within the ROI of your choice.

