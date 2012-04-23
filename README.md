Note
====

SVGQuartzRenderer has not been updated in a log time, nor is it likely that it will be in the future. I had plans to refactor SVGQuartzRenderer to make it more maintainable and to make it easier to implement more of the SVG profile, but due to a lack of time I never got around to it. Also, back when I started this project there were no other SVG renderers available for iOS. Now there is SVGKit (https://github.com/mattrajca/SVGKit), which appears to be more complete and a lot less messy than SVGQuartzRenderer. So I highly recommend using that one instead. If you still need SVGQuartzRenderer for some reson, there is a newer fork available at https://github.com/adamgit/SVGQuartzRenderer

Thanks to boxerab, who contributed a lot, and to adamgit for forking :)

SVGQuartzRenderer
=================

About SVGQuartzRenderer
-----------------------

SVGQuartzRenderer is a basic SVG renderer written in Obj-C that uses CoreGraphics to render SVG files. The goal of SVGQuartzRenderer is to be a simple drop-in SVG renderer that is compatible with the iPhone platform and conforms to a subset of SVG 1.2 Tiny (Everything except Animation).


Current state of SVGQuartzRenderer
----------------------------------
SVGQuartzRenderer is currently quite far from conforming to any SVG Profile at all. It can, however, render some of the more common elements found in an SVG file. Here is a list of its current capabilities:

* Cubic curves
* Rects
* Embedded images
* Text (Note: limited support, only PostScript Core fonts)
* Fill and stroke
* Gradient fills
* Pattern fills (Note: transformation of pattern fills is not yet implemented)

Notable features that are NOT yet supported:

* Arcs
* Quadratic curves
* Shapes other than rect
* Embedded glyphs
* Filters
* FlowRegions for text. This means that any text that has a wrapping boundary (so to speak) won't render.

Known issues
------------
Other than the above listed missing features, there are some issues with how SVGQuartzRenderer handles transformation stacks. In some cases, elements in the SVG will be located in strange places where they are not supposed to be. The easiest solution for the moment is to try and modify the file in InkScape and get it to change the transformation values until SVGQuartzRenderer can handle it.

Text with nested TSpan elements won't work. That will happen if the style of one word is changed. The workaround is to use separate text nodes for each style change.

If you run in to any other bugs, please create an issue here on GitHub.
