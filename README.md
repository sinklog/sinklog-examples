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

### bunyan
```javascript
var bunyan = require('bunyan');
var bsyslog = require('bunyan-syslog');

var log = bunyan.createLogger({
    name: 'foo',
    streams: [ {
        level: 'debug',
        type: 'raw',
        stream: bsyslog.createBunyanStream({
            name: "<log key>",
            type: 'sys',
            facility: bsyslog.local0,
            host: 'sinklog.com',
            port: 514
        })
    }]
});

log.debug({foo: 'bar'}, 'hello %s', 'world');
```

## Java/Android
Use [logback-syslog4j](https://github.com/papertrail/logback-syslog4j)
```xml
<syslogConfig class="org.productivity.java.syslog4j.impl.net.udp.UDPNetSyslogConfig">
      <!-- remote system to log to -->
      <host>sinklog.com</host>
      <!-- remote port to log to -->
      <port>514</port>
      <!-- program name to log as -->
      <ident>
        <your log key>
      </ident>
</syslogConfig>
```

# Viewing logs

## Shell
```bash
$ curl -ns https://sinklog.com/s/<log name>
```

## Browser
You can just visit your log url directly and it will stream in your browser.  Or you can use a WebSocket:

```javascript
var ws = new WebSocket("wss://sinklog.com/s/<log name>");
ws.onmessage = function(e) {
  console.log(e.data); // log line
}
```


