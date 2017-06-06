# Level 1 of the AngularJS Course

```html

1.2 Linking the angular files and the file that has the angular javascript code.  using ng-app to connect to the module that we want to use. The double {} is used for expressions, basically writing javascript code within html.

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

```

```html

1.4 Within the double brackets we learn how to use ng-controller to connect to a controller within app.js and also name it as something else for ease of use.  The double brackets allow us to use the alias to basically access (this) where (this) is the original StoreController.  So store.product.price would be in app.js this.product.price, which if connected to gem would give this.gem.price.

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

```

```html

1.6 Basically showing how to use ng-show and ng-hide. Takes in a boolean.

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

```html

1.7 The way we use ng-repeat is we give what we want to repeat a new name like product then use the in keyword for where the array is.  Since this.products = gems in the app.js and gems is an array of gems(objects) then we use product in store.products to have the product point to every single object one at a time in the gems array.

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="container" ng-controller="StoreController as store">
    <div ng-repeat="product in store.products" class="product row">
      <h3>
        {{product.name}}
        <em class="pull-right">${{product.price}}</em>
      </h3>
    </div>
  </body>
</html>

```
