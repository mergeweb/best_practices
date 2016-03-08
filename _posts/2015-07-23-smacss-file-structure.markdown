---
layout: post
title:  "SMACSS File Structure"
date:   2015-7-23
author: Ben Robertson
categories: scss
---

We follow the SMACSS model of organizing our CSS. SMACSS stands for Scalable Modular Architecture for CSS. The SMACSS way of thinking about CSS is to divide your CSS rules into several categories. Each of these categories will get their own partial in our SCSS structure.

<h4>Base Rules</h4>
Base rules are where we define all the base styles for our CSS--these are global styles that will be used everywhere and that act as a base for us to build our other styles off of.

<h4>Layout Rules</h4>
This is where we define the overall layout of the site. Usually, we break this file into sections (examples: Header, Body, Footer).

<h4>Module Rules</h4>
If we're building a site that has a lot of different modules, we will include a separate modules partial to develop the SCSS for each of those modules. This lets us keep the code separate and reusable.

<h4>State Rules</h4>
State rules define when an object on our site gets a new site. States can include a mobile/tablet media query and if an element is active or inactive.

<h4>Theme Rules</h4>
There are also theme rules, but we aren't really using this right now. Maybe we will later.

<h3>The File Structure</h3>
Here's what the file structure should look like:

{% highlight scss %}
scss
 partials
   _mixins.scss
   _variables.scss
 smacss
   _base.scss
   _layout.scss
   _modules.scss
   _states.scss
 config.rb
 merge.style.scss

{% endhighlight %}

<h3>Wrap it up</h3>
Then we can wrap it all up by importing all the partials into the merge.style.scss file:

{% highlight scss %}
// Import anything from compass here first
@import "partials/variables.scss";
@import "partials/mixins.scss";
@import "smacss/base.scss";
@import "smacss/layout.scss";
@import "smacss/modules.scss";
@import "smacss/states.scss";
{% endhighlight %}

<h3>Future Notes</h3>
It would be really cool if we could create (or find) a compass plugin that automatically creates this file structure. :)
