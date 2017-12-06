# AngularJS
## TypeScript
I really like combining AngularJS with TypeScript since it helps with (duh) type safety, and just makes for a way more enjoyable development experience.
### Promises (async, await)
With TypeScript, you can use `await` and `async` like you can in C#, for example. Internally, TypeScript expects to work with native ES2015 Promises when you use `async`.
However, AngularJS has its own Promise implementation named [$q](https://docs.angularjs.org/api/ng/service/$q), and you might run into issues if you use native Promises. I've used native promises with AngularJS and it does work, however you do have to call `$scope.$apply();` when changing bound data.  
There's a much neater way of doing it though. You can change `window.Promise` and set that to use `$q`, like so:  
```js
app.run(['$window', '$q', ($window, $q) => {
  $window.Promise = $q;
}]);
```
Now, when you use `async` and `await`, it will use `$q` instead. This also means that you no longer have to apply the scope yourself, this will work as normal.
There's one thing we have to fix though. If you look at your compiled code, you'll see a helper in every file that uses async functions.  
Instead, set `compilerOptions.noEmitHelpers` and `compilerOptions.importHelpers` to `true` in your `tsconfig.json`.  
Now they should imported only once.
## Performance
These are a few tricks I've found along the way to improve the performance of your application.
### Debug data
For some reason, AngularJS has `debugInfoEnabled` enabled by default. Not very sensible but alas.  
This debug info is required by tools like [Protractor](http://www.protractortest.org/#/) and [Batarang](https://chrome.google.com/webstore/detail/angularjs-batarang/ighdmehidhipcmcojjgiloacoafjmpfk), but personally I don't use these tools, so it's best to disable it since it gives a nice performance boost in return.  
You can do this by calling `$compileProvider.debugInfoEnabled(false);` in your config method:  
```js
app.config(['$compileProvider', ($compileProvider) => {
  $compileProvider.debugInfoEnabled(false);
}]);
```
## Input
Some tricks that help with inputs like text inputs, etc.
### Debouncing
You can use the [debounce setting](https://docs.angularjs.org/api/ng/directive/ngModelOptions#triggering-and-debouncing-model-updates) in your input's ng-model-options attribute to limit the rate that the ng-model changes.  
This is quite useful in cases where for example, you'd use ng-change to call a function to do a request that uses the user's input (i.e. a typeahead).  
  
You can use it like this:  
```html
<input type='text' ng-model='vm.value' ng-model-options='{debounce: 100}' ng-change='vm.onChange()'/>
```
