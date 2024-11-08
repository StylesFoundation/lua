# Rotation

Rotation是一个用于表达转头的数据对象，你可以使用一行代码创建它，它包含了一些方法用于管理转头
```lua
local yaw = 0
local pitch = 0;
local rotation = client.rotation(yaw,pitch) // 创建

event:apply_rotations(rotation) // 为on_pre_motion传入的Event应用
```

### 方法

|  方法名   | 类型  | 参数  |
|  ----  | ----  | ----  |
|  get_yaw   | float  | void |
|  get_pitch   | float  | void |
|  set_yaw   | void  | float |
|  set_pitch   | void  | float |
|  get_yaw_pitch   | float[]  | void |
|  set_yaw_pitch   | void  | float(yaw), float(pitch) |
|  rotation_with_speed   | [Rotation](rotation.md)  | float(yaw), float(pitch), double(speed) |
|  rotation_with_speed_yaw_only   | [Rotation](rotation.md)  | float(yaw), double(speed) |
|  rotation_with_speed_pitch_only   | [Rotation](rotation.md)  | float(pitch), double(speed) |
