# Explorer
The Explorer is a file explorer. You should be very aware of the fact that it IS a typical file explorer.
Most cases of data loss have been the result of people mistaking it for a cleaning tool and thus assumed that everything it showed was safe to delete. That's not the case, these are all the files on your device.

The Explorer offers the usual operations such as copying, moving, renaming files etc. In contrast to some other file explorer apps it does not display the device in a "simplified" view, such that it shows a button for "System", "SDCard" and "External SDCard". It shows the file system exactly how it exists on the device.

If you look at a line in the explorer you will see two icons. On the left side there is an icon that displays the file type such as directory or file including a preview if possible (and you have SD Maid Pro). The right side displays the result of SD Maids "ownership research". When browsing a folder, SD Maid will ty to determine who the owner of an item is. A successful research will either result in the owners app icon being displayed or a ghost if the owning app is no longer installed. If the results are inconclusive a "?" will be displayed.
So if you ever wondered who created those files/folders on your sdcard, the Explorer can help you with that.

You navigate down the directory tree by tapping folders to enter. Going backwards is done by pressing the devices backbutton or tapping directories on the path in the browser bar at the top.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575338/6e409a60-0361-11e6-808b-b0d62bb101a4.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575338/6e409a60-0361-11e6-808b-b0d62bb101a4.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575339/6f53af50-0361-11e6-921f-e81a232d2eb4.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575339/6f53af50-0361-11e6-921f-e81a232d2eb4.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575342/7087c92e-0361-11e6-88b6-b4fc384c0575.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575342/7087c92e-0361-11e6-88b6-b4fc384c0575.png)

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

## Advanced
If you enter your email in SD Maids settings, the question marks on the right side of unknown entries become interactive, when tapping them a new window will open and extra window in which you can select one of your installed apps as being the owner of that file. Reports are processed manually and I'll update SD Maids definitions are checking the reports.
SD Maid is and will always be a work in progress, as every day new apps come out :). If you see a folder of which you are sure that it belongs to a specific application, and SD Maid does not recognize it, you can report it. In the settings you can enter your email, after you have done that you can press the "?" in the Explorer and report it from inside the app. 