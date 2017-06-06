# Level 1 of the AngularJS Course

```html

1.2 Creating a Store Module

###index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body>
    <h1>{{"Hello, Angular!"}}</h1>
  </body>
</html>

###app.js

var app = angular.module("gemStore", []);

```

```html

1.4 First Controller

###index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body ng-controller='StoreController as store'>
    <div class="product row">
      <h3>
        {{store.product.name}}
        <em class="pull-right">{{store.product.price}}</em>
      </h3>
    </div>
  </body>
</html>

###app.js

(function(){
  var gem = { name: 'Azurite', price: 2.95 };
  var app = angular.module('gemStore', []);
  
  app.controller('StoreController', function() {
    this.product = gem;
  });
  
})();

```

```html

1.6 Not For Sale

###index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="container" ng-controller="StoreController as store">
    <div ng-hide="store.product.soldOut" class="product row">
      <h3>
        {{store.product.name}}
        <em class="pull-right">${{store.product.price}}</em>
      </h3>
      <button ng-show="store.product.canPurchase">Add to Cart</button>
    </div>
  </body>
</html>



```