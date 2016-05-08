# Scheduler
The scheduler allows you to automate running the different cleaning tools. The execution time may differ by +/- 10 minutes on some devices to save battery. The system may bundle several alarms and wakeup calls and not trigger each one immediatly.

## Issues
### Error: Scheduler loosing its settings
If SD Maid has been moved to a secondary storage (external sdcard), the scheduler will loose its countdown on reboot. After rebooting the alarm has to be restored, but apps that are not on internal storage, are not told about reboots. Also see http://developer.android.com/guide/topics/data/install-location.html.