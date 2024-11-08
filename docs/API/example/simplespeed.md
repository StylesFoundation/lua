# Simple Speed
```lua
local moveSpeed
local onGround
local shouldBoost
local lastDist

function getName()
	return "Simple Speed"
end

function init_script()
    shouldBoost = false
    lastDist = 0
end

function on_enable()
    -- 防止空指针
    if(client.nullCheck())
    then
        shouldBoost = false
        lastDist = 0
        moveSpeed = player.base_speed()
    end
end

function on_pre_motion(ctx)
    if(player.is_moving())
    then
        lastDist = 1
        if(player.on_ground())
        then
            if(shouldBoost)
            then
                player.jump()
                moveSpeed = moveSpeed * 2.1449999809265137
            else
                moveSpeed = player.base_speed()
            end
        elseif(shouldBoost)
        then
            moveSpeed = lastDist - 0.66 * (lastDist - player.base_speed())
        else
            moveSpeed = lastDist - lastDist/159
        end
        player.set_speed(moveSpeed)
        shouldBoost = player.on_ground()
    end
    -- 必须返回Event
    return ctx
end
```