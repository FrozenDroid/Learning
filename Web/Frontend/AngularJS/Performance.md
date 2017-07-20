# Performance
These are a few tricks I've found along the way to improve the performance of your application.
## Debug data
For some reason, AngularJS has `debugInfoEnabled` enabled by default. Not very sensible but alas.  
This debug info is required by tools like Protractor and Batarang, but personally I don't use these tools, so it's best to disable it since it gives a nice performance boost in return.  
You can do this by calling `$compileProvider.debugInfoEnabled(false);` in your config method:  
```js
app.config(['$compileProvider', ($compileProvider) => {
  $compileProvider.debugInfoEnabled(false);
}]);
```
