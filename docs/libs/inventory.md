# inventory

### slot
```lua
inventory.slot(int slot) : string
```
获取某个物品slot的名字

### item
```lua
inventory.item(int slot) : ItemStack
```
获取某个物品slot的[ItemStack](../objects/itemstack.md)

### drop
```lua
inventory.drop(int slot)
```
丢弃某个slot的物品

### swap
```lua
inventory.swap(int slot, int slot2)
```
互换两个slot的物品

### click
```lua
inventory.click(int slot)
```
点击某个slot的物品