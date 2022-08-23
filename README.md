# Alexandrie

[![License](https://img.shields.io/github/license/pharo-graphics/Alexandrie.svg)](./LICENSE)
[![Tests](https://github.com/pharo-graphics/Alexandrie/actions/workflows/test.yml/badge.svg)](https://github.com/pharo-graphics/Alexandrie/actions/workflows/test.yml)

A 2D canvas for [Pharo](https://pharo.org/) based on [Cairo](https://www.cairographics.org).

It was born as an alternative for rendering [Bloc](https://github.com/pharo-graphics/Bloc) elements, but it is independent from Bloc.

**Note:** The canvas API is unstable yet. We started coding it by following the ideas written below, but in a next version the API will take better and more stable shape.

### FFI bindings

This project includes FFI bindings to Cairo and FreeType that do not depend on the bindings that exist in Pharo. 

**What's different?**

- Document Pharo code to ease a developer to link with the C API counterpart. 
- Offer direct access to the raw C API of the bound libraries. (See note below)
- Cairo: 
  - It doesn't rely on the "Surface Plugin", like Sparta-Cairo, unlike Athens-Cairo.
  - Focus on using the Cairo API smartly, avoiding redundant calls and early OO abstractions.
- FreeType:
  - For the moment, only cover a small subset of the FreeType API that Cairo needs to draw text.
  - Support color emoji font

**Note for newcomers to Pharo:**

Using this bindings, a developer should be able to follow a C tutorial and easily translate the code to Pharo.
Tip: To find how a C API function is bound in Pharo, you can copy the function name in the official documentation or the tutorial, paste it on any Pharo text editor, right click and select "Method source with it" in the context menu. If there is a method with that name, then start browsing the class, senders, etc. to learn how to use it. If no method contains it, then you can add it by yourself "by example": find a similar bidning to another FFI call and it is often simple.


## Install

Load in a Pharo 11 (should work on previous versions of Pharo, too):

```smalltalk
Metacello new
        baseline: 'Alexandrie';
        repository: 'github://pharo-graphics/Alexandrie/src';
        load.
```

## Testing

The project counts with Test packages that pixel-compare the actual output of the render with PNGs previously exported in the 'tests/' directory of this repo. If any pixel doesn't match with the expected output, the test fails. Browse `AeCanvasTest`.


## License

This code is licensed under the [MIT license](./LICENSE).
