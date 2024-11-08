# entity

Entity API中的第一个参数（int）均为Entity ID

### get_max_health
```lua
entity.get_max_health(int entityId) : float
```
获取一个实体的最大生命值

### set_width
```lua
entity.set_width(int entityID, float width)
```
设置实体宽度

### in_range
```lua
entity.in_range(int entityID, double range) : boolean
```
返回实体是否在指定距离内

### set_health
```lua
entity.set_health(int entityID, float health)
```
设置实体生命值

### rotation_to
```lua
entity.rotation_to(int entityID) : Rotation
```
返回玩家到目标实体的[Rotation](../objects/rotation.md)

### get_health
```lua
entity.get_health(int entityID) : float
```
返回实体生命值

### hurt_time
```lua
entity.hurt_time(int entityID) : int
```
返回实体hurttime

### is_dead_no_hp
```lua
entity.is_dead_no_hp(int entityID) : boolean
```
返回实体是否已经死亡而且没有生命

### is_dead
```lua
entity.is_dead(int entityID) : boolean
```
返回实体是否已经死亡

### is_living_base
```lua
entity.is_living_base(int entityID) : boolean
```
返回实体是否继承`EntityLivingBase`

### is_living
```lua
entity.is_living(int entityID) : boolean
```
返回实体是否继承`EntityLiving`

### is_animal
```lua
entity.is_animal(int entityID) : boolean
```
返回实体是否是动物

### is_mob
```lua
entity.is_mob(int entityID) : boolean
```
返回实体是否是怪物

### is_player
```lua
entity.is_player(int entityID) : boolean
```
返回实体是否是玩家

### is_self
```lua
entity.is_self(int entityID) : boolean
```
返回实体是否是玩家自身

### get_position
```lua
entity.get_position(int entityID) : BlockPos
```
返回实体坐标，以[BlockPos](../objects/blockpos.md)的形式返回

### get_x
```lua
entity.get_x(int entityID) : double
```
返回实体的x坐标

### get_y
```lua
entity.get_y(int entityID) : double
```
返回实体的y坐标

### get_z
```lua
entity.get_z(int entityID) : double
```
返回实体的z坐标

### get_bounding_box
```lua
entity.get_bounding_box(int entityID) : AxisAlignedBoundingBox
```

获取实体碰撞箱，返回[AxisAlignedBoundingBox](../objects/aabb.md)

### absorption
```lua
entity.absorption(int entityID) : int
```
获取实体的伤害吸收值

### inventory
```lua
entity.inventory(int entityId) : ItemTable
```
返回一个[ItemTable](../objects/itemtable.md)

### get_rotation
```lua
entity.get_rotation(int entityId) : Rotation
```
返回实体转头数据，以[Rotation](../objects/rotation.md)形式返回

### is_burning
```lua
entity.is_burning(int entityId) : boolean
```
获取实体是否在燃烧

### is_riding
```lua
entity.is_riding(int entityId) : boolean
```
获取实体是否在骑乘
### is_sneaking
```lua
entity.is_sneaking(int entityId) : boolean
```
获取实体是否在潜行

### is_sprinting
```lua
entity.is_sprinting(int entityId) : boolean
```
获取实体是否在疾跑

### is_blocking
```lua
entity.is_blocking(int entityId) : boolean
```
获取实体是否在格挡

### is_bot
```lua
entity.is_bot(int entityId) : boolean
```
获取实体是否为机器人，完全基于AntiBot的判断，不100%准确，必须开启AntiBot才能返回true

### is_team
```lua
entity.is_team(int entityId) : boolean
```
获取实体是否是队友，非100%准确在所有服务器（仅保证Hypixel准确）

### is_team
```lua
entity.is_team(int entityId) : boolean
```
获取实体是否是队友，非100%准确在所有服务器（仅保证Hypixel准确）

### is_user
```lua
entity.is_user(int entityId) : boolean
```
获取实体是否为Styles用户

### is_friend
```lua
entity.is_friend(int entityId) : boolean
```
获取实体是否为好友

### prev_position
```lua
entity.prev_position(int entityId) : BlockPos
```
返回实体的上一位置，以[BlockPos](../objects/blockpos.md)形式返回

### remove
```lua
entity.remove(int entityId)
```
从世界移除实体

### network
```lua
entity.network(int entityId) : NetworkPlayer
```
获取一个**玩家**的网络游戏信息，以[NetworkPlayer](../objects/netplayer.md)返回

示例返回：
```java
NetworkPlayer{ping=287, name=Darrin900, game_mode=survival}
```

### display_name
```lua
entity.display_name(int entityId) : string
```
获取一个实体的显示名字

### effects
```lua
entity.effects(int entityId) : PotionEffect[]
```

返回一个实体现有的所有药水效果，以[PotionEffect](../objects/effect.md)形式返回

示例：

```lua
function on_enable()
    local list = entity.effects()

    for i = 1, #list do
        local effect = list[i]
        client.print(effect);
    end
end
```

将会输出
```java
PotionEffect{name=potion.moveSpeed, id=1, duration=1769, level=1}
```