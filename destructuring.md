# Destructuring

- fails soft var [a] = []; a is undefined
- can have defaults [a = 1] = []; a is 1

## List matching
#### es5

```javascript
var _ref = [1, 2, 3];
var a = _ref[0];
var b = _ref[2];
a === 1;                # true
b === 3;                # true
```

#### es6
```javascript
var [a, ,b] = [1,2,3];
a === 1;                # true
b === 3;                # true
```

## Object matching
### example 1
#### es5 example
```javascript
var o = { p: 42, q: true };
var p = o.p;
var q = o.q;
```

#### es6 example
```javascript
let o = {p: 42, q: true};
let {p, q} = o;
console.log(p); // 42
console.log(q); // true
```
### example 2
#### es5 example
```javascript
var _a$b = { a: 1, b: 2 };
a = _a$b.a;
b = _a$b.b;
console.log(a);
console.log(b);
```
#### es6 example
```javascript
({a, b} = {a:1, b:2});
console.log(a); // 1
console.log(b); // 1
```

### example 3
#### es5 example
```javascript
function today() {
  return { d: 6, m: 2, y: 2013 };
}
var _today = today();
var day = _today.d;
var month = _today.m;
var year = _today.y;
console.log(day); // 6
console.log(month); // 2
console.log(year);  // 2013
```
#### es6 example
```javascript
function today() { return { d: 6, m: 2, y: 2013 }; }
var { d:day, m: month, y: year } = today();
console.log(day); // 6
console.log(month); // 2
console.log(year);  // 2013
```

### example 4

### es5 example
```javascript
  function getASTNode(){
    this.op = 1;
    this.lhs = {};
    this.lhs.op = 2;
    this.rhs = 3;
    return this;
  }
  var _getASTNode = getASTNode();

  var a = _getASTNode.op;
  var b = _getASTNode.lhs.op;
  var c = _getASTNode.rhs;
  console.log(a) // 1
  console.log(b) // 2
  console.log(c) // 3
```

#### es6 example
```javascript
function getASTNode(){
  this.op = 1;
  this.lhs = {};
  this.lhs.op = 2;
  this.rhs = 3;
  return this;
}
var { op: a, lhs: { op: b }, rhs: c } = getASTNode()
console.log(a) // 1
console.log(b) // 2
console.log(c) // 3
```

### example 5

#### es5 example
```javascript
function r(_ref) {
  var x = _ref.x;
  var y = _ref.y;
  var _ref$w = _ref.w;
  var w = _ref$w === undefined ? 100 : _ref$w;
  var _ref$h = _ref.h;
  var h = _ref$h === undefined ? 100 : _ref$h;
  console.log(x + y + w + h);
}
r({ x: 1, y: 2 });          //returns 203
r({x:1, y:2, w: 3, h: 4});  //returns 10
```
#### es6 example
```javascript
function r({x, y, w = 100, h = 100}) {
  console.log(x + y + w + h);
}
r({x:1, y:2});              //returns 203
r({x:1, y:2, w: 3, h: 4});  //returns 10
```
