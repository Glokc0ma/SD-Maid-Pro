# Scheduler
## Basic use
The scheduler allows you to automate running the different cleaning tools. The execution time may differ by +/- 10 minutes on some devices to save battery. The system may bundle several alarms and wakeup calls and not trigger each one immediatly.

### Tasks
Each option creates and adds a specific task that will be submitted to SD Maid when the scheduler timer expires.

#### CorpseFinder
Adds a scan task and if enabled a delete task that. Acts like pressing scan and then delete in user interface.

#### AppCleaner
Adds a scan task and if enabled a delete task that. Acts like pressing scan and then delete in user interface.

#### Duplicates
Adds a scan task and if enabled a delete task that. Acts like pressing scan and then delete in user interface. The selection method you set as default will be used.

#### Databases
Adds a scan task and if enabled an optimize (vacuum) task. Acts like pressing scan and then delete in user interface.

#### Reboot
Reboots your device after all previous tasks have completed.

* Hot reboot: Reboots only the user interface, but doesn't powercycle the whole device.
* Full reboot: Powercycles the device, like pressing the power button, selecting shutdown, then turning the device on again.

[[[ https://cloud.githubusercontent.com/assets/1439229/18609543/edd8ad9a-7d04-11e6-950c-1b1c83e18804.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609543/edd8ad9a-7d04-11e6-950c-1b1c83e18804.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18609544/f23ce748-7d04-11e6-810c-ec03e6b5f8a0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609544/f23ce748-7d04-11e6-810c-ec03e6b5f8a0.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18609545/f5862bbc-7d04-11e6-8003-912fed1b424e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609545/f5862bbc-7d04-11e6-8003-912fed1b424e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18609546/f7a16f24-7d04-11e6-965d-93a8ef48d4ad.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609546/f7a16f24-7d04-11e6-965d-93a8ef48d4ad.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18609547/f9b8b204-7d04-11e6-8953-e93b3cf3d857.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609547/f9b8b204-7d04-11e6-8953-e93b3cf3d857.png)

## Options
* Skip on low battery: Allows you to configure a minimum battery %. If your battery is below this level, SD Maid will skip execution until the next interval.
* Only on charger: Unless the phone is connected to a charger, the scheduler will skip execution.
 
[[[ https://cloud.githubusercontent.com/assets/1439229/18609584/a11ec538-7d05-11e6-9d15-13958b9fc1e1.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18609584/a11ec538-7d05-11e6-9d15-13958b9fc1e1.png)

## Issues
### Error: Scheduler loosing its settings
If SD Maid has been moved to a secondary storage (external sdcard), the scheduler will loose its countdown on reboot. After rebooting the alarm has to be restored, but apps that are not on internal storage, are not told about reboots. Also see http://developer.android.com/guide/topics/data/install-location.html.