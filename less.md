###Never use only one stylesheet
***

There is never a reason for a file to have a table of contents or even be more than 500 lines of code. Especially in css. Each view or template should use its own css file and reference common css files in a global scope. CSS will be compiled down to a single file in the end, so there is no reason not to divide your CSS files up to be modular and clear. This allows CSS files to be ready for re-use in future projects and in future views.

###`float: left;` vs `display:inline-block;` for layout positioning
***

There are a myriad of reasons why it is preferable to use Inline-block instead of Float but the main reason is: your code will be viewed by others and modified by others. Float is very fragile, in that when you or somebody else attempts to add something **later on**, the entire pages layout can break when adding a single element that isn't in the "float spam". Several Floats on a single page can make it very difficult for others to use your code. Very difficult.

`display: inline-block;` quite literally accomplishes absolutely everything that `float: left;` accomplishes, **without** the entire page layout being "fragile" (breakable by a single new thing being added).

BAD: `<div style="float: left;"></div>`

GOOD: `<div style="display: inline-block;"></div>`

You may also need to use "vertical-align:top;" in order to get the desired result in some cases.

**Exception:** If you need something to be on the right side of the screen, you may need float: right in order for it to be pressed against your outer boundaries. Float is for exactly this: floating BLOCK or INLINE-BLOCK elements **around** a floated element (like an image with a paragraph wrapped around it, newspaper style). This is more or less the only time you will need float.

###Never use inline styling
***

This can also make it hard for others to read what your code is doing. There is always a way to address a css issue with a corresponding class rather than an inline style. Even if you think its only a small deal, it should be avoided at all costs.

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

Learning Links
--------------

[http://www.smashingmagazine.com/2010/11/02/the-important-css-declaration-how-and-when-to-use-it/](http://www.smashingmagazine.com/2010/11/02/the-important-css-declaration-how-and-when-to-use-it/)
[http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/](http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/)
[http://learnlayout.com/inline-block.html](http://learnlayout.com/inline-block.html)
[http://www.sitepoint.com/give-floats-the-flick-in-css-layouts/](http://www.sitepoint.com/give-floats-the-flick-in-css-layouts/)
[http://designshack.net/articles/css/farewell-floats-the-future-of-css-layout/](http://designshack.net/articles/css/farewell-floats-the-future-of-css-layout/)
[http://designshack.net/articles/css/whats-the-deal-with-display-inline-block/](http://designshack.net/articles/css/whats-the-deal-with-display-inline-block/)
[http://straightedgelinux.com/blog/howto/float.html](http://straightedgelinux.com/blog/howto/float.html)
[http://www.vanseodesign.com/css/inline-blocks/](http://www.vanseodesign.com/css/inline-blocks/)
