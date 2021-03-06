# Customization

This page still experimental. You're very welcome to contribute.

## Enhance User Interface

### Angular Animation
There are several types of animation techniques that we can apply in our angularjs application. But in this tutorial I will discuss about the animation at the turn of the page. To do that, we need the ngAnimate module to enable animations throughout the application.

```
{
  "name": "angular1-yii2",
  "description": "AngularJS 1.3 and Yii Framework 2.0",
  "version": "1.0.0",
  "homepage": "https://github.com/hscstudio/angular1-yii2",
  "license": "MIT",
  "private": true,
  "dependencies": {
    "angular": "~1.3.0",
    "angular-mocks": "~1.3.0",
    "bootstrap": "~3.1.1",
    "angular-route": "~1.3.0",
    "angular-resource": "~1.3.0",
    "angular-animate": "~1.3.0"
  }
}
```
https://docs.angularjs.org/tutorial/step_12<br>
https://docs.angularjs.org/guide/animations<br>
https://docs.angularjs.org/api/ngAnimate<br>

### Flash Message

### Angular Lazy Loader
https://oclazyload.readme.io/v1.0/docs/getting-started

When we add some module, we must add include script for sub module in main. By use module ocLazyLoad we can make lazy load in angular, include only when needed.

- Download ocLazyLoad.js (you can install it with bower install oclazyload or npm install oclazyload) and add the file to your project.
- Add the module oc.lazyLoad to your application:
```js
var spaApp = angular.module('spaApp', [
  'ngRoute',
  'ngAnimate',
  'spaApp.site',
  'spaApp.book',
  'oc.lazyLoad', // add this module lazyLoader
]);
```
- Load on demand:
```js
spaApp.controller("MyCtrl", function($ocLazyLoad) {
  $ocLazyLoad.load('testModule.js');
});
```
With $ocLazyLoad you can load angular modules, but if you want to load any component (controllers / services / filters / ...) without defining a new module it's entirely possible (just make sure that you define this component within an existing module).

There are multiple ways to use $ocLazyLoad to load your files, just choose the one that you prefer.

Also don't forget that if you want to get started and the docs are not enough, see the examples in the 'examples' folder!

## Customize RESTful API

### Versioning

### Customize URL

### Error Handling

## Authorization

## Handling File Upload

## Deploying Application
Before we deploy our application, we need do some things.

### Web Client
Read official guide for application production [click here](https://docs.angularjs.org/guide/production).
#### Disabling Debug Data
By default AngularJS attaches information about binding and scopes to DOM nodes, and adds CSS classes to data-bound elements, but we can disable this in production for a significant performance boost with:
```js
spaApp.config(['$compileProvider', function ($compileProvider) {
  $compileProvider.debugInfoEnabled(false);
}]);
```
#### Strict DI Mode
Using strict di mode in your production application will throw errors when a injectable function is not annotated explicitly. Strict di mode is intended to help you make sure that your code will work when minified. However, it also will force you to make sure that your injectable functions are explicitly annotated which will improve angular's performance when injecting dependencies in your injectable functions because it doesn't have to dynamically discover a function's dependencies. It is recommended to automate the explicit annotation via a tool like ng-annotate when you deploy to production (and enable strict di mode)

To enable strict di mode, you have two options:
```html
<div ng-app="spaApp" ng-strict-di>
  <!-- your app here -->
</div>
```
or
```js
angular.bootstrap(document, ['spaApp'], {
  strictDi: true
});
```

#### 
### Web Service
Same with AngularJs, in production environments, we should disable debug mode. It may have a significant and adverse performance effect, besides that the debug mode may expose sensitive information to end users.

Modify file [web/index.php](../web-service/web/index.php) in web-service, set `Yii_DEBUG` const to be `false`, and then `YII_ENV` to be `prod`.
```php
defined('YII_DEBUG') or define('YII_DEBUG', false);
defined('YII_ENV') or define('YII_ENV', 'prod');
```

---

> [Back To Index](index.md) <br>
> [01. Introduction](01-introduction.md) <br> 
> [02. Preparation](02-preparation.md) <br>
> [03. Create Web Service](03-create-web-service.md) <br>
> [04. Create Web Client](04-create-web-client.md) <br>
> [05. Customization](05-customization.md) <br>
> [06. Conclusion](06-conclusion.md) <br>
