# FAQ
## SD Maid Pro
### Why are there two SD Maid apps?
SD Maid consists of two apps, the free app and a paid app. The paid app is a plugin that enables extra features in the free app. The paid app can't be used alone, while the free app (sans pro features) can be used on its own. This is mainly for historical reasons as IAPs (In-App-Purchases) did not exist 5 years ago when SD Maid launched. While this will probably change at some point, it currently also has the advantage that there is no dependency on Google-Services to enable in-app-purchases.

### Factory-Reset / Device-Change
This is not an SD Maid issue, but still a popular question. Apps purchased through Google Play are tied to your Google account, not your device. If you use the same Google account on a new or factory reset device, you will have access to all previous purchases.

### Google Play is not showing the purchase
If Google Play is not showing your purchase, you are either not logged in with the account your purchased the application with or the Google Play app has not yet syncronized with your list of purchases. This is a Google Play issue and has no relation to SD Maid itself.

The following action are known to fix this in some instances:
* Force closing and reopening Google Play.
* Rebooting the device.
* Using "Clear Data" on the Google Play app (`com.android.vending`).

### SD Maid is not enabling the pro features
If the both SD Maid (`eu.thedarken.sdm`) and the SD Maid Pro plugin/unlocker (`eu.thedarken.sdm.unlocker`) are installed, SD Maid should enable all pro features. Detection of the SD Maid Pro happens on app launch and when closing/opening the UI.

Known solutions:
* Force close SD Maid or reboot the device and reopen SD Maid
* The system did not correctly install either SD Maid or the unlocker. Uninstall both apps, reboot your device, install the unlocker app first, then SD Maids free version.
* If either SD Maid or the unlocker has been modified the pro features will also not be unlocked. Ensure that you downloaded the apps from official sources (Google Play or [my server](sdmaid.darken.eu/download)) and that no app on your device modified them. There are some "security apps" that modify installed apps for questionable purporses.

### I can't find SD Maid Pro on my device
The SD Maid Pro plugin only has to be installed, but does not have to be actively launched. Due to this this the app contains an option that will hide its shortcut from your app drawer. To display the shortcut again, either uninstall and reinstall the app, or open SD Maids advanced settings which offers an option to do that.

## Root
### What is root?
So what's this root everyone is talking about? Root is the name of a special user account on your device, a super user account with elevated privileges.
Normally you or apps can't use the account. The act of "rooting" changes that. It makes it accessible and adds a "superuser app" that manages access to the root account. There are pros and cons to rooting, which we don't need to cover here. Just google it, it's a common discussion on many blogs. Whether you root your device is up to you.

### Does SD Maid only work with root?
**No.** SD Maid will adjust it's behavior to fit your device. 

SD Maid being able to use root is a bonus for people with rooted devices. It does not make SD Maid work worse on unrooted devices.

Some people are saying: If you have rooted device you should use SD Maid, but if your device is not rooted, choose a different application. That's wrong. All applications are bound by the same restrictions, how each app uses what is has available, is what makes the difference.
Choose a different app if you don't feel comfortable using SD Maid, if it is too complicated or you simply don't like it, but not because you don't have a rooted device.

Functions that don't work at all without root are usually those that modify other apps, such as freezing or disabling components or uninstalling system apps.

## Does SD Maid only work on sdcards?
**No.** SD Maid will consider any accessible storage in your device. Depending on what can be accessed, this includes internal storage, external storage and usb storage.

## Why should I use SD Maid?

**Because it's thorough and honest.**
If you want a broom, you look for the one that cleans best, any other purchase argument is secondary. SD Maid v0.1 was released on [29.03.2011](http://forum.xda-developers.com/showpost.php?p=12482608&postcount=1). Years of learning and more experience, constant improvements and adaption to every new Android kink, make SD Maid what is is today.
SD Maid is brutally honest, there will be no euphemisms to make your feel better after "cleaning" your device. No hidden agenda to pressure you into using the app itself. A tool to use when needed.

## SD Maid v2/v3/v4
There are different versions available of SD Maid. Every few years SD Maid was completely overhauled to improve it through gained experience and to adopt to new Android environments. During these overhauls the minimum required Android version is usually raised due reduce workload, maintaining compatibility "hacks" for very old Android versions is usually not feasible when supporting the newest Android versions.

It's possibly that newer versions seem slower but downgrading because of that is bad trade, you would gain speed but pay with thoroughness and safety. Searching through more and doing additional checks just costs time. Never versions may show less items to delete, not because they are worse, but because for specific reasons it is no longer considered good to remove these files. The goal is not to delete the most files, but the right files. Every change has a good reason.

In short: **Use the latest version of SD Maid available for your device.**

* SD Maid v2 was the main app version from 2012Q2 to 2013Q1. Its target is Android 2.1 to 2.2.
* SD Maid v3 was the main app version from 2013Q1 to 2016Q1. Its target is Android 2.3 to 4.0.
* SD Maid v4 is the main app version since 2016Q1. Its target version is Android 4.1+.

