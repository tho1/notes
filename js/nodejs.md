
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

var http=require('http');
	var server = http.createServer()

    server.listen( 98)
    
    var io = require('socket.io')
    socket = io.listen(server)
    
    var fs =  require('fs')
    socket.on('open' , function (client) {
		client.on (
			fs.appendFile('mytxt.txt',
				'(' + data + ')',
				
				function(err) {
					if (err) throw err;
				}
			
    };
    
    
    
    var cli : function () {
		this.serverAvailable = true
		
		try {
			this.socket = new io.connect( ' ')
			
		}
		catch (err) {}
		this.socket.emit ('event', func() )
    }
    
    
    String prototype.splitcsv =
		function () {
			var regex = /C\s*'[^']+'|\S*[^,]+)(?=,$)/g;
			return this.match(regex);
		}
		
	var data1 = data.splitcsv();
	


### db sharding


### config.
npm config get prefix
Default Path is : %USERPROFILE%\AppData\Roaming\npm

npm config get cache
Default Path is : %USERPROFILE%\AppData\Roaming\npm-cache

npm config set prefix \npm
example npm config set prefix C:\\dev\\node\\npm


npm config set cache \npm-cache
example npm config set cache C:\\dev\\node\\npm-cache
