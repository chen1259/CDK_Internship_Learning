# Level 5 The app.js file

```js

4.2 We split alot of the directives within app.js and put it within its own closure
inside products.js.  We then call it store-directives module and within the app.js file itself
we are able to use the products.js directives by putting it within our dependencies.

app.js
var app = angular.module('gemStore', ['store-directives']);

product.js
var app = angular.module('store-directives', []); 

```

```js

4.4  Within our controller we add a dependency injection where we depend on $http.
You can see that we put in the array where the include the service $http in single quotes
along with the functions that take in $http as an argument.  We use var store = this because 
once we use $http.get, then the this scope is not the StoreController anymore.  We also set the 
products to an empty array because the page loads faster than the data can get to the whatever.
We use $http.get on our json file and use the success function after it in order to make a promise which
allows us to use a callback function right inside the success which would mean if we successfully get the json 
converted into a js object then we can put it within our products property.

app.controller('StoreController', ['$http', function($http){
	var store = this;
	store.products = [];

	$http.get("/store-products.json").success(function(data) {
	  store.products = data;
	});

}]);

```

