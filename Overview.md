# Overview page
The overview page acts as a small dashboard for your device and SD Maids current status.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575239/d20d1704-0360-11e6-87a7-3886dbe26e60.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575239/d20d1704-0360-11e6-87a7-3886dbe26e60.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575238/d1ea8720-0360-11e6-840d-4f2f0761b49f.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575238/d1ea8720-0360-11e6-840d-4f2f0761b49f.png)

## Storage
Storage refers to permanent device storage that holds files, this should not be confused with memory (aka RAM). Your device has multiple storage areas. SD Maid will list a selection of the most interesting storages. Usually this is public and private storages where apps and user data resides. Other distinct storage areas such as the storage location of your systems firmware is ommitted (for now) because it's not generally something the user has to be concerned with.

These storage areas may be on distinct hardware (storage chips) or share the same hardware. A common example would be most modern devices running Android 5.0+ where private and public storage often share the same underlying device. You often notice this when you see that both areas list the same free/total space.

The storage entries can be tapped to expand them and show additional details such as their path, mount location and options. Storage on Android is complicated, it can be intimidating, but SD Maid will deal with it for you. If you are interested in details though, read on :).

### Storage types
#### Public storage
Public storage generally refers to a type of storage that is readable and (and often writeable) by any app that desires it. This usually means that an app accessing it has permissions such as `WRITE_EXTERNAL_STORAGE`. On newer versions apps may even write to their own folder on public storage, without extra permissions. It should be noted though that this is still on public storage and other apps may read or write files other than their own if they have the aforementioned permission. Public storage storage contains user files such as downloads, pictures taken with the camera, your music and public app files.
A few examples:
* `Android` is where apps are "supposed" to store their public files. Files and directories below this directory are supposed to follow strict naming guidelines which enables the system to clean up after the apps when they are removed again. "Supposed" because this is not enforced and there are plenty of apps that just name their directories arbitrarily often resulting in them being left behind after app uninstall. SD Maids CorpseFinder can help deal with this.
* `DCIM` are your pictures taken with the default camera.
* `Downloads` default directory for browser downloads
* etc.

When talking about public storage, we can distinguish between primary and secondary public storage. The primary public storage is usually (can differ between ROMs) located under `/storage/emulated/0`. There may be other paths leading to the same location, largely for historic reasons, to keep compatibility as the evolution of Androids storage system has been a very chaotic process.
Secondary public storage is mostly availble on devices with an SD Card slot. It's location varies widly because support a secondary public storage was not fully supported by Android for a long time and just "patched in" by device manufactors (where everyone choose a different path *sigh*). Example locations are `/mnt/external_sd`,`/storage/sdcard2` or '/storage/extSdCard'.

