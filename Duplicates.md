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

### Selection procedure
The default selection procedure.

[[[ https://cloud.githubusercontent.com/assets/1439229/19916188/0f90fb00-a0b8-11e6-9e14-96b554b07e65.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/19916188/0f90fb00-a0b8-11e6-9e14-96b554b07e65.png)

## FAQ
### I deleted duplicates but now can't find my pictures
Your gallery app is just not showing the picture because the remaining copy of the image is in a location that's not searched by the gallery app. Make your gallery app search that extra location or move the image into a folder which the gallery app indexes. In some cases a device reboot can help as it forces the devices to reindex media on your device.