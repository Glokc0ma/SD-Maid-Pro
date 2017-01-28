# Searcher
The searcher allows you to search your entire device for files and directories.
You can just search for files or directories by names. You can even search for content inside of files, but be aware that some searches especially through files can take a long time to complete. Clicking an entry tries to open it by way of any compatible installed app on your device. Long pressing it gives you a context menu with a few options:

* Open it in the [Explorer](https://github.com/d4rken/sdmaid-public/wiki/Explorer) for further processing.
* Copy/Move it which will create a copy/move task than you can then paste from the Explorer tool.
* Create an [Exclusion](https://github.com/d4rken/sdmaid-public/wiki/Exclusion) for this entry.
* Delete the item.

[[[ https://cloud.githubusercontent.com/assets/1439229/14575920/6b6ca352-0365-11e6-85cf-1cba000babdc.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575920/6b6ca352-0365-11e6-85cf-1cba000babdc.png)
[[[https://cloud.githubusercontent.com/assets/1439229/14575918/6b6b5c40-0365-11e6-843e-ba27ff0aa103.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575918/6b6b5c40-0365-11e6-843e-ba27ff0aa103.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/14575919/6b6b86b6-0365-11e6-95ec-01504b7b471a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/14575919/6b6b86b6-0365-11e6-95ec-01504b7b471a.png)

## Options
The toolbar has a menu entry for options.
Currently these offer the points:

### Root search
If your device is rooted setting this option causes the [search locations](https://github.com/d4rken/sdmaid-public/wiki/Searcher/_edit#search-locations) to change.

### Files only
If you only want files to be listed (e.g. not directories).

### Case-sensitive
If the search terms you entered should be treated case-sensitive (e.g. `Strawberry` vs `strawberry`).

### Implicit wildcards
If this is turned, SD Maid will append `*` on both sides of your search-input. `berry` would become `*berry*` and match both `Strawberry` and `Blueberry`, instead of just `berry`.

### File age
* Minimum age: The minimum age a files modification date should be.
* Maximum age: The maximum age a files modification date should be.

#### Last modified
Since SD Maid v4.3.X the tool *Last Modified* has been merged into the Searcher tool.
Example:

* To find files modified in the last 3 days, set the minimum age to `-` and the maximum age to `3 days`.
* To find files modified exactly 3 days ago, raise the minimum age to `2 days`.
* To find files older than 3 days, set the minimum age to `3 days` and the maximum age to `-`.

Note, for new files the modification date equals the creation date.

Pressing search with no keywords will result in the same behavior you found previously in the *Last Modified* tool, but since both tools have been merged, you can now make use of additional search functions.
Example: To only find PDF files from 3 days ago you could off the option *implicit wildcards* and enter `*.pdf` as keyword to only list pdf files in the results.

By default items are shown in the order they were found. If either min or max age is set, the results will be sorted in chronological order, newest item first.

[[[ https://cloud.githubusercontent.com/assets/1439229/18595328/7c4ce3d2-7c44-11e6-8de3-f9771a007744.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18595328/7c4ce3d2-7c44-11e6-8de3-f9771a007744.png)

## Settings
No extra settings are available as of `v4.4.1`.

### Search locations
The search locations are set automatically by SD Maid depending on what storages are detected.
Without root, all public storages will be searched, this means any primary and secondary storage that is also visible in SD Maids [Overview page](https://github.com/d4rken/sdmaid-public/wiki/Overview). Rooted devices can enable an option to let the search start at `/` (note: `hwvefs`,`proc`,`dev`,`sys` and `acct` are skipped).