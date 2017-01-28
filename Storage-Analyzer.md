# Storage Analyzer
This features sorts your device content by file size and allows you to quickly find out where most of you space it taken up.

The following locations are supported:
* Primary and secondary public storages (e.g. `/storage/emulated/0`, `/storage/sdcard1` etc)
* Portable storages, think usb otg devices (though support for that is still a WIP as of v4.5.9)
* Primary and secondary private storages (e.g. `/data`, `/mnt/expand`)
* System cache partition (e.g. `/cache`)
* System partition (e.g. `/system`)

[[[ https://cloud.githubusercontent.com/assets/1439229/18743191/2ee5348c-80b8-11e6-9e75-28c34f7c55bc.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18743191/2ee5348c-80b8-11e6-9e75-28c34f7c55bc.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18743203/39da25fa-80b8-11e6-8481-26db8c85792b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18743203/39da25fa-80b8-11e6-8481-26db8c85792b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/22393517/36df3ade-e508-11e6-8230-1e1d77e9100c.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/22393517/36df3ade-e508-11e6-8230-1e1d77e9100c.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/22393604/0c4f35ec-e50a-11e6-9066-a5fcfd472d37.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/22393604/0c4f35ec-e50a-11e6-9066-a5fcfd472d37.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/22393605/0c793b30-e50a-11e6-91d4-90aac06c2154.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/22393605/0c793b30-e50a-11e6-91d4-90aac06c2154.png)

## Settings
### Show inaccessible items
Some storage items such as `/data` and `/cache` can only be scanned with root permission, but their total size may still be determined without root (e.g. using `df`). To show them enable this setting.

[[[ https://cloud.githubusercontent.com/assets/1439229/22393518/36df42d6-e508-11e6-86d8-1018f3580ec7.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/22393518/36df42d6-e508-11e6-86d8-1018f3580ec7.png)