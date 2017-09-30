# Explorer
The Explorer is a file explorer. You should be very aware of the fact that it IS a typical file explorer.
Most cases of data loss have been the result of people mistaking it for a cleaning tool and thus assumed that everything it showed was safe to delete. That's not the case, these are all the files on your device.

The Explorer offers the usual operations such as copying, moving, renaming files etc. In contrast to some other file explorer apps it does not display the device in a "simplified" view, such that it shows a button for "System", "SDCard" and "External SDCard". It shows the file system exactly how it exists on the device.

You navigate down the directory tree by tapping folders to enter. Going backwards is done by pressing the devices backbutton or tapping directories on the path in the browser bar at the top.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575338/6e409a60-0361-11e6-808b-b0d62bb101a4.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575338/6e409a60-0361-11e6-808b-b0d62bb101a4.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575339/6f53af50-0361-11e6-921f-e81a232d2eb4.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575339/6f53af50-0361-11e6-921f-e81a232d2eb4.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575342/7087c92e-0361-11e6-88b6-b4fc384c0575.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575342/7087c92e-0361-11e6-88b6-b4fc384c0575.png)

### File size
The explorer displays two file sizes. Format: `allocated size (file size)`

Allocated size is the space a file occupies on the in the filesystem. A filesystem stores data in blocks with fixed size. If the file size is 1Byte, but the blocksize of the filesystem is 4096Byte, then storing the file means that the allocated size is 4096Byte. Think of it like sorting items into same sized boxes, but each box may only contain one item.

