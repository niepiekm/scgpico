---
Title: Sparta
---
#Sparta
#Introduction

Sparta is an almost stateless vector graphics API for Pharo that provides bindings to the Moz2D rendering backend.
Moz2D is the extracted graphical engine from Mozilla Firefox compiled as standalone shared library together with the extern C bindings required to call the engine from Pharo.

*(All images are rendered using Sparta in Pharo)*
- [![/files/88/sk44t4p7e2mjv70q58qagx01e0qf1d/Sparta-v1-Neon.png](/files/88/sk44t4p7e2mjv70q58qagx01e0qf1d/Sparta-v1-Neon.png)](Sparta%20Neon)

#Backends
Moz2D, and as result Sparta, has support of native OS graphic engines, as well as cross platform ones.

On all platforms Sparta provides support of [Cairo](https://cairographics.org) and [Skia](https://skia.org/). Additionally, high performant [CoreGraphics and CoreGraphics Accelerated](https://developer.apple.com/reference/coregraphics) on Mac OS and [Direct2D](https://msdn.microsoft.com/en-us/library/windows/desktop/dd317121(v=vs.85).aspx) on Windows.
In total Sparta supports 5 different rendering backends. 

#Text
One of the biggest improvements compared to existing graphics engines from Pharo is advanced high quality text rendering with multi-language support.
- [![/files/3a/p4orm22yikqipeype28o2pvk6e5688/Sparta-v1-Multilanguage.png](/files/3a/p4orm22yikqipeype28o2pvk6e5688/Sparta-v1-Multilanguage.png)](Sparta%20Multilanguage)

The current Pharo text rendering engines draw a piece of text with one concrete font and style. If the font does not have an appropriate character, a stub glyph will be rendered instead.
Sparta introduces a notion of font groups that allow us to achieve a smooth fallback font detection based on the selected font style, language and missing glyphs. Fallback font support requires more complex text measurement, as multiple fonts faces are involved to render a single piece of text.

#Filters
Since Sparta is based on the Moz2D backend that was designed for web browsers, we can get support for a wide variety of [filter primitives](https://www.w3.org/TR/SVG/filters.html). Sparta provides an ability to compose multiple filter primitives to get a single, advanced filter. For example, with the help of ColorMatrix and TableTransfer filters we can simulate some popular Instagram-like filters, for example Nashville, Inkwell or Brannan.
- [![/files/0c/muy0u5444f6hqyuv8bc2e9lovwtk0p/Sparta-v1-Filters.png](/files/0c/muy0u5444f6hqyuv8bc2e9lovwtk0p/Sparta-v1-Filters.png)](Sparta%20Filters)

#Basic drawings
We should not forget that first of all Sparta is a vector graphics engine. It allows developers to create, fill and stroke custom paths and shapes. Together with gaussian blur, we can achieve astonishing results that were not possible before.
- [![/files/5a/u4ctbo9b05r8rkeb04f3dgirs0x34v/Sparta-v1-Shapes.png](/files/5a/u4ctbo9b05r8rkeb04f3dgirs0x34v/Sparta-v1-Shapes.png)](Sparta%20Shapes)

#Download and Install

Prepared image\+vm for Mac OSX: [Sparta-v1.1.zip](https://drive.google.com/open?id=0B-bMBVDOi3oTQkZBSUE0ckYzVmM)

Sparta requires an additional shared library that can be compiled from sources on Mac OS and Linux.
- Plugin page on [github/Moz2D](https://github.com/syrel/Moz2D)
- Sparta page on [github/Sparta](https://github.com/syrel/Sparta)
```
Metacello new
  baseline: 'Sparta';
  repository: 'github://syrel/sparta/src';
  load
```
