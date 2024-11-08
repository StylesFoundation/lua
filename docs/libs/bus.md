# bus

bus是一个用于在不同脚本之间传递变量的系统，所有variable均可以在不同lua之间获取

### put_variable
```lua
bus.put_variable(string name, object value);
```

添加一个变量

### has_variable
```lua
bus.has_variable(string name); : boolean
```

判断一个变量是否存在

### delete_variable
```lua
bus.delete_variable(string name);
```

删除一个变量

### get_variable
```lua
bus.get_variable(string name); : object
```

得到一个变量