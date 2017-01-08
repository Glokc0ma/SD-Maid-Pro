# CorpseFinder
The CorpseFinder scans multiple locations where apps are known to place data and tries to match the items it finds to one of your installed apps. If it can't match the item to an installed app, it is considered a corpse.

You can use the settings to specify which different types of corpses SD Maid should look for. The different corpse types are tagged with a color gives a rough indication of their risk. Green means very safe, Red means to be cautious. 

Example:
The Dalvik-Cache corpses are marked green, because a false positive might cause an app to crash, but after rebooting your device it's all good again. App-Data corpses are tagged with red, because a false positive here leads to data loss of that app. These colors do not exist because SD Maid is a bad cleaner, but because it's an honest cleaner.

Corpses can be created by a lot of different events. Currently the most common source of corpses are applications that create folders with custom names on your sdcard. Android does not remove these directories when uninstalling an app. This is both good and bad. Good because you might have files in there you want to keep after removing the app, such as music or ebooks. Bad because without action on your part they will stay around forever and clutter up the sdcard. Corpses can also be created by various random hiccups that can happen when uninstalling or installing an app.
Removing such corpses not only frees up space and removes unnecessary files, but can also fix issues such as being unable to reinstall an app or installed applications forgetting theit settings.

[[[ https://cloud.githubusercontent.com/assets/1439229/14577311/aae83c00-0372-11e6-9516-39c8165e9c93.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577311/aae83c00-0372-11e6-9516-39c8165e9c93.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14577312/abe04bc0-0372-11e6-974e-4d1b4d4ec4c2.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577312/abe04bc0-0372-11e6-974e-4d1b4d4ec4c2.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14577315/afcb3d58-0372-11e6-9414-e6b4716b48fa.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577315/afcb3d58-0372-11e6-9414-e6b4716b48fa.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14577317/b13be4da-0372-11e6-9989-ee0bcb74eaab.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577317/b13be4da-0372-11e6-9989-ee0bcb74eaab.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14577318/b2a7fb56-0372-11e6-9c2f-0ad06049e3b9.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577318/b2a7fb56-0372-11e6-9c2f-0ad06049e3b9.png)

## Settings
### Search location types
In the Corpsefinder's settings you can configure the different types of corpses SD Maid should look for.

#### Sdcard
The type of corpse filter refers to all items on your primary or secondary public storage except for the `Android` folder. Items here can usually be only matched to apps through white-listing techniques and manual databases. Whether SD Maid recognizes an item can be checked within the [Explorer](https://github.com/d4rken/sdmaid-public/wiki/Explorer). If something is not recognized or some leftovers are not being picked up as corpses, create a short [issue ticket](https://github.com/d4rken/sdmaid-public/issues/new).

#### Android/data
This folders resides on any public storage and is the official location for apps to place public files. If the developer follows naming conventions the system will gracefuly deal with any remaining files. If not the Corpsefinder will deal with it. This is considered a black-listing location, meaning that any item that can't be matched is automatically a corpse.

#### Android/obb
Similar to `Android/data` but for extra app install files instead of app data (i.e. not save files, but extra levels etc.)

#### /data/data
Private storage location for files created by apps. Can only be checked with root permission. This is also a black-listing location. This entry also covers `/data/user/0` as well as `/mnt/expand/<id>/user/0`, i.e. any private app data location.

#### /data/app
Contains apps install files including their apk file. Also black-listing location and also requires root permission to be checked.

#### /data/app-lib
Also black-listing location and also requires root permission to be checked. Contains apps library files. On newer Android versions this is usually empty, except for devices who upgraded their Android system several times up to 5.X+. On newer Android versions the library files have been merged with the app install files.

#### /data/app-asec
Contains encrypted app containers. Also black-listing location and also requires root permission to be checked.

#### ./dalvik-cache
Covers both `/data/dalvik-cache`, `/cache/dalvik-cache` and dalvik cache locations. Contains app files required by the Dalvik-Runtime or the Android-Runtime (ART). Yes despite it's name it's also used for ART. Required files within this directory are regenerated on reboot. Also a black-listing location and also requires root permission to be checked.

####  /data/app-private
Only seen in use on < Android 4.2 contains extra app data. Also black-listing location and also requires root permission to be checked.

[[[ https://cloud.githubusercontent.com/assets/1439229/14577319/b468b5a2-0372-11e6-9b88-d7b438bb6b59.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577319/b468b5a2-0372-11e6-9b88-d7b438bb6b59.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14577320/b5b738de-0372-11e6-8bae-51ac54ff3d74.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577320/b5b738de-0372-11e6-8bae-51ac54ff3d74.png)

### Keepers
Some corpses are considered "keepers" by SD Maid (e.g. backups, music) and will not be displayed unless you specify it in the settings. I usually use the CorpseFinder after uninstalling a lot of applications or if I'm having trouble reinstalling an app. But also if i want to make sure that an app has not left any data behind before reinstalling it.

### Uninstall watcher
The uninstall watcher is part of SD Maid Pro. It enables the CorpseFinder to automatically run after an app has been uninstalled. Should the corpse search return any items that are related to previously uninstalled app, then their name and size will be displayed in a popup and you have the change to delete them.

[[[ https://cloud.githubusercontent.com/assets/1439229/21750088/904add74-d5ab-11e6-852e-ac60bc5b63ea.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/21750088/904add74-d5ab-11e6-852e-ac60bc5b63ea.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/21750087/90427d3c-d5ab-11e6-9c6e-364290426c43.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/21750087/90427d3c-d5ab-11e6-9c6e-364290426c43.png)

## FAQ
### Reporting false positives
If you think the CorpseFinder got it wrong and the results contain a false positive, you can long report by long pressing the item or sending me an email. 

[[[ https://cloud.githubusercontent.com/assets/1439229/14577417/0b5d103c-0374-11e6-8064-cae8dca50891.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14577417/0b5d103c-0374-11e6-8064-cae8dca50891.png)