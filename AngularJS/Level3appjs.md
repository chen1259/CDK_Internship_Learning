# Level 3 The app.js file

```js

3.2 This is code that shows that we added the reviews array inside the gems object. Cut off because
there was just more gems information.

var gems = [{
      name: 'Azurite',
      description: "Some gems have hidden qualities beyond their luster, beyond their shine... Azurite is one of those gems.",
      shine: 8,
      price: 110.50,
      rarity: 7,
      color: '#CCC',
      faces: 14,
      images: [
        "images/gem-02.gif",
        "images/gem-05.gif",
        "images/gem-09.gif"
      ],
      reviews: [{
        stars: 5,
        body: "I love this gem!",
        author: "joe@example.org",
        createdOn: 1397490980837
      }, {
        stars: 1,
        body: "This gem sucks.",
        author: "tim@example.org",
        createdOn: 1397490980837
      }]

```

```js

3.3 Same as 3.2 so far.

```

```js

3.6  Made the ReviewController along with setting its defualt review to 
an empty object so we can fill it out through the forms.  Added the addReview function
in order to add the reviews to the actual product reviews array and then reset the form
inputs to empty.

app.controller('ReviewController', function() {
	this.review = {};
	this.addReview = function(product) {
 		product.reviews.push(this.review);
    	this.review = {};
	};
});


```

```js

3.7  Nothing changed so far, same as 3.6.

```

```js

3.9 and 3.10 nothing changed so far

```

```js

3.11 The singular thing that was changed is the controller now has a createdOn
property that is set to the current date that it was made with the Date.now() function.

app.controller("ReviewController", function(){

    this.review = {};

    this.addReview = function(product){
      this.review.createdOn = Date.now();
      product.reviews.push(this.review);
      this.review = {};
    };
  });

```

