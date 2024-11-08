# player

### prev_position
```lua
player.prev_position() : BlockPos
```
返回玩家的上一位置，以[BlockPos](../objects/blockpos.md)形式返回

### set_position
```lua
player.set_position(double x, double y, double z)
```
设置玩家位置

### create_position
```lua
player.create_position(double x, double y, double z) : BlockPos
```
创建一个[BlockPos](../objects/blockpos.md)对象

### set_position
```lua
player.set_position(double x, double y, double z)
```
设置玩家位置

### set_motion
```lua
player.set_motion(double motionX, double motionY, double motionZ)
```
设置玩家Motion

### motion
```lua
player.motion() : BlockPos
```
返回玩家玩家的Motion x y z，以[BlockPos](../objects/blockpos.md)形式返回

### position
```lua
player.position() : BlockPos
```
返回玩家玩家的坐标，以[BlockPos](../objects/blockpos.md)形式返回

### moveInput
```lua
player.moveInput() : MovementInput
```
返回玩家玩家的MovementInput，以[MovementInput](../objects/movementinput.md)形式返回

### message
```lua
player.message(string message)
```
让玩家发送消息

### right_click_mouse
```lua
player.right_click_mouse()
```
点击右键

### click_mouse
```lua
player.click_mouse()
```
点击左键

### jump
```lua
player.jump()
```
跳跃

### set_sprinting
```lua
player.set_sprinting(boolean sprint)
```
设置疾跑状态

### distance_to
```lua
player.distance_to(double x, double y, double z) : double
```
获取玩家到指定位置的距离

### distance_to_entity
```lua
player.distance_to_entity(int entityID) : double
```
获取玩家到指定实体的距离

### send0x0A
```lua
player.send0x0A()
```
发送`C0APacketAnimation`

### send0x07
```lua
player.send0x07(string action, string facing, BlockPos position)
```
发送`C07PacketPlayerDigging`，传入Action，Facing和[BlockPos](../objects/blockpos.md)，BlockPos可以使用`create_position`方法创建

Action可以填写以下字符串之一

```lua
START_DESTROY_BLOCK // 开始破坏
ABORT_DESTROY_BLOCK // 取消破坏
STOP_DESTROY_BLOCK // 停止破坏
DROP_ALL_ITEMS // 丢弃所有物品
DROP_ITEM // 丢弃物品
RELEASE_USE_ITEM // 释放使用
SWAP_HELD_ITEMS // 切换手持物品
```

Facing可以填写以下字符串之一

```lua
DOWN
UP
EAST
WEST
SOUTH
NORTH
```

### send0x08
```lua
player.send0x08(ItemStack stack)
```
发送`C08PacketPlayerBlockPlacement`，传入[ItemStack](../objects/itemstack.md)

### send0x0B
```lua
player.send0x0B(string action)
```
发送`C0BPacketEntityAction`，传入Action

Action可以填写以下字符串之一
```lua
START_SNEAKING // 开始潜行
STOP_SNEAKING // 停止潜行
STOP_SLEEPING // 停止睡觉
START_SPRINTING // 开始疾跑
STOP_SPRINTING // 停止疾跑
RIDING_JUMP // 骑行生物跳跃
OPEN_INVENTORY // 打开物品栏
```

### send0x03
```lua
player.send0x03(boolean onGround)
```
发送`C03PacketPlayer`，传入OnGround

### send0x09
```lua
player.send0x09(int slot)
```
发送`C09PacketHeldItemChange`，传入slot id

### send0x0d
```lua
player.send0x0d(int windowId)
```
发送`C0DPacketCloseWindow`，传入window Id

### send0x04
```lua
player.send0x04(double x, double y, double z, boolean onGround)
```
发送`C04PacketPlayerPosition`，传入坐标和OnGround

### send0x05
```lua
player.send0x05(float yaw, float pitch, boolean onGround)
```
发送`C05PacketPlayerLook`，传入转头信息和OnGround

### angles
```lua
player.angles() : Rotation
```
返回玩家转头数据，以[Rotation](../objects/rotation.md)形式返回

### prev_angles
```lua
player.prev_angles() : Rotation
```
返回玩家上一Tick转头数据，以[Rotation](../objects/rotation.md)形式返回

### set_angles
```lua
player.set_angles(float yaw, float pitch)
```
设置玩家yaw pitch

### apply_angles
```lua
player.apply_angles(Rotation rotation)
```
设置玩家转头，应用[Rotation](../objects/rotation.md)中的数据

### using_item
```lua
player.using_item() : boolean
```
返回玩家是否在使用物品，例如吃东西或者格挡

### swing_item
```lua
player.swing_item()
```
让玩家发送挥手

### use_item
```lua
player.use_item()
```
让玩家发送使用物品

### held_item
```lua
player.held_item() : ItemStack
```
返回玩家手持物品的[ItemStack](../objects/itemstack.md)

### id
```lua
player.id() : int
```
返回玩家的Entity ID

### health
```lua
player.health() : float
```
返回玩家的生命值

### fall_distance
```lua
player.fall_distance() : float
```
返回玩家的掉落距离

