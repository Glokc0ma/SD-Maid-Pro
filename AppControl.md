# AppControl
Is your one stop shop for all action related to controlling installed applications. After scanning you will have a searchable list of your installed apps. System apps are not shown by default, this has to be enabled in the settings.
Some options may only be available (possible) if SD Maid has been granted root permissions.

The list of apps is by default sorted by their installdate, with the newest apps first. Each app entry contains the app icon on the left, the app name and their package name, as well as the total app size on the row end. The bottom of each app entry contains a set of tags with specific attributes an app may have.

* `System` indicates that this app is a system. This may entail that it is priviledged to enhanced app permissions and actions regarding the app may be limited on unrooted devices.
* `Frozen` the app is disabled. It may not launch by any means and it will not be visible in the devices app launcher.
* `Stopped` the app has been forcefully stopped. It may not launch itself by any means until it has been manually launched by you.
* `Boot` the app contains broadcast receivers that allow the applications to do work after device reboots. If the app has such broadcast receivers but none are enabled, the tag is slightly greyed out.

Some actions can be executed on multiple apps, some only on single items. To execute actions on multiple apps long press an app then tap to select additional apps.

[[[ https://cloud.githubusercontent.com/assets/1439229/14576165/48de7be2-0367-11e6-8cdb-c9743011d39b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576165/48de7be2-0367-11e6-8cdb-c9743011d39b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576166/4a13d6ba-0367-11e6-8820-5fb317144d5a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576166/4a13d6ba-0367-11e6-8820-5fb317144d5a.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576235/aed12ac6-0367-11e6-8ccd-a1b3a69a8f5a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576235/aed12ac6-0367-11e6-8ccd-a1b3a69a8f5a.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576303/268eff3e-0368-11e6-8710-09e13f663354.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576303/268eff3e-0368-11e6-8710-09e13f663354.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576236/b00b66c2-0367-11e6-87f3-840c2ad074b8.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576236/b00b66c2-0367-11e6-87f3-840c2ad074b8.png)

## Actions
Some of these actions are only accessible in the apps details which can be reached by tapping an entry in the list.

### Run app
Launches the app.

### Kill app
Tries to kill the app. Without root permission this is done with [killBackgroundProcesses](http://developer.android.com/reference/android/app/ActivityManager.html). How effective this is depends on the app itself, though generally it is not that effectives for killing system apps. If root permission are available, SD Maid will use the linux `kill` applets on all pids running under that process.

### Force stop app
Tries to force stop the app. Essentially the same action as you have in the systems app settings. For an app do this we need root permission. The app can't launch itself until you open it once manually. This state will persist even if SD Maid is uninstalled.

### Export apk
Tries to copy the apps `.apk` file from internal private storage to your public storages download directory. If the app is encrypted, then this action requires root, unencrypted apps can also be exported without root.

### Freeze app
Requires root. Disables the app. The app will not be visible and can't start itself. It has to be enabled again to work. No dataloss occurs and this state also persists if you uninstall SD Maid. Any good app enabled/disabler app can enable apps that have been disabled with SD Maid and vice versa.

### Delete app
Deletes the app and it's data. This includes the systems uninstall process as well as actions similar to SD Maids [Corpsefinder](https://github.com/d4rken/sdmaid-public/wiki/Corpsefinder). Unrooted devices have to confirm each uninstall, rooted devices can batch uninstall without extra confirmation.

### Reset app
Returns the app to it's install state. This will the apps data, but not the app itself. Similar to `Clear data` in the systems app settings, but it also includes extra app directories outside of default directories. that the system does not know about.

### Receiver manager (autostart)
This feature requires root. It allows you to manage [BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html). These are Android components that can react to specific events such as incoming calls, display state changing or plugging the device in the charger. Receivers can be enabled or disabled. Similar to disabling whole apps, these actions persist even if uninstalling SD Maid. Other root tools if well written should be able to undo SD Maids operations and vice versa.

BroadcastReceiver can listen to custom internal events (`Intent`'s) as well as predefined system events. If SD Maid can attribute the BroadcasterReceiver as being register for a specific system event, the event type will be listed below the receiver name. Note that one receiver can be responsible for multiple event types.

**Use this with caution, disabling items without knowing what you are doing will cause the app to malfunction in unforseen ways.**

The most popular type of receiver people are usually looking for are `ON_BOOT` receivers which allow an app to do actions after booting/rebooting the device. While a badly written app can slow down device boots significantly if executes useless actions directly after booting, it is important to note that there are many **legit** use-cases for such a receiver. Specifically in SD Maids own case, it is required to restore the alarm for the [Scheduler](https://github.com/d4rken/sdmaid-public/wiki/Scheduler).

[[[ https://cloud.githubusercontent.com/assets/1439229/14576238/b518f436-0367-11e6-9c18-c313471908a2.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576238/b518f436-0367-11e6-9c18-c313471908a2.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576241/b7e336cc-0367-11e6-8ee9-c05d494acb62.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576241/b7e336cc-0367-11e6-8ee9-c05d494acb62.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576243/bb52af4a-0367-11e6-94da-d27fe173065b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576243/bb52af4a-0367-11e6-94da-d27fe173065b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14576245/bc7b1d4e-0367-11e6-9f06-71c6c06e8054.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576245/bc7b1d4e-0367-11e6-9f06-71c6c06e8054.png)