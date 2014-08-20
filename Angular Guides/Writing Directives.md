```javascript
myApp.directive("someDirective",
['$http',
function($http) {
  return {
    restrict: 'A',
    scope: {
      someVariablePassedViaAttribute: '=someVariablePassedViaAttribute'
    },
    templateUrl: "templates/directives/someDirective.html",
    replace: true,
    link: function(scope, element, attrs) {
    
    // DIRECTIVE LOGIC
    
    }
  };
}]);
```
