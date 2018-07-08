# 引用类型-1

## Object 类型

- 构造函数定义

```JavaScript
var person = new Object();
person.name = "Nicholas";
person.age = 29;
```

- 字面量定义

```JavaScript
var person = {
name : "Nicholas",
age : 29
};
```

- 在通过对象字面量定义对象时，实际上不会调用 Object 构造函数（Firefox 2 及更早版本会调用 Object 构造函数；但 Firefox 3 之后就不会了）。
- 对象属性的访问

```JavaScript
alert(person["name"]); //"Nicholas"
alert(person.name); //"Nicholas"

//方括号访问属性，可以使用变量方式
var propertyName = "name";
alert(person[propertyName]); //"Nicholas"
```

## Array 类型

### 1. 数组的定义

```JavaScript
var colors = new Array(3); // 创建一个包含3 项的数组
var names = new Array("Greg"); // 创建一个包含1 项，即字符串"Greg"的数组
var colors = Array(3); // 创建一个包含3 项的数组
var names = Array("Greg"); // 创建一个包含1 项，即字符串"Greg"的数组
var colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
var names = []; // 创建一个空数组
var values = [1,2,]; // 不要这样！这样会创建一个包含2 或3 项的数组
var options = [,,,,,]; // 不要这样！这样会创建一个包含5 或6 项的数组
```

### 2. 数组长度：长度可以操作即可改变数组

```JavaScript
var colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
colors.length = 2;
alert(colors[2]); //undefined
colors[colors.length] = "black"; //（在位置2）添加一种颜色
```

### 3. 检测数组

```JavaScript
if (value instanceof Array){
    //对数组执行某些操作
}
if (Array.isArray(value)){
    //对数组执行某些操作
    //支持 Array.isArray()方法的浏览器有IE9+、Firefox 4+、Safari 5+、Opera 10.5+和Chrome。
}
```

### 4. 转换方法

- Array 重新了 toLocaleString()、toString()和 valueOf()方法

```JavaScript
var colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
alert(colors.toString()); // red,blue,green
alert(colors.valueOf()); // red,blue,green
alert(colors); // red,blue,green，默认String方法进行转换
```

- 可以自定义重写方法

```JavaScript
var person1 = {
    toLocaleString : function () {
        return "Nikolaos";
    },
    toString : function() {
        return "Nicholas";
    }
};
var person2 = {
    toLocaleString : function () {
        return "Grigorios";
    },
    toString : function() {
        return "Greg";
    }
};
var people = [person1, person2];
alert(people); //Nicholas,Greg
alert(people.toString()); //Nicholas,Greg
alert(people.toLocaleString()); //Nikolaos,Grigorios
```

- 数组转为字符串

```JavaScript
var colors = ["red", "green", "blue"];
alert(colors.join(",")); //red,green,blue
alert(colors.join("||")); //red||green||blue
```

### 5. 栈方法

```JavaScript
var colors = new Array(); // 创建一个数组
var count = colors.push("red", "green"); // 推入两项
alert(count); //2
count = colors.push("black"); // 推入另一项
alert(count); //3
var item = colors.pop(); // 取得最后一项
alert(item); //"black"
alert(colors.length); //2
```

### 6. 队列方法

```JavaScript
var colors = new Array("yellow"); //创建一个数组
var count = colors.unshift("red", "green"); //推入两项
alert(count); //3
count = colors.unshift("black"); //推入另一项
alert(count); //3
var item = colors.pop(); //取得最后一项
alert(item); //"green"
alert(colors.length); //2
```

### 7. 排序方法

- reverse 数据反转

```JavaScript
var values = [1, 2, 3, 4, 5];
values.reverse();
alert(values); //5,4,3,2,1=>数据反转
```

- 简单排序

```JavaScript
var values = [0, 1, 5, 10, 15];
values.sort();
alert(values); //0,1,10,15,5
```

- 自定义排序

```JavaScript
function compare(value1, value2) {
    if (value1 < value2) {
        return 1;
    } else if (value1 > value2) {
        return -1;
    } else {
        return 0;
    }
}
var values = [0, 1, 5, 10, 15];
values.sort(compare);
alert(values); // 15,10,5,1,0
```

