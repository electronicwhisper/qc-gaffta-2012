# `JavaScript`

## basic math.qtz

Illustrates how `JavaScript` can be used as a more powerful `Mathematical Expression`, in this case returning two output values.

## structures.qtz

Uses `JavaScript` to create a **Structure**, combining three input values into a **Structure** containing the values.

## structures2.qtz

Illustrates a use for creating **Structure**s and also shows destructuring using `JavaScript` (look inside the `Iterator`). Note that you have to handle the case for when the input **Structure** is null, due to how QC error checks `JavaScript`.

## structures2 with trail.qtz

The same as before, but now we're skipping some of the members of the `Queue`. In so doing, we create a trailing effect. This pattern of using a `Queue` with an `Iterator`, but skipping some of the values, can be used anywhere you would normally use `Queue` and `Iterator`.

Exercise: try using this technique with alpha delay.qtz from class 2.

## state.qtz

Illustrates how variables declared outside of the main function preserve their state. Thus `JavaScript` patches are not stateless (like `Mathematical Expression`). They can have memory (like `Queue`, `Accumulator`, `Smooth`, etc).