###Never Use Only One Stylesheet
***

There is never a reason for a file to have a table of contents or even be more than 500 lines of code. Especially in css. Each view or template should use its own css file and reference common css files in a global scope. IE: If you have a style on the home page that is unique, don't make it available on every page. Have you css be compiled down to a single file in the end if you like but keep things modular and clear. All css files should be ready for re-use in future projects and in future views.

###Reference Elements in a unique Way
***

If you need to style an ```<a>``` tag in a view, don't use the generic a{} in your css file. This means that all future ```<a>``` tags will inherit this style and may reach out to other pages. If you must do this, make sure that the parent container is referenced in a unique way. IE:

.less
```
.link-list{
  a{
    backgroud-color:red;
  }
}
```

.html

```
<div class="link-list">
  <a href="foo.com"></a>
  <a href="bar.com"></a>
  <a href="zoo.com"></a>
</div>
```

###Float:left vs display:inline-block
***

There are a lot of reasons why it is preffered to use Inline-block instead of float but the main reason is that your code will be viewed by others and modified by otheres. Several Floats on a single page can make it very difficult for others to use your code.

BAD: ```<div style="float: left;"></div>```

GOOD: ```<div style="display: inline-block;"></div>```

You may also need to use "vertical-align:top;" in order to get the desired result.

Exception: If you need something to be on the right side of the screen, you may need float: right in order for it to be pressed against your outer boundaries.

###Never Use an Inline Style
***

This can also make it hard for others to read what your code is doing. There is always a way to address a css issue with a corresponding class rather than an inline style. Even if you think its only a small deal, it shoudl be avoided at all costs.

###Never use `!important`
***

If you find that you need `!important`, you are probably down the css rabbit hole. This means that you have so many styles that you are constantly not knowing which one takes precedence. Once one `!important` is resolved, other `!important` tags can also behave weirdly. This will cause you many more headaches than the time it might save you in the short term. In short: don't use `!important`.

If you're not sure why your CSS isn't being applied, remember css works on a **specificity scale**, meaning, quite simply, *somewhere else in the CSS, there is a selector that is more **specific** than the one you are attemping to write*. Simply make yours more specific, and your styles will take precendance without needing `!important`

```css

// an example style that might cause precedence issues
body .page-wrapper a {
  color: red;
}

// this isn't as specific as the other style, so it will get overwritten by color: red;
.main-content a {
  color: blue; // gets overwritten by first style
}

// to make it more specific, be more specific by adding a class or id, or by being more specific about what the anchor tag is contained within
.main-content a.custom {
  color: blue; // doesn't get overwritten by first style
}

```
