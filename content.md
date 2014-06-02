# Velocity.js

[@Takazudo](https://twitter.com/Takazudo)

----

## Resources

* [Velocity.js](http://julian.com/research/velocity/)
* [CSS vs. JS Animation: Which is Faster?](http://davidwalsh.name/css-js-animation)
* [Improving UI Animation Workflow with Velocity.js | CSS-Tricks](http://css-tricks.com/improving-ui-animation-workflow-velocity-js/)


----

## What this is

* Another implementation of `$.fn.animate`
* Compatible with `$.fn.animate`
* has some extra features

----

## Why jQuery's $.fn.animte so slow

* triggers layout thrashing many times<br>➔ stuttering at start
* invokes GC many times<br>➔ stuttering during animatino
* no RequestAnimationFrame<br>➔ low FPS

----

## CSS Transitions

* No DOM related stuttering<br>(memory, layout thrashing...)
* RequestAnimationFrame based
* GPU powered

----

## cons of CSS Transitions

* effective with only some properties.<br>(`transform`, `opacity`, `filter`)
* IE 9 or less can't use it
* cannnot control via JS

----

## pros of JS animation

* can control more
* can decide when to apply hardware acceleration
* old IE friendly

----

## What Velocity.js does

* organize all animations by one master<br> clock using RequestAnimationFrame
* sync querying, updating
* cache properties' value
* cache unit conversion ratios
* ignore imperceptible value changes

----

## Examples

```
$element
  /* Slide the element down into view. */
  .velocity({ opacity: 1, top: "50%" })
  /* After a delay of 1000ms, slide the element out of view. */
  .velocity({ opacity: 0, top: "-50%" }, { delay: 1000 });
```

Velocity uses $.queue().  
compatible with $.animate.

---

```
$element
  .delay(1000)
  /* Use Velocity to animate the element's top property over a duration of 2000ms. */
  .velocity({ top: "50%" }, 2000)
  /* Use a standard jQuery method to fade the element out once Velocity is done animating top. */
  .fadeOut(1000);
```

can be mixed.

---

```
$element
  /* Scroll the browser to the top of this element over a duration of 1000ms. */
  .velocity("scroll", 1000)
  /* Then rotate the element around its Y axis by 360 degrees. */
  .velocity({ rotateY: "360deg" }, 1000);
```

has some cool features.

----

## Conclusion

* `Velocity.js` looks nice.
* We can change some to `$.fn.animate` when it got bugged.

So I think this is worth to try.
