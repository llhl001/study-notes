# 函数

函数对任何语言来说都是一个核心的概念。通过函数可以封装任意多条语句，而且可以在任何地方、
任何时候调用执行。ECMAScript 中的函数使用 function 关键字来声明，后跟一组参数以及函数体。

## 函数的定义和调用

```JavaScript
//定义函数
function sayHi(name, message) {
alert("Hello " + name + "," + message);
}

//函数调用
sayHi("Nicholas", "how are you today?");
```

## 函数的返回值

- 指定返回值

```JavaScript
function sum(num1, num2) {
    return num1 + num2;
    alert("Hello world"); // 永远不会执行，return不要写代码
}
var result = sum(5, 10);//结果为15
```

- 无返回值

```JavaScript
function sayHi() {
    return;
}
var result = sayHi();//结果为undefined
```

- 默认返回值

```JavaScript
function sum(number1, number2) {
   var sum = number1 + number2；
}
var result = sum();//结果为undefined，没有指定返回值默认：return；
```

## 严格模式的限制

- 不能把函数命名为 eval 或 arguments；
- 不能把参数命名为 eval 或 arguments；
- 不能出现两个命名参数同名的情况

### 理解参数

- 显示使用函数参数

```JavaScript
function sum(number1, number2) {
   var sum = number1 + number2；
}
```

- arguments 隐式参数（模拟重载）

```JavaScript
function doAdd() {
    if(arguments.length == 1) {
        alert(arguments[0] + 10);
    } else if (arguments.length == 2) {
        alert(arguments[0] + arguments[1]);
    }
}
doAdd(10); //20
doAdd(30, 20); //50
```

- arguments 操作（非严格模式）

```JavaScript
function doAdd(num1, num2) {
    //arguments[1]的值改变也使得num1的值改变
    arguments[1] = 10;
    alert(arguments[0] + num2); //10+num2
}
```

- arguments 操作（严格模式）

```JavaScript
function doAdd(num1, num2) {
    //代码报错，严格模式arguments是伪数组不允许改变值
    arguments[1] = 10;
}
```

## 没有重载

> 函数名相同后面的函数会覆盖前面的函数，ECMAScript 函数不能重载。

```JavaScript
function addSomeNumber(num){
    return num + 100;
}
function addSomeNumber(num) {
    return num + 200;
}
var result = addSomeNumber(100); //300
```