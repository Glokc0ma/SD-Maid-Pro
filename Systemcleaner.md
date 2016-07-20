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

A user filter can be be exported as well as imported. The export format for such filter is a `.json` which can also be edited manually with a text editor.

[[[ https://cloud.githubusercontent.com/assets/1439229/17000496/2223cce4-4ec3-11e6-857b-837f99452205.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000496/2223cce4-4ec3-11e6-857b-837f99452205.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000497/2249845c-4ec3-11e6-8000-8e7c0b59b0e1.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000497/2249845c-4ec3-11e6-8000-8e7c0b59b0e1.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000498/224f3ce4-4ec3-11e6-8070-9e476acaa019.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000498/224f3ce4-4ec3-11e6-8070-9e476acaa019.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000499/22520a0a-4ec3-11e6-854a-73d58a9ee92e.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000499/22520a0a-4ec3-11e6-854a-73d58a9ee92e.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000500/225af430-4ec3-11e6-819e-5c855f6340ad.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000500/225af430-4ec3-11e6-819e-5c855f6340ad.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/17000501/225b6ff0-4ec3-11e6-88fe-e9a4381aa3da.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/17000501/225b6ff0-4ec3-11e6-88fe-e9a4381aa3da.png)