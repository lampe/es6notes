## Object literals

### es6 example
```javascript
var theProtoObj = {
  ads: function ads(){}
};
var handler = {}
var obj = {
    // The same as handler:handler
    handler,
    // Methods. The same as function: toString() {}
    toString() {
     // Super calls
     return "d " + super.toString();
    },
    // Computed (dynamic) property names
    [ "prop_" + (() => 42)() ]: 42
};
```
