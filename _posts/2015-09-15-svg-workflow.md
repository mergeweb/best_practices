---
layout: post
title:  "SVG Workflow 1.0"
date:   2015-9-15
author: Ben Robertson
categories: svg
---

When working with web images, we like to use SVG as much as possible. Because they are scalable, they look good everywhere. And because we can include them inline we can make our sites faster and more performant by limiting the amount of requests we make using images.

It used to be that you would receive a comp and when you started development you would slice out all the little arrows, grid, and other random icons as PNGs and then stick them in an image tag every time you needed to use one (or you included them as a background image). This can lead to pages with over 100 requests!

To save on requests, maintainability, and code cleanliness, here is the official Up&Up SVG Workflow version 1.0.

### 1. Get your SVGs out of the comps

Look through your comps in Illustrator. Find the icons that you will use as SVGs. Anything that is scalable icon or graphic will work. Think arrows, grids, and other icon things.

Select one of these icons, making sure you've got all the pieces of it. Copy it, open a new Illustrator file, and paste in your image. Make sure you fit your artboard to your new artwork and group together all the elements in the image (option+G). Then, click File -> Save As, and save your file as an SVG into an SVG folder in your project.

There will be a pop up that starts with SVG Profiles. Choose SVG 1.1 and under advanced options / css properties, select Style Elements. This will place all styles (like colors) into style tags in your SVGs and makes them easier to remove later.

Repeat these steps till you've got all your SVGs into your project folder.

### 2. Optimize your SVGs

To optimize your SVGs, you can open each file, copy the code, and paste it into the wonderful tool [SVG OMG](https://jakearchibald.github.io/svgomg/) for each file. This will take you a long time, but you should do it with one SVG so you can see what the tool actually does.

Then you should install the command line tool, which depends on node.js. To install run: 

`npm install -g svgo`

To run it on a single file:

`svgo filename.svg --pretty --enable=sortAttrs`

The best way to do it though is to optimize your whole folder of SVGs all in one fell swoop. You can do it like this if you are outside of the folder:

`svgo -f ../path/to/folder/with/svg/files --pretty --enable=sortAttrs`

Or you can do it like this inside of your SVG folder:

`svgo -f . --pretty --enable=sortAttrs`

These commands will override your old SVGs with the new, optimized code. If you would rather output new files, specifiy an output folder with `-o`:

`svgo -f ../path/to/folder/with/svg/files -o ../path/to/folder/with/svg/output --pretty --enable=sortAttrs`

For full documentation of the svgo optimizer see the [github repo](https://github.com/svg/svgo)

### 3. Use the SVGs, Luke


