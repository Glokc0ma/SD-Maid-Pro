# FAQ
## General
### I just want to clean my device, what to do?
* Install SD Maid, if you own [SD Maid Pro](https://play.google.com/store/apps/details?id=eu.thedarken.sdm.unlocker), then also install the Unlocker now.
* Start SD Maid, the app will open on the [Quickaccess](https://github.com/d4rken/sdmaid-public/wiki/QuickAccess) page.
* Press the green scan bar at the bottom of the screen.
* Because this is the first time you started SD Maid, you will be asked to complete the [setup](https://github.com/d4rken/sdmaid-public/wiki/Setup).
* After completing the setup, SD Maid will run the "scan" part of each tool.
* When the scan finishes you can press "execute" to delete/optimize, or press a specific tool to view more details.

### Screen overlay detected
The warning "Screen overlay detected" is a popup dialog you may see when trying to grant app permissions on an Android 6.0+ device. This is a security feature (from Android, not SD Maid) which prevents you from granting any permissions while an app is active that can draw on the screen, because malicious apps could alter the text of the permission dialog. The warning is not SD Maid specific and it's not SD Maid using the a screen overlay, but another application on your device.

Solution:
* Open settings
* Disable the overlay permissions for all listed apps
* Grant SD Maid (or any other app) it's permission
* Enable the overlay permissions again

[[[ https://cloud.githubusercontent.com/assets/1439229/19970701/1d9a9e9c-a1dd-11e6-8ed5-06fb81443707.jpg | height = 150px]]](https://cloud.githubusercontent.com/assets/1439229/19970701/1d9a9e9c-a1dd-11e6-8ed5-06fb81443707.jpg)

### External storage and Android 4.4
Arbitrary external (removable) storage access is not possible on Android 4.4, files can only be read, not modified. This means that non-system apps can neither delete, edit or create files on the external storage outside of a few specific directories, e.g. music apps can't edit `. mp3` and SD Maid can't delete files.

There are only 4 solutions:
* Upgrade the device to Android 5.0 or later.
* Downgrade the device to Android 4.3 or earlier.
* Root the device and modify the ROM to exhibit pre Android 4.4 behavior (for apps that can't use root permission).
* Root the device and allow the app to use root permission.

Either solution would work for SD Maid.

External (removable) sdcards were never officially supported by Android up until Android 4.4+. Prior to Android 4.4 device manufactors applied workarounds where they mounted the external storage to an arbitrary location and grouped it toegether with the normal workaround by mounting the removable sdcard somewhere on the device and changing the ROM to grant access to both internal and external public storage when the permission [WRITE_EXTERNAL_STORAGE](https://developer.android.com/reference/android/Manifest.permission.html#WRITE_EXTERNAL_STORAGE) is granted to apps. Android 4.4 officially introduced a way to get the path of the external sdcard and an additional permission for it named `WRITE_MEDIA_STORAGE`, but this permission is only available to system apps. For unknown reasons (possibly pressure from Google), manufactors also stopped applying their workaround in Android 4.4, leaving apps without a way to gain write access to external sdcards on Android 4.4. Android 5.0 then introduced the storage access framework, which made it possible (although complicated) to gain write access to external storage again. Users stuck on Android 4.4 are just out of luck.

### Does SD Maid only work on sdcards?
**No.** SD Maid will consider any accessible storage in your device. Depending on what can be accessed, this includes internal storage, external storage and usb storage.

### Why should I use SD Maid?

**Because it's thorough and honest.**
If you want a broom, you look for the one that cleans best, any other purchase argument is secondary. SD Maid v0.1 was released on [29.03.2011](http://forum.xda-developers.com/showpost.php?p=12482608&postcount=1). Years of learning and more experience, constant improvements and adaption to every new Android kink, make SD Maid what is is today.
SD Maid is brutally honest, there will be no euphemisms to make your feel better after "cleaning" your device. No hidden agenda to pressure you into using the app itself. A tool to use when needed.

### SD Maid v2/v3/v4
There are different versions available of SD Maid. Every few years SD Maid was completely overhauled to improve it through gained experience and to adopt to new Android environments. During these overhauls the minimum required Android version is usually raised due reduce workload, maintaining compatibility "hacks" for very old Android versions is usually not feasible when supporting the newest Android versions.

It's possibly that newer versions seem slower but downgrading because of that is bad trade, you would gain speed but pay with thoroughness and safety. Searching through more and doing additional checks just costs time. Never versions may show less items to delete, not because they are worse, but because for specific reasons it is no longer considered good to remove these files. The goal is not to delete the most files, but the right files. Every change has a good reason.

In short: **Use the latest version of SD Maid available for your device.**

* SD Maid v2 was the main app version from 2012Q2 to 2013Q1. Its target is Android 2.1 to 2.2.
* SD Maid v3 was the main app version from 2013Q1 to 2016Q1. Its target is Android 2.3 to 4.0.
* SD Maid v4 is the main app version since 2016Q1. Its target version is Android 4.1+.

### MobileIron
SD Maid doesn't require root, does not root a device and neither indicates a rooted device. Until MobileIron 9.3, SD Maid was blacklisted by packagename which could cause enterprise devices using the MobileIron system to be flagged as "out of compliance" while SD Maid was installed. If you previously had issues with this, update your MobileIron client to `9.3` or later and the issue should be fixed.

### Recover deleted files
If you accidentally deleted some files, you may be able to recover them. Restoring data depends on where the files were originally located and whether the space, that their deletion freed, has been occupied again.

Before attempting any recovery you should check if your files are actually missing. Almost everyone views their media files through gallery apps. What the gallery apps shows can be affected by SD Maid (e.g. deleted thumbnails). Use a file explorer and check if the files you are missing are actually gone. Check folders such as `DCIM` and `Pictures` on your internal and external storage. To fix the gallery app you can use SD Maids Explorer option "Force media scan", try a reboot, attach and detach from a computer or just wait a bit until the system does a media scan on it's own.

#### Removable storage
Your best chance to restore files that were deleted from a removeable sdcard (e.g. `/storage/sdcard1`) is to plug the sdcard (or the device) into a desktop computer and run software from there.

Recovery software:
* http://www.cgsecurity.org/wiki/PhotoRec
* https://www.piriform.com/recuva

#### Internal storage
Recovering files from internal storage requires a rooted device, e.g. internal sdcard (`/storage/emulated/0`) or private storage (`/data/data`). Root is required because recovery apps need to directly access the underlying storage device.

Recovery apps:
* https://play.google.com/store/apps/details?id=fahrbot.apps.undelete
* https://play.google.com/store/apps/details?id=com.defianttech.diskdigger

### Hanging "In queue"
The first time you run any action in a new session, SD Maid will have to make some preparations (check file consistency, check permissions etc). You will see the progress state "In queue" because your task is queued behind the preparations/setup task. In almost all cases where SD Maid seems to hang here it's related to the root check.

At some point SD Maid checks if your device is rooted. This is done by basically just asking for root access and waiting for an answer. Usually there should just be an error or a "no" if the device is not rooted or the root request was declined. If there is no answer at all though then SD Maid waits until a timer runs out, this is what happens when it "hangs". To test if this is the issue you are seeing, long press the settings entry to enter the debug menu, enable the option `Disable root check`, kill and restart SD Maid. If it now works as expected then there is something weird with your system that you might want to look into.

Known causes & solutions:
* Incomplete root attempt. Reroot your device.
* Incomplete unroot attempt. Reroot your device, then unroot it correctly.
* You just updated SD Maid and your super user app did not handle this correctly. Try removing SD Maid from the list apps in the super user app. Reboot your device and let SD Maid request root again. If that doesn't help uninstall SD Maid, remove it from the super user app, reboot your device and reinstall SD Maid. If that doesn't help either, clear the super user apps data and reboot.
* Sometimes the ROMs are delivered with incomplete root from the manufactor. Either root it or disable the root check in SD Maid.

## SD Maid Pro
### Free vs Pro Version
The "Pro" version of SD Maid also called the "Unlocker" is a plugin, it's not a standalone application.
You should install it toegether with the free version of SD Maid and then start the free version. It will detect the plugin and enable all extra features.

Current upgrades:
* User defined SystemCleaner filter
* Deletion function in the AppCleaner tool
* Deletion function in the Duplicates tool
* Scheduled operations via timer
* Scheduled reboots (power cycle or software restart)
* A widget to execute the main tools.
* File/app previews in all tools
* A searchable history of SD Maids actions
* Launcher shortcutus to specific tools
* Additional search options
* Android 7.1 app icon shortcuts
* (Forced) app moving to external storage on supported devices.
* Sleeping well, knowing the developer is motivated to keep developing :tada: 

### Why are there two SD Maid apps?
SD Maid consists of two apps, the free app and a paid app. The paid app is a plugin that enables extra features in the free app. The paid app can't be used alone, while the free app (sans pro features) can be used on its own. This is mainly for historical reasons as IAPs (In-App-Purchases) did not exist 5 years ago when SD Maid launched. While this will probably change at some point, it currently also has the advantage that there is no dependency on Google-Services to enable in-app-purchases.

### Factory-Reset / Device-Change
This is not an SD Maid issue, but still a popular question. Apps purchased through Google Play are tied to your Google account, not your device. If you use the same Google account on a new or factory reset device, you will have access to all previous purchases.

### Google Play is not showing the purchase
Apps are purchased per Google account, not per device. Switching devices doesn't mean you have to buy an app again. If Google Play is not showing your purchase, you are either not logged in with the account your purchased the application with or the Google Play app has not yet syncronized with your list of purchases. You can see your purchases [here](https://wallet.google.com/manage/#transactions:filter=ALL) or [here](https://play.google.com/apps). This is a Google Play issue and has no relation to SD Maid itself.

The following action are known to fix this in some instances:
* Force closing and reopening Google Play.
* Rebooting the device.
* Using "Clear Data" on the Google Play app (`com.android.vending`).

### Google Play is asking me to buy the app again
If you uninstall an app shortly after purchasing it, Google Play automatically refunds your purchase. Currently the automatic refund window is [2 hours](https://support.google.com/googleplay/answer/2479637?hl=en). This is only happens once per app.

### SD Maid is not enabling the pro features
If the both SD Maid (`eu.thedarken.sdm`) and the SD Maid Pro plugin/unlocker (`eu.thedarken.sdm.unlocker`) are installed, SD Maid should enable all pro features. Detection of the SD Maid Pro happens on app launch and when closing/opening the UI.

Known solutions:
* Force close SD Maid or reboot the device and reopen SD Maid
* The system did not correctly install either SD Maid or the unlocker. Uninstall both apps, reboot your device, install the unlocker app first, then SD Maids free version.
* If either SD Maid or the unlocker has been modified the pro features will also not be unlocked. Ensure that you downloaded the apps from official sources (Google Play or [my server](sdmaid.darken.eu/download)) and that no app on your device modified them. There are some "security apps" that modify installed apps for questionable purporses.

### I can't find SD Maid Pro on my device
The SD Maid Pro plugin only has to be installed, but does not have to be actively launched. Due to this this the app contains an option that will hide its shortcut from your app drawer. To display the shortcut again, either uninstall and reinstall the app, or open SD Maids advanced settings which offers an option to do that.

## Root
### What is root?
So what's this root everyone is talking about? Root is the name of a special user account on your device, a super user account with elevated privileges.
Normally you or apps can't use the account. The act of "rooting" changes that. It makes it accessible and adds a "superuser app" that manages access to the root account. There are pros and cons to rooting, which we don't need to cover here. Just google it, it's a common discussion on many blogs. Whether you root your device is up to you.

### Does SD Maid only work with root?
**No.** SD Maid will adjust it's behavior to fit your device. 

SD Maid being able to use root is a bonus for people with rooted devices. It does not make SD Maid work worse on unrooted devices.

Some people are saying: If you have rooted device you should use SD Maid, but if your device is not rooted, choose a different application. That's wrong. All applications are bound by the same restrictions, how each app uses what is has available, is what makes the difference.
Choose a different app if you don't feel comfortable using SD Maid, if it is too complicated or you simply don't like it, but not because you don't have a rooted device.

Functions that don't work at all without root are usually those that modify other apps, such as freezing or disabling components or uninstalling system apps.

```
Imagine you buy an offroad vehicle, like a Jeep or a LandRover Defender.
Do you have to drive offroad? No, but if you want to, then you can.
It still works perfectly well being driven on a normal road. 
```