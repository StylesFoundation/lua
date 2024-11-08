# util

### parse_json
```lua
util.parse_json(string json) : JsonObject
```
解析Json，返回[JsonObject](https://www.javadoc.io/doc/com.google.code.gson/gson/latest/com.google.gson/com/google/gson/JsonObject.html)

### get_hwid
```lua
util.get_hwid(string hashKey) : string
```
生成hwid，hashKey随便填 

## 文件操作

所有文件操作的根目录为客户端的数据目录，也就是`C:\Users\%USERNAME%\Styles\data`文件夹

### create_file
```lua
util.create_file(string name)
```
创建文件

### exists
```lua
util.exists(string name) : boolean
```
返回一个文件是否存在，支持判断文件和文件夹

### read_file
```lua
util.read_file(string name) : string
```
阅读文本，返回文件内容，如果文本不存在返回空字符串

### write_file
```lua
util.write_file(string name, string contents)
```
向指定文本文件写入文本

### create_directory
```lua
util.create_directory(string name)
```
创建文件夹