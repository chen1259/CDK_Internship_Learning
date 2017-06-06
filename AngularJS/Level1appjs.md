# Level 1, the javascript files

```js

1.2 Creating a module which is connected through html with ng-app.  The [] is for dependencies 
with angular which we do not have right now.  "GemStore" is used in the ng-app directive 
within the 1.2 html file.

var app = angular.module("gemStore", []);

```js

1.4 Writing a controller.  The gem is just an object for now with some properties that we will 
use in html.  The controller will be used in order to put the information of the gem object 
into html.  The this.product is basically pointing to the gem object and is used to make things 
easier to read in html.

(function(){
  var gem = { name: 'Azurite', price: 2.95 };
  var app = angular.module('gemStore', []);
  
  app.controller('StoreController', function() {
    this.product = gem;
  });
  
})();

```

```js

1.6 Added to 2 boolean properties that interact with ng-hide and ng-show

(function() {
  var app = angular.module('gemStore', []);

  app.controller('StoreController', function(){
    this.product = gem;
  });

  var gem = {
    name: 'Azurite',
    price: 110.50,
    canPurchase: false,
    soldOut: true
  };
})();


```

```js

1.7  We have an array of objects now so this.products = gems would actually 
point towards an array of gems.  We need to use ng-repeat in order to loop 
through all of the objects and display them on html the angularjs way.

(function() {
  var app = angular.module('gemStore', []);

  app.controller('StoreController', function(){
    this.products = gems;
  });

  var gems = [
    { name: 'Azurite', price: 2.95 },
    { name: 'Bloodstone', price: 5.95 },
    { name: 'Zircon', price: 3.95 }
  ];
})();

```
