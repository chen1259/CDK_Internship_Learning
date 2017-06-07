# Level 4 The app.js file

```js

4.2 No app.js used so far

```

```js

4.3 We create an element descriptive in our app.js that will
be able to circumvent the use of ng-include. Basically make our own custom 
directive to make coding faster.

app.directive('productDescription', function() {
	return {
	  restrict: 'E',
	  templateUrl: 'product-description.html'
	};
});

```

```js

4.4 An attribute directive is just put differently but used the same as an
element directive. This uses an A instead of an E in the restrict.

app.directive("productSpecs", function() {
	return {
	  restrict: 'A',
	  templateUrl: 'product-specs.html'
	};
}); 

```

```js

4.6 We refactor our code so that the controller related with out directive is put within 
our directive.  We introduce the controller property where you basically put all the functions the
controller would do after it and the controllerAs property that replaces the productTabs as tab renaming 
for ng-controller.

app.directive("productTabs", function(){
	return {
	  restrict: 'E',
	  templateUrl: 'product-tabs.html',
	  controller: function() {
	      this.tab = 1;

	      this.isSet = function(checkTab) {
	        return this.tab === checkTab;
	      };

	      this.setTab = function(setTab) {
	        this.tab = setTab;
	      };
	   },
	  controllerAs: 'tab'
	};
});

```

```js

4.7 We change is so that the directive includes the productGallery controller. 
We put in the controller and controllerAs property as appropiate.

app.directive('productGallery', function() {
	return {
	  restrict: 'E',
	  templateUrl: 'product-gallery.html',
	  controller: function(){
	    this.current = 0;
	    this.setCurrent = function(imageNumber){
	      this.current = imageNumber || 0;
	    };
	  },
	  controllerAs: 'gallery'
	};
});

```
