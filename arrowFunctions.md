## Arrow functions
- Arrow functions are always anonymous
- lexically binds the this value (does not bind its own this, arguments, super, or new.target)
- You Can’t Override An Arrow Function’s “this”


### example1
#### es5 syntax

```javascript
var evens = [1,2,3,4];
var odds = evens.map(function (v) {
  return v + 1;
});
console.log(odds);
```

#### es6 syntax

```javascript
let evens = [1,2,3,4];
let odds = evens.map(v => v + 1);
console.log(odds);
```

### pseudo code

```javascript
let odds = evens.map(PARAMS (FUNCTION=>) PARAMS + 1 )
```

### example2
#### es5 syntax

```javascript
var fives = [];
var nums = [1,2,3,4,5,6,7,8,9,10,15,20];
nums.forEach(function (v) {
  if (v % 5 === 0) fives.push(v);
});
console.log(fives);
```

#### es6 syntax

```javascript
let fives = [];
let nums = [1,2,3,4,5,6,7,8,9,10,15,20];
nums.forEach(v => {
  if (v % 5 === 0)
    fives.push(v);
});
console.log(fives);
```

### example3
#### es5 syntax

```javascript
var bob = {
  _name: "micha",
  _friends: ['maxi', 'dimi'],
  printFriends: function printFriends() {
    // var _this = this;
    this._friends.forEach(function (f) {
      console.log(this);                          # returns the window object
      console.log(this._name + " knows " + f);    # retruns undefined knows maxi
      (function () {
        console.log(this, 'inner function');      # returns the window object
        console.log(this._name + " knows " + f);  # returns undefined knows dimi
      })();
    });
  }
};
bob.printFriends();
};
```

#### es6 syntax
```javascript
var bob = {
  _name: "micha",
  _friends: ['maxi', 'dimi'],
  printFriends() {
    this._friends.forEach(f => {
      console.log(this);                          # returns the bob object
      console.log(this._name + " knows " + f);    # returns micha know maxi
      (() => {
        console.log(this, 'inner function');      # returns the bob object
        console.log(this._name + " knows " + f);  # returns micha know maxi
      })()
    });
  }
};
bob.printFriends();
```