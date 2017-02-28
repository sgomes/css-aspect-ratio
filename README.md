# CSS Aspect Ratio

This package provides a simple implementation of fixed aspect ratio in pure CSS.
It requires support for [CSS Custom Properties](https://www.w3.org/TR/css-variables-1/).

Original implementation adapted from
https://sgom.es/posts/2017-02-17-css-custom-properties-as-your-api/


## Rationale / background

A common problem is how to avoid content shifting down as images load. This is usually solved by
adding the height and width of an image in HTML, so that the browser can allocate enough space
for the content ahead of time.

```html
<img src="kitten.jpg" height="1024" width="768" alt="A cute kitten">
```

However, if you want to adjust the dimensions for the image in CSS (say, by applying a `max-width`
to the image), you lose the ability to maintain the aspect ratio. Instead, the width and height
get applied separately, and the image gets deformed.

This package allows you to specify the width and have the height calculated automatically,
ensuring that the aspect ratio is maintained even if the image is resized.

It's also generic enough to be applied to any block, not just images.


## Usage

In HTML:

```html
<div class="aspect-ratio"
 style="width: 768px; --aspect-ratio-w: 4; --aspect-ratio-h: 3;">

  <img src="kitten.jpg" alt="A cute kitten">
</div>
```

`aspect-ratio` takes two custom properties:
- `--aspect-ratio-w` defines the width portion of the aspect ratio, e.g. 16 in 16:9.
- `--aspect-ratio-h` defines the height portion of the aspect ratio, e.g. 16 in 16:9.


## Progressive enhancement

CSS Aspect Ratio works as progressive enhancement, leaving the resizing entirely to the browser
if custom properties are not supported.