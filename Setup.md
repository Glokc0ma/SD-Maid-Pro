# Setup
SD Maids setup consists of a few steps where you are asked to grant SD Maid certain access and permissions. Some are mandatory, some are not.

## Primary Storage Setup
Primary storage is only required on Android 6.0+ devices. It is necessary because the general read/write permission for public storage can only be aquired during runtime since Android 6.0. Granting these permissions is mandatory as otherwise SD Maid will not function (what good is SD Maid if it can't access any files).
Although ROOT permission superseed any other permission, even on rooted devices it needs to be granted. Trying to skip this step or abort it will close SD Maid.

[[[ https://cloud.githubusercontent.com/assets/1439229/14230404/bde057c4-f955-11e5-8050-898550e8e3c0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230404/bde057c4-f955-11e5-8050-898550e8e3c0.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230402/bddbf094-f955-11e5-91d6-b7a93e50c46c.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230402/bddbf094-f955-11e5-91d6-b7a93e50c46c.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230403/bddc000c-f955-11e5-9b4e-d557fccda9f5.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230403/bddc000c-f955-11e5-9b4e-d557fccda9f5.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230401/bddb7ee8-f955-11e5-8197-36870aff4f95.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230401/bddb7ee8-f955-11e5-8197-36870aff4f95.png)

## Secondary Storage Setup
Secondary storage setup is a step that is only available on Android 5.0+. It's purpose is to grant SD Maid read/write access to storage locations through the system built-in [Android Storage Accessframework (SAF)](http://developer.android.com/guide/topics/providers/document-provider.html).
Since Android 4.4 most devices no longer allow apps to write to the secondary storage (e.g. external/removable sdcards) and accessing sdcards through the SAF only works since 5.0. So sadly Android 4.4 users are out of luck.
Anyways, if you reach this step, SD Maid will display a list of storage locations she would like to be granted access to. 

#### Steps
* Tap an orange entry, remember the location it displays, e.g. `/storage/sdcard1`
* In the new window open the drawer on the left and select the related storage entry
* If there is no entry for your sdcard, close the drawer again, tap the overflow menu button in the top right corner and select `Show sdcards`, then repeat the previous step.
* After selecting the respective storage you should now see it's content in the main window.
* At the top right or bottom right corner, press the select button.
You should now have returned to SD Maid and the previously orange entry is green. Rinse and repeat for every entry.

[[[ https://cloud.githubusercontent.com/assets/1439229/14230453/787daed6-f958-11e5-9718-be013e87e86e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230453/787daed6-f958-11e5-9718-be013e87e86e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230454/7a0150d2-f958-11e5-9c1d-08de69ffad7b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230454/7a0150d2-f958-11e5-9c1d-08de69ffad7b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230455/7b4b0fe6-f958-11e5-9b1a-2bbb5a7d972e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230455/7b4b0fe6-f958-11e5-9b1a-2bbb5a7d972e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230457/7f1a8e62-f958-11e5-8713-951b4500f49e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230457/7f1a8e62-f958-11e5-8713-951b4500f49e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14230458/7f3ff5b2-f958-11e5-9472-beec5c35c369.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14230458/7f3ff5b2-f958-11e5-9472-beec5c35c369.png)

### Error: Documents window is empty (shows no sdcards)
On some devices the `Documents` app that opens after pressing the orange entry is empty. No storage can be chosen despite having clicked `Show sdcards`. This means that your ROM (not SD Maid) does not correctly recognize your extra storage. Known devices with this issue: Galaxy S7 edge.

#### Known solutions
* Formatting the sdcard. Possibly removing and reinserting the sdcard.
* Note: Currently due to a bug in SD Maid this skip can not be stepped. Update 4.1.4 will fix this soon.

[[[ https://cloud.githubusercontent.com/assets/1439229/14278110/4e3c0e36-fb26-11e5-9c91-65d23eb48676.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14278110/4e3c0e36-fb26-11e5-9c91-65d23eb48676.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14278050/0fa0defe-fb26-11e5-9062-0508bd60400b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14278050/0fa0defe-fb26-11e5-9062-0508bd60400b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14278051/10a37028-fb26-11e5-9332-1be70f417221.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14278051/10a37028-fb26-11e5-9332-1be70f417221.png)
[[[https://cloud.githubusercontent.com/assets/1439229/14278054/11e17aa2-fb26-11e5-8023-bbc16fd4cac2.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14278054/11e17aa2-fb26-11e5-8023-bbc16fd4cac2.png)

### Error: Activity not found
The activity through which you grant SD Maid access is part of the "Documents" app, specifically the app with the packagename `com.android.documentsui`. This should be available on any 5.0+ ROM as it is part of the Android Open Source Project (AOSP). If you are getting this error you or someone else modified the ROM such that this app is either not installed or disabled. To check for it's existance you can enable "Show system apps" and then search for the packagename using SD Maids AppControl tool.

#### Known solutions
* Checking on rooted devices if the app `Documents` has been accidentally disabled.
* Writing the manufactor an angry mail why his 5.0+ ROM is not Android CTS compliant.

### Error: Invalid storage / Invalid input
If you select the wrong storage location (or SD Maid is just not happy with the selection for any reason) you will see and error message and the entry will stay orange. In some cases it is possible that you selected the correct storage and it still said "Invalid" and didn't accept it. Reasons for that are usually related to your devices ROM (e.g. [#312](../issues/312) or [#231](../issues/231)).

#### Known solutions
* In some cases removing, formatting and reinserting the sdcard helps (Known cases: Galaxy S7 edge).
* As a temporary solution you can permantly skip this step by choosing "Don't show again" from the overflow menu in the top right corner. On rooted devices skipping this has no adverse effect.

[[[https://cloud.githubusercontent.com/assets/1439229/14256420/51aa30f8-fa99-11e5-9853-5d6b41e4cbbc.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14256420/51aa30f8-fa99-11e5-9853-5d6b41e4cbbc.png)