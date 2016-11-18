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
