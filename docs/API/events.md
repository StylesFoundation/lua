# 事件

你需要添加每个小节的名字的方法来监听相关事件，部分事件有参数传入，需要给方法添加参数

### getName

这个方法是一个特殊方法必须定义，返回当前Script Module的名字

### init_script

此事件将在脚本初始化时候调用

### on_key_press

此事件将在玩家按下键盘（游戏内）时调用，传入Keycode 

```lua
function on_key_press(key)
    client.print(key)
end

```

### on_send_packet

此事件将在数据包发送到服务器前调用

|  参数   | 类型  | 描述  |
|  ----  | ----  | ----  |
| id  | int |数据包ID |

这个事件可以通过返回Boolean值取消，下面的代码示范了取消这个事件

```lua
function on_send_packet(id)
    return true;
end
```

### on_receive_packet

此事件将在接收到来自服务器的数据包，客户端处理前调用

|  参数   | 类型  | 描述  |
|  ----  | ----  | ----  |
| id  | int |数据包ID |

同`on_send_packet`这个事件可以通过返回Boolean值取消，下面的代码示范了取消这个事件

```lua
function on_receive_packet(id)
    return true;
end
```

上述的数据包事件所有数据包ID，请查看[支持的数据包类型](packets.md)页面，其他类型的数据包不会经过Event

### on_pre_update

此事件将在本地玩家更新前调用

### on_post_update

此事件将在本地玩家更新后调用

### on_player_move

这个事件将在处理玩家移动时调用，传入事件自身，具有以下方法

|  方法名   | 类型  |
|  ----  | ----  |
| get_x  | double |
| get_y  | double |
| get_z  | double |
| set_x  | void |
| set_y  | void |
| set_z  | void |

set方法传入的参数均为Double，返回event将会应用修改，下面这个示例演示了如何取消所有移动

```lua
function on_player_move(event)
    event:set_x(0)
    event:set_y(0)
    event:set_z(0)
    return event;
end
```

### on_pre_motion

此事件将在游戏向服务器发送位置/转头数据包之前调用，将传入Event自身

|  方法名   | 类型  | 参数  |
|  ----  | ----  | ----  |
|  apply_rotations   | void  | [Rotation](../objects/rotation.md)  |
|  on_ground   | boolean  | void |
|  set_on_ground   | void  | boolean |
|  get_yaw   | float  | void |
|  get_pitch   | float  | void |
|  set_yaw   | void  | float |
|  set_pitch   | void  | float |
| get_x  | double | void |
| get_y  | double | void |
| get_z  | double | void |
| set_x  | void | double |
| set_y  | void | double |
| set_z  | void | double |

返回事件将应用修改，示例：

!!! danger "警告"

    下方的示范代码包含无效的Rotation，可能引起反作弊检测，只是演示代码，切勿使用它进入任何带有反作弊的服务器，否则可能引起回弹甚至封禁

```lua
function on_pre_motion(event)
    if(player.is_moving())
    then
        event:set_pitch(-180);
    end
    return event
end
```

### on_post_motion

此事件将在游戏向服务器发送位置/转头数据包之后调用（没有传入event）

### on_render_world

此事件将在游戏渲染世界时调用（Aka. Render3D）

### on_render_screen

同类型、参数子事件`on_render_bloom`, `on_render_blur`, `on_render_glow

此事件将在游戏渲染HUD时调用，将传入Event自身，无需返回该事件

这个Event包含两个方法

|  方法名   | 类型  | 参数  |
|  ----  | ----  | ----  |
|  partial_ticks   | float  | void  |
|  scaled_resolution   | [ScaledResolution](../objects/scaledresolution.md)  | void  |

监听示例

```lua
function on_render_blur(event)
    -- 绘制模糊
end

function on_render_screen(event)
    -- 获取ScaledResolution
    local sr = event:scaled_resolution()
end
```

### on_pre_attack

此事件将在玩家攻击实体前调用，传入目标的EntityID

### on_post_attack

此事件将在玩家攻击实体后调用，传入目标的EntityID

!!! note "提示"

    KillAura的攻击不会处理这两个event


### on_eagle_move

此事件将在玩家可能需要safewalk时调用

一些群友说这个方法条件写错了，但是其实是因为玩家只要有移动就会调用（并不遵守每秒20tick），返回true即可实现safewalk

### on_tick

此事件将在游戏更新Tick时调用

### on_message_receive

此事件将在玩家接收聊天时调用，传入消息，返回处理过的消息，如果无需修改消息直接返回消息即可

### on_chat

此事件将在玩家发送聊天时调用，传入消息，返回处理过的消息，如果无需修改消息直接返回消息即可

这个示例演示了如何给IRC发送（以#）开头的文字添加自定义颜色代码

```lua
local mode

function getName()
	return "IRCSuffix"
end

function init_script()
    mode = module_manager.register_mode("IRCSuffix","Suffix",{"None","WHITE","RED","GOLD","AQUA"},"WHITE")
end

function on_chat(message)
    if string.sub(message, 1, 1) == "#" then
        local data = string.sub(message, 2)
        local suffix = mode:get_string()

        if suffix == "None" then
            return message
        elseif suffix == "WHITE" then
            return "#&f" .. data
        elseif suffix == "RED" then
            return "#&c" .. data
        elseif suffix == "GOLD" then
            return "#&6" .. data
        elseif suffix == "AQUA" then
            return "#&b" .. data
        end
    end
    return message
end
```


### on_visual_rotation_update

此事件将在更新视觉转头时候调用，不会发包，传入[Rotation](../objects/rotation.md)


示例：
```lua
function on_visual_rotation_update(event)
    if(player.is_moving())
       event:set_pitch(-180);
    return event
end
```

### on_toggle

此事件在玩家开关模块时调用，传入模块名和状态

```lua
function on_module_toggle(module_name,stage)
    client.print(module_name);
    client.print(stage);
end
```

### on_enable

此事件将在当前脚本module打开时调用

### on_disable

此事件将在当前脚本module禁用时调用