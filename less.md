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

###Never use !important
***

If you find that you need !important, you are probably down the css rabit hole. This means that you have so many styles that you are constantly not knowing which one takes precedence. Once one !important is resolved, other !important tags can also behave weirdly. This will cause you many more headaches than the time it might save you in the short term.
