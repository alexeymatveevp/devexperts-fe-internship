---
aliases: relative, absolute
---

There are two kinds of units in CSS:

# Absolute length units

The following are all **absolute** length units — they are not relative to anything else, and are generally considered to always be the same size. Here is some of them:

| Unit | Name                | Equivalent to             |
|------|---------------------|---------------------------|
| `px` | Pixels              | 1px = 1/96th of 1in       |
| `cm` | Centimeters         | <1cm = 37.8px = 25.2/64in |
| `mm` | Millimeters         | 1mm = 1/10th of 1cm       |
| `Q`  | Quarter-millimeters | 1Q = 1/40th of 1cm        |
| `in` | Inches              | 1in = 2.54cm = 96px       |
| `pc` | Picas               | 1pc = 1/6th of 1in        |
| `pt` | Points              | 1pt = 1/72nd of 1in       |

## Relative length units

Relative length units are relative to something else, perhaps the size of the parent element's font, or the size of the viewport. The benefit of using relative units is that with some careful planning you can make it so the size of text or other elements scales relative to everything else on the page. Some of the most useful units for web development are listed in the table below. Here is some of them:

| Unit       | Relative to                                                                                                                                                           |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `em`       | Font size of the parent, in the case of typographical properties like `font-size`, and font size of the element itself, in the case of other properties like `width`. |
| `ex`       | x-height of the element's font.                                                                                                                                       |
| `ch`       | The advance measure (width) of the glyph "0" of the element's font.                                                                                                   |
| `rem`      | Font size of the root element.                                                                                                                                        |
| `lh`       | Line height of the element.                                                                                                                                           |
| `rlh`      | Line height of the root element. When used on the `font-size` or `line-height` properties of the root element, it refers to the properties' initial value.            |
| `vw`       | 1% of the viewport's width.                                                                                                                                           |
| `vh`       | 1% of the viewport's height.                                                                                                                                          |
| `vmin`     | 1% of the viewport's smaller dimension.                                                                                                                               |
| `vmax`     | 1% of the viewport's larger dimension.                                                                                                                                |
| `vb`       | 1% of the size of the initial containing block in the direction of the root element's block axis.                                                                     |
| `vi`       | 1% of the size of the initial containing block in the direction of the root element's inline axis.                                                                    |
| `svw, svh` | 1% of the small viewport's width and height, respectively.                                                                                                            |
| `lvw, lvh` | 1% of the large viewport's width and height, respectively.                                                                                                            |
| `dvw, dvh` | 1% of the dynamic viewport's width and height, respectively.                                                                                                          |
