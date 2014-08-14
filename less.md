###General Style Example
***

- two space indentation
- blank line between new selectors
- mixins at the top of a selector
- opening braces on selector definition line
- closing braces on own lines

```sass

body {

  &.page-wrapper {
    width: 1200px;
    margin: 0 auto;
    
    .some-nested-element {
      // some nested styles
    }
    
    #some-other-nested-element {
      .some-mixin(red);
      padding: 20px;
    }
  }
}

.some-mixin(@color) {
  color: @color;
}

```

###Never use only one stylesheet
***

There is never a reason for a file to have a table of contents or even be more than 500 lines of code. Especially in css. Each view or template should use its own css file and reference common css files in a global scope. CSS will be compiled down to a single file in the end, so there is no reason not to divide your CSS files up to be modular and clear. This allows CSS files to be ready for re-use in future projects and in future views.

###`float: left;` vs `display:inline-block;` for layout positioning
***

There are a myriad of reasons why it is preferable to use `inline-block` instead of `float` but the main reason is: your code will be viewed by others and modified by others. `float` is very fragile, in that when you or somebody else attempts to add something **later on**, the entire pages layout can break when adding a single element that isn't in the "float spam", or if a `clearfix` is forgotten. Simply: it's more error prone and harder to maintain. Several `float`'s on a single page can make it very difficult for others to use your code.

`display: inline-block;` quite literally accomplishes **absolutely everything that** `float: left;` **accomplishes**, **without** the entire page layout being "fragile" (breakable by a single new thing being added or forgotten).

BAD: `<div style="float: left;"></div>`

GOOD: `<div style="display: inline-block;"></div>`

You may also need to use `vertical-align:top;` in order to get the desired result in some cases.

**Exception:** If you need something to be on the right side of the screen, you may need `float: right;` in order for it to be pressed against your outer boundaries. `float` is for exactly this: **floating** (having other elements "wrap around") an element (like an image with a paragraph wrapped around it, newspaper style). This is more or less the only time you will need `float`.

**Note** If you need to get multiple items side my side. `float: left` is one way to achieve this... following by `float: left` on the parent container... and it's parent... etc. A preferable solution is to use display inline block, but this can result to small spaces inbetween each element. There are multiple ways to get around this, all of which seem kinda hacky, but the simplest way is (in Nick's opinion) is to add a `margin-left: -4px` to the inline-block elements to pull them back together. Check out [here](http://css-tricks.com/fighting-the-space-between-inline-block-elements/) for some more solutions.

###Never use inline styling
***

This can also make it hard for others to read what your code is doing. There is always a way to address a css issue with a corresponding class/id/specificity rather than an inline style. Even if you think its only a small deal, it should be avoided at all costs.

###Never use `!important`
***

If you find that you need `!important`, you are probably down the css rabbit hole. This means that you have so many styles that you are constantly not knowing which one takes precedence. Once one `!important` is resolved, other `!important` tags can also behave weirdly. This will cause you many more headaches than the time it might save you in the short term. In short: don't use `!important`.

If you're not sure why your CSS isn't being applied, remember css works on a **specificity scale**, meaning, quite simply, *somewhere else in the CSS, there is a selector that is more **specific** than the one you are attemping to write*. Simply make yours more specific, and your styles will take precendance without needing `!important`

```css
// an example style that might cause precedence issues
body .page-wrapper a {
  color: red;
}

// this isnt as specific as the other style, so it will get overwritten by color: red;
.main-content a {
  color: blue; // gets overwritten by first style
}

// to make it more specific, be more specific by adding a class or id, or by being more specific about what the anchor tag is contained within
.main-content a.custom {
  color: blue; // doesn't get overwritten by first style
}

```

###Keeping the footer at the bottom of the page (CSS-only)
***

This is a common, often frustrating problem which can be solved with simple css and html, *no hacks or javascript required*. Here is the html for the most basic of examples:

```html
<body>
	<div id="wrapper">
		<div id="header"></div>
		<div id="content"></div>
		<div id="footer"></div>
	</div>
</body>
```

The wrapper is a container for all the page content, which is here split into header, content and footer. The main thing here is that the wrapper must be directly inside the `<body>` element as shown. Everything else is taken care of by the css.

```css
html,
body {
	margin: 0;
	padding: 0;
	height: 100%;
}

#wrapper {
	min-height: 100%;
	position: relative;
}

#header {
	padding: 10px;
	background: #5ee;
}

#content {
	padding: 10px;
	padding-bottom: 80px; /* Height of the footer element */
}

#footer {
	width: 100%;
	height: 80px;
	position: absolute;
	bottom: 0;
	left: 0;
	background: #ee5;
}
```

If you run into issues with the footer not being pushed down far enough, inspect the `<html>`, `<body>`, wrapper, and content divs to ensure that they are all filling 100% of the page height **(not just window height)**. 

Floated child elements throughout the page can cause the top-level containing divs to not expand to full height. To remedy this, you can place a `.clearfix` div inside the bottom of the last container element under the floated content.

For reference and further explanation of what's happening, [this article](http://www.cssreset.com/how-to-keep-footer-at-bottom-of-page-with-css/) was sourced to compile this small tutorial.

###Reliable, new clearfix
***

Very useful little fix that can help solve container height css issues.

```css
.clearfix:after {
  visibility: hidden;
  display: block;
  font-size: 0;
  content: " ";
  clear: both;
  height: 0;
}
.clearfix { display: inline-table; }
/* Hides from IE-mac \*/
* html .clearfix { height: 1%; }
.clearfix { display: block; }
/* End hide from IE-mac */
```

Place a `<div class="clearfix"></div>` right before the closing tag of a container with floated children to allow the container to expand to the correct height. Here's a very basic example of how to use:

```html
<div id="content">
  <div class="floated-div">
    <div class="more-content">
    
    </div>
  </div>
  <div class="clearfix></div>
</div>
```

Learning Links
--------------

- [http://www.cssreset.com/how-to-keep-footer-at-bottom-of-page-with-css/](http://www.cssreset.com/how-to-keep-footer-at-bottom-of-page-with-css/)
- [http://www.smashingmagazine.com/2010/11/02/the-important-css-declaration-how-and-when-to-use-it/](http://www.smashingmagazine.com/2010/11/02/the-important-css-declaration-how-and-when-to-use-it/)
- [http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/](http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/)
- [http://learnlayout.com/inline-block.html](http://learnlayout.com/inline-block.html)
- [http://www.sitepoint.com/give-floats-the-flick-in-css-layouts/](http://www.sitepoint.com/give-floats-the-flick-in-css-layouts/)
- [http://designshack.net/articles/css/farewell-floats-the-future-of-css-layout/](http://designshack.net/articles/css/farewell-floats-the-future-of-css-layout/)
- [http://designshack.net/articles/css/whats-the-deal-with-display-inline-block/](http://designshack.net/articles/css/whats-the-deal-with-display-inline-block/)
- [http://straightedgelinux.com/blog/howto/float.html](http://straightedgelinux.com/blog/howto/float.html)
- [http://www.vanseodesign.com/css/inline-blocks/](http://www.vanseodesign.com/css/inline-blocks/)
