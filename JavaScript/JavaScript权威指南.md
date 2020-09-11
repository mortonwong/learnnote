# 前端工具

- Vs Code 自动补全规则： https://docs.emmet.io/cheat-sheet/

# 词法结构

## 忽略分号时,分号补充规则

1. **下一行和当前行**不可合并解析

   ```JavaScript
   var a
   var b //自动补分号
   ```

2. **下一行和当前行**可以合并解析

   ```javascript
   var a
   a
   =
   3	//解析为var a;a=3;
   ```

3. 下一行和当前行既可以合并,也可以分开,要加分号

   ```javascript
   var a=x+y
   (a+b).toString()	//括号当做了函数调用，解析为var a=x+y(a+b).toString()
   
   /*应该自己加分号*/
   var a=x+y;
   (a+b).toString()
   ```

4. 遇到return，continue，break 独自成行，自动加分号

   ```javascript
   return
   true
   //解析为 return;true; 而不是 return true
   ```

5. 自增和自减运算符 ++ 和 -- , 默认作为前置表达式

   ```javascript
   a
   ++
   b
   //解析为 a;++b;
   ```

   

# 类型\值\变量

## 基本

**五个基本类型**：数字、字符串、布尔值、null、undefined，其它类型均为对象Object。

**对象**是 property的集合，无论属性和函数都是property，函数（Function类）、数组（Array类）都是对象，JavaScript还定义了 日期类、正则类（RegExp）、错误类（Error）

var定义的变量具有**词法作用域**，作用域取决于是不是在函数中，在函数外的则具有全局作用域

## 数字

1. JavaScript的数字都是**64位浮点数**
2. 可用**十六进制**表示 0xAB，一般不可用八进制表示075
3. 浮点数表示可用**科学计数法**，2.3e2

### Math对象

这个全局对象有各种数字操作的方法

```javascript
Math.random() //0~1.0的随机数
Math.round(n) //四舍五入取整数
Math.ceil(n) //向上取整数
Math.floor(n) //向下取整数
```

### 特殊值

- infinity : 无限大
- -infinity : 负无穷大
- 0 : 下溢表示
- -0 : 下溢表示,负趋近于0
- NaN : 非数字,**NaN和NaN不相等**

### 判断是否为数字

isNaN() 判断是否是NaN

isFinite() 不是infinity\-infinity\NaN时为 true

### 负零和正零

作为运算结果时不相等,其他时候相等

```javascript
1/0 === 1/-0 //返回false，正无穷大和负无穷大不相等
```

### 浮点数的四舍五入错误

```javascript
0.3-0.2 === 0.2-0.1 //返回false，因为在二进制表示中运算结果不相等，是因为浮点数只是极限接近0.1
```

## 字符串

字符串类型是基本数据类型，它是有方法的基本数据类型，并不是对象

### 字符串方法

```javascript

s.length //长度属性,返回16位为单位的长度,有些字符是32为Unicode表示,这种字符的长度为2
s.charAt(index) //返回索引值的字符,现在可用s[index]更方便
s.substring(1,4) //返回索引为1~3的字符串,值不可为负
s.slice(1,4) //返回索引为1~4-1的字符串，值可为负，负则从结尾开始数
s.substr(1,4) //返回索引开始为1，长度为4的字符串，值可为负，负则从结尾开始数
s.replace('1','2')
s.toUpperCase() //替换为大写
```

### 模式匹配

RegExp对象是类似Date的全局对象，变量值为/**/形式，则是正则直接量，也代表正则对象，可以使用正则对象的方法

```javascript
var pattern = /\d+/g
pattern.test(s) //返回true则匹配成功

s.search(pattern) //首次匹配成功的索引
s.match(pattern) //匹配结果生成数组
s.replace(pattern,'#') //所有匹配结果替换成字符
s.split(pattern) //生成以pattern匹配结果作为分隔符的数组
```

## null和undefined

### null 

表示 空值

`**typeof null** //输出 Object,认为null是一种特殊的对象值,含义是非对象,但其实null是一种基本类型`

### undefined

表示 未定义,变量没有初始化

### 相等运算符

`null == undefined 为true`

`null === undefined 为false`

## 全局对象

`var global = this`

在浏览器客户端JavaScript中,window对象是全局对象

所有的全局属性都是全局对象是属性

## 包装对象

### 为什么字符串、数字、布尔值基本类型有属性和方法

在调用它们的属性和方法时，会临时创建对象String、Number来访问，在使用完之后销毁

Number、String、Boolean对象的值，和基本类型的值，在typeof、==、=== 需要注意