- 在默认情况下，sort()方法按升序排列数组项——即最小的值位于最前面，最大的值排在最后面。
- 为了实现排序，sort()方法会调用每个数组项的 toString()转型方法，然后比较得到的字符串，以确定如何排序

### 8. 操作方法

- concat 方法

```JavaScript
var colors = ["red", "green", "blue"];
var colors2 = colors.concat("yellow", ["black", "brown"]);
alert(colors); //red,green,blue
alert(colors2); //red,green,blue,yellow,black,brown
```

- slice 方法

```JavaScript
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(1);
var colors3 = colors.slice(1,4);
alert(colors2); //green,blue,yellow,purple
alert(colors3); //green,blue,yellow
```

- splice 方法

| 参数              | 描述                                                                  |
| :---------------- | :-------------------------------------------------------------------- |
| index             | 必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。 |
| howmany           | 必需。要删除的项目数量。如果设置为 0，则不会删除项目。                |
| item1, ..., itemX | 可选。向数组添加的新项目。                                            |

```JavaScript
var colors = ["red", "green", "blue"];
var removed = colors.splice(0,1); // 删除第一项
alert(colors); // green,blue

alert(removed); // red，返回的数组中只包含一项
removed = colors.splice(1, 0, "yellow", "orange"); // 从位置1 开始插入两项
alert(colors); // green,yellow,orange,blue

alert(removed); // 返回的是一个空数组
removed = colors.splice(1, 1, "red", "purple"); // 插入两项，删除一项
alert(colors); // green,red,purple,orange,blue
alert(removed); // yellow，返回的数组中只包含一项
```

### 9. 位置方法

- indexOf 方法

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
alert(numbers.indexOf(4)); //3
alert(numbers.indexOf(4, 4)); //5  参数：搜索值，开始索引
```

- lastIndexOf 方法

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
alert(numbers.lastIndexOf(4)); //5
alert(numbers.lastIndexOf(4, 4)); //3 参数：搜索值，开始索引
```

> 使用 indexOf()和 lastIndexOf()方法查找特定项在数组中的位置非常简单，支持它们的浏览器包
> 括 IE9+、Firefox 2+、Safari 3+、Opera 9.5+和 Chrome。

### 10. 迭代方法

- every()：对数组中的每一项运行给定函数，如果该函数对每一项都返回 true，则返回 true。

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
var everyResult = numbers.every(function(item, index, array){
    return (item > 2);
});
alert(everyResult); //false
```

- some()：对数组中的每一项运行给定函数，如果该函数对任一项返回 true，则返回 true。

```JavaScript
var someResult = numbers.some(function(item, index, array){
    return (item > 2);
});
alert(someResult); //true
```

- filter()：对数组中的每一项运行给定函数，返回该函数会返回 true 的项组成的数组。

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
    var filterResult = numbers.filter(function(item, index, array){
return (item > 2);
});
alert(filterResult); //[3,4,5,4,3]
```

