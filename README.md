# Example integrations for Sinklog.com
Obtain a log key from https://sinklog.com/

## Python
See [python-sinklog](https://github.com/sinklog/python-sinklog).


## NodeJS
### winston
```bash
$ npm install winston 
$ npm install winston-syslog
```

Add the logger:
```javascript
var winston = require('winston');
//
// Requiring `winston-syslog` will expose 
// `winston.transports.Syslog`
//
require('winston-syslog').Syslog;

winston.add(winston.transports.Syslog, {appName: "<log key>"});
```
