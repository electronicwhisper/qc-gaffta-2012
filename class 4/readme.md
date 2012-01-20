# Class 4

## Graphics Processing Unit (GPU)

Traditional processors (CPUs) are single-threaded. This means that they can only do one thing at a time. Modern computers are *multi-core* which means they have 2 or maybe 4 CPUs, but still you can only now do 2 or 4 things at a time.

Contrast this with a GPU which consists of thousands of "slimmed down" processors, each operating independently. So a CPU is designed to a single, complicated computation as fast as possible, whereas a GPU is designed to a lots of simple computations in parallel.

The GPU is very useful for computing real-time graphics (hence the name). It's also useful for other highly parallelizeable computation tasks such as physics simulations, audio processing, and bitcoin mining (see [General Purpose GPU](http://en.wikipedia.org/wiki/GPGPU)).

For this class, we'll be using the GPU to do 2D image processing, where each pixel is computed independently. You can think of this as *each pixel is its own computer, whose sole purpose is to figure out what color to be*.

## Core Image Filter

The `Core Image Filter` patch is like the `Mathematical Expression` patch, but works at the level of *pixels* in **Image**s.

The [Core Image](http://en.wikipedia.org/wiki/Core_Image) programming language is a subset of [GLSL](http://en.wikipedia.org/wiki/GLSL). It is an Apple-only technology. It is optimized so that a chain of Core Image filters will all get put into a pipeline automatically, so you can chain Core Image filters without a significant increase in processing time.

### Kernels

The *kernel* is a function that is executed independently for *every pixel in the output image*. So for a 640x480 image, the kernel is run 307,200 times all in parallel on the GPU.

The kernel returns a color (a red, green, blue, and alpha value).

The kernel can access any input parameter, including input images (which it can sample colors from). The kernel can also access its current pixel position using the `destCoord()` function.

Note that `destCoord()` is the only thing that varies with respect to each independent execution of the kernel. So you can think of `destCoord()` like `Iterator Variables` in an `Iterator`! (There are a few other functions that vary but they are just conveniences, the same way Current Index and Current Position are just conveniences for each other.)

### Data types

* **float**
    * A number.
    * Number literals need decimal points to be interpreted as floats. That is, `3` is an integer but `3.0` is a float. Use `3.0`. (You can also use `3.`).

* **vec2**, **vec3**, **vec 4**
    * A *vector*, or list, of 2, 3 or 4 **float**s.
    * Use a **vec2** to represent a position in 2D space.
    * Use a **vec4** to represent a color (red, green, blue, alpha). **_color** (as a type for the kernel input) is a **vec4**
    * You can access the *components* (members) of the vector using the accessors `.x`, `.y`, `.z`, `.w` or `.r`, `.g`, `.b`, `.a` (these are synonyms).
        
        For example, if I have a **vec2** called `position`, I can access its first component as `position.x` and its second component as `position.y`. Alternatively I could access its first component as `position.r` and its second component as `position.g`.
    * Creating vectors, examples:
    
            vec2 position = vec2(320.0, 240.0) // creates a vec2 with .x set to 320, .y set to 240
            vec4 color = vec4(1.0, 0.0, 0.0, 1.0) // represents the color red
    
    * Operations on vectors are performed *component-wise*. Examples:
    
            vec2 a = vec2(1.0, 3.0);
            vec2 b = vec2(2.0, 4.0);
            a + b; // will make vec2(3.0, 7.0)
            a * b; // will make vec2(2.0, 12.0)
            
            float c = 2.0;
            a + c; // will make vec2(3.0, 5.0)
            a * c; // will make vec2(2.0, 6.0)
    
    * You can [swizzle](http://en.wikipedia.org/wiki/Swizzling_(computer_graphics)) the components of a vector. Examples:
    
            vec4 color = vec4(0.9, 0.6, 0.2, 1.0);
            
            color.grba // will make vec4(0.6, 0.9, 0.2, 1.0)
            color.rg; // will make vec2(0.9, 0.6)
            color.rrra // will make vec4(0.9, 0.9, 0.9, 1.0)

* **sampler**
    * An image.
    * You can get the color (a **vec4**) at a specific pixel position (a **vec2**) using the sample function. Example:
    
            vec2 position = vec2(100.0, 200.0);
            vec4 color = sample(image, position); // will grab the color of image at pixel position 100, 200
    
    * You can get the size of an image using `samplerSize(image)` which returns a **vec2** with width and height. Example:
    
            vec2 size = samplerSize(image);
            float width = size.x;
            float height = size.y;
    
### Loops and Conditionals

Core Image has an interesting restriction. `for` loops and `if then else` conditionals must be pre-determined at compile time. This means that `if then else` conditionals are basically useless and `for` loops must only run a constant number of times.

This restriction allows the compiler to know precisely how long a kernel will take to execute which allows it to optimize more effectively.

To create a conditional, use the *ternary operator*:

    // returns twice x if x is greater than 3, otherwise returns 0.
    x > 3.0 ? x * 2.0 : 0.0;

Often you can cleverly use math functions (like `min`, `max`, and `abs`) to get around needing ternary operators.

### Output Image

The output **Image** will be as large as the largest input **Image** (i.e. the largest **sampler**). If your kernel has no **sampler** input parameters (i.e. it is a *generator*), then your output **Image** will have infinite extent and you'll need to crop it with `Image Crop`.

### Challenges (for the mathematically inclined)

* Implement [Conway's Game of Life](http://en.wikipedia.org/wiki/Conway's_Game_of_Life) using a `Core Image Filter` and an `Accumulator`.
* Make a filter that takes an image and distorts a geometric pattern, [op art](http://en.wikipedia.org/wiki/Op_art) style.
* Generate a [Mandelbrot fractal](http://en.wikipedia.org/wiki/Mandelbrot_set).
* Generate [quasicrystals](http://mainisusuallyafunction.blogspot.com/2011/10/quasicrystals-as-sums-of-waves-in-plane.html) ([solution](https://github.com/electronicwhisper/quasicrystal)).
* Make a [Droste Effect](http://en.wikipedia.org/wiki/Droste_effect) filter. Now make it [spiral around](http://www.webdesignerdepot.com/2009/09/50-stunning-examples-of-the-droste-effect/).
