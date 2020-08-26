# js基础
## 1.js历史
- https://www.jianshu.com/p/db1b230e3415
- 1990年浏览器诞生，蒂姆伯纳斯李
- 1993年  美国伊利诺大学 马克安德林  mosic浏览器  图形化浏览器
- 1994年  马克和吉姆克拉克   Netscape网景公司  netscape navigation
- 1996 
    - 微软收购sp有glass  ->IE
    - TE3  jscript
    - 网景公司  livescript
    - java火起来（sun公司）livescript改名javascript
- 2001年   IE6  XP诞生  JS引擎产生
- 2003年   mozilla公司  firefox
- 2008年  Google基于webkit blink gears->v8引擎
    - 直接翻译机器码
    - 独立于浏览器运行
- 2009  甲骨文oracle收购sun公司，js的所有权给甲骨文

## 2.变量
### 字面量
- 不可改变的值，12345，可以直接使用，但不会直接用，会定义一个变量保存 let a = 1235
### 标识符
- 包括变量名，函数名，属性名
- 命名标识符规则：可以包含字母数字_$
- 驼峰命名法

## 3.数据类型
### 基本数据（值）类型（单一值，值和值之间没有关系）
- Number数字
    - 最大值：Number.MAX_VALUE
    - 当大于最大值时会返回  Infinity 表示正无穷  -Infinity 表示负无穷  类型是数值型
    - 当字符串或其他类型与数字型相计算返回NaN
    - 整数运算保证精确
    - 浮点数计算可能不精确，所以不能进行精确度高的运算放到服务器进行计算
- String字符串
    - 转义字符 \
    - 在底层以字符数组形式保存的
        - str.length   字符串长度
        - str[0]   字符串指定字符
        - str.charAt()  字符串指定字符
- Boolean布尔
- Undefined未定义
    - 声明变量但是不赋值
- Null空值
    - 用来表示为空（不存在）的对象
    - typeof null会返回object

### 对象（引用）数据类型
- 对象(Object)
- 数组(Array)
- 函数(Function)
### 强制类型转换
- 转换为string
    - 调用被转换数据类型的toString（），a.toString
        - 不会影响原变量，将转换结果返回
        - null和undefined没有toString方法
    - 调用String函数,String(a)
        - 将被转换数据作为参数传给函数
        - 对于number Boolean等于调用toString
        - 对于null undefined 就是直接转换为'null'   'undefined'
- 转换为number
    - Number()函数
        - 字符串-->数字：纯数字转换为数值型，有非法数字转换为NaN，空串转换为0
        - 布尔值-->数字：true=1 false=0
        - Null-->数字：0
        - UNdefined-->数字：NaN
    - parseInt() 把一个字符串转换为数字
        - 将有效整数内容取出转换为数值型，123px，取整
        - 第一个数字开始取到有非法数字出现
        - 对非字符串的类型会先转换为字符串
        - parseFloat()取出小数
- 转换为Boolean
    - 使用Boolean函数
        - 数字-->布尔：除了0和NaN都是true
        - 字符串-->布尔:除了空串都是true
        - null和undefined-->布尔：false
        - 对象-->布尔：true
    - 为任意的数据类型做两次非运算，即可将其转换为布尔值

### 判断数据类型转换
- typeof
    - 数值/字符串/布尔值/undefined/function
    - 不能判断null和object，object和array
- instanceof
    - 判断对象的具体类型
    - 用于检查对象是否是同一个类的实例
- ===
    - ‘123’ === string 
- Object.prototype.toString.call()
    - Object对象和它的原型链上各自有一个toString()方法，第一个返回的是一个函数，第二个返回的是值类型
    - 可以检测所有的数据类型
- Object.prototype.toString.call([1,2,3])//"[object Array
- constructor
    - 类似instanceof

