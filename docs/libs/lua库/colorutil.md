# ColorUtil

### rgb
```lua
local rgb = ColorUtil.rgb(255,255,255)
```

```lua
local ColorUtil = {}

-- 生成RGB颜色的函数
function ColorUtil.rgb(r, g, b)
    -- 确保颜色分量在0到255之间
    r = math.min(255, math.max(0, r))
    g = math.min(255, math.max(0, g))
    b = math.min(255, math.max(0, b))

    -- 构建颜色值
    local color = (r * 256 + g) * 256 + b

    return color
end

-- 导出 ColorUtil 模块
return ColorUtil
```