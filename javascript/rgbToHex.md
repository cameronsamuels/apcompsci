## rgbToHex.js - Method

```javascript
// rgbToHex.js
function rgbToHex(rgb) {
  var hex = [];
  rgb.forEach(function(i) {
    hex.push((i.length == 1 ? "0": "") + i.toString(16));
  });
  return hex.join("");
}
```

**Purpose**
<br>This method is used to convert a RGB-formatted color represented in a string into hex

**Method parameters**
<br>The RGB-formatted color &mdash; `rgb` as string

**Return value**
```javascript
rgbToHex([255, 255, 255]) → "ffffff"
rgbToHex([250, 87, 57]) → "fa5739"
rgbToHex([255, 0, 85]) → "ff0055"
```
