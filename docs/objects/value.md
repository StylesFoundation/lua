# Value

[Value](/value.md)是用于管理客户端设置的对象

### 方法

|  方法名   | 类型  | 参数  | 描述  |
|  ----  | ----  | ----  | ----  |
|  get_value   | 根据类型  | void |  获取当前的值 | 
|  get_name   | string  | void |  获取value名字 | 
|  get_description   | string  | void |  获取value描述 | 
|  set_description   | void  | string |  设置value描述 | 
|  get_boolean   | boolean  | void |  获取数值，适用于BooleanValue | 
|  set_boolean   | void  | boolean |  设置数值，适用于BooleanValue | 
|  is_mode   | boolean  | void |  返回Value是否是ModeValue | 
|  is_boolean   | boolean  | void |  返回Value是否是BooleanValue | 
|  is_number   | boolean  | void |  返回Value是否是DoubleValue | 
|  is_color   | boolean  | void |  返回Value是否是ColorValue | 
|  is_text   | boolean  | void |  返回Value是否是TextValue | 
|  is_item   | boolean  | void |  返回Value是否是ItemsValue | 
|  is_target   | boolean  | void |  返回Value是否是TargetValue | 
|  is_label   | boolean  | void |  返回Value是否是Label | 
|  set_string   | void  | string |  设置字符串数值，适用于TextValue和ModeValue | 
|  get_modes   | string[]  | void |  获取模式表，适用于ModeValue | 
|  is_current   | boolean  | string |  判断是否为当前Value，适用于ModeValue | 
|  get_string   | string  | void |  获取字符串数值，适用于TextValue和ModeValue | 
|  get_int   | int  | void |  获取int方式数值，适用于DoubleValue | 
|  set_int   | void  | int |  设置int方式数值，适用于DoubleValue | 
|  get_double   | double  | void |  获取double方式数值，适用于DoubleValue | 
|  set_double   | void  | double |  设置double方式数值，适用于DoubleValue | 
|  get_max   | double  | void |  获取最大数值，适用于DoubleValue | 
|  get_min   | double  | void |  获取最小数值，适用于DoubleValue | 
|  get_increment   | double  | void |  获取increment数值，适用于DoubleValue | 
|  set_hue   | void  | int |  设置hue数值，适用于ColorValue | 
|  set_brightness   | void  | int |  设置brightness数值，适用于ColorValue | 
|  set_saturation   | void  | int |  设置saturation数值，适用于ColorValue | 
|  get_hue   | int  | void |  获取hue数值，适用于ColorValue | 
|  get_brightness   | int  | void |  获取brightness数值，适用于ColorValue | 
|  get_saturation   | int  | void |  获取saturation数值，适用于ColorValue | 
|  get_rgb   | int  | void |  获取rgb数值，适用于ColorValue | 
|  set_rgb   | void  | int |  设置rgb数值，适用于ColorValue | 
|  select   | void  | int.. |  选择物品ID，适用于ItemsValue | 
|  edit   | void  | string |  修改标签，适用于Label | 
|  is_valid   | boolean  | int |  返回是否是目标，输入EntityID，适用于TargetValue | 
|  is_checked   | boolean  | string |  返回目标Option是否已勾选，适用于ListValue | 
|  set_checked   | void  | string, boolean |  设置一个option被勾选 | 