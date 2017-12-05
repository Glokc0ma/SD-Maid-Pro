# Exclusions
Exclusions exclude items from SD Maids tools.

## Creating exclusions
Note: For a new exclusion to take effect, the tool it should be applied to has to be refreshed.

### Directly from results
The easiest way to create an exclusion is to long press the item you want to exclude, in the tool where you don't want to see it again. Select it and choose "Exclusion" from the context menu. SD Maid will fill in all necessary details.

[[[ https://cloud.githubusercontent.com/assets/1439229/18717055/09aa5498-801f-11e6-97ad-8485379c8b4e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18717055/09aa5498-801f-11e6-97ad-8485379c8b4e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18717226/9527dba8-801f-11e6-9e8f-420eec3f0e4a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18717226/9527dba8-801f-11e6-9e8f-420eec3f0e4a.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/18717283/b914d5c0-801f-11e6-9dcc-87cc5dce8985.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/18717283/b914d5c0-801f-11e6-9dcc-87cc5dce8985.png)

### By browsing to it
You can do the same through locating the file in SD Maids [Explorer](https://github.com/d4rken/sdmaid-public/wiki/Explorer), which also offers such an action when selecting a file. Note that SD Maid will make it a **global exclusion** if you don't change it.

[[[ https://cloud.githubusercontent.com/assets/1439229/17080573/57bf10b0-5135-11e6-8ed5-9aeb519aafec.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080573/57bf10b0-5135-11e6-8ed5-9aeb519aafec.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17080574/63a98a9a-5135-11e6-8682-cc2f9462698c.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080574/63a98a9a-5135-11e6-8682-cc2f9462698c.png)

### Manually
 Alternatively you can manually create an exclusion by venturing the ExclusionManager, which you can find at the bottom of the navigation drawer.

[[[ https://cloud.githubusercontent.com/assets/1439229/17080579/8078c528-5135-11e6-878c-0180743520f8.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080579/8078c528-5135-11e6-878c-0180743520f8.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17080592/b3d69fda-5135-11e6-933d-bb7177812068.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080592/b3d69fda-5135-11e6-933d-bb7177812068.png)

### Exclusion types
#### Simple
The simple exclusions is the type you get when you create a new exclusion. It matches if the input text contains the exclusion text.
Example: A simple exclusion with the text `/Cake/` would match `/tasty/Cake/Strawberry`.
Matching is case-sensitive.

#### Regex
A regex exclusion allows you to exclude items based on a [regular expression](https://en.wikipedia.org/wiki/Regular_expression). It matches if the regular expression matches the input text.
To switch from simple to regex exclusion, choose the respective option in the toolbar during exclusion creation. 
Note: As exclusions are checked for thousands of files. Many exclusions of this type or inefficient regular expressions can significantly slow down operations. A handy site to play with regular expressions is [regex101](http://regex101.com/).

[[[ https://cloud.githubusercontent.com/assets/1439229/17080594/c4afa0c2-5135-11e6-920d-e12da9ac0270.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080594/c4afa0c2-5135-11e6-920d-e12da9ac0270.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17080596/cae45ce4-5135-11e6-95a2-197c76e9cfbd.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080596/cae45ce4-5135-11e6-95a2-197c76e9cfbd.png)

## Modifying exclusions
Exclusions can be deleted or modified by tapping an entry in the ExclusionManager or by trying to create an exclusion that matches an already existing exclusion.
Note: For changed exclusions to take effect, the tool it should be applied to has to be refreshed.

## Effect on tools
Exclusions are applied during the SCAN phase of each tool. If modified your exclusions you have to refresh the tools data in order for the new exclusions to take effect. How an exclusion takes effect depends on the tool:
* Searcher: Applied to each items _filepath_
* AppControl: Applied to each apps _packagename_ and _appname_
* CorpseFinder: Applied to each items _filepath_
* SystemCleaner: Applied to each items _filepath_
* AppCleaner: Applied to each items _filepath_, _packagename_ and _appname_
* Duplicates: Applied to each items _filepath_
* Databases: Applied to each files _filepath_ and _packagename
* LastModified: Applied to each items _filepath_

## Importing/Exporting
Exclusions can be imported/exported in form of JSON files. Each file may hold multiple exclusions.
Format example:
```
{
    "version": 4,
    "exclusions": [
        {
            "type": "SIMPLE_CONTAINS",
            "tags": [
                "SYSTEMCLEANER",
                "APPCLEANER",
                "DATABASES"
            ],
            "contains_string": "com.android.systemui"
        },
        {
            "type": "REGEX",
            "tags": [
                "SYSTEMCLEANER",
                "APPCLEANER",
                "DATABASES"
            ],
            "regex_string": "^(?>eu\\.thedarken\\.sdm)$"
        }
    ]
}
```

[[[ https://cloud.githubusercontent.com/assets/1439229/17080606/fd4e199a-5135-11e6-8271-bacacc8698d0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080606/fd4e199a-5135-11e6-8271-bacacc8698d0.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17080609/0949717c-5136-11e6-8f0a-7415e2823df5.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080609/0949717c-5136-11e6-8f0a-7415e2823df5.png)

## Default exclusions
SD Maid already comes with a set of default exclusions for items. Some of these are locked, meaning that you can remove them (e.g. SD Maid excluding itself), other can be removed. Only remove default exclusions if you know what you are doing.
Example:
* `com.android.systemui` is a non-locked default exclusion. If the app is running (which the system UI always is) SD Maid has to kill it before working on it. While not critical, killing the system UI can lead to soft-reboot which can lead other apps to malfunction. As the system UI doesn't offer much to do for SD Maid anyways, a default exclusion was added for it.

[[[ https://cloud.githubusercontent.com/assets/1439229/17080612/14331caa-5136-11e6-884b-daada890c539.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17080612/14331caa-5136-11e6-884b-daada890c539.png)

## FAQ
### Exclusions & AppCleaner on unrooted devices
See [AppCleaner without Root `freestoryAndNotify`](https://github.com/d4rken/sdmaid-public/wiki/AppCleaner#some-appcleaner-exclusions-dont-work-without-root).