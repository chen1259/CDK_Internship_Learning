# Level 4 The index.html file

```html

4.2 We basically delete a section of html we have and put it in another html file
that is more specific in what it is used for.  This snippet is able to be reused while
giving more info on what it does exactly. For this example we use ng-include along with the file name
within single quotes but this isn't the most optimal way.

<div ng-include="'product-description.html'" ng-show="tab.isSet(1)">
</div>

```

```html

4.3 We will use a element directive.  The ng-show is repeated but it is possible if need be 
to put angular in your own custom directives.  Also, the - means whatever letter after it is 
Uppercase for a camelcase way in the app.js code.

<product-description ng-show="tab.isSet(1)"></product-description>

```

```html

4.4 We just include the product-specs directive within the div.

<div ng-show="tab.isSet(2)" product-specs>
</div>

```

```html

4.6 We refactor a controller so that is within our custom directive. We then replace
it with the element directive in html.

<product-tabs>
</product-tabs>

```

```html

4.7 Same as 4.6 but for the gallery

<product-gallery></product-gallery>

Remember there is an actual file made named product-gallery.html that will have all
the code that we refactored.

```
