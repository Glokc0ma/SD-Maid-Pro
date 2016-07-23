# Exclusions
Exclusions exclude items from SD Maids tools.

## Creating exclusions
The easiest way to create an exclusion is to long press the item you want to exclude and then to choose "Exclusion" from the context menu. SD Maid will the creation screen for exclusions prefilled with all necessary information.
Alternatively you can manually create an exclusion by venturing the ExclusionManager, which you can find at the bottom of the navigation drawer.
Note: For a new exclusion to take effect, the tool it should be applied to has to be refreshed.

### Exclusion types
#### Simple
The simple exclusions is the type you get when you create a new exclusion. It matches if the input text contains the exclusion text.
Example: A simple exclusion with the text `/Cake/` would match `/tasty/Cake/Strawberry`.
Matching is case-sensitive.

#### Regex
A regex exclusion allows you to exclude items based on a [regular expression](https://en.wikipedia.org/wiki/Regular_expression). It matches if the regular expression matches the input text.
To switch from simple to regex exclusion, choose the respective option in the toolbar during exclusion creation. 
Note: As exclusions are checked for thousands of files. Many exclusions of this type or inefficient regular expressions can significantly slow down operations. A handy site to play with regular expressions is [regex101](http://regex101.com/).

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

## Default exclusions
SD Maid already comes with a set of default exclusions for items. Some of these are locked, meaning that you can remove them (e.g. SD Maid excluding itself), other can be removed. Only remove default exclusions if you know what you are doing.
Example:
* `com.android.systemui` is a non-locked default exclusion. If the app is running (which the system UI always is) SD Maid has to kill it before working on it. While not critical, killing the system UI can lead to soft-reboot which can lead other apps to malfunction. As the system UI doesn't offer much to do for SD Maid anyways, a default exclusion was added for it.