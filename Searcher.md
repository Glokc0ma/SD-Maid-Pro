# Searcher
The searcher allows you to search your device. You can just search for files or directories by names. You can even search for content inside of files, but be aware that some searches especially through files can take a long time to complete. Clicking an entry tries to open it by way of any compatible installed app on your device. Long pressing it gives you a context menu with a few options:

* Open it in the [Explorer](https://github.com/d4rken/sdmaid-public/wiki/Explorer) for further processing.
* Copy/Move it which will create a copy/move task than you can then paste from the Explorer tool.
* Create an [Exclusion](https://github.com/d4rken/sdmaid-public/wiki/Exclusion) for this entry.
* Delete the item.

Note that wildcards such as * are currently automatically appended, so if you enter "\*file\*" SD Maid will execute a search for "\*\*file**" which will likely return no results.

A few extra settings such as
* Root search
* Files only
* Case-sensitive
can be toggled from the menu in the toolbar.

Search locations on unrooted devices include all public storage, while on devices with root everything starting from `/` is searched.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575920/6b6ca352-0365-11e6-85cf-1cba000babdc.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575920/6b6ca352-0365-11e6-85cf-1cba000babdc.png)
[[[https://cloud.githubusercontent.com/assets/1439229/14575918/6b6b5c40-0365-11e6-843e-ba27ff0aa103.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575918/6b6b5c40-0365-11e6-843e-ba27ff0aa103.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575919/6b6b86b6-0365-11e6-95ec-01504b7b471a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575919/6b6b86b6-0365-11e6-95ec-01504b7b471a.png)