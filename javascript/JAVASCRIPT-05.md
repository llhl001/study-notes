# 基本语句

语句通常使用一或多个关键字来完成给定任务。语句可以很简单，例如通知函数退出；也可以比
较复杂，例如指定重复执行某个命令的次数。

## if 语句

- 简单判断

```JavaScript
if (i > 25){}
  alert("Greater than 25."); // 单行语句
else {
  alert("Less than or equal to 25."); // 代码块中的语句
}
```

- 多个条件判断

```JavaScript
if (i > 25) {
  alert("Greater than 25.");
} else if (i < 0) {
  alert("Less than 0.");
} else {
  alert("Between 0 and 25, inclusive.");
}
```

## do-while 语句

```JavaScript
var i = 0;
do {
  i += 2;
} while (i < 10);
alert(i);//i小于10一直执行，第一次先执行在判断while条件
```

## while 语句

```JavaScript
var i = 0;
while (i < 10) {
  i += 2;
}
alert(i);//i小于10一直执行，第一次先判断while条件在执行语句
```

## for 语句

```JavaScript
var count = 10;
for (var i = 0; i < count; i++){
  alert(i);
}
alert(i); //10，定义for循环的条件变量，外部也可以访问
```

## for-in 语句

```JavaScript
//ES5以前对象的变量值null或者undefined会报错
//ES5开始不再抛错只是不循环，不过最好还是做判断
for (var propName in window) {
  document.write(propName);
}
```

## label 语句（不建议使用）

```JavaScript
start: for (var i=0; i < count; i++) {
  alert(i);
}
//在continue语句或者break后加上 start就可以跳转到上面的代码执行
```

## break 语句

```JavaScript
var num = 0;
for (var i=1; i < 10; i++) {
if (i % 5 == 0) {
  break;//立刻跳出循环
}
num++;
}
alert(num); //4
```

## continue 语句

```JavaScript
for (var i=1; i < 10; i++) {
if (i % 5 == 0) {
  continue;//跳出当前这一次循环，后面的代码不执行继续下一次循环
}
num++;
}
alert(num); //8
```

## with 语句（不建议使用）

> 严格模式下不允许使用 with 语句

```JavaScript
//原来的语句
var qs = location.search.substring(1);
var hostName = location.hostname;
var url = location.href;

//转换为with语句
with(location){
  var qs = search.substring(1);
  var hostName = hostname;
  var url = href;
}
```

## switch 语句

> switch 语句在比较值时使用的是全等操作符，因此不会发生类型转换（例如：字符串"10"不等于数值 10）。

- 基本 switch 语句

```JavaScript
switch (i) {
  case 25:
    alert("25");
    break;
  case 35:
    alert("35");
    break;
  case 45:
    alert("45");
    break;
  default:
    alert("Other");
}
```

- 合并执行条件

```JavaScript
switch (i) {
  case 25:
  /* 合并两种情形 */
  case 35:
    alert("25 or 35");
    break;
  case 45:
    alert("45");
    break;
  default:
    alert("Other");
}
```

- 表达式条件

```JavaScript
switch ("hello world") {
  case "hello" + " world":
    alert("Greeting was found.");
    break;
  case "goodbye":
    alert("Closing was found.");
    break;
  default:
    alert("Unexpected message was found.");
}
```

- 表达式判断

```JavaScript
var num = 25;
switch (true) {
  case num < 0:
    alert("Less than 0.");
    break;
  case num >= 0 && num <= 10:
    alert("Between 0 and 10.");
    break;
  case num > 10 && num <= 20:
    alert("Between 10 and 20.");
    break;
  default:
    alert("More than 20.");
}
```