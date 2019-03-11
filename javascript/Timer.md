## Timer.js - Class

```javascript
// Timer.js
class Timer {
  constructor() {
    this.start();
  }
  start() {
    this.base = new Date();
  }
  getRealTime() {
    return new Date() - this.base;
  }
  getTime() {
    var time = this.getRealTime();
    var str = Math.floor(time / 60000) + ":";
    var seconds = Math.floor(time % 60000 / 1000);
    str += (seconds < 10 ? "0" : "") + seconds + ":";
    return str + time.toString().substring(time.toString().length - 3);
  }
  
}
```

**Purpose**
<br>This class represents a stopwatch.
It contains an instance variable `base` that holds a `Date` value representing the start time.
It has a method `getRealTime()` that returns an `int` representing the milleseconds since the `base` time.
It has a method `getTime()` that returns a `String` representing the formatted time since the `base` time (MM:SS:SSS).
