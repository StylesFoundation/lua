# world

### biome
```lua
world.biome() : string
```
获取当前所在的生物群系名

### set_timer
```lua
world.set_timer(float speed)
```
设置全局Timer速度

### livings
```lua
world.livings() : int[]
```
获取当前世界加载的EntityLivingBase实体id列表

### entities
```lua
world.entities() : int[]
```
获取当前世界加载的实体id列表

### timer
```lua
world.timer() : float
```
获取timer速度

### is_single_player
```lua
world.is_single_player() : boolean
```
返回是否是单人游戏

### get_server
```lua
world.get_server() : string
```
返回服务器IP

### block
```lua
world.block(double x, double y, double z) : string
```
获取指定方块位置的方块类型

### get_timer_partial_ticks
```lua
world.get_timer_partial_ticks() : float
```

获取partialTicks

### get_screen_title
```lua
world.get_screen_title() : string
```
获取当前打开的容器标题，如果没有打开则返回`nil`