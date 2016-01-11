# Example integrations for Sinklog.com
Obtain a log key from https://sinklog.com/

## Shell
```bash
$ logger -t <log key> -n sinklog.com "log message"
```

For `logger` versions that don't support the `-n` option to send to remote servers, install [python-sinklog](https://github.com/sinklog/python-sinklog), which includes a convenient CLI for Sinklog.

## Python
See [python-sinklog](https://github.com/sinklog/python-sinklog).


## NodeJS
### winston
```javascript
var winston = require('winston');
require('winston-syslog').Syslog;

winston.add(winston.transports.Syslog, {host: "sinklog.com", appName: "<log key>"});
```
