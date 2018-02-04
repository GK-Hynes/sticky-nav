# Sticky Nav

A page built to practice making a sticky nav using just vanilla JavaScript. Built for Wes Bos' [JavaScript 30](https://javascript30.com/) course.

[![Screenshot of the sticky nav page](https://res.cloudinary.com/gerhynes/image/upload/v1517694082/Screenshot-2018-2-3_Sticky_Nav_soyswq.png)](https://gk-hynes.github.io/sticky-nav/)

## Notes

First select the nav.

Make a function, `fixNav`, that will run on page scroll.

What you need to do is figure out how far the nav is from the top of the page, how far you have scrolled, and make the nav fixed when those two numbers coincide.

Inside `fixNav`, if `window.scrollY` is greater than or equal to `topOfNav`, add a class of `fixed-nav` to the body (this way you can target elements other than just the nav).

In your CSS, when there is a class of `fixed-nav`, the nav will have `position: fixed` and a `box-shadow`.

At this point, the nav is working but when it becomes fixed the content jumps up. This happens because when you make the nav fixed it is no longer taking up space in the document. This causes a reflow on the page.

You need to offset the body by the same amount as the now-fixed nav.

```js
function fixNav() {
  if (window.scrollY >= topOfNav) {
    document.body.style.paddingTop = nav.offsetHeight + "px";
    document.body.classList.add("fixed-nav");
  } else {
    document.body.style.paddingTop = 0;
    document.body.classList.remove("fixed-nav");
  }
}
```

The nav has, by default, a hidden logo.

To make the logo appear, when the body has a class of `fixed-nav` give the li with a class of `logo` a `max-width` bigger than it would ever need to be.

```css
.fixed-nav li.logo {
  max-width: 500px;
}
```

You can't just use `width: auto` because you cannot animate the width of something to be from 0 to `auto`. You need to use `max-width` to get the transition to occur.

Finally, the blog content has a class of `site-wrap` set to `scale(0.98)`. When there is a class of `fixed-nav`, make the content scale up to 1.

```css
.fixed-nav .site-wrap {
  transform: scale(1);
}
```
