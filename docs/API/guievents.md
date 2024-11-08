# Gui
Styles提供了接口允许使用脚本实现Gui，只需要实现不同的方法即可，这是一个示例
```lua
function getName()
	return "Example Gui"
end

function init_script()
end

function on_enable()
    client.display_gui_screen() -- 打开模块时显示这个脚本的UI
    module_manager.set_state(getName()) -- 关闭脚本
end

-- 实现draw_screen
function draw_screen(mouseX,mouseY,renderTicks)
    render.string("Hello World!",mouseX,mouseY,-1,true)
end
```

### init_gui

此事件将在初始化Gui时调用（每次显示GUI）

### draw_screen

```lua
function draw_screen(mouseX,mouseY,renderTicks)
```

渲染UI时调用

### key_typed

```lua
function key_typed(typedChar,keyCode)
```

按下键盘时调用

### mouse_click_move

```lua
function mouse_click_move(mouseX,mouseY,clickedMouseButton,timeSinceLastClick)
```

鼠标按下拖拽时调用

### mouse_clicked

```lua
function mouse_clicked(mouseX,mouseY,button)
```

鼠标点击时调用

### mouse_released

```lua
function mouse_released(mouseX,mouseY,state)
```

鼠标释放时调用

### handle_mouse_input

```lua
function handle_mouse_input()
```

处理鼠标时调用

### update_screen

```lua
function update_screen()
```

更新UI时调用

### on_gui_closed

```lua
function on_gui_closed()
```

UI关闭时调用