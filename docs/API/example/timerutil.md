# 时间计算

使用[Stopwatch.lua](../../libs/lua库/stopwatch.md)，确保它已经放进libs文件夹

注意，这是是个例子，不能作为脚本加载进Styles

```lua
-- 创建一个Stopwatch对象
local stopwatch = Stopwatch:new()

-- 使用方法
stopwatch:reset()  -- 重置计时器
local elapsed = stopwatch:getElapsedTime()  -- 获取经过的时间（毫秒）
client:print("Elapsed Time: " .. elapsed .. " milliseconds")

local timeLimit = 5000  -- 设置时间限制为5秒
if stopwatch:hasTimeElapsed(timeLimit) then
    client:print("Time limit exceeded!")
end

-- 重置计时器并设置一个特定时间点
local specificTime = os.time() * 1000 - 10000  -- 设置为10秒前的时间点
stopwatch:reset(specificTime)

if stopwatch:hasTimeElapsed(timeLimit) then
    client:print("Time limit exceeded again!")
end

```