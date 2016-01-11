# Example integrations for Sinklog.com
Obtain a log key from https://sinklog.com/

## Shell
```bash
$ logger -t <log key> -n sinklog.com "log message"
```

## Python
See [python-sinklog](https://github.com/sinklog/python-sinklog).


## NodeJS
### winston
```javascript
var winston = require('winston');
require('winston-syslog').Syslog;

winston.add(winston.transports.Syslog, {host: "sinklog.com", appName: "<log key>"});
```
