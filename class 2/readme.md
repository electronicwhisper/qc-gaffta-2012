# Class 2

## Part 1: Macro Patches, going deeper

* `Trackball`
* `Replicate in Space`
* `Iterator`
* Working with **Structures**
* `Queue`

## Part 2: Extending Quartz Composer

* Plug-Ins
* OSC
* Syphon
* Kinect

## Downloads for this class

The following are direct download links to .zip's and .dmg's. Current as of 12 Jan 2012.

* [Video Delay Plug-In](http://kriss.cx/tom/downloads/VideoDelay.zip) by Tom Butterworth. 

* [qcOSC Plug-In](http://hexler.net/pub/qcosc/qcOSC-v0.6.zip) by hexler. A more reliable OSC receiver than the one that comes with Quartz Composer.

* [FaceOSC](https://github.com/downloads/kylemcdonald/ofxFaceTracker/FaceOSC.zip), by Kyle Mcdonald. Tracks facial features and outputs as OSC messages on port 8338. (QC for Lion has a new `Facial Recognition` patch, but I haven't played with it yet.)

* Syphon by vade, Tom Butterworth, et al. You'll need [Syphon Quartz Composer Plug-In](http://syphon-implementations.googlecode.com/files/Syphon%20For%20Quartz%20Composer%20Public%20Beta%202.dmg), [Syphon Simple Server/Client](http://syphon-implementations.googlecode.com/files/Syphon%20Demo%20Apps%20Public%20Beta%202.dmg) (for testing), [Syphon Recorder](http://bit.ly/h1cLS5) (useful for recording Syphon image streams to disk)

* [triplex toolkit](http://tryplex.googlecode.com/files/tryplex%20toolkit%20v0.222.zip) by Sebastian Kox. Packages together everything you need to do Kinect skeleton tracking. Follow [these installation instructions](http://code.google.com/p/tryplex/wiki/Installation#Running_tryplex_with_Synapse).

For more things to play with, see (and add to!) [Quartz Composer Plug-Ins](https://github.com/electronicwhisper/qc-gaffta-2012/wiki/Quartz-Composer-Plug-Ins) and [Other Fun Stuff](https://github.com/electronicwhisper/qc-gaffta-2012/wiki/Other-Fun-Stuff) on the wiki.

## Plug-Ins

To install plug-ins that you download, you'll want to put the .plugin file into:

`/Library/Graphics/Quartz Composer Plug-Ins`

If this folder doesn't exist, create it.

Note however that plug-ins from [Kineme](http://kineme.net/) want to live in:

`/Library/Graphics/Quartz Composer Patches`

I have made a [list on the wiki](https://github.com/electronicwhisper/qc-gaffta-2012/wiki/Quartz-Composer-Plug-Ins) with all of the QC Plug-Ins that I know of.