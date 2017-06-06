# Level 2 of the Angular JS Course on Code School

```html

2.2 Instead of using the dollar sign to print out the price of something, we can use
filters with the {{ String/Integer | filter }} format.  Filter can be OrderBy:, LimitTo:,
,Date: , and other stuff that you can look up.


<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="container" ng-controller="StoreController as store">
    <div class="product row" ng-repeat="product in store.products">
      <h3>
        {{product.name}}
        <em class="pull-right">{{product.price | currency}}</em>
      </h3>
    </div>
  </body>
</html>

```

```html

2.3 Displaying the First Image

index.html
<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body ng-controller="StoreController as store">
    <!--  Products Container  -->
    <div class="list-group">
      <!--  Product Container  -->
      <div class="list-group-item" ng-repeat="product in store.products">
        <h3>
          {{product.name}}
          <em class="pull-right">{{product.price | currency}}</em>
        </h3>
        <!-- Image Gallery  -->
        <div class="gallery">
          <img ng-src="{{product.images[0]}}" />
        </div>
      </div>
    </div>
  </body>
</html>

```

```html

2.4 We use product.images[0] and ng-src because src in a regular <img /> will not work.  
product.images[0] gives us the path to the image from the images array that is a part of the\
gems property. We then repeat to make thumbnails with ng-repeat="image in product.images" and ng-src="{{image}}"

index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="list-group" ng-controller="StoreController as store">
    <!--  Product Container  -->
    <div class="list-group-item" ng-repeat="product in store.products">
      <h3>{{product.name}} <em class="pull-right">{{product.price | currency}}</em></h3>

      <!-- Image Gallery  -->
      <div class="gallery">
        <div class="img-wrap">
          <img ng-src="{{product.images[0]}}" />
        </div>
        <ul class="img-thumbnails clearfix">
          <li ng-repeat="image in product.images" class="small-image pull-left thumbnail" >
            <img ng-src="{{image}}" />
          </li>
        </ul>
      </div>
    </div>
  </body>
</html>

```


```html

2.5 This time we only show the gallery if there are images of the product in the first place.  I used w/e was put in the 
ng-show where if the array has 0 pictures then we do not show it, but there are other ways to show this as well.
index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body ng-controller="StoreController as store">
    <!--  Products Container  -->
    <div class="list-group">
      <!--  Product Container  -->
      <div class="list-group-item" ng-repeat="product in store.products">
        <h3>
          {{product.name}}
          <em class="pull-right">{{product.price | currency}}</em>
        </h3>

        <!-- Image Gallery  -->
        <div ng-show="!product.images.length == 0" class="gallery">
          <img class="img img-circle img-thumbnail center-block" ng-src="{{product.images[0]}}" />
          <ul class="clearfix">
            <li class="small-image pull-left thumbnail" ng-repeat="image in product.images"> <img ng-src="{{image}}" /> </li>
          </ul>
        </div>
      </div>
    </div>
  </body>
</html>


```


```html

2.7 From here we look at how to make different tabs so responsive with angularjs.  
We didn't do any html in this part though.

index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body ng-controller="StoreController as store">

    <!--  Products Container  -->
    <div class="list-group">
      <!--  Product Container  -->
      <div class="list-group-item" ng-repeat="product in store.products">
        <h3>
          {{product.name}}
          <em class="pull-right">{{product.price | currency}}</em>
        </h3>

        <!-- Image Gallery  -->
        <div ng-show="product.images.length">
        <!-- Fail 1 Message -->
        <div ng-show="product.images">
          <img class="img img-circle img-thumbnail center-block" ng-src="{{product.images[0]}}" />
          <ul class="clearfix">
            <li class="small-image pull-left thumbnail" ng-repeat="image in product.images"> <img ng-src="{{image}}" /> </li>
          </ul>
        </div>

      </div>
    </div>
  </body>
</html>

```


```html

2.8 We actually use the tab code now by using ng-class.  The format is ng-class="{ classname:expression }".
What we got would be give the li the active class if the panel.tab is currently set to 1, 2, 3 depending on which single 
tab we want to show.  The ng-click is something that happens once we click the <a> link.  We use the setTab function
in order to set the current tab of the product controller into the corresponding number we need.

index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="list-group" ng-controller="StoreController as store">
    <header>
      <h1 class="text-center">Flatlander Crafted Gems</h1>
      <h2 class="text-center">– an Angular store –</h2>
    </header>
    <div class="list-group-item" ng-repeat="product in store.products">
      <h3>
        {{product.name}}
        <em class="pull-right">{{product.price | currency}}</em>
      </h3>
      <section ng-show="product.images.length">
        <img ng-src="{{product.images[0]}}" />
        <ul class="list-inline thumbs">
          <li class="thumbnail" ng-repeat="image in product.images">
            <img ng-src="{{image}}" />
          </li>
        </ul>
      </section>

      <section ng-controller="TabController as panel" class="tab">
        <ul class="nav nav-pills">
          <li ng-class="{ active:panel.tab === 1 }">
            <a ng-click="panel.setTab(1)" href>Description</a></li>
          <li ng-class="{ active:panel.tab === 2 }">
            <a ng-click="panel.setTab(2)" href>Specs</a></li>
          <li ng-class="{ active:panel.tab === 3 }">
            <a ng-click="panel.setTab(3)" href>Reviews</a></li>
        </ul>
        <div ng-show="panel.isSet(1)">
          <h4>Description</h4>
          <blockquote>{{product.description}}</blockquote>
        </div>
        <div ng-show="panel.isSet(2)">
          <h4>Specs</h4>
          <blockquote>Shine: {{product.shine}}</blockquote>
        </div>
        <div ng-show="panel.isSet(3)">
          <h4>Reviews</h4>
          <blockquote></blockquote>
        </div>
      </section>
    </div>
  </body>
</html>



```

