---
layout: post
title:  "CSS Standards and Normalization"
date:   2016-11-01
author: Josh Boland and Ben Robertson
categories: scss
---

This document is a working draft.

## Purpose
The purpose of this document will be to define some standardized best practices for how our CSS is composed and organized in our projects.

## Principles
The Goals of Drupal 8's CSS philosophy will serve as a good starting point for our CSS philosophy. Well-architected CSS should be:

>#### 1. Predictable
>CSS throughout Drupal core and contributed modules should be consistent and understandable. Changes should do what you would expect without side-effects.

>#### 2. Reusable
>CSS rules should be abstract and decoupled enough that you can build new components quickly from existing parts without having to recode patterns and problems you’ve already solved. – Philip Walton, CSS Architecture

>#### 3. Maintainable
>As new components and features are needed, it should be easy to add, modify and extend CSS without breaking (or refactoring) existing styles.

>#### 4. Scalable
>CSS should be easy to manage for a single developer or for large, distributed teams (like Drupal’s).

>Source:  [CSS architecture (for Drupal 8)](https://www.drupal.org/docs/develop/standards/css/css-architecture-for-drupal-8)

In addition, we should keep Mark Otto's Golden Rule in mind:

> Every line of code should appear to be written by a single person, no matter the number of contributors.

> [Code Guide](http://codeguide.co/#golden-rule) by Mark Otto

## Style Guide

High level (borrowed from [css guidelines](http://cssguidelin.es/#syntax-and-formatting)):
 - Sass, not scss.
 - Four (4) space indents, no tabs.
 - Multi-line css
 - Meaningful use of white space.

### Sass
 Moving forward, we will depart from our Scss convention and start using Sass. This has the benefit of less brackets {} and semi-colons and overall a cleaner feel.

 Each project should include Sass linting. Use our [default .sass-lint.yml file](https://gist.github.com/mergeweb/d317ffde258f718a2aa0d033161ac2fc). It will point out the rules below for you.

### Four space indents
 Since we aren't using brackets, this keeps the Sass clearer and also is aligned with our Javascript and PHP standards.

### Multi-line css
 Selectors and properties each get their own line. Do it like this:
 ```sass
.container
    width: 95%
    max-width: 40em
 ```

### Meaningful use of white space
White space can give context to class definitions. Include two empty lines between top-level css blocks, and one line between properties and nested classes.

Example:
```sass
.card
    padding: 1rem
    margin: 1rem

    &__header // leave one empty line above this since it is nested
        border-bottom: 1px solid gray


.card--white // two empty lines above this new class block
    background-color: white


```

### Nesting Depth
Nesting depth should be limited to 2.

Example:
```sass
.block
    &__element
        &--modifier // Deepest Nest Allowed


```

### Limit line length to 80 characters
This helps make the code more readable without horizontal scrolling. Because you're writing multi-line css, this should really only come into play for comments. Limiting your line length will make your comments easier to read and therefore more useful. For instances like long urls or gradient syntax, don't worry about it.

Example:
```sass
// This file is where you override default Bootstrap variables. You can find
// a list of the default Bootstrap variables in _variables.scss
```

### Use single line comments
Your comments don't have to be on one single line, just don't use `/* These kinds of comments */`, because they will end up in the compiled css. Your comments, even if they are multi-line, should look like this:

```sass
// Have fun with it. You better get your coat out, this is going to be a cold
// painting. Trees live in your fan brush, but you have to scare them out.
// We don't have to be concerned about it. We just have to let it fall where it
// will. Put your feelings into it, your heart, it's your world. In life you
// need colors.
```

### Clean Import paths
You don't need to include leading underscores or filename extensions in your import paths. To stay consistent, your imports should look like this:

```sass
@import "base/typography" // where this file is base/_typography.sass
@import "base/colors"

@import "layout/grid"
@import "layout/containers"
```

### Class Name Format
Class names should use full words rather than abbreviations. Remember that your class names are written for the benefit of other developers, not the computer. Prefer `class="button"` to `class="btn"`.

Class names for components should use dashes between words. Prefer `class="component-name"` to `class="componentname"`.

We will use a BEM-style class naming system. BEM stands for Block Element Modifier. You can also thing about it as Component, Sub-object, Variant.

Examples:
```sass
.block
    .block--modifier
    .block__element
    .block__element--modifier


.component-name
    .component-name--variant
    .component-name__sub-object
    .component-name__sub-object--variant


.component-name
    &--variant
    &__sub-object
    &__sub-object--variant
```

<i>Source: [Drupal 8 CSS Architecture | Class Name Formatting](https://www.drupal.org/docs/develop/standards/css/css-architecture-for-drupal-8#formatting)</i>
