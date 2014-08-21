An exmaple model definition is below
```javascript
myApp.factory('Model',
['$http', '$rootScope', '$location',
function($http, $rootScope, $location) {

  function Model (modelData) {
    if (modelData && typeof(modelData) === 'object') {
      this.build(modelData);
    } else if (modelData && typeof(modelData) === 'integer') {
      this.loadFromId(modelData);
    }
  }

  Model.prototype = {

    build: function(modelData) {
      angular.extend(this, modelData);
    },

    loadFromId: function(id) {
      var _this = this;
      $http.get('/model/' + id)
      .success(function(modelData) {
        _this.build(modelData.data);
      }).error(handleTheError);
    },

    delete: function() {
      var _this = this;
      $http.delete('/model/' + _this.id)
      .success(function() {
        return true;
      }).error(handleTheError);
    },

    create: function() {
      var _this = this;
      $http.post('/model/', _this)
      .success(function(data) {
        $location.path('/model/' + data.id);
      }).error(handleTheError);
    },

    update: function() {
      var _this = this;
      $http.put('/model/' + _this.id, _this)
      .success(function(updatedModel) {
        _this.build(updatedModel.data);
      }).error(handleTheError);
    }

  };

  return Model;
}]);
```
This exmaple gives you a pretty good idea of how you can use a factory to build a model to not only store model data, but also have functions built in to update it's record on the server side. Calling a simple `model.update()` will automatically create a post request and send it to the server it was loaded from with it's data. This is also a great place to put any logic that will alter model data, since it will be available with every instance of the model.