```html

2.9 We just added the ng-show stuff for the current tab, basically linked it so that it
showed the correct tab that we chose.  Also added in the product.description and product.shine.

index.html

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="list-group" ng-controller="StoreController as store">
    <!--  Store Header  -->
    <header>
      <h1 class="text-center">Flatlander Crafted Gems</h1>
      <h2 class="text-center">– an Angular store –</h2>
    </header>
    <div class="list-group-item" ng-repeat="product in store.products">
      <h3>
        {{product.name}}
        <em class="pull-right">{{product.price | currency}}</em>
      </h3>
      <!-- Image Gallery  -->
      <section ng-show="product.images.length">
        <img ng-src="{{product.images[0]}}" />
        <ul class="list-inline thumbs">
          <li class="thumbnail" ng-repeat="image in product.images">
            <img ng-src="{{image}}" />
          </li>
        </ul>
      </section>

      <!-- Product Tabs -->
      <section class="tab" ng-controller="TabController as tab">
        <ul class="nav nav-pills">
          <li ng-class="{ active: tab.isSet(1) }">
            <a href ng-click="tab.setTab(1)">Description</a></li>
          <li ng-class="{ active: tab.isSet(2) }">
            <a href ng-click="tab.setTab(2)">Specs</a></li>
          <li ng-class="{ active: tab.isSet(3) }">
            <a href ng-click="tab.setTab(3)">Reviews</a></li>
        </ul>
        <div ng-show="tab.isSet(1)">
          <h4>Description</h4>
          <blockquote>{{product.description}}</blockquote>
        </div>
        <div ng-show="tab.isSet(2)">
          <h4>Specs</h4>
          <blockquote>Shine: {{product.shine}}</blockquote>
        </div>
        <div ng-show="tab.isSet(3)">
          <h4>Reviews</h4>
        </div>
      </section>

    </div>
  </body>
</html>


```

```html

2.10 We change it so that the gallery is showed through the current gallery number.  We change the 
gallery's current number with setCurrent but I don't think we ever use that changing function in this.

<!DOCTYPE html>
<html ng-app="gemStore">
  <head>
    <link rel="stylesheet" type="text/css" href="bootstrap.min.css" />
    <script type="text/javascript" src="angular.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </head>
  <body class="list-group" ng-controller="StoreController as store">
    <header>
      <h1 class="text-center">Flatlander Crafted Gems</h1>
      <h2 class="text-center">– an Angular store –</h2>
    </header>
    <div class="list-group-item" ng-repeat="product in store.products">
      <h3>
        {{product.name}}
        <em class="pull-right">{{product.price | currency}}</em>
      </h3>

      <!-- Image Gallery  -->
      <div ng-controller="GalleryController as gallery" class='gallery' ng-show="product.images.length">
        <img ng-src="{{product.images[gallery.current]}}" />
        <ul class="list-inline thumbs">
          <li class="thumbnail" ng-repeat="image in product.images">
            <img ng-src="{{image}}" />
          </li>
        </ul>
      </div>

      <section class="tab" ng-controller="TabController as tab">
        <ul class="nav nav-pills">
          <li ng-class="{ active: tab.isSet(1) }">
            <a href ng-click="tab.setTab(1)">Description</a></li>
          <li ng-class="{ active: tab.isSet(2) }">
            <a href ng-click="tab.setTab(2)">Specs</a></li>
          <li ng-class="{ active: tab.isSet(3) }">
            <a href ng-click="tab.setTab(3)">Reviews</a></li>
        </ul>
        <div ng-show="tab.isSet(1)">
          <h4>Description</h4>
          <blockquote>{{product.description}}</blockquote>
        </div>
        <div ng-show="tab.isSet(2)">
          <h4>Specs</h4>
          <blockquote>Shine: {{product.shine}}</blockquote>
        </div>
        <div ng-show="tab.isSet(3)">
          <h4>Reviews</h4>
        </div>
      </section>
    </div>
  </body>
</html>


```
