An example of a controller definition is as follows:
```javascript
myApp.controller('SomeControllerName',
['$angularDependency', '$otherAngularDependency', 'someService', 'someModel',
function($angularDependency, $otherAngularDependency, someService, someModel) {
  
  // Controller Logic
  
}]);
```
Controllers act like the interface or glue between your models (or page data) and your templates (views). This is done by adding things to the `$scope` object, which can be injected into a controller just like any other dependancy (see the example above).

Within your template, any expression given will be evaulated on the scope, which means that if you have `{{users}}` or `ng-repeat="user in users"` in your template, then you need to have an object called `user` on the `$scope`. The same applies if you have a `ng-click="approveUser()"` on an element in your template; you'll need a function called `approveUser()` on your `$scope`.

One important thing that we're trying to push for when we write controllers is that we're trying to abstract as much logic as possible away from them. Smaller controllers are easier to test/debug, and it will also prevent us from repeating similar logic within our applications. You are encouraged to put any business logic inside of a service and import that service instead. Or, if that logic pertains to a model, add the function to the model definition and import the model. Feel free to check out those sections for some examples.
