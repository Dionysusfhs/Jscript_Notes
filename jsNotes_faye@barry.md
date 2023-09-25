# javascript笔记 @barry

## 一、变量


undefined，null，number，string，boolean，**object**，symbol

总结：
1.js的变量在声明时无需指定类型；

2.js 变量声明的方式有 `let` 和 `const` 两种；

3.使用 const 关键字声明的变量必须初始化，且不允许被修改。



## 二、逻辑结构

`if`  / `for` / `while` / `do while`

### 2.1 if
```javascript
const name = 'barry'

if (name === 'faye') {
  console.log(`I'm faye`)
} else if (name === 'barry') {
  console.log(`I'm barry`)
} else {
  console.log(`I'm other~`)
}
```
###2.2 for
```javascript
// for 
for (let index = 0; index < 3; index = index + 1) {
  console.log(index)
}
```
###2.3 while
```javascript
// while 
let index = 0;

while (index < 3) {
  console.log(index)
  index = index + 1
}
```
###2.4 do while
```javascript
// do while
let index = 0

do {
	console.log(index)
	index = index + 1
} while (index < 3)
```

## 三、函数

​		对于调用者来说，调用者要使用一个函数的目的就是为了进行运算，为节省调用者的时间，调用者调用一个函数时必须知道该函数做了哪些事，因此函数的名称至关重要。名称代表了函数的行为，因此必须以一个动作开头，同时函数进行了一些运算，因此为了函数的重复利用，一个函数必须仅仅完成一件确定的事。

​		例子

​		函数输入：两个自然数a，b

​		函数名称：自然数相加

​		函数结果：相加的和

```javascript
function addTwoNatureNumbers(a, b) {
  return a + b
}

const result = addTwoNatureNumbers(1, 3)

console.log('result', result)
```

​		函数的声明需要使用 function 关键字，之后跟函数名，之后是 (变量1，变量2) 之后 { 函数体 }

​		可以具有任意数量的变量，但变量名彼此不允许重复，同时变量名应该为名词



​		==箭头函数==

```javascript
const addTwoNatureNumbers = (add1, add2) => {
  return add1 + add2
}

const result = addTwoNatureNumbers(1, 3)

console.log('result', result)
```

​		

​		==函数还可以在声明阶段自动执行==

```javascript
function printLog() {
  console.log('some log')
}

printLog()

console.log(printLog)
```
##四、对象类型

​		常见的对象类型有：Array, Function, Set, Map, RegExp, Date
###4.1Array

​		Array（数组）通常用于存储一系列相同类型的值（ js 允许不同类型的值存储在同一个数组中，但请不要这么做）

1. includes() 用于判断数组中是否存在目标值;
```javascript
const numArray = [1, 2, 3, 4, 5]
console.log(numArray.includes(2))
console.log(numArray.includes(7))
```

2. join() 用于使用给定的分隔符将数组元素拼接为一个字符串;
```javascript
console.log(numArray.join(','))
```

3. length用于获取数组的元素个数;
```javascript
console.log(numArray.length)
```

4. fill用于使用目标内容填充数组
```javascript
console.log(numArray.fill(1))
```
5. copyWithin()
==numArray.copyWithin(target, start, end)
这个函数最多可接收三个参数，第一个参数指定一个目标位置，第二个参数同样指定一个目标位置，第三个参数仍然指定一个目标位置。
将数组中第 target 位置的内容依次替换为 从数组 start 位置到 end 位置中的每一个元素==
```javascript
const numArray = [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(numArray.copyWithin(0, 6, 8))
```
6. sort()对数组进行排序

7. reverse()反转数组元素
```javascript
const numArray = [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(numArray.reverse())
console.log(numArray.reverse().sort())
```
8. indexOf()寻找 target 在原数组中的位置，未找到时返回 -1
```javascript
const numArray = [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(numArray.indexOf(3))
```
8.5.lastIndexOf()从末尾向前查找，返回遇到的第一个相同元素的下标,与 indexOf 相对应

9. pop()移除数组末尾的元素并将其返回
```javascript
const numArray = [1, 2, 3, 4, 5, 6, 7, 8, 1, 9]
console.log(numArray.pop())
console.log(numArray)
```
10. push()向数组末尾添加元素，并返回添加的元素值

11. shift()与 pop() 类似，但从数组头部进行

12. unshift()与 push() 类似，但从数组头部进行

###4.2Function

   1.slice()  数组切片

​	返回数组中以第一个参数为下标开始，第二个参数为下标结束的元素，不改变原数组。（第二个参数缺省默认到数组结束）

```javascript
const numArray = [1, 2, 3, 4, 5, 6, 7, 8, 1, 9]
console.log(numArray.slice(1))
console.log(numArray.slice(1, 4))
console.log(numArray)
```

   2.concat()  用于拼接原数组及各个参数

​	可以把当前数组与另一数组连接起来，返回一个新的数组，也可以添加元素，返回新的数组
```javascript
const numArray = [1, 2, 3,]
console.log(numArray.concat(4))
console.log(numArray.concat([4]))
console.log(numArray.concat([4, 6]))
console.log(numArray.concat([4, 6], 3))
console.log(numArray.concat([4, [6]], 3))
console.log(numArray.concat(6, 8))
console.log(numArray)
```

   3.reduce()

```
const numArray = [1, 2, 3, 4]

const res = numArray.reduce((res, current) => {
  return res + current
}, 0)

console.log('res', res)
```

​	参数 2 是调用者手动为累加过程提供的初始值

​	如果调用者没有手动给出这个值, 那 reduce() 会将数组的第一个元素取出作为初始值

​	但无论如何, 数组中的每一个元素都会参与累加的过程
