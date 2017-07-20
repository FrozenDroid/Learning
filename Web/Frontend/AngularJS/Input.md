# Input
Some tricks that help with inputs like text inputs, etc.

## Debouncing
You can use the [debounce setting](https://docs.angularjs.org/api/ng/directive/ngModelOptions#triggering-and-debouncing-model-updates) in your input's ng-model-options attribute to limit the rate that the ng-model changes.  
This is quite useful in cases where for example, you'd use ng-change to call a function to do a request that uses the user's input (i.e. a typeahead).  
  
You can use it like this:  
```html
<input type='text' ng-model='vm.value' ng-model-options='{debounce: 100}' ng-change='vm.onChange()'/>
```
