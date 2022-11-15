---
aliases: pixel perfect, plugin for pixel pefrect
---

## What is Pixel Perfect?

**Pixel Pefect** - this is the full correspondence of the layout of the element, the size and position specified in the design layout, to the nearest pixel.


## How to layout for Pixel Perfect?

In order for the layout to match the design, you need to specify the exact sizes and groups of fonts, line heights, indents between elements and blocks, and image sizes. I recommend using only [[CSS Units|relative css-units]] units whenever possible to keep your layout [[flexible | Flexible Pixel Perfect]].

One of the most convenient ways to check if the site and layout match is with the dedicated [PerfectPixel plugin](https://www.welldonecode.com/perfectpixel/). With it, you can apply the layout to the layout in the browser and check which elements need to be corrected.


## How to check layout with PerfectPixel?

To check the layout, first you need to [download](https://www.welldonecode.com/perfectpixel/) the PerfectPixel plugin for the Chrome, Opera or Edge browser. For Firefox, you can use [Pixel Perfect Pro](https://addons.mozilla.org/ru/firefox/addon/pixel-perfect-pro/) , but for Safari, the plugin is still under development.

After installation, a pink icon will appear in the browser panel - this is PerfectPixel. If it does not appear, add it yourself. To do this, open "Extensions" (located on the panel or in the browser settings) and pin the icon to the quick launch menu.

Sometimes the plugin is not available to work with sites running locally, that is, not hosted on the Internet. In such cases, open the "Extensions" section in the browser and find PerfectPixel in it. Then click on the "Details" button and change the two functions in the settings: "allow opening local files via links" and "allow access on all sites".

The next step is to export the layout page in PNG format from Figma. You can also take a screenshot of the required area or component in PNG format and use it.

To test your site, open it in a browser and then set the width in  the developer tools to the same width as the exported layout. If, for example, a designer prepared a layout for a mobile version of 320px wide, set the width to 320px as well. To do this, open the developer tools using the combinations:

**OS X** - `Control + Command + I`
**Windows** - `F12`
**Linux** - `Ctrl + Shift + I`

In the developer tools, click on the toggle device mode icon, and then set the appropriate viewport (window) width. This is necessary in order for the layout to fit exactly on the site page, because layouts are exported static, and the width of the page in the browser depends on the screen resolution of your device.

Next, click on the PerfectPixel icon and add a layer for comparison - page layout. After loading the layout, check the dimensions: the example below shows how to set the size to 1:1. If necessary, align the layout location in height and width, or fix it in the center.

There are three buttons above the position field. The first sets the transparency of the layout layer. The second fixes this layer. The third one, in color inversion mode, shows the difference between the site and the layout. Use these buttons to compare layout and approved designs.


## What can go wrong?

The most common pixel perfect beginner mistakes are wrong layer alignment, ignoring letter spacing or line height, and chaotic editing order. Because of this, the layout begins to “creep”, and the overlay again and again shows the difference between the arrangement of elements. There are several ways to avoid such errors.

Set the position of the layout: center it or align it to the top left corner of the site. Adjust padding and size from top to bottom, from left to right. So much faster and less risk that you have to redo something.

If you are using fluid layout, check compliance only on the same dimensions that the designer used in the layout. On intermediate states, if their appearance is not provided by the layout, it is not necessary to achieve similarity.

And most importantly: start working with PerfectPixel only when you have completely completed work on a block or page: add styles and graphics. If you change any elements after checking, you will have to re-adjust the site to the layout.

## How accurate should the match be?

It is impossible and unnecessary to make a site pixel by pixel with a layout, and there are reasons for this. One of them is the specifics of how fonts are displayed in different browsers and operating systems. For example, if the layout in Chrome is made exactly according to the model, then in Safari the elements may differ.

Modern design tools such as [[figma]] allow you to create interfaces that are very easy to lay out using the Pixel Perfect approach, but it is important that the designer sticks to one style guide and correctly understands the principles of flexible containers and other graphics editor features.

The main rule of modern ideal layout is to keep the designer's ideas while the component is flexible depending on the content. You can read more about this in the article - [[Flexible Pixel Perfect]]