# Duplicates
The Duplicates tool compares files by content and helps you delete extra copies while making sure you have at least one copy left.

The underlying routines use size and checksums (MD5) to determine which files are exactly the same, paired with lots of failsafes.

[[[ https://cloud.githubusercontent.com/assets/1439229/19916184/0f900dbc-a0b8-11e6-8f71-25b5beee3f03.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916184/0f900dbc-a0b8-11e6-8f71-25b5beee3f03.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916185/0f904214-a0b8-11e6-856a-04a430729d2e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916185/0f904214-a0b8-11e6-856a-04a430729d2e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916187/0f908152-a0b8-11e6-8a5a-b1d687ced1ce.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916187/0f908152-a0b8-11e6-8a5a-b1d687ced1ce.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/19916189/0f9363a4-a0b8-11e6-9ad7-770602854e80.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916189/0f9363a4-a0b8-11e6-9ad7-770602854e80.png)

## Autoselection
Now a lot of people ask which duplicates to delete and there is no right or wrong answer to this question. At least none that an app could make, it's all up to preference. 

Example
> Lets say you have two music albums called "Best running tracks of 2013" and "My favorite motorcycle music" and both obviously contain the track "Darken - Singing in the shower.mp3". You have the same file in two different locations. Now which one should be deleted, or none at all? I can't answer that and neither can SD Maid, only you can.
> In any case the DuplicateFinder will make sure you always have one copy left.

SD Maid offers a few ways of automatically selecting items:
* Keep the file with the newest modification date
* Keep the file with the oldest modification date
* Keep the most nested item (the item that is most nested, e.g. `/nested/more_nested/most_nested`)
* Keep the top level item (shortest path, e.g. `/sdcard/top_level`)
* Keep a random item
* Keep on primary storage (the remaining file should be on your devices internal sdcard)
* Keep on secondary storage (the remaining file should be on your external removable sdcard)

The procedure set as default will be used when the Duplicates tool is used through the [Scheduler](https://github.com/d4rken/sdmaid-public/wiki/Scheduler), [QuickAccess](https://github.com/d4rken/sdmaid-public/wiki/QuickAccess) or Widget.

[[[ https://cloud.githubusercontent.com/assets/1439229/19916186/0f90605a-a0b8-11e6-82c9-6944858a89e2.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916186/0f90605a-a0b8-11e6-82c9-6944858a89e2.png)

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