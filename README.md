# Library for simple bash logging

## Quick howto
Just source library in your script and you can use log function
```
source lib/bash-log
log info "Info logging message"
log 6 "Info logging message"
```
You can use severity levels defined by RFC, see https://en.wikipedia.org/wiki/Syslog#Severity_level

We added additional debug levels debug2 = 8, debug3 = 9

## Features

### Verbosity
You can set verbosity of logging, default is 6 (info)
```
__VERBOSE=8
```
so messages with lower severity level is not printed.

### Output to file
You can define output file to log into file. If empty (default), stderr is used.
```
__OUTPUT = /path/to/log/file
```
### Pipe usage
You can pipe messages to log
```
echo "Info logging message" | log info
```

You can output stdout and stderr of your command with different log level with
```
example-command  > >(log 4) 2> >(log 0)
```

### Syslog facility usage

You can define ```__FACILITY=...``` to log to syslog facility - see https://en.wikipedia.org/wiki/Syslog#Facility
