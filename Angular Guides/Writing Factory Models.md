
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
