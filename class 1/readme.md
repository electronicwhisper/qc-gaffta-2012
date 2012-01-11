# Class 1

The goal of this class was to get familiar with the user interface of Quartz Composer, get a feeling for its capabilities, and learn how to use some of the basic patches that it comes with.

We started by looking at ourselves. We opened the Patch Library (upper left button). We made a `Video In` patch by dragging it onto our workspace. The `Video In` patch grabs the image from our webcam. We wired its `Image` output pin (output pins are on the right) into the `Image` input pin (input pins on the left) of a `Billboard` renderer. We played with the other input pins on the `Billboard`, `X Position`, `Rotation`, etc. We can adjust an input pin manually by double clicking on it. We can also hit the parameters button (in upper right) to show the parameters pane to examine and adjust input pins.

We explored the *coordinate space* of the renderer, with X ranging from -1 on the left side to +1 on the right side, with 0 in the center. Then, depending on the aspect ratio of our viewer, Y goes from about -.75 on the bottom to +.75 on the top. We discovered that this is actually a 3D space by using a `Sphere` renderer in addition to the `Billboard`.

Once we had a few renderers in our workspace, we used the upper right corners of our renderers to change the layering order.

In addition to our webcam input using the `Video In` patch, we can load movies (anything Quicktime can play) into QC by dragging them onto our workspace from the Finder. We can pull up the *inspector* for the patch that is our movie, go to Settings (or shortcut ⌘2), and change to Asynchronous Mode. This will make our movie play sound and give us extra input pins for manipulating the play rate, start position, etc. of our movie.

We played with some of the Image Filter patches, like `Crystallize` and `Twirl Distortion`. Notice that the coordinate space for these patches is different than the renderers. Our numbers are scaled in pixels, with X going from left to right and Y going from bottom to top (not top to bottom!).

So far we've played with two *data types*, `Image` and `Number`. Notice that when we hover our mouse over any pin, we can see both its type and its current value. (Gotcha: if a patch isn't plugged in to a renderer--if its sitting alone in the workspace for example--QC will not activate it, so its output pins will not change as expected.) When we make wires they're colored yellow if the input data type matches the output data type. If there is some data conversion going on, the wire will appear orange (for example plugging a `Number` into a `Color`). If there is a severe data type mismatch (e.g. plugging a `Number` into an `Image`), the wire will appear red.

We animated a `Number` by making an `LFO` patch. It's worth taking the time to play with `LFO` to understand how its input parameters shape the wave that it outputs.

We manipulated numbers with the `Mathematical Expression` patch. By using the inspector to modify its settings, we can type an arbitrary mathematical expression (as your would a formula in a spreadsheet). Any words we use in this expression will show up as input pins on the patch. This is very useful!

We played with color (another data type) by making an `HSL Color` patch.

Other patches we looked at as a class were: `Audio In`, `Mouse`, `Image in String`, `Smooth`, `Color Mixer`.

We looked at the blending modes of the `Billboard` renderer. These are useful, for example, if you don't want an `Image in String` to have a black background.

Finally we started looking at macro patches such as `Render in Image`. We'll go into these more next class.