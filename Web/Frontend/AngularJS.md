# AngularJS
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
