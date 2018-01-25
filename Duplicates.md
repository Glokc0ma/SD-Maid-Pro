# Duplicates
The Duplicates tool compares files by content and helps you delete extra copies while making sure you have at least one copy left.

The underlying routines use size and checksums (MD5) to determine which files are exactly the same, paired with lots of failsafes.

[[[ https://cloud.githubusercontent.com/assets/1439229/19916184/0f900dbc-a0b8-11e6-8f71-25b5beee3f03.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916184/0f900dbc-a0b8-11e6-8f71-25b5beee3f03.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916185/0f904214-a0b8-11e6-856a-04a430729d2e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916185/0f904214-a0b8-11e6-856a-04a430729d2e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916187/0f908152-a0b8-11e6-8a5a-b1d687ced1ce.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916187/0f908152-a0b8-11e6-8a5a-b1d687ced1ce.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916189/0f9363a4-a0b8-11e6-9ad7-770602854e80.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916189/0f9363a4-a0b8-11e6-9ad7-770602854e80.png)

## Autoselection
A lot of people ask which duplicates to delete and which to keep and there is no right or wrong answer to this question. At least none that an app could make, it's all up to preference. 

Example:
> Lets say you have two music albums called "Best running tracks of 2013" and "My favorite motorcycle music" and both obviously contain the track "Darken - Singing in the shower.mp3". You have the same file in two different locations. Now which one should be deleted, or none at all? I can't answer that and neither can SD Maid, only you can.
> In any case the DuplicateFinder will make sure you always have one copy left.

SD Maid determines which duplicates to keep through a list of _Criteria_ (a list of tests/ a set of preferences). Each files in a set of duplicates will be compared and ordered based on these criteria, the most preferred file is kept while other duplicates are be deleted.

The criteria are configured in a list of descending priority. You can drag and rearrange this list. The criterion at the top is the most important one. If two files are equal in regards to the top criterion, then they are compared based on the second criterion.

### Criteria
The configured preferences will also be used when the Duplicates tool is used through the [Scheduler](https://github.com/d4rken/sdmaid-public/wiki/Scheduler), [QuickAccess](https://github.com/d4rken/sdmaid-public/wiki/QuickAccess) or Widget.

Currently these criteria are supported:

#### Media Provider
The media provider is an app that holds a database of most media files (including their metadata) on your device. Other apps such as galleries use this information to know which files to display. My default it suggests to keep _indexed files_ and to delete not _not indexed files_. Meaning we keep the duplicate files we can actually see in an gallery app while we delete other duplicate version of that file that are likely not directly visible to us.

#### Storage Location
The storage location refers to the physical storage device the files reside on. You can choose between _primary storage_, which is usually the built-in storage and _secondary storage_ which usually refers to removable sdcards. By default this criterion prefers files on secondary storage by assuming that it is more likely the user wants to free space on internal storage.

#### Path nesting
Path nesting refers to the amount of subdirectories a file is in. The default setting prefers _shallowly nested files_ as those are more accessible to the user. When you look at your storage you are more likely to look in `/sdcard/Pictures` than in `/sdcard/Android/data/some.app/pictures`.

#### Modification date
Even if two files have different modification dates, they can still have the same content. This criterion prefers older files by default as the newer file is likely an unwanted copy.

Example: You take a picture with your camera and at a later point in time you send that picture to someone with another app. That other app creates a copy of the picture in its own folder. It's likely that you want to keep the file at it's original location (in your camera folder) as this is where you expect it.


[[[ https://user-images.githubusercontent.com/1439229/35372927-9f160414-019c-11e8-839c-c72d1b04392f.png | height = 300px]]](https://user-images.githubusercontent.com/1439229/35372927-9f160414-019c-11e8-839c-c72d1b04392f.png)

## Settings
### Search locations
Where the tool will search. By default SD Maid will search all public storages. You can modify this and remove locations but be careful when adding locations to not ask SD Maid to search the same storage twice. SD Maid has a lot of failsafes against this, but Androids filesystem is quite complicated.

### Prune Media Storage
The Media Storage app is a database/ an index of all media files (and their meta data) on your device. Othernames for this you will find are: Apps (e.g. galleries) use it to know what to display. The _Media Storage_ app can get out of sync causing issues like gallery apps displaying black squares (thumbnails). If this option is enabled and the Duplicates tool deletes a file then SD Maid will also check the media index for references to the now deleted file and if one is found delete it. This keeps the media index directly in sync. If you disable this option you may see stale references to images until you reboot the device or otherwise force the _Media Storage_ app to syncronize.

Deleting an entry from the media index does not delete the file it references, and vice versa, deleting a media file from your device does not always delete it's references in the media index.

This is known under multiple names: _Media Storage, Media Index, MediaProvider, MediaStore_.

[[[ https://user-images.githubusercontent.com/1439229/35373059-3598848e-019d-11e8-827f-0c36ae0f78cb.png | height = 300px]]](https://user-images.githubusercontent.com/1439229/35373059-3598848e-019d-11e8-827f-0c36ae0f78cb.png)

## FAQ
### I can't find my pictures
Your gallery app is just not showing the picture because the remaining copy of the image is in a location that's not searched by the gallery app. 

* Make sure the autoselection criterion _Media Storage_ is at the top and that you have selected _Prefer indexed files_
* In some cases a device reboot can help as it often forces the devices to reindex media on your device.
* Some gallery app have options to change the search pathes or move the image into a folder which the gallery app indexes.

### My gallery app shows black thumbnails
The list of images the gallery app gets from the _Media Provider_ likely contains stale references. Make sure _Prune Media Storage_ is enabled in the settings.

### read failed (I/O error)
This error happens when SD Maid encounters an unexpected error while trying to calculate checksums. Possible reasons:

* You manually changed the search pathes and now SD Maid is trying to search a location that is not readable with the available permission. By default SD Maid will correctly choose the pathes to scan all public storage (internal & external sdcard). You can reset the search pathes by removing them all. If no custom search pathes are defined, SD Maid will use the default search pathes.
* The sdcard SD Maid is trying to read is faulty and/or has a corrupt file system. Remove the sdcard and try again. If the error no longer happens, try a different sdcard. If the error is still gone than the original sdcard was faulty. Backup any important data from it ASAP. You may try fixing and/or formatting it from a desktop computer which can fix corrupt filesystems but if the card itself is faulty, it will corrupt itself again.

[[[ https://cloud.githubusercontent.com/assets/1439229/24590357/fe4cb89c-17eb-11e7-9cce-c6d4cecc2630.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/24590357/fe4cb89c-17eb-11e7-9cce-c6d4cecc2630.png)