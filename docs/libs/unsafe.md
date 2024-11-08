# unsafe

这个API玩家必须开启Allow Unsafe Function才可以使用

### get
```lua
unsafe.get(string url) : string
```
请求Http链接，返回结果

### fetch
```lua
unsafe.fetch(string url) : string
```
加载远程lua，如果成功则返回模块名字，如果失败则返回Failed