Usually the allocated size is within a few KB (the blocksize) of the file size. Depending on the file system there can be exception such as [sparse files](https://en.wikipedia.org/wiki/Sparse_file).

In the following screenshot, the file `.twrps` is `0.91KB` in size but occupies `8KB` of filesystem space.

[[[ https://user-images.githubusercontent.com/1439229/31046927-d2c81a6e-a601-11e7-98a4-8f2f440cb4d5.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046927-d2c81a6e-a601-11e7-98a4-8f2f440cb4d5.png)

### Permissions
Androids basic file system access is based on the linux permission attributes `READ`(r), `WRITE`(w), `EXECUTE`(x) for the permission groups `OWNER`, `GROUP` and `OTHER`. SD Maid displays these permissions in that order, e.g. `rwxrwxrwx` meaning read, write and execute permission for owner, group and other.

This holds true for most of an Android devices storage except for public internal and external storage (depending on device ROMs and Android versions). These locations may be accessed through a "fuse-daemon" which wraps the storage itself and lets the system enforce additional access rules. Due to this an item or location could have the permission `rwxrwxrwx` but still not be accessible (read or writable) for SD Maid and apps. SD Maid's explorer displays this by changing the color of the permission label. An orange color indicates that SD Maid can read, but not write to that location, while a red color indicates that SD Maid can neither read nor write to that location.

### Icons
If you look at a line in the Explorer you will see multiple icons. On the left side there is an icon that displays the file type such as directory or file including a preview if possible (and you have SD Maid Pro).

The right side displays the result of SD Maids "ownership research". When browsing a folder, SD Maid will try to determine who the owner of an item is. A successful research will either result in the owners app icon being displayed or a ghost if the owning app is no longer installed. If the results are inconclusive a `?` will be displayed.

#### Known owner
[[[ https://user-images.githubusercontent.com/1439229/31046683-31946174-a5fd-11e7-944e-587c1cce3d98.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046683-31946174-a5fd-11e7-944e-587c1cce3d98.png)

If an app icon is shown then SD Maid knows who the owner is. Multiple icons may be shown if SD Maid knows multiple owners for this item.

#### Unknown owner
[[[ https://user-images.githubusercontent.com/1439229/31046684-32e068b6-a5fd-11e7-9daa-12a23fd7f058.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046684-32e068b6-a5fd-11e7-9daa-12a23fd7f058.png)

A `?` means that SD Maid doesn't know the owner of this item. If you know the owner, press the questionmark and help improve SD Maid.

#### SystemCleaner target
[[[ https://user-images.githubusercontent.com/1439229/31046686-340f9874-a5fd-11e7-9c69-4eeb6345ec63.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046686-340f9874-a5fd-11e7-9c69-4eeb6345ec63.png)

The SystemCleaner icon is shown for files that match any SystemCleaner filter. Note SD Maid will test all filters, even those that are not enabled. In this example the folder `calimoto` matches the empty directory filter and also has an unknown owner.

#### Corpse
[[[ https://user-images.githubusercontent.com/1439229/31046680-2f48abfa-a5fd-11e7-80cc-a376501e4091.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046680-2f48abfa-a5fd-11e7-80cc-a376501e4091.png)

A normal corpse will be marked by the CorpseFinder's icon in white. Running the CorpseFinder should show this item in the scan results. Note that Explorer checks all CorpseFinder filters, even those that are turned off.

#### Keepers
[[[ https://user-images.githubusercontent.com/1439229/31046679-2dfc28d0-a5fd-11e7-9908-c71d57f20607.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046679-2dfc28d0-a5fd-11e7-9908-c71d57f20607.png)

The orange CorpseFinder icon signifies a corpse that is flagged as "keeper". It is considered a "desirable remanent". This is usually reserved for files such as photos that you may want to keep even without the camera app. To show these corpses among the CorpseFinder results you have to turn on explicitly enable "Show desirable remnants" in the settings.

#### Common
[[[ https://user-images.githubusercontent.com/1439229/31046910-9675f84c-a601-11e7-954f-cb78dc579713.png | height = 100px]]](https://user-images.githubusercontent.com/1439229/31046910-9675f84c-a601-11e7-954f-cb78dc579713.png)

Items that are flagged as "common" will display a teal CorpseFinder icon. Items are flagged as "common" if they name is too short or too common to make a safe decision regarding ownership. For safety reasons, SD Maid currently does not support automated deletion of these items. In this example the folders name `backups` is used too often my too many apps, it would be very prone to false positive results.

## Operations
Most operations are item related, that means you have to long press an item to select one (or multiple) such that the context menu becomes visible and then select an operation out of the context menu.
Note that due to Android constisting of many different storage areas, not all operations success on every time.

A few extra operations are not shown by default and have to be enabled in the settings.

Note: SD Maid will remount a read-only partition if necessary for the operation to succeed.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575344/72caea86-0361-11e6-998d-9f85d03d2277.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575344/72caea86-0361-11e6-998d-9f85d03d2277.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575856/fd364456-0364-11e6-9282-286cd4740836.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575856/fd364456-0364-11e6-9282-286cd4740836.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575347/7692bb62-0361-11e6-885d-7da503063047.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575347/7692bb62-0361-11e6-885d-7da503063047.png)

### Delete
Deletes the selected items...

### New item creation
Creating new files or directories is currently the only operation that works without selecting an item first.

### Copy / Move / Paste
Basic file operations that allow you to copy or move files. Select the files you want to copy/move, then choose an operation from the context menu, the selection will close and you should see a new paste (clipboard) icon in the toolbar. Now you can move around in the directories and when you found your destination, paste the items into it.

### Rename
Renames the select file or directory

### Size
Calculates the select items sizes. If multiple items are selected, each items size is calculated, then added.

### Exclude
Opens a new window to exclude the selected path from select tools. See [Exclusions](https://github.com/d4rken/sdmaid-public/wiki/Exclusions).

### Change permission
Allows you to change the owner, group and other file permissions. Note that this does usually not work on public storage or any storage that can be accessed without root as the system enforces specific permissions for these locations.

### Share
Attempts to share the selected file through another app, e.g. mailing a picture. It is currently not supported to share files that the other application can not access itself.

### Create filter
Helps you create a user filter for the [SystemCleaner](https://github.com/d4rken/sdmaid-public/wiki/SystemCleaner).

### Save directory structure
Will create a text file on your primary storage (e.g. root of your sdcard) that contains the file/directory structure (recursively) of the selected items. A better way than screenshots to share specific file setups with other users (or me :p).

### Extract
Tries to extract an ZIP based archive (`.zip`, `.apk` etc) into a new directory in the current path. The directory will be the filename appened with `-(1)` (or `-(2)` and so forth). Extraction is currently only possible on public storage.

## Bookmarks
On the right screen side sliding out side drawer. It contains a bookmarks manager that provides a set of shortcuts to interesting default locations. You can add new entries by entering a folder, then opening the bookmarks drawer and pressing the plus button to the right of the path in the browser bar. Bookmarks can be removed by long pressing them.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575343/71a67382-0361-11e6-839f-6103d337ee30.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575343/71a67382-0361-11e6-839f-6103d337ee30.png)

## Settings
### Remember
Try to start in the same directy as you were previously in, after closing+reopening SD Maid.

### Research owner
Whether SD Maid should try to determine owner ship of files and directors. This is responsible for the little app icons in each row. This setting also influences whether SD Maid displays a small sdcard symbol in each row that is a mount-point on the device.

### SystemCleaner
Whether SD Maid should test if this file/directory fits any existing SystemCleaner filter. This includes both default and user-made filters. If it fits, the SystemCleaner icon will be displayed.

### AppCleaner
Whether SD Maid should test if this file/directory fits any existing AppCleaner filter. This includes both default and user-made filters. If it fits, the AppCleaner icon will be displayed.

### Sort mode
How list entries should be sorted, by default it's sorted like in Windows. By name, but directories first.

### Add shortcut
Adds an "app-like" shortcut to your launcher that directly takes you to the Explorer and loads the current directory.

### Actions
There are a few extra file/directory context actions that are not shown by default, you can enable them here.

[[[ https://cloud.githubusercontent.com/assets/1439229/14576144/10608e7c-0367-11e6-8f62-689ce0f3392a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14576144/10608e7c-0367-11e6-8f62-689ce0f3392a.png)