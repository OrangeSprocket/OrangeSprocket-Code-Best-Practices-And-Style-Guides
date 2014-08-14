###Float:left vs display:inline-block

There are a lot of reasons why it is preffered to use Inline-block instead of float but the main reason is that your code will be viewed by others and modified by otheres. Several Floats on a single page can make it very difficult for others to use your code.

BAD: ```<div style="float: left;"></div>```

GOOD: ```<div style="display: inline-block;"></div>```

You may also need to use "vertical-align:top;" in order to get the desired result.

Exception: If you need something to be on the right side of the screen, you may need float: right in order for it to be pressed against your outer boundaries.
