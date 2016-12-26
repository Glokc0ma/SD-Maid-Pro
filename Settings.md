# Settings
## General 

[[[ https://cloud.githubusercontent.com/assets/1439229/20633161/f5d047ea-b343-11e6-9774-b3b06542ccdf.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20633161/f5d047ea-b343-11e6-9774-b3b06542ccdf.png)
[[[ https://cloud.githubusercontent.com/assets/1439229/20633168/f8f03872-b343-11e6-8358-26f0830e8199.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20633168/f8f03872-b343-11e6-8358-26f0830e8199.png)

## Bug reporting

[[[ https://cloud.githubusercontent.com/assets/1439229/20633171/fcb1d326-b343-11e6-9c78-9402fcc3e8a5.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20633171/fcb1d326-b343-11e6-9c78-9402fcc3e8a5.png)

## Advanced settings
Settings affecting core functionality which may not be suited for inexperienced users. Usually you don't need to change these.

### Multithreading
How many actions SD Maid may run simultaneously. Each tool (CorpseFinder, SystemCleaner etc) may only run one task at a time, but multiple tools may run in parallel. This does not translate 1:1 to thread use at just reading the file-system already requires 3-4 threads. Increasing this usually doesn't improve performance as the I/O controller and the kernels I/O scheduler are usually the bottleneck, not the CPU.
Low memory devices may reduce this parameter to reduce SD Maids peak memory usage, because running into memory limits can cause the system to kill SD Maid.

### Experimental features
Some features may have passed an initial beta test, but due to lack of data or being too complicated or just being experimental they have still been hidden within the production release. 

This option is automatically enabled for beta releases.

### Storage access
Allows to view, add or remove storage permissions granted to SD Maid within Androids "Storage access framework". This is related to this [secondary storage setup](https://github.com/d4rken/sdmaid-public/wiki/Setup#secondary-storage-setup).
You usually don't need to do anything, but may use this to manually add a storage permission if you permanently skipped a setup step. Removing a permission here may trigger the setup again during the session. Adding anything here besides the root public storage's has no benefit.

[[[ https://cloud.githubusercontent.com/assets/1439229/20633173/ff674ec0-b343-11e6-8e83-bc30a5fa9d9a.png | height = 300px]]](https://cloud.githubusercontent.com/assets/1439229/20633173/ff674ec0-b343-11e6-8e83-bc30a5fa9d9a.png)