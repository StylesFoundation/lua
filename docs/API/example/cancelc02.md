# Cancel C02
```lua
function getName()
	return "Cancel C02"
end

function init_script()
end

function on_send_packet(id)
    if (id == 0x02)
    then
        return true
    end
    return false
end
```