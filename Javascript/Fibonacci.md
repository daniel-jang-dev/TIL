```javascript
/* Version 1 */
function fib(i) {
  return i === 0 ? 0 : i === 1 ? 1 : fib(i - 1) + fib(i - 2);
}
```

```javascript
/* Version 2 */
function fib(n) {

  var f0 = 0;
  var f1 = 1;
  var f2 = 1;

  if(n === 0) return f0;
  if(n === 1) return f1;
  if(n === 2) return f2;

  for(var i = 3; i <= n; i++) {
    f0 = f1;
    f1 = f2;
    f2 = f0 + f1;
  }
  return f2;
}
```
