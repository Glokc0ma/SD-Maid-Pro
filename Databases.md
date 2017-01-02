# Databases
Databases scans your device for sqlite3 databases. On the found databases it allows you to execute the action [SQLite VACUUM](https://sqlite.org/lang_vacuum.html).

When databases grow in size, additional "pages" are added to it. When the data is deleted, the database does not necessarily shrink in size and the additional (now empty) pages still exist. This features looks for such empty pages and removes them. No data is lost. It will free a small amount of space and slightly speed up database access.

## FAQ
### Some of my database fail to be optimized
It is completely normal that not all databases can be processed by SD Maid. Databases with unknown custom features/options may be skipped or fail to be processed. In these cases it is recommended to exclude them (long press -> select exclude).


[[[ https://cloud.githubusercontent.com/assets/1439229/20381741/0b9cca04-aca9-11e6-9dc9-8f71e45877a0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381741/0b9cca04-aca9-11e6-9dc9-8f71e45877a0.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/20381745/0f07dad0-aca9-11e6-9954-933decf58fe0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381745/0f07dad0-aca9-11e6-9954-933decf58fe0.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/20381747/1018a71a-aca9-11e6-9ef2-3321c6e3a40a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381747/1018a71a-aca9-11e6-9ef2-3321c6e3a40a.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/20381751/129a009c-aca9-11e6-9d7d-8129066945e0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381751/129a009c-aca9-11e6-9d7d-8129066945e0.png)

## Settings
### Search locations
Where SD Maid will look for databases. By default this is alread set to all accessible public (and private if rooted) storages.

### Follow symbolic links
If enabled, SD Maid follows symbolic links while searching for databases. This setting may be of interest to you if SD Maid finds the same database twice or none at all, due to your storage setup (folder-mount, link2sd etc).

### Skip running apps
Some apps don't take kindly to their database being in use by another app. They assume their database was corrupted and recreate it while loosing the previous data. SD Maids default settings prioritize safety over thoroughness and thus databases of running apps are skipped.

Theoretically, improving databases access for those apps that are running should have the most impact (whether you can notice that is a different story), as they are likely to be among your most used apps. Active apps like instant-messenger or email apps are usually the msot problematic. They run often and also react to events, which means there is a high chance that they try to access their database while it's being worked on.

This risk is both higher and lower on unrooted devices. Higher because SD Maid can only kill app services without root permission, and lower because such at risk apps rarely put databases in public storage (and private storage can't be accessed by SD Maid without root).
On rooted devices it's vice versa. SD Maid can SIGSTOP the app process (i.e. freeze it in place) which means it can't unexpectedly start and access the database, but there are also a lot more databases that will be processed.

You would disable this option if you want to maximize the tools effectiveness and are willing to troubleshoot a few app issues. You would use the tool without the option and then add an exclusion for every negatively affected app.

[[[ https://cloud.githubusercontent.com/assets/1439229/20381754/13c4a058-aca9-11e6-964c-72ac04fe93d3.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381754/13c4a058-aca9-11e6-964c-72ac04fe93d3.png)