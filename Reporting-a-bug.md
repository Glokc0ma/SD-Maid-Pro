# How to report a bug?

While it would be the perfect bug report if you follow all of the following steps, a bug report missing of a few details or better than no bug report at all.

## Step 1 - Known issues
Some bugs or issues might already be known, to check that visit the [issue tracker](https://github.com/d4rken/sdmaid-public/issues). Here you find a list of known issues and requests. Click "bug" and check current and recently closed bugs if any of them are similar to your issue. If you find a similar issue post a comment under it, otherwise make a new issue. In any case, keep following these steps.

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

### Step 2 - Advanced report
#### Crash report
If SD Maid crashed I should have gotten an automatic crash report (unless you turned that off, but why would you...). To find this crash report on my server I need to identify your SD Maid installation. This happen through a UUID which is a unique and anonymous identifier SD Maid generates on it's first start. You can find it by going into the Overview section and expanding the box containing SD Maids version information. Tap it to copy it to your clipboard and add it to your issue ticket.

#### **Debugrun log**
The best thing you can provide is a debug log.
If you can still enter SD Maid and reach the advanced settings, do it and press "Debug run" which will cause SD Maid to restart in debug mode.
Now everything SD Maid does will be written into a log file, attach this log file to your issue ticket. Note that the file may private information inform of file names and pathes on your device.

The logfile can be found on your internal sdcard under:
```
<sdcard>/Android/data/eu.thedarken.sdm/files/logfiles/
```

In some cases you may not be able to reach the advanced settings because SD Maid crashes or missbehaves before that. In that case it is possible to force a debug run by creating a file or directory named ```sdm_force_debug_run``` on your internal sdcard. Make sure SD Maid is not running, then on launch the file will be consumed and for that session SD Maid will do a debug run.