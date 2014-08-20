Defining a module
--------
Defining a module should be done as follows...

```javascript
OSAngularApp.module('moduleName',
['$someBuiltInDependancy', 'someService', 'someModel'
function($someBuiltInDependancy, someService, someModel) {

  // logic

}]);
```

Following this definition ensures that when we minify the codebase, it won't error out due to depenancy injection issues, because we're defining the minified-aliases as strings in the array.

"Why not put the whole starter module definition on one line, er-go `app.module('name', ['$dep', function($dep) {`?"

Because when your modules have a lot of depenancies, this happens...

`app.module('name', ['$dependancy1', '$dependancy2', '$dependancy3', '$dependancy4', '$dependancy5', function($dependancy1, $dependancy2, $dependancy3, $dependancy4, $dependancy5) {`