SD Maid can access public storage without root on any device except on Android 4.4 (see: [Kitkat sdcard problem](https://www.google.com/search?q=android+kitkat+sd+card+write+permission), where reading the secondary public storage is possible but not writing (this includes deletion) to it. SD Maid will of course try, but likely fail.

While the primary public storage is commonly the internal device storage that can not be removed and the secondary storage usually is a removeable external sdcard, this can differ on some firmwares (yes the Android storage system is a complicated one...).

#### Private storage
Private storage refers to an internal storage area on each device, where the systems day-to-day files are stored, app install files (*.apk etc) and private app data. Each app has their own folder and can not view other apps folders (except for apps with root access). Doing any meaningful work on private storage is only possible with root permission.

The primary private storage is located under `/data` (while this does not always have to be the case, i have not yet found any exception).
Intresting folders under `/data` are:
* `/data/user` where private app data is stored. Specifically `/data/user/0` (which is a symbolic link to `/data/data` for compatibility reasons). If your device has multiuser support, there will also be `/data/user/10` etc.
* `/data/app` for apk files of installed apps

Secondary private storage is a relative new phenomen since Android 6.0+. You can a secondary private storage if you have an external sdcard and allow Android to "adopt" it. This will create a location under `/mnt/expand/` where app install and data files can also be placed.


[[[ https://cloud.githubusercontent.com/assets/1439229/14560837/7a23d67a-0312-11e6-82fe-cdc7d451ea9f.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14560837/7a23d67a-0312-11e6-82fe-cdc7d451ea9f.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14560836/7a23b2da-0312-11e6-8bc9-e544095c6ef1.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14560836/7a23b2da-0312-11e6-8bc9-e544095c6ef1.png)

## SD Maid status information
This entry shows SD Maids as well as the unlockers current version, a few internal stats such as the item count in its databases and the current mode (e.g. debug mode). You will also find the "Install UUID" (Universally Unique Identifier) here which you can provide in case automatic bug reports from you have to be found. Tapping the UUID will copy it to your clipboard. This is a random id that gets generated on SD Maids first launch, wiping SD Maids data will generate a new one.

[[[ https://cloud.githubusercontent.com/assets/1439229/14560840/7a26e342-0312-11e6-98de-a6ddcf37d59d.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14560840/7a26e342-0312-11e6-98de-a6ddcf37d59d.png)

## Device information
Nothing too intresting, just shows your device/model, Android version and platform architecture (e.g. what processor type).

[[[ https://cloud.githubusercontent.com/assets/1439229/14560839/7a25e942-0312-11e6-839b-92472ee3fe46.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14560839/7a25e942-0312-11e6-839b-92472ee3fe46.png)

## Root status
This will reflect whether SD Maid is currently running with or without root permission. If it is running with root permission it will display the type and version of the superuser binary and superuser app.

[[[ https://cloud.githubusercontent.com/assets/1439229/14560835/7a228090-0312-11e6-962d-cb747ca1bc81.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14560835/7a228090-0312-11e6-962d-cb747ca1bc81.png)


## Binary status
Binaries are extra files that SD Maid uses during its operations. SD Maid provides its own binaries because it has to rely on them to perform in very specific ways. Normally SD Maid can use the binaries within its own folders and it's nothing we have to be concerned with. If we bring root access in to the equation things get a little bit more complicated. Depending on device and firmware, there may be restrictions on where a binary can be executed with root permissions. To allow for the greatest device compatibility, SD Maid tries alternative setups, looking for one that works.
The current setup types (in decreasing priority) are:
* `INTERNAL` SD Maid using it's internal binary setup. This is the default case. This should also be the only case you see if you don't have a rooted device.
* `SYSTEM` SD Maid has found a preinstalled binary that was deemed compatible.
* `INJECTED_ROOTFS` SD Maid has injected its own binary at a temporary location in the ramdisk (e.g. `/tmp_sdm/`). This is temporary until the next reboot.
* `INJECTED_SYSTEMLESSROOT` SD Maid has injected its own binary into a systemless root location setup by another app such as SuperSu (e.g. /su/bin/).
* `INJECTED_SYSTEM` SD Maid has injected its own binary into the systems binary folder (e.g. `/system/xbin/`).

If a better setup type is possible, previous setups are undone.

### Binary status
SD Maid requires a set of utilities to carry out its operations to copy, delete and search for files. These utilities come in form of so called "applets" which are usually part of Android itself. To function correctly SD Maid needs to be able to rely on the behavior of these utilities. To ensure this SD Maid conducts tests on applets from various sources on each device. These info boxes show which applets are used. The color indicates how preferrable it is to use each applet. Green is best while red is worst. SD Maid considers an applet source "worse" if SD Maid has to make modifications to be able to run at all. Conditions are checked at every new SD Maid session and if better alternatives are available SD Maid will automatically adapt.

[[[ https://user-images.githubusercontent.com/1439229/30681327-41875014-9ea5-11e7-9864-7d42c3b32a97.png | height = 300px]]](https://user-images.githubusercontent.com/1439229/30681327-41875014-9ea5-11e7-9864-7d42c3b32a97.png)
