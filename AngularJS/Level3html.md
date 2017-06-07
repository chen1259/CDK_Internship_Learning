# Level 3 The index.html file

```html

3.2 Within the code we need to repeat the reviews which we do with ng-repeat on the 
<li>'s.  Then we add in the review information in this format.

<li ng-repeat="review in product.reviews">
    <blockquote>
        <strong>{{review.stars}} Stars</strong>
            {{review.body}}
        cite class="clearfix">{{review.author}}</cite>
    </blockquote>
</li>

```

```html

3.3 We added ng-model into each of the inputs in order to connect to the review object itself. Review is just a made up
new variable and is not connected to anything just yet.

<!--  Review Form -->
<form name="reviewForm">
  <!--  Live Preview -->
  <blockquote>
    <strong> Stars</strong>
    
    <cite class="clearfix">—</cite>
  </blockquote>

  <!--  Review Form -->
  <h4>Submit a Review</h4>
  <fieldset class="form-group">
    <select class="form-control" ng-model="review.stars" ng-options="stars for stars in [5,4,3,2,1]"  title="Stars">
      <option value="">Rate the Product</option>
    </select>
  </fieldset>
  <fieldset class="form-group">
    <textarea class="form-control" ng-model="review.body" placeholder="Write a short review of the product..." title="Review"></textarea>
  </fieldset>
  <fieldset class="form-group">
    <input type="email" ng-model="review.author" class="form-control" placeholder="jimmyDean@example.org" title="Email" />
  </fieldset>
  <fieldset class="form-group">
    <input type="submit" class="btn btn-primary pull-right" value="Submit Review" />
  </fieldset>
</form>

```

```html

<!--  Live Preview -->
3.4 Displays a live preview of what you are writing within the review input forms as connected through 3.3 code.

<blockquote>
	<strong>{{review.stars}} Stars</strong>
  		{{review.body}}
	<cite class="clearfix">-{{review.author}}</cite>
</blockquote>

```

```html

3.6 Nothing has changed within the HTML so far

```

```html

3.7 We use ng-submit to call the function that pushes our info to the product.reviews array with our controller
once the form is submitted.  We setup our ng-controller and give it an alias of reviewCtrl.  We also changed the
live preview and input form's ng-model to use the reviewCtrl controller.  We can also use ng-optins for the select and 
option element in order to get the options setup fast and correctly.  

<!--  Review Form -->
<form name="reviewForm" ng-submit="reviewCtrl.addReview(product)" ng-controller="ReviewController as reviewCtrl">

  <!--  Live Preview -->
  <blockquote>
    <strong>{{reviewCtrl.review.stars}} Stars</strong>
    {{reviewCtrl.review.body}}
    <cite class="clearfix">—{{reviewCtrl.review.author}}</cite>
  </blockquote>

  <!--  Review Form -->
  <h4>Submit a Review</h4>
  <fieldset class="form-group">
    <select ng-model="reviewCtrl.review.stars" class="form-control" ng-options="stars for stars in [5,4,3,2,1]" title="Stars">
      <option value="">Rate the Product</option>
    </select>
  </fieldset>
  <fieldset class="form-group">
    <textarea ng-model="reviewCtrl.review.body" class="form-control" placeholder="Write a short review of the product..." title="Review"></textarea>
  </fieldset>
  <fieldset class="form-group">
    <input ng-model="reviewCtrl.review.author" type="email" class="form-control" placeholder="jimmyDean@example.org" title="Email" />
  </fieldset>
  <fieldset class="form-group">
    <input type="submit" class="btn btn-primary pull-right" value="Submit Review" />
  </fieldset>
</form>

```

```html

3.9 We start off validation by using the keywords novalidate in order to disable the regular html validation in
the form element and also put in the required keyword at the ends of the inputs in order to show that we absolutely
need this to be filled correctly.  Also we added in reviewForm.$valid in order to have the form pushed in only if
the reviewForm is valid.  We use the name of the form and then the .$valid thing to do this and the && in order to not
call the function if the first thing wasn't already valid.

<!--  Review Form -->
<form name="reviewForm" ng-controller="ReviewController as reviewCtrl" ng-submit="reviewForm.$valid && reviewCtrl.addReview(product)" novalidate>

  <!--  Live Preview -->
  <blockquote >
    <strong>{{reviewCtrl.review.stars}} Stars</strong>
    {{reviewCtrl.review.body}}
    <cite class="clearfix">—{{reviewCtrl.review.author}}</cite>
  </blockquote>

  <!--  Review Form -->
  <h4>Submit a Review</h4>
  <fieldset class="form-group">
    <select ng-model="reviewCtrl.review.stars" class="form-control" ng-options="stars for stars in [5,4,3,2,1]" title="Stars" required>
      <option value="">Rate the Product</option>
    </select>
  </fieldset>
  <fieldset class="form-group">
    <textarea ng-model="reviewCtrl.review.body" class="form-control" placeholder="Write a short review of the product..." title="Review"></textarea>
  </fieldset>
  <fieldset class="form-group">
    <input ng-model="reviewCtrl.review.author" type="email" class="form-control" placeholder="jimmyDean@example.org" title="Email" required />
  </fieldset>
  <fieldset class="form-group">
    <input type="submit" class="btn btn-primary pull-right" value="Submit Review" />
  </fieldset>
</form>

```

```css

3.10 Just some form styling.  Angular allows the input forms to have these classes where ng-pristine means nothing is
in there/not touched, ng-dirty means something was typed in, and ng-invalid/ng-valid is straightforward in if that invdividual
input was typed out correctly.

.ng-invalid.ng-dirty {
  border-color:red;
}

.ng-valid.ng-dirty {
  border-color:green;
}

```

```html

3.11 Added the {{review.createdOn | date}} in order to show when the review was created on with 
the date filter.

<blockquote>
	<strong>{{review.stars}} Stars</strong>
		{{review.body}}
	<cite class="clearfix">—{{review.author}} on {{review.createdOn | date}}</cite>
</blockquote>

```