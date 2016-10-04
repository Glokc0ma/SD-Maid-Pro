# AppCleaner
The AppCleaner is responsible for **expendable** files that can be attribuetd to a specific installed application. Files that are expedendable should fullfil the following criteria:
* App automatically recreates them if necessary
* Deleting them does not cause errors within an app
* No user created information is lost (e.g. a picture taken with the camera is "user created").

This generally includes all official cache locations (i.e. `/data/data/<pkg>/cache/` and `/<sdcard>/Android/data/<pkg>/cache/`) as well as uncommon cache locations (due to non-standard directory naming or location) and specific directories that have been manually added to SD Maids databases.

The AppCleaner works on a per App basis, meaning that any file it checks is related to a known installed app. This is in contrast to the SystemCleaner which is generally unaware of any app<->file relation.

[[[ https://cloud.githubusercontent.com/assets/1439229/19081899/361729ec-8a5c-11e6-97a0-3067db432b78.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081899/361729ec-8a5c-11e6-97a0-3067db432b78.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19081898/36126cc2-8a5c-11e6-8344-bd568411c4d8.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081898/36126cc2-8a5c-11e6-8344-bd568411c4d8.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19081900/361c5ea8-8a5c-11e6-8faa-96eb0f74ed8a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081900/361c5ea8-8a5c-11e6-8faa-96eb0f74ed8a.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19081896/360df32c-8a5c-11e6-865a-43a815644185.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081896/360df32c-8a5c-11e6-865a-43a815644185.png)

## Filter

The filter configuration which can be accessed from the toolbar allows you to further configure which type of "expendable" files SD Maid looks for.

### Default
This are general filters for categories of expendable files.

* "Default caches" targets the files in default `<pkg>/cache/` folders on public and private storages.
* "Hidden caches" targets cache like files that are in non-default cache directories, e.g. `videoCache`, `.cache`.
* "WebView caches" targets files downloaded by app internal browsers, e.g. if you an app shows you a webpage inside itself.

[[[ https://cloud.githubusercontent.com/assets/1439229/19081902/3629b0b2-8a5c-11e6-9eab-483b94a46f4b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081902/3629b0b2-8a5c-11e6-9eab-483b94a46f4b.png)

### Other
These filteres have specific targets such as certain filetypes or just one specific app.

* "Bug reporting" targets files created by bug/crash reporting tools in apps. Turning this on might make it more difficult for developers to improve their app if it crashes on your device. It can be quite useful though if you don't have internet and an app still creates files that it will never be able to send.
* "Analytics" similar to "Bug reporting" just targeting analytics related files such as statistics about what you do in an app.
* "Advertisement" files created or belonging to advertisement functionality, e.g. caches or collected infos.
* "WhatsApp sent files" targets files that WhatsApp creates when you send someone a picture of video through WhatsApp.
* "WhatsApp received files" files received through WhatsApp.

[[[ https://cloud.githubusercontent.com/assets/1439229/19081901/36216e98-8a5c-11e6-89a5-b28ad52d9ae3.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081901/36216e98-8a5c-11e6-89a5-b28ad52d9ae3.png)

## Settings

* Include System-Apps: Whether system apps should be included in the results.
* Sort mode: How the results should be sorted.
* Minimum cache age: SD Maid can filter out files that are below a minimum cache age (in days). Note that SD Maid can not enforce this for all files on unrooted devices. See FAQ on why some exclusions don't work.
* Skip running apps: Skip currently running apps. If running apps are not skipped they are killed before deleting their cache.
* Show inaccessible items: Some items, especially on 6.0+ without root may be known to SD Maid, but can't be accessed (i.e. deleted).
* `freeStorageAndNotify` is a trick that can be used on some ROMs (< Android 6.0) to clear private caches without root. It basically triggers the `System>Storage>Clear Cache` action. This can be turned off because using it also clears the default public caches. If you have cache files in public caches that you don't want deleted, e.g. have exclusions for, you have to disable this function such that SD Maids exclusions can take effect (because using this function outsources some work to the system which doesn't know about SD Maids exclusions).

[[[ https://cloud.githubusercontent.com/assets/1439229/19081897/360e14b0-8a5c-11e6-81a5-0bf10d6acd01.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19081897/360e14b0-8a5c-11e6-81a5-0bf10d6acd01.png)

## When to use it?
### Low space
Unless you are really low on free space it's generally not beneficial empty all your app caches every day. It's not harmful to your device or apps though. Low free space can negatively impact device performance, but this only happens below 10% or less (varies with storage) free space. Above it you would gain better performance by keeping a moderate file cache.

#### Example
Imagine an email app, its great to have fast access to some mails, but the cache also contains things like pictures from 3 day old emails. Now be honest how often do you really go back to view a few days old content? In most cases I'd rather have more free space and let the app just re-cache the files when they are needed. Additionally some of the cache files might already be stale now and would have to be reloaded anyways or not at all.

### Misbehaving apps
Some apps create ridiculous amounts of files in their cache folders, some during normal operations, some because of bugs. Large amounts of small files can negatively impact app performance as traversing all these files costs time. There are cases where apps use buggy analytics software that causes them to never transmit and or delete their analytics files, leading to over ~50.000 files to accumulate and slowing down the app (through the slowed down analytics software).
It's also possible that apps screwed app their own cache management and start to display wrong files or fail to load, clearing their cache might help and is often less effort than reinstalling the app and setting it up again.

## FAQ
### Why delete cache?
First lets get something straight: **Caches are not a bad thing.** Loading files from cache instead of downloading or recalculating them again can make loading faster and save device resources (battery/cpu/bandwidth). 

In a perfect app world, all apps manage their cache perfectly and a tool such as this would be unnecessary. But the world isn't perfect and apps missmanage their cache by e.g. not limiting it's size. Often the user is given no control over it except for wiping the whole cache. The AppCleaner aims to provide the user with detailed information and more fine grained control over each apps cache.

### Why not just use the systems built-in functions?
There are locations with cache-like files that Androids built-in function does not cover, but AppCleaner does. 
The systems cache clearing routines only cover the default caches (e.g. `/data/data/<pkg>/cache` and `<sdcard>/Android/data/<pkg>/cache`).
Apps are not forced to use these directories and may also create directories and files on the root of the sdcard and save their cache in those directories or use weird constelations such as `.cache` or `/files/cache`. This may be unintentional due to mistakes or not knowing any better, but can also be deliberate. The AppCleaner helps you manage this.

### What about clearing cache via recovery?
The AppCleaner deletes individual application caches. Clearing cache via recovery wipes the `/cache` partition which is unrelated to app caches and contains system. 
On older Android versions (around 2.3?) the cache partition was heavily used to store temporary files when downloading an app through the Android Market. Today it's not that much in use on a daily base. AFAIK some built in backup code uses it, as well as recovery and OTA updates, though there is much variance between ROMs. In essence is not used by normal apps due to special permissions being required to access it.

### Differences between rooted and unrooted devices
The AppCleaner differs slightly between rooted and unrooted device. The cleanable amount is roughly the same, but unrooted devices can't clean some files individually, meaning that to remove certain files, you have to press the "Delete all" button. This is necessary because without root we have to abuse a hidden system function called `freeStorageAndNotify` which tricks the system into running it's own cache routine which deletes the official private app caches we can't access on unrooted devices.

This is means that you can still click an entry and it will clean just that app, but there might be additional files belonging to this app that can only be removed if you use the 'clean all' routine. Such entries are labeled with an extra and icon and will also display "20+? Elements" (this entry has 20 files/folders plus an unknown amount of extra items). It's unfortunately the only way to achieve this without the luxury of root as we can't access the files directly, but instead have to ask the system for this information and this is all the information/options we get. 

### Cache deletion on unrooted devices running Android 6.0+
The aforementioned `freeStorageAndNotify` is no longer available since Android 6.0. This means that SD Maid is no longer able to use this trick to clear private app cache on unrooted devices. SD Maid will still process caches on public storage. A lot of other "cache cleaner" app are not aware of this change in Android 6.0 and act like they still work, but on further investigation nothing is deleted. This also breaks many other apps that solely relied on this trick to for file deletion (even on public storage that is accessible).

### Some AppCleaner exclusions don't work without root
If you are using the AppCleaner on an unrooted device, you may have noticed that despite creating an exclusion for a specific app, it is still part of the scan results. This happens because we have to use the `freeStorageAndNotify` trick to delete the private cache files. Using this trick means that not SD Maid, but the system itself does the deletion and the system does not know about SD Maids exclusions. Since SD Maid v4.2.0+ `freeStorageAndNotify` can be turned off in the settings.