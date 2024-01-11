
## Node internal

### insert module
https://gist.github.com/jakub-g/385ee6b41085303a53ad92c7c8afd7a6

### assert

### cluster

### debugging

### regular expression 
```
String.prototype.splitCSV = function () {
  var regex = /(\s*'[^']+'|\s*[^]+)(?=,$)/g;
  return this.match(regex);
}

var arrayVal = [];
arrayVal = data.splitCSV();
```


## Npm modules

### eslint

### esm
* https://redfin.engineering/node-modules-at-war-why-commonjs-and-es-modules-cant-get-along-9617135eeca1

### pm2
nodemon 

### socket.io
import sock


### db sharding
