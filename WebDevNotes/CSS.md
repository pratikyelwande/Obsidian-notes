### Boilerplate of CSS-
```
*{margin: 0;

padding: 0;

box-sizing: border-box

;}

html, body{

    width:100% ;

    height: 100%;

}
```


Box=Div

We cannot give width and height to the INLINE.
## Flex
x-axis: Cross - justify
y-axis: main - align-items

1rem= 16px

### **`vh` (Viewport Height)**

- **Definition**: 1% of the viewport height (visible browser window height).
- **Usage**: Great for full-height sections or elements that need to scale with the screen height.
- **Example**: `50vh` is 50% of the viewport’s height.

---

### **`%` (Percentage)**

- **Definition**: A percentage relative to the **parent element's size**.
- **Usage**: Used for flexible layouts, where the size depends on the containing element.
- **Example**: `width: 50%` makes an element half the width of its parent container.

---

### **`em`**

- **Definition**: Relative to the **font size of the parent element**.
- **Usage**: Useful for spacing and font sizing that scales with the parent element’s font size.
- **Example**: If a parent has `font-size: 16px`, then `2em` would be `32px` for that child.

---

### **`rem` (Root Em)**

- **Definition**: Relative to the **root element’s font size** (usually `<html>`).
- **Usage**: Useful for consistent sizing across the page, regardless of nesting.
- **Example**: If the root font size is `16px`, `1rem` will always be `16px`, and `2rem` will be `32px`, no matter the nesting.

google search- locomotive scrolltrigger codepen and copy the js file
```
gsap.registerPlugin(ScrollTrigger);

// Using Locomotive Scroll from Locomotive https://github.com/locomotivemtl/locomotive-scroll

const locoScroll = new LocomotiveScroll({
  el: document.querySelector("#main"),
  smooth: true
});
// each time Locomotive Scroll updates, tell ScrollTrigger to update too (sync positioning)
locoScroll.on("scroll", ScrollTrigger.update);

// tell ScrollTrigger to use these proxy methods for the ".smooth-scroll" element since Locomotive Scroll is hijacking things
ScrollTrigger.scrollerProxy("#main", {
  scrollTop(value) {
    return arguments.length ? locoScroll.scrollTo(value, 0, 0) : locoScroll.scroll.instance.scroll.y;
  }, // we don't have to define a scrollLeft because we're only scrolling vertically.
  getBoundingClientRect() {
    return {top: 0, left: 0, width: window.innerWidth, height: window.innerHeight};
  },
  // LocomotiveScroll handles things completely differently on mobile devices - it doesn't even transform the container at all! So to get the correct behavior and avoid jitters, we should pin things with position: fixed on mobile. We sense it by checking to see if there's a transform applied to the container (the LocomotiveScroll-controlled element).
  pinType: document.querySelector(".smooth-scroll").style.transform ? "transform" : "fixed"
});


// each time the window updates, we should refresh ScrollTrigger and then update LocomotiveScroll. 
ScrollTrigger.addEventListener("refresh", () => locoScroll.update());

// after everything is set up, refresh() ScrollTrigger and update LocomotiveScroll because padding may have been added for pinning, etc.
ScrollTrigger.refresh();

  
const scroll = new LocomotiveScroll({
    el: document.querySelector('[data-scroll-container]'),
    smooth: true
});
```