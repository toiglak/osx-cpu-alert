# osx-cpu-alert
Creates a notification if load (CPU usage) is above a maximum (for Mac OS X)

My computer was churning and used up my battery, so I wanted a notification if 5-min load is above a threshold. If so, I can check activity monitor and see what's eating my battery.

In the future, I may make it battery-only (no notification if running on AC).

## Config & install
1. Put the two files somewhere permanent.
2. Change the `max_load` value in `cpu_alert.rb` to your desired level. My normal load is around 1.2 so I used 3.
3. Update the location of the script in the plist file.
4. Copy the plist to ~/Library/LaunchAgents

## My notes

```
launchctl load <path to plist in ~/Library/LaunchAgents>
launchctl unload <path to plist in ~/Library/LaunchAgents>
```

You can use following to debug the task (add to plist):

```xml
<key>StandardErrorPath</key>
<string>/tmp/local.job.err</string>
<key>StandardOutPath</key>
<string>/tmp/local.job.out</string> 
```

Make sure to put the `cpu_alert.rb` in location that interpreter can access (Documents is not accessilbe by default). `/Users/<user>` should be accessible though.