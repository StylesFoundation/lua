# Lua五分钟指南

翻译自 https://learnxinyminutes.com/docs/lua/

```lua
-- 两个短横线开头表示一行注释。

--[[
     添加两个['s和]'s使其成为
     多行注释。
--]]

----------------------------------------------------
-- 1. 变量和流程控制。
----------------------------------------------------

num = 42  -- 所有数字都是双精度浮点数。
-- 别担心，64位双精度浮点数具有52位用于
-- 存储精确的整数值；机器精度对于需要<52位的整数来说
-- 不是问题。

s = 'walternate'  -- 不可变字符串，类似于Python。
t = "双引号也可以"
u = [[ 双方括号
       开始和结束
       多行字符串。]]
t = nil  -- 取消定义t；Lua具有垃圾回收。

-- 使用关键字do/end来表示代码块：
while num < 50 do
  num = num + 1  -- 没有++或+=类型的运算符。
end

-- 条件语句：
if num > 40 then
  print('超过40')
elseif s ~= 'walternate' then  -- ~= 表示不等于。
  -- 相等检查使用==，类似于Python；适用于字符串。
  io.write('不超过40\n')  -- 默认为标准输出。
else
  -- 变量默认是全局的。
  thisIsGlobal = 5  -- 骆驼命名法很常见。

  -- 如何使变量成为局部的：
  local line = io.read()  -- 读取下一行标准输入。

  -- 字符串连接使用..运算符：
  print('冬天要来了，' .. line)
end

-- 未定义的变量返回nil。
-- 这不是一个错误：
foo = anUnknownVariable  -- 现在foo = nil。

aBoolValue = false

-- 只有nil和false是假值；0和''为真！
if not aBoolValue then print('它是假的') end

-- 'or'和'and'是短路逻辑运算符。
-- 这类似于C/js中的a?b:c运算符：
ans = aBoolValue and '是的' or '否'  --> '否'

karlSum = 0
for i = 1, 100 do  -- 范围包括两端。
  karlSum = karlSum + i
end

-- 使用"100, 1, -1"作为范围来倒数：
fredSum = 0
for j = 100, 1, -1 do fredSum = fredSum + j end

-- 通常情况下，范围是begin, end[, step]。

-- 另一个循环构造：
repeat
  print('未来的方式')
  num = num - 1
until num == 0

----------------------------------------------------
-- 2. 函数。
----------------------------------------------------

function fib(n)
  if n < 2 then return 1 end
  return fib(n - 2) + fib(n - 1)
end

-- 闭包和匿名函数是可以的：
function adder(x)
  -- 返回的函数在调用adder时创建，
  -- 并记住了x的值：
  return function (y) return x + y end
end
a1 = adder(9)
a2 = adder(36)
print(a1(16))  --> 25
print(a2(64))  --> 100

-- 返回值、函数调用和赋值都可以使用
-- 长度不匹配的列表，未匹配的接收者是nil；
-- 未匹配的发送者被丢弃。

x, y, z = 1, 2, 3, 4
-- 现在x = 1，y = 2，z = 3，4被丢弃。

function bar(a, b, c)
  print(a, b, c)
  return 4, 8, 15, 16, 23, 42
end

x, y = bar('zaphod')  --> 打印 "zaphod  nil nil"
-- 现在x = 4，y = 8，值15...42被丢弃。

-- 函数是一等公民，可以是局部/全局的。
-- 这两者是相同的：
function f(x) return x * x end
f = function (x) return x * x end

-- 这两者也是相同的：
local function g(x) return math.sin(x) end
local g; g  = function (x) return math.sin(x) end
-- 'local g'声明使g的自我引用有效。

-- 顺便说一下，三角函数在弧度中工作。

-- 具有一个字符串参数的调用不需要括号：
print '你好'  -- 可以正常工作。

----------------------------------------------------
-- 3. 表。
----------------------------------------------------

-- 表 = Lua的唯一复合数据结构；
-- 它们是关联数组。
-- 类似于php数组或js对象，它们是
-- 哈希查找字典，也可以用作列表。

-- 将表用作字典/映射时：

-- 字典字面量默认具有字符串键：
t = {key1 = 'value1', key2 = false}

-- 字符串键可以使用类似js的点表示法：
print(t.key1)  -- 打印 'value1'。
t.newKey = {}  -- 添加新的键/值对。
t.key2 = nil   -- 从表中删除key2。

-- 任何（非nil）值的字面量表示法：
u = {['@!#'] = 'qbert', [{}] = 1729, [6.28] = 'tau'}
print(u[6.28])  -- 打印 "tau"

-- 对于数字和字符串，键匹配基本上是按值进行的
-- 但对于表来说是按标识进行的。
a = u['@!#']  -- 现在a = 'qbert'。
b = u[{}]     -- 我们可能期望1729，但实际是nil：
-- b = nil，因为查找失败。它失败
-- 是因为我们使用的键与用于存储原始值的键
-- 不是同一个对象。所以
-- 字符串和数字更适用于键。

-- 调用一个表参数的函数不需要括号：
function h(x) print(x.key1) end
h{key1 = 'Sonmi~451'}  -- 打印 'Sonmi~451'。

for key, val in pairs(u) do  -- 表迭代。
  print(key, val)
end

-- _G是所有全局变量的特殊表。
print(_G['_G'] == _G)  -- 打印 'true'。

-- 使用表作为列表/数组时：

-- 列表字面量隐式设置了整数键：
v = {'value1', 'value2', 1.21, 'gigawatts'}
for i = 1, #v do  -- #v表示列表的大小。
  print(v[i])  -- 索引从1开始！！非常疯狂！
end
-- '列表'不是一个真正的类型。v只是一个表，
-- 具有连续的整数键，被视为一个列表。

----------------------------------------------------
-- 3.1 元表和元方法。
----------------------------------------------------

-- 表可以具有元表，元表提供表的运算符重载行为。稍后我们将看到
-- 元表支持js原型行为。

f1 = {a = 1, b = 2}  -- 表示分数 a/b。
f2 = {a = 2, b = 3}

-- 这将失败：
-- s = f1 + f2

metafraction = {}
function metafraction.__add(f1, f2)
  sum = {}
  sum.b = f1.b * f2.b
  sum.a = f1.a * f2.b + f2.a * f1.b
  return sum
end

setmetatable(f1, metafraction)
setmetatable(f2, metafraction)

s = f1 + f2  -- 在f1的元表上调用__add(f1, f2)

-- f1, f2没有元表的键，不同于
-- js中的原型，所以必须像这样检索它getmetatable(f1)。元表是一个正常的表
-- 具有Lua了解的键，如__add。

-- 但是下一行会失败，因为s没有元表：
-- t = s + s
-- 下面的类似模式将修复这个问题。

-- 在元表上重载点查找的__index：
defaultFavs = {animal = 'gru', food = 'donuts'}
myFavs = {food = 'pizza'}
setmetatable(myFavs, {__index = defaultFavs})
eatenBy = myFavs.animal  -- 成功！谢谢，元表

-- 直接表查找失败时将使用元表的__index值进行重试，这会递归进行。

-- __index值也可以是一个函数(tbl, key)
-- 以进行更自定义的查找。

-- __index,add等的值称为元方法。
-- 完整列表。在此a是一个具有元方法的表。

-- __add(a, b)                     用于a + b
-- __sub(a, b)                     用于a - b
-- __mul(a, b)                     用于a * b
-- __div(a, b)                     用于a / b
-- __mod(a, b)                     用于a % b
-- __pow(a, b)                     用于a ^ b
-- __unm(a)                        用于-a
-- __concat(a, b)                  用于a .. b
-- __len(a)                        用于#a
-- __eq(a, b)                      用于a == b
-- __lt(a, b)                      用于a < b
-- __le(a, b)                      用于a <= b
-- __index(a, b)  <fn or a table>  用于a.b
-- __newindex(a, b, c)             用于a.b = c
-- __call(a, ...)                  用于a(...)

----------------------------------------------------
-- 3.2 类似类的表和继承。
----------------------------------------------------

-- 类并不是内置的；可以使用不同的方式
-- 使用表和元表来创建它们。

-- 以下是此示例的解释：

Dog = {}                                   -- 1.

function Dog:new()                         -- 2.
  newObj = {sound = 'woof'}                -- 3.
  self.__index = self                      -- 4.
  return setmetatable(newObj, self)        -- 5.
end

function Dog:makeSound()                   -- 6.
  print('我说 ' .. self.sound)
end

mrDog = Dog:new()                          -- 7.
mrDog:makeSound()  -- '我说woof'         -- 8.

-- 1. Dog充当类；实际上是一个表。
-- 2. 函数tablename:fn(...)与
--    函数tablename.fn(self, ...)相同
--    冒号只是添加了一个名为self的第一个参数。
--    请查看下面的7和8，了解self如何获得其值。
-- 3. newObj将成为类Dog的一个实例。
-- 4. self = 正在实例化的类。通常
--    self = Dog，但继承可以更改它。
--    当我们同时设置newObj的元表和self的__index为self时，
--    newObj获得了self的函数。
-- 5. 提示：setmetatable返回其第一个参数。
-- 6. 冒号在2中的功能与上述2中相同，但这次我们期望
--    self是一个实例，而不是一个类。
-- 7. 与Dog.new(Dog)相同，因此self = Dog在new()中。
-- 8. 与mrDog.makeSound(mrDog)相同；self = mrDog。

----------------------------------------------------

-- 继承示例：

LoudDog = Dog:new()                           -- 1.

function LoudDog:makeSound()
  s = self.sound .. ' '                       -- 2.
  print(s .. s .. s)
end

seymour = LoudDog:new()                       -- 3.
seymour:makeSound()  -- 'woof woof woof'      -- 4.

-- 1. LoudDog获取了Dog的方法和变量。
-- 2. self具有来自new()的'sound'键，见3。
-- 3. 与LoudDog.new(LoudDog)相同，并转换为
--    Dog.new(LoudDog)，因为LoudDog没有'new'键，
--    但具有__index = Dog在其元表上。
--    结果：seymour的元表是LoudDog，且
--    LoudDog.__index = LoudDog。因此seymour.key将
--    = seymour.key，LoudDog.key，Dog.key，哪个表是
--    首个具有给定键的表。
-- 4. 在LoudDog中找到'makeSound'键；这
--    与LoudDog.makeSound(seymour)相同。

-- 如果需要，子类的new()与基类的相同：
function LoudDog:new()
  newObj = {}
  -- 设置newObj
  self.__index = self
  return setmetatable(newObj, self)
end
```