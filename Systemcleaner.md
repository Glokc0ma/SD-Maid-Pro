# SystemCleaner
The SystemCleaner is purely file/directory based filtering engine in contrast to tools like [AppCleaner](https://github.com/d4rken/sdmaid-public/wiki/Appcleaner) it has no notion of "apps". It scans the whole device and tries to sort found items into different filter based on each items metadata. Each filter specifies criteria that a file has to meet before being placed into that filter. Every item can only be sorted into one filter.

## Filter
A filter specifies a set of rules that a file has to meet before it is sorted into it. SD Maid provides a set of default filters that you can choose from, but you can also import userfilters or create your own filter.

### Empty directories
You may notice that the empty directories filter still shows items despite already running it previously. The reason behind that is that the SystemCleaner only works based on the information an individual file or directory provides. This means that a directory "A" is not empty if contains a directory "B", even if directory "B" is empty. So in constellations such as A/B/C where A only contains B, and B only contains C, you need to do 3 iterations until A is deleted due to be an empty directory.

## UserFilter
You can create your own filter (i.e. a "UserFilter") to target specific files for which SD Maid does offer a default filter. To create a filter open the filter manager, switch to the "User" tab and use the "+" icon. Try to make the filter as specific as possible and **make sure to check what has been sorted into it after a scan** before you start deleting.

**Note** that a file on primary public storage (e.g. internal sdcard) may be reached through multiple pathes. In the following example all pathes may lead to the same file:
* `/sdcard/Strawberry.pdf`
* `/storage/emulated/0/Strawberry.pdf`
* `/mnt/sdcard/Strawberry.pdf`
* `/data/media/0/Strawberry.pdf` (if you are rooted)

SD Maid will not find the file under all of the pathes though. This means that if you create a filter using complete pathes check which path you are using before pulling your hair because a filter is not working. It is recommended to use the path listed in SD Maids [Overview](https://github.com/d4rken/sdmaid-public/wiki/Overview) which is the official path the Android system provides.

A user filter can be be exported as well as imported. The export format for such filter is a `.json` which can also be edited manually with a text editor.