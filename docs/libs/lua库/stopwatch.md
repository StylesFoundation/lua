# Stopwatch

一个时间计算lua

### new
```lua
local stopwatch = Stopwatch:new()
```
创建一个Stopwatch对象

### hasTimeElapsed
```lua
stopwatch:hasTimeElapsed(long ms) : boolean
```
返回是否已经到达时间，单位毫秒
### hasTimeElapsedRest
```lua
stopwatch:hasTimeElapsedRest(long ms, boolean reset) : boolean
```
返回是否已经到达时间，单位毫秒
### getElapsedTime
```lua
stopwatch:getElapsedTime() : long
```
返回时间
### reset
```lua
stopwatch:reset()
```
重置

```lua
Stopwatch = {}
Stopwatch.__index = Stopwatch

function Stopwatch:new()
    local self = setmetatable({}, Stopwatch)
    self.lastMS = os.time() * 1000
    return self
end

function Stopwatch:hasTimeElapsed(time)
    return os.time() * 1000 - self.lastMS > time
end

function Stopwatch:hasTimeElapsedRest(time, reset)
    if self:hasTimeElapsed(time) then
        if reset then
            self:reset()
        end
        return true
    end
    return false
end

function Stopwatch:getElapsedTime()
    return os.time() * 1000 - self.lastMS
end

function Stopwatch:reset()
    self.lastMS = os.time() * 1000
end

function Stopwatch:reset(time)
    self.lastMS = time
end
```