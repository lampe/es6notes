## Object literals

```javascript
var theProtoObj = {
  ads: function ads(){}
};
var handler = {}
var obj = {
    handler,
    // Methods
    toString() {
     // Super calls
     return "d " + super.toString();
    },
    // Computed (dynamic) property names
    [ "prop_" + (() => 42)() ]: 42
};
```
