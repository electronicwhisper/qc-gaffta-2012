# Class 3

## Recording Quartz Composer output

* To record live output, I recommend Syphon Recorder. See below.
* To record offline output (i.e. not live but rather slowly rendered output), I recommend [Quartz Crystal](http://kineme.net/QuartzCrystal) by Kineme. This has the advantage that you can do high-resolution, high-framerate renders of compositions which cannot render at high framerates live (for example, if you've created a video effect and you want to apply it to an HD video). The disadvantage is you cannot have any live input.

## [Syphon](http://syphon.v002.info/)

* Like OSC, but for sharing images between applications.
* Downloads
    * [Syphon Quartz Composer Plug-In](http://syphon-implementations.googlecode.com/files/Syphon%20For%20Quartz%20Composer%20Public%20Beta%202.dmg)
    * [Syphon Simple Server/Client](http://syphon-implementations.googlecode.com/files/Syphon%20Demo%20Apps%20Public%20Beta%202.dmg) for testing
    * [Syphon Recorder](http://bit.ly/h1cLS5) records Syphon image streams to disk
* When `Syphon Server` is set to Source as OpenGL Scene, it will grab *any layers below it* in the Viewer.

## `Accumulator`

This is the standard pattern we see when using `Accumulator`,

![Accumulator Pattern](https://github.com/electronicwhisper/qc-gaffta-2012/raw/master/class%203/accumulator%20pattern.png)

We can use `Accumulator` to create feedback effects (like video delay effects) and to make drawing-like applications.

## `JavaScript`

* Think of `JavaScript` as a more advanced `Mathematical Expression`.
* The `main` function has extra stuff to annotate the *types* of the inputs and outputs (i.e. **Number**, **String**, **Structure**, etc.). Other than that, we're using straight JavaScript (without the DOM of course).
* The `main` function is called any time any input changes.
* Variables outside the `main` function maintain state. See the state example.
* QC **Structure**s translate to JavaScript Arrays and Objects.