### max_health
```lua
player.max_health() : float
```
返回玩家的最大生命值

### name
```lua
player.name() : string
```
返回玩家的名字

### base_speed
```lua
player.base_speed() : double
```
返回基础速度

### held_item_slot
```lua
player.held_item_slot() : int
```
返回玩家手持物品格子编号

### set_held_item_slot
```lua
player.set_held_item_slot(int slot)
```
设置玩家手持物品格子编号

### hurt_time
```lua
player.hurt_time() : int
```
返回玩家受伤间隔

### food_stats
```lua
player.food_stats() : int
```
返回玩家饱食度

### absorption
```lua
player.absorption() : float
```
返回玩家金生命值

### eye_height
```lua
player.eye_height() : float
```
返回玩家眼睛高度

### facing
```lua
player.facing() : string
```
返回玩家Facing名，返回以下其中一个
```lua
DOWN
UP
EAST
WEST
SOUTH
NORTH
```

### over_mouse
```lua
player.over_mouse() : int
```

返回玩家准星瞄准的类型，什么都没瞄准返回`1`，实体返回他的Entity ID，其他返回`-1`

### over_mouse
```lua
player.over_mouse() : int
```

返回玩家准星瞄准的类型，什么都没瞄准返回`1`，实体返回他的Entity ID，其他返回`-1`

### convert_speed
```lua
player.convert_speed(MoveEvent event, double speed)
```

设置MoveEvent的Speed，关于MoveEvent，请查看[Events](../API/events.md)中的`on_player_move`

### kill_aura_target
```lua
player.kill_aura_target() : int 
```
返回KillAura目标的Entity ID，如果没目标返回0

### kill_aura_targets
```lua
player.kill_aura_targets() : int[]
```
返回KillAura所有目标的Entity ID表，适用于Multi或Switch模式

### on_ground
```lua
player.on_ground() : boolean
```
返回玩家是否在地面上

### is_blocking
```lua
player.is_blocking() : boolean
```
返回玩家是否在格挡

### is_in_water
```lua
player.is_in_water() : boolean
```
返回玩家是否在水里

### is_in_lava
```lua
player.is_in_lava() : boolean
```
返回玩家是否在岩浆里

### burning
```lua
player.burning() : boolean
```
返回玩家是否在燃烧

### is_sneaking
```lua
player.is_sneaking() : boolean
```
返回玩家是否在潜行

### set_sneaking
```lua
player.set_sneaking(boolean sneak)
```

设置玩家潜行状态
### is_in_cobweb
```lua
player.is_in_cobweb() : boolean
```

返回玩家是否在蜘蛛网里

### angles_for_cords
```lua
player.angles_for_cords(double x, double y, double z) : Rotation
```

获取[Rotation](../objects/rotation.md)到某个指定坐标

### dead
```lua
player.dead() : boolean
```
返回玩家是否已死亡

### sprinting
```lua
player.sprinting() : boolean
```
返回玩家是否在疾跑

### riding
```lua
player.riding() : boolean
```
返回玩家是否在骑行

### on_ladder
```lua
player.on_ladder() : boolean
```
返回玩家是否在梯子上

### collided_vertically
```lua
player.collided_vertically() : boolean
```
返回玩家是否垂直在和方块碰撞

### collided_horizontally
```lua
player.collided_horizontally() : boolean
```
返回玩家是否水平在和方块碰撞

### is_potion_active
```lua
player.is_potion_active(int id) : boolean
```
返回玩家是否有某种药水效果

### ticks_existed
```lua
player.ticks_existed() : int
```
返回玩家存在的Ticks

### place_block
```lua
player.place_block(int slot, BlockPos pos, string facing, BlockPos Vec) : boolean
```
放置方块，返回是否成功

facing可以填写以下字符串中的一个
```lua
DOWN
UP
EAST
WEST
SOUTH
NORTH
```

### is_moving
```lua
player.is_moving() : boolean
```
返回玩家是否在移动

### is_on_edge
```lua
player.is_on_edge() : boolean
```
返回玩家是否在方块边缘

### get_speed
```lua
player.get_speed() : double
```
返回玩家的当前速度

### set_speed
```lua
player.set_speed(double speed)
```
设置玩家速度

### send0x02
```lua
player.send0x02(int entityID, string action)
```
发送`C02PacketUseEntity`，第一个参数填写目标实体的ID，第二个填写Action

Action可以填写以下字符串中的任意一个
```lua
INTERACT
ATTACK
INTERACT_AT
```

### is_in_void
```lua
player.is_in_void() : boolean
```
返回玩家是否在虚空中

### is_third_person_view
```lua
player.is_third_person_view() : boolean
```
返回玩家是否为第三人称视角

### set_fall_distance
```lua
player.set_fall_distance(float distance)
```
设置掉落距离

### food
```lua
player.food() : int
```
返回当前饱食度

### send_message
```lua
player.send_message(string message)
```
让玩家发送信息

### inventory
```lua
player.inventory() : ItemTable
```
返回一个[ItemTable](../objects/itemtable.md)