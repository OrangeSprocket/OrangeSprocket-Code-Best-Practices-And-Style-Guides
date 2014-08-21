An example of a controller definition is as follows:
```javascript
myApp.controller('SomeControllerName',
['$angularDependency', '$otherAngularDependency', 'someService', 'someModel',
function($angularDependency, $otherAngularDependency, someService, someModel) {
  
  // Controller Logic
  
}]);
```
Controllers act like the interface between your models (or page data) and your templates (views). This is done by adding things to the <code>$scope</code> object, which can be injected into a controller just like any other dependancy (see the example above).

Within your template, any expression given will be evaulated on the scope, which means that if you have <code>{{users}}</code> or <code>ng-repeat="user in users"</code> in your template, then you need to have an object called <code>user</code> on the $scope. The same appies if you have a <code>ng-click="approveUser()"</code> on an element in your template; You'll need a function called <code>approveUser()</code> on your scope.

One important thing that we're trying to push for when we write controllers is that we're trying to abstract as much logic as possible from them. Smaller controllers are easier to test/debug, and it will also help us from repeating similar logic within our applications. It is encouraged to put any business logic inside of a service and import that service, of if that logic pertains to a model, then add the function to the model definition. Feel free to check out those sections for some examples.
