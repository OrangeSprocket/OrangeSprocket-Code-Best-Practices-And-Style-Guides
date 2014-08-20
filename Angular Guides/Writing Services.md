```javascript
myApp.service('someService',
['someDependency', '$http',
function(someDependency, $http) {
  return {

    someFunction: function(someParam1, someParam2) {
      return someParam1 + someParam2;
    }

  };
}]);
```
