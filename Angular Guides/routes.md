Overview
--------
Angular apps should always use the [UI-Router module](http://angular-ui.github.io/ui-router/) for handling routes and resolves. The UI-Router module allows for nested and inheriting states, that will solve a ton of issues (and prevent a lof of boilerplate code) that we've experienced working with the default Angular routing system (on italic and other projects).

Notes
-----

- Use URL parameters (`{parameter}`) for mandatory data, and Query parameters (`?parameter=value&other=other`) for optional ones
- Take advantage of nested states when necessary, and the scope-inheritance therein
- Route Resolve functions **are not for business logic**, therefore...
- Route Resolve functions **should never be more than one line**. If it's more than one, it's probably something you should extract out into a service/helper function that is called on one line instead. See examples below.
- Never forgot the `$urlRouterProvider.otherwise('/fallbackURL');` to handle `404`'s, etc.

Here is a sample UI router `ngRoutes.js` file.

```javascript
OSAngularApp.config(
  ['$stateProvider', '$urlRouterProvider',
  function($stateProvider, $urlRouterProvider) {

  $stateProvider

  // This route is a static page with no controller and therefore no resolves
  .state('home', {
    url: '/',
    templateUrl: '/templates/home.html'
  })
  
  // This route has a controller, but no resolves
  .state('some_state', {
    url: '/some_route',
    templateUrl: '/templates/some_route_template.html',
    controller: 'ngSomeRouteController'
  })
  
  // This route has a controller, and some plain resolves that do not depend on URL/query parameters
  .state('some_state_2', {
    url: '/some_route_2',
    templateUrl: '/templates/some_route_2_template.html',
    controller: 'ngSomeRoute2Controller',
    resolve: {
      someDataToResolve: ['SomeDataService', function(SomeDataRetrievalService) {
        return SomeDataRetrievalService.goGetThatData();
      }]
    }
  })

  // This route has query parameters (?___=___) and the resolves use that query to get data from a service
  .state('some_state_3', {
    url: '/some_route_3/?parameter',
    templateUrl: '/templates/some_route_3_template.html',
    controller: 'ngSomeRoute3Controller',
    resolve: {
      parameter: ['$stateParams', 'SomeDataRetrievalService', function($stateParams, SomeDataRetrievalService) {
        return SomeDataRetrievalService.goGetSomeSpecificDataBasedOnThisQuery($stateParams.parameter);
      }]
    }
  });
  
  // This route passes OPTIONAL query parameters directly as the resolves. If the query parameters aren't present, it resolves to false
  .state('some_state_4', {
    url: '/some_route_4?parameter',
    templateUrl: '/templates/some_route_4_template.html',
    controller: 'ngSomeRoute4Controller',
    resolve: {
      parameter: ['$stateParams', function($stateParams) {
        return ($stateParams.parameter === null) ? false : $stateParams.parameter;
      }],
    }
  })

  // This route has URL parameters ({parameter}) and the resolves use that query to get data from a service
  .state('some_state_5', {
    url: '/some_route_5/{parameter}/',
    templateUrl: '/templates/some_route_5_template.html',
    controller: 'ngSomeRoute5Controller',
    resolve: {
      parameter: ['$stateParams', 'SomeDataRetrievalService', function($stateParams, SomeDataRetrievalService) {
        return SomeDataRetrievalService.goGetSomeSpecificDataBasedOnThisQuery($stateParams.parameter);
      }]
    }
  });

  $urlRouterProvider.otherwise('/dashboard');

}]);
```
