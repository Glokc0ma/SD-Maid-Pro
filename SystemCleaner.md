# SystemCleaner
The SystemCleaner is a file/directory based filtering engine. It full fills a task similar to the [AppCleaner](https://github.com/d4rken/sdmaid-public/wiki/Appcleaner) tool, but it has no notion of "apps". It searches the whole device and tries to sort found items into different filter based on each items metadata. The default SystemCleaner filter target expendable files that can't be attributed to a specific app.

[[[ https://cloud.githubusercontent.com/assets/1439229/17000226/c7e6c9bc-4ec1-11e6-8653-e29d2f73a30b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000226/c7e6c9bc-4ec1-11e6-8653-e29d2f73a30b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000299/289a2240-4ec2-11e6-946d-0cf2b03f4918.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000299/289a2240-4ec2-11e6-946d-0cf2b03f4918.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000327/4d3c9254-4ec2-11e6-8b02-4e325c01b47d.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000327/4d3c9254-4ec2-11e6-8b02-4e325c01b47d.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000333/5295df26-4ec2-11e6-8154-342fe3652a37.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000333/5295df26-4ec2-11e6-8154-342fe3652a37.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000337/596a889c-4ec2-11e6-9f66-e6cbe549bb01.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000337/596a889c-4ec2-11e6-9f66-e6cbe549bb01.png)

## Filter
A filter specifies a set of rules that a file has to meet before it is sorted into it. SD Maid provides a set of default filters that you can choose from, but you can also import userfilters or create your own filter.

Each filter has a color icon ranging from green to red. The color gives a rough indication on how important files in that filter may be or how dangerous it would be if SD Maid would make a mistake. It's part of SD Maids motto to provide you with honest information.

Example:
A filter for files from crashed applications may be green because these files are expendable and are created after the app has crashed, which means that it is unlikely to affect a running app. A filter targeting temporary files is likely red, because these are ofte created and used by running apps. Deleting it could lead to an app crashing or not yet saved data being lost.

### Empty directories
You may notice that the empty directories filter still shows items despite already running it previously. The reason behind that is that the SystemCleaner only works based on the information an individual file or directory provides. This means that a directory "A" is not empty if contains a directory "B", even if directory "B" is empty. So in constellations such as A/B/C where A only contains B, and B only contains C, you need to do 3 iterations until A is deleted due to be an empty directory.

[[[ https://cloud.githubusercontent.com/assets/1439229/17000392/99798a46-4ec2-11e6-9ff9-eee0bb04de9f.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000392/99798a46-4ec2-11e6-9ff9-eee0bb04de9f.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000400/a38e41fc-4ec2-11e6-95ca-ca717711a086.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000400/a38e41fc-4ec2-11e6-95ca-ca717711a086.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000401/a3b9a2e8-4ec2-11e6-9648-d92a0ed915ce.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000401/a3b9a2e8-4ec2-11e6-9648-d92a0ed915ce.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000402/a3bbe670-4ec2-11e6-97b1-82b540a58d2b.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000402/a3bbe670-4ec2-11e6-97b1-82b540a58d2b.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000403/a3c4310e-4ec2-11e6-8883-239bea368b55.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000337/596a889c-4ec2-11e6-9f66-e6cbe549bb01.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000404/a3c56402-4ec2-11e6-8f16-96e7100f1d9f.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000404/a3c56402-4ec2-11e6-8f16-96e7100f1d9f.png)

## UserFilter
You can create your own filter (i.e. a "UserFilter") to target specific files for which SD Maid does offer a default filter. To create a filter open the filter manager, switch to the "User" tab and use the "+" icon. Try to make the filter as specific as possible and **make sure to check what has been sorted into it after a scan** before you start deleting.

**Note** that a file on primary public storage (e.g. internal sdcard) may be reached through multiple pathes. In the following example all pathes may lead to the same file:
* `/sdcard/Strawberry.pdf`
* `/storage/emulated/0/Strawberry.pdf`
* `/mnt/sdcard/Strawberry.pdf`
* `/data/media/0/Strawberry.pdf` (if you are rooted)

SD Maid will not find the file under all of the pathes though. This means that if you create a filter using complete pathes check which path you are using before pulling your hair because a filter is not working. It is recommended to use the path listed in SD Maids [Overview](https://github.com/d4rken/sdmaid-public/wiki/Overview) which is the official path the Android system provides.

### Criteria
#### Label
The head line used for the entry. 
* JSON value `label`

#### Description
The entries description. 
* JSON value `description`

#### Identifier
A unique identifier for the filter within SD Maid. If you create this filter from within SD Maid it will automatically be generated for you.
* JSON value `identifier` (Valid values: Needs to end with ".scuf.sdm" (system cleaner user filter sd maid).)

#### Color
A hex color code for the filter. Can currently only be changed by editing the filter file.
* JSON value `color` (Valid values: `#??????`)

#### Root only
Whether SD Maid should show the filter if root is not available. Can currently only be changed by editing the filter file.
* JSON value `rootOnly` (Valid values: `true`,`false`)

#### Target type
If the target should be a file or directory.
* JSON value `targetType` (Valid values: `FILE`,`DIRECTORY`)

#### Location
If the target should be in a specific location on your device.
* JSON array `locations`

Valid values: 
* `SDCARD`, public primary and secondary storage
* `PUBLIC_MEDIA`, Android/media on public primary and secondary storage
* `PUBLIC_DATA`, Android/data on public primary and secondary storage
* `PUBLIC_OBB`, Android/obb on public primary and secondary storage
* `PRIVATE_DATA`, /data/user/0
* `APP_LIB`, /data/app-lib
* `APP_ASEC`, /data/app-asec 
* `APP_APP`, /data/app
* `APP_APP_PRIVATE`, /data/app-private
* `DALVIK_DEX`, /data/dalvik-cache/arm
* `DALVIK_PROFILE`, /data/dalvik-cache/profile
* `DOWNLOAD_CACHE`, /cache
* `DATA`, /data
* `PORTABLE`, USB devices
 
#### Base path
A targets path has to start with one of these entries.
* JSON array `mainPath`

#### Path contains
The targets path has to contain one of these strings
* JSON array `pathContains`

#### Name starts with
The targets name has to start with one of these entries.
* JSON array `possibleNameInits`
   
#### Name ends with
The targets name has to end with one of these entries.
* JSON array `possibleNameEndings`
  
#### Exclusions
The targets path should not contain any of these entries.
* JSON array `exclusions`

#### Maximum size
The maximum size the target is allowed to be in bytes.
* JSON value `maximumSize`

#### Minimum size
The minimum size the target has to be in bytes.
* JSON value `minimumSize`

#### Maximum age
The maximum age the target can be in miliseconds.
* A valid match fulfils `NOW - lastModification =< maximumAge`
* JSON value `minimumAge`

#### Minimum age
The minimum age the target has to be in miliseconds.
* A valid match fulfils `NOW - lastModification >= minimumAge`
* JSON value `minimumAge`


#### Regular expression
A regular expression that will be applied to the whole path and has to match.
* JSON array `regexes`

[[[ https://cloud.githubusercontent.com/assets/1439229/17000496/2223cce4-4ec3-11e6-857b-837f99452205.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000496/2223cce4-4ec3-11e6-857b-837f99452205.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000497/2249845c-4ec3-11e6-8000-8e7c0b59b0e1.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000497/2249845c-4ec3-11e6-8000-8e7c0b59b0e1.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000498/224f3ce4-4ec3-11e6-8070-9e476acaa019.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000498/224f3ce4-4ec3-11e6-8070-9e476acaa019.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000499/22520a0a-4ec3-11e6-854a-73d58a9ee92e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000499/22520a0a-4ec3-11e6-854a-73d58a9ee92e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000500/225af430-4ec3-11e6-819e-5c855f6340ad.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000500/225af430-4ec3-11e6-819e-5c855f6340ad.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000501/225b6ff0-4ec3-11e6-88fe-e9a4381aa3da.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000501/225b6ff0-4ec3-11e6-88fe-e9a4381aa3da.png)

## Export
A user filter can be be exported as well as imported. The export format for such filter is a `.json` which can also be edited manually with a text editor. This is a sample file showing most attributes:

```
{
    "version": 4,
    "label": "Downloaded PDFs",
    "description": "Delete all downloaded PDF files.",
    "identifier": "0ef6d43f4d46.scuf.sdm",
    "color": "#03a9f4",
    "rootOnly": false,
    "targetType": "FILE",
    "locations": [
        "SDCARD"
    ],
    "mainPath": [
        "\/storage\/emulated\/0\/Download\/"
    ],
    "pathContains": [
        "files\/cache"
    ],
    "possibleNameInits": [
        "January"
    ],
    "possibleNameEndings": [
        ".pdf"
    ],
    "exclusions": [
        "important"
    ],
    "maximumSize": 1000000,
    "minimumSize": 100,
    "maximumAge": 86400000,
    "minimumAge": 3600000,
    "regexes": [
        ".+?January.+?.pdf"
    ]
}
```

[[[ https://cloud.githubusercontent.com/assets/1439229/24829195/bfe3f152-1c6d-11e7-8128-d60c734591e1.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/24829195/bfe3f152-1c6d-11e7-8128-d60c734591e1.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/24829196/bfe41b00-1c6d-11e7-8bee-1d18a76367ac.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/24829196/bfe41b00-1c6d-11e7-8bee-1d18a76367ac.png)

## Settings
The system cleaner has no extra settings as of `v4.4.1`.