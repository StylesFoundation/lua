# module_manager

管理客户端模块的API，所有模块名字均不分大小写

## Module

### get_modules
```lua
module_manager.get_modules() : string[]
```
返回一个包含所有module名字的table

### get_key
```lua
module_manager.get_key(string name) : int
```
返回一个module绑定的按键码

### get_category
```lua
module_manager.get_category(string name) : string
```
返回一个module类型

### get_suffix
```lua
module_manager.get_suffix(string name) : string
```
返回一个module的后缀


### enable
```lua
module_manager.enable(string name)
```
启用一个指定名称的Module

### disable
```lua
module_manager.disable(string name)
```
禁用一个指定名称的Module

### get_state
```lua
module_manager.get_state(string name) : boolean
```
获取一个指定Module是否存在

### set_state
```lua
module_manager.set_state(string name, boolean enable)
```
设置一个Module开关

### get_description
```lua
module_manager.get_description(string name) : string
```
获取一个module的描述

### set_description
```lua
module_manager.set_description(string name, string description)
```
设置一个module的描述

### set_suffix
```lua
module_manager.set_suffix(string name, string suffix);
```

设置一个模块的后缀

## Value

[Value](../objects/value.md)是用于管理客户端设置的对象，valueAPI允许你为任意module注册参数

### register_label
```lua
module_manager.register_label(string moduleName, string name) : Value
```
注册一个Label，返回Value自身

### register_boolean
```lua
module_manager.register_boolean(string moduleName, string name, boolean enable) : Value
```
注册一个BooleanValue，返回Value自身

### register_number
```lua
module_manager.register_number(string moduleName, string name, double value, double minimum, double maximum, double increment) : Value
```
注册一个DoubleValue，返回Value自身

### register_mode
```lua
module_manager.register_mode(string moduleName, string name, string[] modes, string value) : Value
```
注册一个ModeValue，返回Value自身，示例：
```lua
local mode = module_manager.register_mode("IRCSuffix","Suffix",{"None","WHITE","RED","GOLD","AQUA"},"WHITE")
```

### register_list
```lua
module_manager.register_list(string moduleName, string name, string[] options) : Value
```
注册一个ListValue，返回Value自身

### register_target
```lua
module_manager.register_target(string moduleName, string name) : Value
```
注册一个TargetValue，返回自身

### register_label
```lua
module_manager.register_label(string moduleName, string name) : Value
```
注册一个Label，返回Value自身

### register_item
```lua
module_manager.item(string moduleName, string name) : Value
```
注册一个ItemsValue，返回Value自身

!!! warning "警告"

    TextValue的`value`参数不可以为空，如果希望用户自己输入，请填写`""`

### register_color
```lua
module_manager.register_color(string moduleName, string name, int rgb) : Value
```

注册一个ColorValue，返回Value自身