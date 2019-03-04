## hexToRGB.js - Method

```javascript
// hexToRGB.js
function hexToRGB(hex) {
  var len = hex.length / 3;
  var div = [
    hex.substring(0, len),
    hex.substring(len, len * 2),
    hex.substring(len * 2)
  ];
  
  var rgb = [];
  div.forEach(function(i) {
    if (len == 1) i += i;
    rgb.push(parseInt(i, 16));
  });
  
  return rgb.join();
}
```

**Purpose**
<br>This method is used to convert a hex color code represented in a string into RGB format

**Method parameters**
<br>The hex color &mdash; `hex` as string

**Return value**
```javascript
hexToRGB("ffffff") → "255,255,255"
hexToRGB("FA5739") → "250,87,57"
hexToRGB("f05") → "255,0,85"
```
