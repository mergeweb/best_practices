---
layout: post
title:  "Responsive Images"
date:   2016-03-24
author: Ben Robertson
categories: general
---

It's 2016 and we are going to level up our responsive images. We have previously implemented responsive images with the good ole  `max-width: 100%; height: auto;` trick, but the problem with that is that even though we are displaying smaller images on smaller devices, we are still sending them the big one. This means slower page load on mobile, more expensive pages for our users, and overall frustration on mobile.

The trick to performant responsive images is letting the browser decide which version of an image to serve to a user. We can do this with some enhancements to the `<img>` tag or the new `<picture>` tag. Let's start with the `<img>` tag since we will be using that more frequently.

## Upgrade Your <img> Tags

Here's what a typical image tag looks like on one of our sites:

`<img class="some-class" src="path/to/image.jpg" alt="a picture of bill murray">`

To make these images more performant, we need to send more information to the browser using two new `<img>` attributes: `srcset` and `sizes`.

### srcset

The first new attribute we need to utilize is the `srcset` attribute. The `srcset` attribute tells the browser about different versions (ie different `src`'s) of the image that are available. Here's an example of an image that includes `srcset`:

~~~
<img srcset="/public/img/resp-img/shoes-large.jpg 1024w,
              /public/img/resp-img/shoes-medium.jpg 300w,
              /public/img/resp-img/shoes-small.jpg 150w"
      src="/public/img/resp-img/shoes-small.jpg"
      alt="a picture of a shoe">
~~~

<img srcset="/public/img/resp-img/shoes-large.jpg 1024w,
              /public/img/resp-img/shoes-medium.jpg 300w,
              /public/img/resp-img/shoes-small.jpg 150w"
      src="/public/img/resp-img/shoes-small.jpg"
      alt="a picture of a shoe">

So for this image, we tell the browser that there are three versions of the image available. To the right of the src path, we tell the browser how wide the image is. So image-large.jpg is 1440 pixels wide (you can also use 3x, or 2x for pixel density changes).

With this information in hand, the browser can start to figure out what version of the image is most appropriate in the current context.

### sizes

The browser can use all the help it can get however, and that's where the `sizes` attribute comes in. `sizes` attribute tells the browser how much space the image is supposed to take up in our design.

Here's our example from above with the sizes attribute added in:

~~~
<img srcset="/public/img/resp-img/shoes-large.jpg 1024w,
              /public/img/resp-img/shoes-medium.jpg 300w,
              /public/img/resp-img/shoes-small.jpg 150w"
     sizes="(min-width: 50em) 720px,
            (min-width: 35em) 150px,
            100vw"
    src="/public/img/resp-img/shoes-small.jpg"
    alt="a picture of a shoe">
~~~

<img srcset="/public/img/resp-img/shoes-large.jpg 1024w,
              /public/img/resp-img/shoes-medium.jpg 300w,
              /public/img/resp-img/shoes-small.jpg 150w"
     sizes="(min-width: 50em) 1024px,
            (min-width: 35em) 150px,
            100vw"
    src="/public/img/resp-img/shoes-small.jpg"
    alt="a picture of a shoe">

The first two entries are media queries. The first entry says that when the viewport has a min-width of 50ems, the image will always be 250px wide.

The second entry says that if the viewport has a min-width of 35ems, the image will be 33vw wide.

The last entry says that the image will be full-width for viewports under 35em wide.

## The Bigger `<picture>`

## Integrating with CMS
