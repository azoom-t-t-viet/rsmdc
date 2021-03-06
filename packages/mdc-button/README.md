<!--docs:
title: "Buttons"
layout: detail
section: components
excerpt: "Material Design-styled buttons."
iconId: button
path: /catalog/buttons/
-->

# Buttons

<!--<div class="article__asset">
  <a class="article__asset-link"
     href="https://material-components.github.io/material-components-web-catalog/#/component/button">
    <img src="{{ site.rootpath }}/images/mdc_web_screenshots/buttons.png" width="363" alt="Buttons screenshot">
  </a>
</div>-->

Buttons allow users to take actions, and make choices, with a single tap.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/go/design-buttons">Material Design guidelines: Buttons</a>
  </li>
  <li class="icon-list-item icon-list-item--link">
    <a href="https://material-components.github.io/material-components-web-catalog/#/component/button">Demo</a>
  </li>
</ul>

## Installation

```
npm install @rsmdc/button
```

## Basic Usage

### HTML Structure

```html
<button class="mdc-button">
  Button
</button>
```

> _NOTE_: Examples here use the generic `<button>`, but users can also apply the `mdc-button` class to `<a>` elements.

### Styles

```scss
@import "@rsmdc/button/mdc-button";
```

### JavaScript Instantiation

The button will work without JavaScript, but you can enhance it to have a ripple effect by instantiating `MDCRipple` on the root element. See [MDC Ripple](../mdc-ripple) for details.

```js
import {MDCRipple} from '@rsmdc/ripple';

const buttonRipple = new MDCRipple(document.querySelector('.mdc-button'));
```

> See [Importing the JS component](../../docs/importing-js.md) for more information on how to import JavaScript.

## Variants

### Contained Button

To style a contained button, add the `mdc-button--raised` class to the `<button>` element for a contained button with elevation, or the `mdc-button--unelevated` class for a contained button flush with the surface.

### Outlined Button

To style an outlined button, add the class `mdc-button--outlined` to the `<button>` element.

### Icons 

To add an icon, add an element with the `mdc-button__icon` class inside the button element and set the attribute `aria-hidden="true"`. The icon is set to 18px to meet legibility requirements.

We recommend you use [Material Icons](https://material.io/icons/) from Google Fonts:

```html
<button class="mdc-button">
  <i class="material-icons mdc-button__icon" aria-hidden="true">favorite</i>
  Button
</button>
```

It's also possible to use an SVG icon:

```html
<button class="mdc-button">
  <svg class="mdc-button__icon" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" viewBox="...">
  ...
  </svg>
  Button
</button>
```

### Disabled

To disable a button, add the `disabled` attribute directly to the `<button>`, or set the `disabled` attribute on the `<fieldset>` containing the button.
Disabled buttons cannot be interacted with and have no visual interaction effect.

```html
<button class="mdc-button" disabled>
  Button
</button>
```

## Style Customization

### CSS Classes

CSS Class | Description
--- | ---
`mdc-button` | Mandatory. Defaults to a text button that is flush with the surface.
`mdc-button--raised` | Optional. Styles a contained button that is elevated above the surface.
`mdc-button--unelevated` | Optional. Styles a contained button that is flush with the surface.
`mdc-button--outlined` | Optional. Styles an outlined button that is flush with the surface.
`mdc-button--dense` | Optional. Makes the button text and container slightly smaller.
`mdc-button__icon` | Optional. Indicates an icon element.

### Sass Mixins

To customize a button's color and properties, you can use the following mixins.

#### Basic Sass Mixins

MDC Button uses [MDC Theme](../mdc-theme)'s `primary` color by default. Use the following mixins to customize it.

Mixin | Description
--- | ---
`mdc-button-filled-accessible($container-fill-color)` | Sets the container fill color for a contained (_raised_ or _unelevated_) button, and updates the button's ink, icon, and ripple colors to meet accessibility standards

#### Advanced Sass Mixins

These mixins will override the color of the container, ink, outline or ripple. It is up to you to ensure your button meets accessibility standards.

Mixin | Description
--- | ---
`mdc-button-container-fill-color($color)` | Sets the container fill color to the given color.
`mdc-button-icon-color($color)` | Sets the icon color to the given color.
`mdc-button-ink-color($color)` | Sets the ink color to the given color, and sets the icon color to the given color unless `mdc-button-icon-color` is also used.
`mdc-button-corner-radius($corner-radius)` | Sets the corner radius to the given number (defaults to 2px).
`mdc-button-horizontal-padding($padding)` | Sets horizontal padding to the given number.
`mdc-button-outline-color($color)` | Sets the outline color to the given color.
`mdc-button-outline-width($width, $padding)` | Sets the outline width to the given number (defaults to 2px) and adjusts padding accordingly. `$padding` is only required in cases where `mdc-button-horizontal-padding` is also included with a custom value.

##### Caveat: Edge and CSS Custom Properties

In browsers that fully support CSS custom properties, the above mixins will work if you pass in a [MDC Theme](../mdc-theme) property (e.g. `primary`) as an argument. However, Edge does not fully support CSS custom properties. If you are using the `mdc-button-container-fill-color` mixin, you must pass in an actual color value for support in Edge.
