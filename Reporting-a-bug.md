# How to report a bug?

While it would be the perfect bug report if you follow all of the following steps you can start with basic information and still add more at a later point or on request.
**A bug report missing a few details is better than no bug report at all.**

## Step 1 - Known issues
Some bugs or issues might already be known, to check that visit the [issue tracker](https://github.com/d4rken/sdmaid-public/issues). Check [current and recently closed issues](https://github.com/d4rken/sdmaid-public/issues?utf8=%E2%9C%93&q=is%3Aissue). If you find a similar issue post a comment under it, otherwise make a new issue. 

## Step 2 - Basics
Gather basic information about your setup, which includes
* What kind of device you have (e.g. Nexus 5)
* What kind of Android version and or custom ROM it's running (e.g. latest stock Android 6.0.1)
* If your device is rooted or unrooted (e.g. Rooted with SuperSU v2.67)
* What version of SD Maid and (if applicable) SD Maid Pro you were running (e.g. SD Maid v4.1.0, Unlocker v4.0.2)
* Long press the settings menu entry, which will open the debug menu. At the top of the page is your install-id tap it to copy it and attach it to your bug report. This way I will be able to check for automatic crash reports from your device.

Good, now we have a baseline for what kind of device setup you have. Now add a little description describing your issue:
* What happened?
* What did you expect to happen?
* What actions did you take?
* Can you reproduce it, i.e. does this happen everytime?

## Step 3 - Advanced report
**The following instructions are valid for SD Maid v4.2.6+.**
### Crash report
If SD Maid crashed I should have gotten an automatic crash report (unless you turned that off, but why would you...). To find this crash report on my server I need to identify your SD Maid installation. This happen through a UUID which is a unique and anonymous identifier SD Maid generates on it's first start. You can find it by going into the Overview section and expanding the box containing SD Maids version information or by long pressing the settings menu entry. Tap it to copy it to your clipboard and add it to your issue ticket.

### **Debugrun log**
The best thing you can provide to help fix an issue is a debug log of the problem manifesting. A debug log is a very detailed description of everything SD Maid did. Note that the file may private information in form of file names and pathes on your device.

A debug run is initiated if SD Maids detects the file ```sdm-force-debug-run``` in its public files folder.
Example:
```
/storage/emulated/0/Android/data/eu.thedarken.sdm/files/sdm-force-debug-run
```

If the file exists and you restart SD Maid, the file will be consumed and the current session will be a debug run. If you are unsure if SD Maid is completely shutdown, just force close it.

The trigger file can be created manually (through any file tool) or you can have SD Maid create the file for you.

The most comfortable option is having SD Maid create the file for you. This obviously only works if you can still enter SD Maid: 
* Open SD Maid
* Open the navigation menu
* Long press the settings entry at the bottom
* Press the button "Create debug trigger".
* Done. SD Maids next session will be a debug run :+1:.


[[[ https://cloud.githubusercontent.com/assets/1439229/16135841/8977d1e0-3426-11e6-8d1c-e9daac0cc980.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/16135841/8977d1e0-3426-11e6-8d1c-e9daac0cc980.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/16135843/8aa8d852-3426-11e6-821a-948771b82ec6.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/16135843/8aa8d852-3426-11e6-821a-948771b82ec6.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/16135846/8cd0f42a-3426-11e6-8411-fb55720bdea7.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/16135846/8cd0f42a-3426-11e6-8411-fb55720bdea7.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/16135847/8e33e2a0-3426-11e6-9f93-ddcc9d4c9b34.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/16135847/8e33e2a0-3426-11e6-9f93-ddcc9d4c9b34.png)

The created logfiles will be on your primary public storage in the same location where the trigger file was created.

Since SD Maid v4.3.0:
```
<sdcard>/Android/data/eu.thedarken.sdm/cache/logfiles/
```
This folder is used as SD Maid can write to it without any extra permissions or requirements, thus we can use the debug run to troubleshoot permission issues too :wink:.
