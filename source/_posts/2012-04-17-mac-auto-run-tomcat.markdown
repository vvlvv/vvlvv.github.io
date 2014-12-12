---
layout: post
title: "mac auto run tomcat"
date: 2012-04-17 17:22
comments: true
categories: mac
---
* launchd_wrapper.sh

```
#!/bin/bash

# NOTE: this is an OSX launchd wrapper shell script for Tomcat (to be placed in $CATALINA_HOME/bin)

CATALINA_HOME=/Users/username/tomcat

function shutdown() {
    date
    echo "Shutting down Tomcat"
    $CATALINA_HOME/bin/catalina.sh stop
}

date
echo "Starting Tomcat"
export CATALINA_PID=/tmp/$$

# Uncomment to increase Tomcat's maximum heap allocation
# export JAVA_OPTS=-Xmx512M $JAVA_OPTS

. $CATALINA_HOME/bin/catalina.sh start

# Allow any signal which would kill a process to stop Tomcat
trap shutdown HUP INT QUIT ABRT KILL ALRM TERM TSTP

echo "Waiting for `cat $CATALINA_PID`"
wait `cat $CATALINA_PID`
```


* org.apache.tomcat.plist

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0"><!-- NOTE: place this file in /Library/LaunchDaemons -->
    <dict>
        <key>Label</key>
        <string>org.apache.tomcat</string>
        <key>OnDemand</key>
        <false/>
        <key>RunAtLoad</key>
        <true/>
        <key>EnvironmentVariables</key>
        <dict>
            <key>CATALINA_HOME</key>
            <string>/Users/username/tomcat</string>
            <key>JAVA_HOME</key>
            <string>/Library/Java/Home</string>
        </dict>
        <key>ProgramArguments</key>
        <array>
            <string>/Users/username/tomcat/bin/launchd_wrapper.sh</string>
        </array>
        <key>ServiceDescription</key>
        <string>Tomcat</string>
        <key>StandardErrorPath</key>
        <string>/Users/username/tomcat/logs/launchd.stderr</string>
        <key>StandardOutPath</key>
        <string>/Users/username/tomcat/logs/launchd.stdout</string>
        <key>UserName</key>
        <string>root</string><!-- MUST be root in order to run tomcat on port 80 -->
    </dict>
</plist>
```

* tomcat

```
#!/bin/bash

# convenience script for easily starting/stopping tomcat on OSX
# (to be placed in /usr/local/bin. remember to run chmod +x on it)
if [ 'start' = "$1" ]; then 
    echo Starting tomcat service...
    COMMAND=load
elif [ 'stop' = "$1" ]; then 
    echo Stopping tomcat service...
    COMMAND=unload
fi

if [ 'restart' = "$1" ]; then
    echo Restarting tomcat service...
    sudo launchctl unload -w /Library/LaunchDaemons/org.apache.tomcat.plist
    sudo launchctl load -w /Library/LaunchDaemons/org.apache.tomcat.plist
elif [ -n "$COMMAND" ]; then 
    sudo launchctl $COMMAND -w /Library/LaunchDaemons/org.apache.tomcat.plist
fi
```

> 本该淡淡然~~~