- forEach()：对数组中的每一项运行给定函数。这个方法没有返回值。

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
    numbers.forEach(function(item, index, array){
//执行某些操作
});
```

- map()：对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。

```JavaScript
var numbers = [1,2,3,4,5,4,3,2,1];
var mapResult = numbers.map(function(item, index, array){
    return item * 2;
});
alert(mapResult); //[2,4,6,8,10,8,6,4,2]
```

### 11. 归并方法

- reduce 方法

```JavaScript
var values = [1,2,3,4,5];
var sum = values.reduce(function(prev, cur, index, array){
    return prev + cur;
});
alert(sum); //15=>1+2+3+4+5
```

- reduceRight 方法

```JavaScript
var values = [1,2,3,4,5];
var sum = values.reduceRight(function(prev, cur, index, array){
    return prev + cur;
});
alert(sum); //15=>5+4+3+2+1
```

## Date 类型

- 时间转换

```JavaScript
var someDate = new Date(Date.parse("May 25, 2004"));
```

- 时间比较：Date 类型的 valueOf()方法，则根本不返回字符串，而是返回日期的毫秒表示

```JavaScript
var date1 = new Date(2007, 0, 1); //"January 1, 2007"
var date2 = new Date(2007, 1, 1); //"February 1, 2007"
alert(date1 < date2); //true
alert(date1 > date2); //false
```

- 时间各个浏览器有差异，所以使用详细查询 API 或者引用第三方类库方便处理操作

## RegExp 类型

### 1. 基本表达式

```JavaScript
var expression = / pattern / flags ;
```

### 2. 模式

- g：表示全局（global）模式，即模式将被应用于所有字符串，而非在发现第一个匹配项时立即
  停止；
- i：表示不区分大小写（case-insensitive）模式，即在确定匹配项时忽略模式与字符串的大小写；
- m：表示多行（multiline）模式，即在到达一行文本末尾时还会继续查找下一行中是否存在与模
  式匹配的项。

```JavaScript
var pattern1 = /at/g;   //匹配字符串中所有"at"的实例
var pattern2 = /[bc]at/i;   //匹配第一个"bat"或"cat"，不区分大小写
var pattern3 = /.at/gi;   //匹配所有以"at"结尾的3 个字符的组合，不区分大小写
```

### 3. 不同方式定义

```JavaScript
var pattern1 = /[bc]at/i; //匹配第一个"bat"或"cat"，不区分大小写
var pattern2 = new RegExp("[bc]at", "i");  //与pattern1 相同，只不过是使用构造函数创建的
```

### 4. 匹配位置

```JavaScript
var re = /cat/g;,i;
for (i=0; i < 10; i++){
    //每次匹配都从上一次的位置开始，到了末尾再从第一个字符开始
    re.test("catastrophe");
}
for (i=0; i < 10; i++){
    //每次匹配都从第一个字符开始，因为正则表达式每次都是新创建的
    re = new RegExp("cat", "g");
    re.test("catastrophe");
}
```

### 5. 实例属性

- global：布尔值，表示是否设置了 g 标志。
- ignoreCase：布尔值，表示是否设置了 i 标志。
- lastIndex：整数，表示开始搜索下一个匹配项的字符位置，从 0 算起。
- multiline：布尔值，表示是否设置了 m 标志。
- source：正则表达式的字符串表示，按照字面量形式而非传入构造函数中的字符串模式返回。

```JavaScript
var pattern1 = /\[bc\]at/i;

alert(pattern1.global); //false
alert(pattern1.ignoreCase); //true
alert(pattern1.multiline); //false
alert(pattern1.lastIndex); //0
alert(pattern1.source); //"\[bc\]at"

var pattern2 = new RegExp("\\[bc\\]at", "i");

alert(pattern2.global); //false
alert(pattern2.ignoreCase); //true
alert(pattern2.multiline); //false
alert(pattern2.lastIndex); //0
alert(pattern2.source); //"\[bc\]at"
```

### 6. 实例方法

- exec 方法全局匹配

```JavaScript
var text = "mom and dad and baby";
var pattern = /mom( and dad( and baby)?)?/gi;

var matches = pattern.exec(text);
alert(matches.index); // 0
alert(matches.input); // "mom and dad and baby"
alert(matches[0]); // "mom and dad and baby"
alert(matches[1]); // " and dad and baby"
alert(matches[2]); // " and baby"
```

- exec 单个匹配

```JavaScript
var text = "cat, bat, sat, fat";
var pattern1 = /.at/;

var matches = pattern1.exec(text);
alert(matches.index); //0
alert(matches[0]); //cat
alert(pattern1.lastIndex); //0

matches = pattern1.exec(text);
alert(matches.index); //0
alert(matches[0]); //cat
alert(pattern1.lastIndex); //0
```

```JavaScript
var pattern2 = /.at/g;

var matches = pattern2.exec(text);
alert(matches.index); //0
alert(matches[0]); //cat
alert(pattern2.lastIndex); //3

matches = pattern2.exec(text);
alert(matches.index); //5
alert(matches[0]); //bat
alert(pattern2.lastIndex); //8
```

- test 检测是否匹配

```JavaScript
var text = "000-00-0000";
var pattern = /\d{3}-\d{2}-\d{4}/;
if (pattern.test(text)){
    alert("The pattern was matched.");
}
```

### 6. 构造函数属性

- 各个浏览器对构造函数属性的实现有差异，需要使用详细的查看 api 在使用

### 7. 模式的局限性

- ECMAScript 中的正则表达式功能还是比较完备的，但仍然缺少某些语言（特别是 Perl）所支
  持的高级正则表达式特性
- 即使存在这些限制，ECMAScript 正则表达式仍然是非常强大的，能够帮我们完成绝大多数模式匹
  配任务