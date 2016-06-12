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

Good, now we have a baseline for what kind of device setup you have. Now add a little description describing your issue:
* What happened?
* What did you expect to happen?
* What actions did you take?
* Can you reproduce it, i.e. does this happen everytime?

## Step 3 - Advanced report
### Crash report
If SD Maid crashed I should have gotten an automatic crash report (unless you turned that off, but why would you...). To find this crash report on my server I need to identify your SD Maid installation. This happen through a UUID which is a unique and anonymous identifier SD Maid generates on it's first start. You can find it by going into the Overview section and expanding the box containing SD Maids version information. Tap it to copy it to your clipboard and add it to your issue ticket.

### **Debugrun log**
The best thing you can provide is a debug log.
You can trigger this in 2 ways:
* If you can still enter SD Maid: In SD Maid v4.2.6+ long press the settings entry in the menu to view debug options, in SD Maid v4.2.5 or older you can find the debug options in the advanced settings. After a full restart SD Maid will be in debug mode and log all actions.

* If you can't enter SD Maid anymore because some goes wrong early on: In some cases you may not be able to reach the advanced settings because SD Maid crashes or missbehaves before that. In that case it is possible to force a debug run by creating a file or directory named ```sdm_force_debug_run``` in the root directory your internal sdcard (e.g. `/storage/emulated/0`). Make sure SD Maid is not running, then on launch the file will be consumed and for that session SD Maid will do a debug run.

Everything SD Maid does will be written into a log file, attach this log file to your issue ticket. Note that the file may private information in form of file names and pathes on your device.
```
<sdcard>/Android/data/eu.thedarken.sdm/files/logfiles/
```

