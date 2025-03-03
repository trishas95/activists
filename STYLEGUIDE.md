# Style Guidelines for activist.org

Thank you for following our style guide! The team asks that you familiarize yourself with this guide and follow it for any contributions. Doing so makes PRs and general code collaboration much more effective :)

We'll also link to this document in cases where these guidelines have not been followed. If that's what brought you here, no stress! Thanks for your interest and your drive to contribute to open-source and activist in particular! ❤️

If you have questions or would like to communicate with the team, please [join us in our public Matrix chat rooms](https://matrix.to/#/#activist_community:matrix.org). We'd be happy to hear from you!

<a id="contents"></a>

## **Contents**

- [Vue and Nuxt](#vue-and-nuxt)
- [Tailwind](#tailwind)
- [Formatting](#formatting)
- [Colors](#colors)
- [Font](#font)
- [Text size](#text-size)
- [Padding](#padding)
- [Common styles](#common-styles)

<a id="vue-and-nuxt"></a>

## Vue and Nuxt [`⇧`](#contents)

The frontend for activist is written in the framework [Vue.js](https://vuejs.org/) and specifically the meta-framework [Nuxt.js](https://nuxt.com/).

The team chose Vue because of its broad usage across the development industry as well as relative ease of use and adoption for new contributors. Most of all we appreciate the structure that Vue adds to a project by leveraging the order of HTML and adding scripting and styling on top. Nuxt expands on Vue seamlessly and includes many [modules](https://nuxt.com/modules) to make development much easier.

Vue files (`.vue`) are Single-File Components that have `<template>`, `<script>` and `<style>` blocks. Conventions for writing Vue for activist include:

- `<template>` blocks should come first, `<script>` second and `<style>` last
- [TypeScript](https://www.typescriptlang.org/) should be used where ever possible within `<script>` blocks
  - This will be more strictly enforced as the project matures

<!-- <a id="typescript"></a>

## TypeScript -->

<a id="tailwind"></a>

## Tailwind [`⇧`](#contents)

activist uses [Tailwind CSS](https://tailwindcss.com/) for CSS styling and [Headless UI](https://headlessui.com/) unstyled, accessible components for more complex page elements like dropdowns and popups. Tailwind styles are applied via space-separated `class="STYLE STYLE STYLE"` attributes on HTML elements in Vue `<template>` blocks. The following sections will detail the specific styles that are used throughout the codebase.

Please note that as activist uses Tailwind, this means that `<style>` blocks are often times not used within Vue Single-File Components. `<style>` blocks should only be used in cases where including the styles within the `<template>` block would be overly complex or if Tailwind does not support a certain style parameter. The team understands that Tailwind at times can lead to very long style classes, but because of this we make use of the custom classes below to combine commonly used elements into consistent, responsive drop-in attributes.

<a id="formatting"></a>

## Formatting [`⇧`](#contents)

activist uses [Prettier](https://prettier.io/) to format the code and [Headwind](https://github.com/heybourn/headwind) to sort Tailwind CSS classes. We'll eventually set it up so that code is autoformatted within the PR flow, and generally the team isn't worried about formatting as it's done on save locally as we work.

<a id="common-styles"></a>

## Common styles [`⇧`](#contents)

The following are custom Tailwind classes from [frontend/assets/css/tailwind.css](https://github.com/activist-org/activist/blob/main/frontend/assets/css/tailwind.css) that are consistently used within the activist frontend codes:

- `focus-brand`

  - Creates a custom brand styled orange ring around an element when it is focussed for both light and dark mode
  - Should be used on all elements that the user can focus (buttons, links, dropdowns, menu items, etc)

- `link-text`

  - Color and hover color are defined for links for both light and dark mode

- `card-style`

  - Applies styles for consistent cards across activist's pages
  - Colors are defined for light and dark mode with border width and radius also being applied
  - Used in cases like about page sections, search results, etc

<a id="colors"></a>

## Colors [`⇧`](#contents)

The file [frontend/tailwind.config.ts](https://github.com/activist-org/activist/blob/main/frontend/tailwind.config.ts) defines all colors within the `colors` section of the `theme` configuration. All brand colors are split first by `light` and `dark` mode in their names and then the general usage of the color followed by qualifiers such as `hover`. The reason for this naming criteria is to avoid repeat styling keywords like `text-text-light` that might lead to confusion or leaving it as just `text-light` rather than applying the usage and then the color. The prior style would correctly be applied via `text-light-text`.

Note that tailwind allows for alpha components for opacity to be applied to colors directly within the class declaration. We thus do not need to save versions of colors with transparency unless they are inherently used with an alpha less than one. An example of a color that has an inherent non-one alpha is `light-text` (`"rgba(0, 0, 0, 0.85)"`). To apply an alpha component to a color in Tailwind you follow it with a slash and the alpha that should be used as in the following example:

```html
<!-- The background of this div has 40% opacity. -->
<div class="bg-light-cta-orange/40"></div>
```

<a id="font"></a>

## Font [`⇧`](#contents)

The fonts for activist are [Red Hat Text and Red Hat Display](https://www.redhat.com/en/about/brand/standards/typography) as defined in [frontend/tailwind.config.ts](https://github.com/activist-org/activist/blob/main/frontend/tailwind.config.ts). `Red Hat Text` is applied throughout the website and `Red Hat Display` is used for all headers by applying `font-display`. As headers are generally defined by `responsive-h#` custom classes that include `font-display`, it will be rare that you'll need to apply it directly. See the next section for more details.

<a id="text-size"></a>

## Text size [`⇧`](#contents)

[frontend/assets/css/tailwind.css](https://github.com/activist-org/activist/blob/main/frontend/assets/css/tailwind.css) defines custom combinations of default and activist defined Tailwind text and header sizes. The naming criteria for text classes follows Tailwind's text sizes and includes `responsive-text-xs`, `s`, `base`, `md`, `lg`, `xl`, and `2xl`.

Custom responsive header classes are generally larger than their equivalents for text and further all have `font-display` applied to them. The naming criteria of responsive headers follows that of HTML headers so that the team remembers that when a `responsive-h#` tag is used that it should be applied to a coinciding `<h#>` tag for accessibility. Note that headers should generally have a `bold` style applied to them as well, with for example page headers being defined as follows:

```html
<!-- The size and weight styles for page headers. -->
<h1 class="font-bold responsive-h1">Page Header</h1>
```

<a id="padding"></a>

## Padding [`⇧`](#contents)

There are a few custom padding classes that can be used for `px` and `py` styling as defined in [frontend/assets/css/tailwind.css](https://github.com/activist-org/activist/blob/main/frontend/assets/css/tailwind.css). Please use consistent custom padding classes to assure that elements move together at different breakpoints.
