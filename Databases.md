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
[[[ https://cloud.githubusercontent.com/assets/1439229/20381751/129a009c-aca9-11e6-9d7d-8129066945e0.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381751/129a009c-aca9-11e6-9d7d-8129066945e0.png)

## Settings
### Search locations
Where SD Maid will look for databases. By default this is alread set to all accessible public (and private if rooted) storages.

### Follow symbolic links
If enabled, SD Maid follows symbolic links while searching for databases. This setting may be of interest to you if SD Maid finds the same database twice or none at all, due to your storage setup (folder-mount, link2sd etc).

### Skip running apps
By default, SD Maid will skip running apps to prevent negative side-effects. Some apps don't take kindly to their database being in use by another app, then assume their database was corrupted, causing them to recreate it.
When not skipping running apps, SD Maid will attempt to stop the app before working on it's database.

[[[ https://cloud.githubusercontent.com/assets/1439229/20381754/13c4a058-aca9-11e6-964c-72ac04fe93d3.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20381754/13c4a058-aca9-11e6-964c-72ac04fe93d3.png)