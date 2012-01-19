# Class 4

## Graphics Processing Unit (GPU)



## Core Image Filter

* Like the `Mathematical Expression` patch, but works at the level of pixels in **Image**s

* Programming language is a subset of [GLSL](http://en.wikipedia.org/wiki/GLSL)

    * Apple only.
    * Optimized so that a chain of Core Image filters all get put into a pipeline automatically.

* The *kernel* is executed for *every pixel in the output image*, independently, in parallel. The kernel can access any input parameter, including input images (which it can sample colors from).

    * Get the kernel's current pixel position using the `destCoord()` function.

* Data types
    
    * **float**. A number.
        * Number literals need decimal points to be interpreted as floats. That is, `3` is an integer but `3.0` is a float. Use `3.0`.
    
    * **vec2**, **vec3**, **vec 4**
        * A *vector*, or list, of 2, 3 or 4 **float**s.
        * Use a **vec2** to represent a position in 2D space.
        * Use a **vec4** to represent a color (red, green, blue, alpha). **_color** (as a type for the kernel inputs) is a **vec4**
        * You can access the *components* (members) of the vector using the accessors `.x`, `.y`, `.z`, `.w` or `.r`, `.g`, `.b`, `.a` (these are synonyms). For example, if I have a **vec2** called `position`, I can access its first component as `position.x` and its second component as `position.y`. Alternatively I could access its first component as `position.r` and its second component as `position.g`.
        * Creating vectors, examples:
        
            vec2 position = vec2(320.0, 240.0) // creates a vec2 with .x set to 320, .y set to 240
            vec4 color = vec4(1.0, 0.0, 0.0, 1.0) // represents the color red
        
        * Operations on vectors, examples:
        
            vec2 a = vec2(1.0, 3.0);
            vec2 b = vec2(2.0, 4.0);
            a + b; // will make vec2(3.0, 7.0)
            a * b; // will make vec2(2.0, 12.0)
            
            float c = 2.0;
            a + c; // will make vec2(3.0, 5.0)
            a * c; // will make vec2(2.0, 6.0)
    
    * sampler
        * An image.
        * You can get the color (a **vec4**) at a specific pixel position (a **vec2**) using the sample function. Example:
        
            vec2 position = vec2(100.0, 200.0);
            vec4 color = sample(image, position); // will grab the color of image at pixel position 100, 200
        
* Built-in functions

* Loops

* Conditionals
