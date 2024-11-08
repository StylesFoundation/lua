# input

### set_key_down
```lua
input.set_key_down(string name, boolean stage);
```

设置一个按键的状态，仅支持Minecraft内的按键名，支持的按键列表：

- key.attack
- key.use
- key.forward
- key.left
- key.back
- key.right
- key.jump
- key.sneak
- key.sprint
- key.drop
- key.inventory
- key.chat
- key.playerlist
- key.pickItem
- key.command
- key.screenshot
- key.togglePerspective
- key.smoothCamera
- key.streamStartStop
- key.streamPauseUnpause
- key.streamCommercial
- key.streamToggleMic
- key.fullscreen
- key.spectatorOutlines
- key.hotbar.1
- key.hotbar.2
- key.hotbar.3
- key.hotbar.4
- key.hotbar.5
- key.hotbar.6
- key.hotbar.7
- key.hotbar.8
- key.hotbar.9
- key_of.key.zoom

### get_third_person_view_state
```lua
input.get_third_person_view_state() : int
```
获取第三人称状态

### get_scroll
```lua
input.get_scroll() : int
```
获取鼠标DWheel

### is_mouse_down
```lua
input.is_mouse_down(int button) : boolean
```
获取某个鼠标按钮是否被按下，0为左键，1为右键，2为中键

### get_key_name
```lua
input.get_key_name(int keyCode) : string
```
获取某个键盘码的键名字，返回例如RShift

### get_key_number
```lua
input.get_key_number(string name) : int
```
通过键位名返回lwjgl键盘码

### is_key_down
```lua
input.is_key_down(int lwjglKeycode) : boolean
```
获取某个按键是否按下，以下是LWJGL键盘码列表
```java
int KEY_NONE = 0;
int KEY_ESCAPE = 1;
int KEY_1 = 2;
int KEY_2 = 3;
int KEY_3 = 4;
int KEY_4 = 5;
int KEY_5 = 6;
int KEY_6 = 7;
int KEY_7 = 8;
int KEY_8 = 9;
int KEY_9 = 10;
int KEY_0 = 11;
int KEY_MINUS = 12;
int KEY_EQUALS = 13;
int KEY_BACK = 14;
int KEY_TAB = 15;
int KEY_Q = 16;
int KEY_W = 17;
int KEY_E = 18;
int KEY_R = 19;
int KEY_T = 20;
int KEY_Y = 21;
int KEY_U = 22;
int KEY_I = 23;
int KEY_O = 24;
int KEY_P = 25;
int KEY_LBRACKET = 26;
int KEY_RBRACKET = 27;
int KEY_RETURN = 28;
int KEY_LCONTROL = 29;
int KEY_A = 30;
int KEY_S = 31;
int KEY_D = 32;
int KEY_F = 33;
int KEY_G = 34;
int KEY_H = 35;
int KEY_J = 36;
int KEY_K = 37;
int KEY_L = 38;
int KEY_SEMICOLON = 39;
int KEY_APOSTROPHE = 40;
int KEY_GRAVE = 41;
int KEY_LSHIFT = 42;
int KEY_BACKSLASH = 43;
int KEY_Z = 44;
int KEY_X = 45;
int KEY_C = 46;
int KEY_V = 47;
int KEY_B = 48;
int KEY_N = 49;
int KEY_M = 50;
int KEY_COMMA = 51;
int KEY_PERIOD = 52;
int KEY_SLASH = 53;
int KEY_RSHIFT = 54;
int KEY_MULTIPLY = 55;
int KEY_LMENU = 56;
int KEY_SPACE = 57;
int KEY_CAPITAL = 58;
int KEY_F1 = 59;
int KEY_F2 = 60;
int KEY_F3 = 61;
int KEY_F4 = 62;
int KEY_F5 = 63;
int KEY_F6 = 64;
int KEY_F7 = 65;
int KEY_F8 = 66;
int KEY_F9 = 67;
int KEY_F10 = 68;
int KEY_NUMLOCK = 69;
int KEY_SCROLL = 70;
int KEY_NUMPAD7 = 71;
int KEY_NUMPAD8 = 72;
int KEY_NUMPAD9 = 73;
int KEY_SUBTRACT = 74;
int KEY_NUMPAD4 = 75;
int KEY_NUMPAD5 = 76;
int KEY_NUMPAD6 = 77;
int KEY_ADD = 78;
int KEY_NUMPAD1 = 79;
int KEY_NUMPAD2 = 80;
int KEY_NUMPAD3 = 81;
int KEY_NUMPAD0 = 82;
int KEY_DECIMAL = 83;
int KEY_F11 = 87;
int KEY_F12 = 88;
int KEY_F13 = 100;
int KEY_F14 = 101;
int KEY_F15 = 102;
int KEY_F16 = 103;
int KEY_F17 = 104;
int KEY_F18 = 105;
int KEY_KANA = 112;
int KEY_F19 = 113;
int KEY_CONVERT = 121;
int KEY_NOCONVERT = 123;
int KEY_YEN = 125;
int KEY_NUMPADEQUALS = 141;
int KEY_CIRCUMFLEX = 144;
int KEY_AT = 145;
int KEY_COLON = 146;
int KEY_UNDERLINE = 147;
int KEY_KANJI = 148;
int KEY_STOP = 149;
int KEY_AX = 150;
int KEY_UNLABELED = 151;
int KEY_NUMPADENTER = 156;
int KEY_RCONTROL = 157;
int KEY_SECTION = 167;
int KEY_NUMPADCOMMA = 179;
int KEY_DIVIDE = 181;
int KEY_SYSRQ = 183;
int KEY_RMENU = 184;
int KEY_FUNCTION = 196;
int KEY_PAUSE = 197;
int KEY_HOME = 199;
int KEY_UP = 200;
int KEY_PRIOR = 201;
int KEY_LEFT = 203;
int KEY_RIGHT = 205;
int KEY_END = 207;
int KEY_DOWN = 208;
int KEY_NEXT = 209;
int KEY_INSERT = 210;
int KEY_DELETE = 211;
int KEY_CLEAR = 218;
int KEY_LMETA = 219;
/** @deprecated */
int KEY_LWIN = 219;
int KEY_RMETA = 220;
/** @deprecated */
int KEY_RWIN = 220;
int KEY_APPS = 221;
int KEY_POWER = 222;
int KEY_SLEEP = 223;
```