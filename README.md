Project Workflow
---------------------
When addressing bugs (or writing features on new projects where we track those stories via issues), the process from start to finish is as follows:

1.  Choose which issue/feature you want to write
2.  **Self-assign** that github issue to yourself
3.  Pull the latest code from Master
4.  Create a branch with a name that contains your initials, and some purpose of the branch (for example: `SS-bug-fixes` or `JO-bug-fixes`)
5.  Perform a `git commit` for every feature/issue you fix on your branch. For example `git commit -am "Fixes issue #541"`.
6.  Once you are done working on your branch and are ready to merge it into master, create a `pull request` on github.com. 
7.  **Tag the issues that you addressed** in your pull request with `Waiting for Merge`
8.  Get another member of the team to review your pull request, and if it passes inspection, they will merge it into master.
9.  Upon merging it, assuming you wrote proper descriptions / commit messages, **all of the issues you addressed should automatically close** on github.com.
10.  The automatic continuous integration will now deploy the site automatically to the staging environment. After a few moments when the automatic deployment is complete, the Q/A team can now check the staging site to verify all of the fixes are fixed.
11.  If, after Q/A, they are determined to be **not** fixed or if there are residual issues, the Q/A team will re-open the issues that were automatically closed, or they'll create new issues.

Language Style Guides
---------------------

Style guides for code @ OrangeSprocket

[HTML Style Guide](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Language%20Style%20Guides/HTML-Formatting-Guide.md)

[JavaScript Style Guide](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Language%20Style%20Guides/JavaScript-Style-Guide.md)

[LESS Style Guide](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Language%20Style%20Guides/Less-Style-Guide.md)


Angular Guides
--------------

A best-practices and formatting guide for angular apps @ OrangeSprocket

[Testing Angular](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Testing%20Angular.md)

[Writing Controllers](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20Controllers.md)

[Writing Directives](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20Directives.md)

[Writing .run()](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20.run().md)

[Writing Factory Models](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20Factory%20Models.md)

[Writing Routes](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20Routes.md)

[Writing Services](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Angular%20Guides/Writing%20Services.md)


Git Guides
----------
[Tags for new projects](https://github.com/OrangeSprocket/OrangeSprocket-Code-Best-Practices-And-Style-Guides/blob/master/Git%20Guides/Tags%20for%20New%20Projects.md)
