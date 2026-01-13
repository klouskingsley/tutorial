# JavaScript 教程

## 目录

- [一、类型](#一类型)
  - [1.1 基本类型](#11-基本类型)
    - [1.1.1 字符串 (String)](#111-字符串-string)
    - [1.1.2 数字 (Number)](#112-数字-number)
    - [1.1.3 布尔 (Boolean)](#113-布尔-boolean)
    - [1.1.4 Symbol](#114-symbol)
  - [1.2 复合类型](#12-复合类型)
    - [1.2.1 数组 (Array)](#121-数组-array)
    - [1.2.2 Map](#122-map)
    - [1.2.3 Set](#123-set)
    - [1.2.4 对象 (Object)](#124-对象-object)
  - [1.3 基本类型和复合类型的区别](#13-基本类型和复合类型的区别)
  - [1.4 空类型](#14-空类型)
  - [1.5 其他类型](#15-其他类型)
    - [1.5.1 函数类型](#151-函数类型)
    - [1.5.2 Date](#152-date)
  - [1.6 类型判断](#16-类型判断)
  - [1.7 类型转换](#17-类型转换)
- [二、语法](#二语法)
  - [2.1 声明](#21-声明)
  - [2.2 赋值](#22-赋值)
  - [2.3 错误处理](#23-错误处理)
- [三、流程控制](#三流程控制)
  - [3.1 条件语句](#31-条件语句)
  - [3.2 循环语句](#32-循环语句)
  - [3.3 控制语句](#33-控制语句)
- [四、作用域](#四作用域)
- [五、this](#五this)
- [六、函数](#六函数)
  - [6.1 函数声明方式](#61-函数声明方式)
  - [6.2 函数参数](#62-函数参数)
  - [6.3 箭头函数 vs 普通函数](#63-箭头函数-vs-普通函数)
  - [6.4 高阶函数](#64-高阶函数)
  - [6.5 内置函数和对象](#65-内置函数和对象)
- [七、Class](#七class)
- [八、Promise 和 async/await](#八promise-和-asyncawait)
  - [8.1 回调地狱问题](#81-回调地狱问题)
  - [8.2 Promise 基础](#82-promise-基础)
  - [8.3 Promise 静态方法](#83-promise-静态方法)
  - [8.4 async/await](#84-asyncawait)
  - [8.5 实际应用示例](#85-实际应用示例)

---

## 一、类型

JavaScript 是一门动态类型语言，变量的类型在运行时确定。

### 1.1 基本类型

#### 1.1.1 字符串 (String)

字符串用于表示文本数据。

```javascript
// 字符串的三种声明方式
let str1 = 'hel'lo';        // 单引号
let str2 = "world";        // 双引号
let str3 = `hello world`;  // 模板字符串（反引号）

console.log(str1);  // hello
console.log(str2);  // world
console.log(str3);  // hello world
```

**对字符串的操作：**

```javascript
let str = "Hello, JavaScript!";

// 获取长度
console.log(str.length);  // 18

// 访问字符
console.log(str[0]);       // H
console.log(str.charAt(0)); // H

// 查找子串
console.log(str.indexOf("Java"));     // 7
console.log(str.includes("Hello"));   // true
console.log(str.startsWith("Hello")); // true
console.log(str.endsWith("!"));       // true

// 截取字符串
console.log(str.slice(0, 5));     // Hello
console.log(str.substring(7, 17)); // JavaScript
console.log(str.substr(7, 10));    // JavaScript

// 大小写转换
console.log(str.toUpperCase());  // HELLO, JAVASCRIPT!
console.log(str.toLowerCase());  // hello, javascript!

// 去除空格
let padded = "  hello  ";
console.log(padded.trim());      // "hello"
console.log(padded.trimStart()); // "hello  "
console.log(padded.trimEnd());   // "  hello"

// 替换
console.log(str.replace("Hello", "Hi"));  // Hi, JavaScript!
console.log("aaa".replaceAll("a", "b"));  // bbb

// 分割
console.log("a,b,c".split(","));  // ["a", "b", "c"]

// 拼接
console.log("Hello".concat(" ", "World"));  // Hello World
console.log("Hello" + " " + "World");       // Hello World

// 重复
console.log("ab".repeat(3));  // ababab

// 填充
console.log("5".padStart(3, "0"));  // 005
console.log("5".padEnd(3, "0"));    // 500

// 模板字符串
let name = "Tom";
let age = 18;
console.log(`我叫${name}，今年${age}岁`);  // 我叫Tom，今年18岁

// 多行字符串
let multiLine = `第一行
第二行
第三行`;
console.log(multiLine);
```

#### 1.1.2 数字 (Number)

JavaScript 中的数字类型包括整数和浮点数。

```javascript
// 整数和浮点数都是 number 类型
let int = 42;
let float = 3.14;
let double = 3.141592653589793;

console.log(typeof int);    // number
console.log(typeof float);  // number
```

**BigInt - 大整数：**

```javascript
// 普通数字的精度限制
console.log(9999999999999999);     // 10000000000000000 (精度丢失)

// BigInt 可以表示任意大的整数
let bigNum = 9999999999999999n;    // 在数字后加 n
let bigNum2 = BigInt("9999999999999999");

console.log(bigNum);               // 9999999999999999n
console.log(typeof bigNum);        // bigint

// BigInt 运算
console.log(10n + 20n);  // 30n
console.log(10n * 20n);  // 200n

// 注意：BigInt 不能和普通数字混合运算
// console.log(10n + 20);  // 报错！
console.log(10n + BigInt(20));  // 30n
```

**特殊数值：**

```javascript
// NaN - Not a Number
console.log(0 / 0);           // NaN
console.log(parseInt("abc")); // NaN
console.log(NaN === NaN);     // false (NaN 不等于自身)
console.log(Number.isNaN(NaN)); // true

// Infinity - 无穷大
console.log(1 / 0);           // Infinity
console.log(-1 / 0);          // -Infinity
console.log(Infinity + 1);    // Infinity
console.log(Number.isFinite(Infinity));  // false
console.log(Number.isFinite(100));       // true
```

**进制：**

```javascript
// 十进制 (默认)
let decimal = 255;

// 二进制 (0b 开头)
let binary = 0b11111111;

// 八进制 (0o 开头)
let octal = 0o377;

// 十六进制 (0x 开头)
let hex = 0xff;

console.log(decimal);  // 255
console.log(binary);   // 255
console.log(octal);    // 255
console.log(hex);      // 255

// 转换为其他进制的字符串
let num = 255;
console.log(num.toString(2));   // "11111111" (二进制)
console.log(num.toString(8));   // "377" (八进制)
console.log(num.toString(16));  // "ff" (十六进制)

// 从字符串解析
console.log(parseInt("11111111", 2));  // 255
console.log(parseInt("377", 8));       // 255
console.log(parseInt("ff", 16));       // 255
```

**数字操作和 Math 对象：**

```javascript
// 基本运算符
console.log(10 + 3);   // 13 加
console.log(10 - 3);   // 7  减
console.log(10 * 3);   // 30 乘
console.log(10 / 3);   // 3.3333... 除
console.log(10 % 3);   // 1  取余
console.log(10 ** 3);  // 1000 幂运算

// 自增自减
let a = 5;
console.log(b = a++);  // 5 (先返回后自增)
console.log(a);    // 6
console.log(++a);  // 7 (先自增后返回)

// 数字方法
let n = 3.14159;
console.log(n.toFixed(2));       // "3.14" (保留小数位)
console.log(n.toPrecision(3));   // "3.14" (有效数字)
console.log(Number.isInteger(5)); // true
console.log(Number.parseInt("10px"));   // 10
console.log(Number.parseFloat("3.14m")); // 3.14

// Math 对象
console.log(Math.PI);           // 3.141592653589793
console.log(Math.E);            // 2.718281828459045

console.log(Math.abs(-5));      // 5 (绝对值) absolute
console.log(Math.round(4.5));   // 5 (四舍五入) 
console.log(Math.ceil(4.1));    // 5 (向上取整)
console.log(Math.floor(4.9));   // 4 (向下取整)
console.log(Math.trunc(4.9));   // 4 (去除小数部分)

console.log(Math.max(1, 2, 3)); // 3 (最大值)
console.log(Math.min(1, 2, 3)); // 1 (最小值)

console.log(Math.pow(2, 3));    // 8 (幂)
console.log(Math.sqrt(16));     // 4 (平方根)
console.log(Math.cbrt(27));     // 3 (立方根)

console.log(Math.random());     // 0-1 之间的随机数
// 生成 1-10 的随机整数
console.log(Math.floor(Math.random() * 10) + 1);

console.log(Math.sin(Math.PI / 2));  // 1 (三角函数)
console.log(Math.log(Math.E));       // 1 (自然对数)
console.log(Math.log10(100));        // 2 (以10为底的对数)
```

#### 1.1.3 布尔 (Boolean)

布尔类型只有两个值：`true` 和 `false`。

```javascript
let isTrue = true;
let isFalse = false;

console.log(typeof isTrue);  // boolean
```

**布尔运算：**

```javascript
// 逻辑运算符
console.log(true && true);   // true (与)
console.log(true && false);  // false
console.log(true || false);  // true (或)
console.log(false || false); // false
console.log(!true);          // false (非)
console.log(!false);         // true

// 比较运算符
console.log(5 > 3);    // true
console.log(5 < 3);    // false
console.log(5 >= 5);   // true
console.log(5 <= 4);   // false
console.log(5 == "5"); // true (值相等，会类型转换)
console.log(5 === "5"); // false (严格相等，类型也要相同)
console.log(5 != "5");  // false
console.log(5 !== "5"); // true

// 短路求值
let result1 = true && "hello";   // "hello" (返回最后一个真值)
let result2 = false && "hello";  // false (返回第一个假值)
let result3 = false || "hello";  // "hello" (返回第一个真值)
let result4 = true || "hello";   // true

console.log(result1, result2, result3, result4);

// 实际应用：默认值
let username = null;
let displayName = username || "匿名用户";
console.log(displayName);  // "匿名用户"

// 空值合并运算符 (??) - 只有 null 和 undefined 才会取默认值
let value1 = 0;
let value2 = null;
console.log(value1 || 100);   // 100 (0 是假值)
console.log(value1 ?? 100);   // 0 (0 不是 null/undefined)
console.log(value2 ?? 100);   // 100
```

**假值 (Falsy) 和真值 (Truthy)：**

```javascript
// 假值：转换为布尔时为 false
console.log(Boolean(false));     // false
console.log(Boolean(0));         // false
console.log(Boolean(-0));        // false
console.log(Boolean(0n));        // false
console.log(Boolean(""));        // false
console.log(Boolean(null));      // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN));       // false

// 真值：除假值外都是真值
console.log(Boolean(true));      // true
console.log(Boolean(1));         // true
console.log(Boolean("hello"));   // true
console.log(Boolean([]));        // true (空数组是真值!)
console.log(Boolean({}));        // true (空对象是真值!)
```

#### 1.1.4 Symbol

Symbol 是 ES6 新增的基本类型，表示唯一的标识符。

```javascript
// 创建 Symbol
let sym1 = Symbol();
let sym2 = Symbol();
console.log(sym1 === sym2);  // false (每个 Symbol 都是唯一的)

// 带描述的 Symbol
let sym3 = Symbol("description");
console.log(sym3.toString());  // Symbol(description)
console.log(sym3.description); // description

// Symbol 作为对象属性键
let id = Symbol("id");
let user = {
    name: "Tom",
    [id]: 12345  // Symbol 作为键
};

console.log(user.name);   // Tom
console.log(user[id]);    // 12345

// Symbol 属性不会出现在普通遍历中
console.log(Object.keys(user));         // ["name"]
console.log(Object.getOwnPropertySymbols(user));  // [Symbol(id)]

// 全局 Symbol
let globalSym1 = Symbol.for("app.id");
let globalSym2 = Symbol.for("app.id");
console.log(globalSym1 === globalSym2);  // true (相同键返回相同 Symbol)
console.log(Symbol.keyFor(globalSym1));  // "app.id"

// 内置 Symbol
console.log(Symbol.iterator);   // Symbol(Symbol.iterator)
console.log(Symbol.toStringTag); // Symbol(Symbol.toStringTag)
```

### 1.2 复合类型

#### 1.2.1 数组 (Array)

数组是有序的元素集合。

```javascript
// 创建数组
let arr1 = [1, 2, 3];
let arr2 = new Array(1, 2, 3);
let arr3 = Array.of(1, 2, 3);
let arr4 = Array.from("abc");  // ["a", "b", "c"]

console.log(arr1);  // [1, 2, 3]
console.log(arr4);  // ["a", "b", "c"]

// 访问元素
let fruits = ["apple", "banana", "orange"];
console.log(fruits[0]);      // apple
console.log(fruits.at(-1));  // orange (负索引)
console.log(fruits.length);  // 3

// 修改数组
fruits[1] = "grape";
console.log(fruits);  // ["apple", "grape", "orange"]

// 添加和删除元素
let arr = [1, 2, 3];
arr.push(4);        // 末尾添加
console.log(arr);   // [1, 2, 3, 4]

arr.pop();          // 末尾删除
console.log(arr);   // [1, 2, 3]

arr.unshift(0);     // 开头添加
console.log(arr);   // [0, 1, 2, 3]

arr.shift();        // 开头删除
console.log(arr);   // [1, 2, 3]

// splice - 任意位置增删改
let arr5 = [1, 2, 3, 4, 5];
arr5.splice(2, 1);          // 从索引2删除1个元素
console.log(arr5);          // [1, 2, 4, 5]

arr5.splice(2, 0, 3);       // 从索引2插入元素
console.log(arr5);          // [1, 2, 3, 4, 5]

arr5.splice(2, 1, "three"); // 替换
console.log(arr5);          // [1, 2, "three", 4, 5]

// 查找
let nums = [1, 2, 3, 2, 1];
console.log(nums.indexOf(2));      // 1 (第一个匹配的索引)
console.log(nums.lastIndexOf(2));  // 3 (最后一个匹配的索引)
console.log(nums.includes(3));     // true

let users = [{id: 1}, {id: 2}, {id: 3}];
console.log(users.find(u => u.id === 2));      // {id: 2}
console.log(users.findIndex(u => u.id === 2)); // 1

// 切片
let arr6 = [1, 2, 3, 4, 5];
console.log(arr6.slice(1, 3));  // [2, 3] (不改变原数组)
console.log(arr6);              // [1, 2, 3, 4, 5]

// 合并
let a1 = [1, 2];
let a2 = [3, 4];
console.log(a1.concat(a2));     // [1, 2, 3, 4]
console.log([...a1, ...a2]);    // [1, 2, 3, 4] (展开运算符)

// 排序
let arr7 = [3, 1, 4, 1, 5, 9];
arr7.sort((a, b) => a - b);  // 升序
console.log(arr7);           // [1, 1, 3, 4, 5, 9]
arr7.sort((a, b) => b - a);  // 降序
console.log(arr7);           // [9, 5, 4, 3, 1, 1]

// 反转
let arr8 = [1, 2, 3];
arr8.reverse();
console.log(arr8);  // [3, 2, 1]

// 遍历方法
let numbers = [1, 2, 3, 4, 5];

// forEach - 遍历
numbers.forEach((num, index) => {
    console.log(`索引${index}: ${num}`);
});

// map - 映射
let doubled = numbers.map(n => n * 2);
console.log(doubled);  // [2, 4, 6, 8, 10]

// filter - 过滤
let evens = numbers.filter(n => n % 2 === 0);
console.log(evens);  // [2, 4]

// reduce - 归约
let sum = numbers.reduce((acc, n) => acc + n, 0);
console.log(sum);  // 15

// every - 是否全部满足
console.log(numbers.every(n => n > 0));  // true

// some - 是否有一个满足
console.log(numbers.some(n => n > 4));   // true

// flat - 扁平化
let nested = [1, [2, [3, [4]]]];
console.log(nested.flat());     // [1, 2, [3, [4]]]
console.log(nested.flat(2));    // [1, 2, 3, [4]]
console.log(nested.flat(Infinity)); // [1, 2, 3, 4]

// flatMap - map + flat
let arr9 = [1, 2, 3];
console.log(arr9.flatMap(x => [x, x * 2]));  // [1, 2, 2, 4, 3, 6]

// join - 转为字符串
console.log([1, 2, 3].join("-"));  // "1-2-3"
```

#### 1.2.2 Map

Map 是键值对的集合，键可以是任意类型。

```javascript
// 创建 Map
let map = new Map();

// 添加键值对
map.set("name", "Tom");
map.set(1, "one");
map.set({}, "object");

console.log(map.size);  // 3

// 获取值
console.log(map.get("name"));  // Tom
console.log(map.get(1));       // one

// 检查键是否存在
console.log(map.has("name"));  // true
console.log(map.has("age"));   // false

// 删除
map.delete("name");
console.log(map.has("name"));  // false

// 从数组创建 Map
let map2 = new Map([
    ["a", 1],
    ["b", 2],
    ["c", 3]
]);

// 遍历 Map
map2.forEach((value, key) => {
    console.log(`${key}: ${value}`);
});

// 使用 for...of
for (let [key, value] of map2) {
    console.log(`${key} => ${value}`);
}

// 获取所有键/值
console.log([...map2.keys()]);    // ["a", "b", "c"]
console.log([...map2.values()]);  // [1, 2, 3]
console.log([...map2.entries()]); // [["a", 1], ["b", 2], ["c", 3]]

// Map 转为对象
let obj = Object.fromEntries(map2);
console.log(obj);  // {a: 1, b: 2, c: 3}

// 对象转为 Map
let map3 = new Map(Object.entries({x: 10, y: 20}));
console.log(map3);  // Map(2) {"x" => 10, "y" => 20}

// 清空 Map
map2.clear();
console.log(map2.size);  // 0
```

#### 1.2.3 Set

Set 是值的集合，所有值都是唯一的。

```javascript
// 创建 Set
let set = new Set();

// 添加值
set.add(1);
set.add(2);
set.add(2);  // 重复的值会被忽略
set.add(3);

console.log(set.size);  // 3
console.log(set);       // Set(3) {1, 2, 3}

// 检查值是否存在
console.log(set.has(2));  // true
console.log(set.has(4));  // false

// 删除值
set.delete(2);
console.log(set.has(2));  // false

// 从数组创建 Set (去重)
let arr = [1, 2, 2, 3, 3, 3];
let uniqueSet = new Set(arr);
console.log([...uniqueSet]);  // [1, 2, 3]

// 数组去重的简便方法
let unique = [...new Set([1, 2, 2, 3, 3, 3])];
console.log(unique);  // [1, 2, 3]

// 遍历 Set
let set2 = new Set(["a", "b", "c"]);

set2.forEach(value => {
    console.log(value);
});

for (let value of set2) {
    console.log(value);
}

// Set 运算
let setA = new Set([1, 2, 3]);
let setB = new Set([2, 3, 4]);

// 并集
let union = new Set([...setA, ...setB]);
console.log([...union]);  // [1, 2, 3, 4]

// 交集
let intersection = new Set([...setA].filter(x => setB.has(x)));
console.log([...intersection]);  // [2, 3]

// 差集
let difference = new Set([...setA].filter(x => !setB.has(x)));
console.log([...difference]);  // [1]

// 清空 Set
set2.clear();
console.log(set2.size);  // 0
```

#### 1.2.4 对象 (Object)

对象是属性的无序集合。

```javascript
// 对象声明方式

// 1. 字面量
let obj1 = {
    name: "Tom",
    age: 18
};

// 2. 构造函数
let obj2 = new Object();
obj2.name = "Jerry";

// 3. Object.create
let obj3 = Object.create(null);  // 没有原型的纯净对象

// 访问属性
console.log(obj1.name);      // Tom
console.log(obj1["name"]);   // Tom (可以用变量作为键)

let key = "age";
console.log(obj1[key]);      // 18

// 修改和添加属性
obj1.name = "Tommy";
obj1.gender = "male";
console.log(obj1);  // {name: "Tommy", age: 18, gender: "male"}

// 删除属性
delete obj1.gender;
console.log(obj1);  // {name: "Tommy", age: 18}

// 检查属性是否存在
console.log("name" in obj1);           // true
console.log(obj1.hasOwnProperty("name")); // true

// 简写属性和方法
let name = "Tom";
let age = 18;

let person = {
    name,       // 等同于 name: name
    age,        // 等同于 age: age
    sayHi() {   // 方法简写
        console.log(`Hi, I'm ${this.name}`);
    }
};
person.sayHi();  // Hi, I'm Tom

// 计算属性名
let propName = "dynamicKey";
let obj4 = {
    [propName]: "value",
    ["key" + 1]: "value1"
};
console.log(obj4);  // {dynamicKey: "value", key1: "value1"}

// 遍历对象
let user = {name: "Tom", age: 18, city: "Beijing"};

// for...in (遍历可枚举属性，包括继承的)
for (let key in user) {
    console.log(`${key}: ${user[key]}`);
}

// Object.keys / values / entries
console.log(Object.keys(user));    // ["name", "age", "city"]
console.log(Object.values(user));  // ["Tom", 18, "Beijing"]
console.log(Object.entries(user)); // [["name", "Tom"], ["age", 18], ["city", "Beijing"]]

// 对象合并
let defaults = {a: 1, b: 2};
let options = {b: 3, c: 4};

// Object.assign
let merged1 = Object.assign({}, defaults, options);
console.log(merged1);  // {a: 1, b: 3, c: 4}

// 展开运算符 (推荐)
let merged2 = {...defaults, ...options};
console.log(merged2);  // {a: 1, b: 3, c: 4}

// 对象冻结和密封
let frozen = Object.freeze({x: 1});
// frozen.x = 2;  // 严格模式下报错，非严格模式静默失败
console.log(frozen.x);  // 1

let sealed = Object.seal({y: 1});
sealed.y = 2;     // 可以修改
// sealed.z = 3;  // 不能添加新属性
console.log(sealed);  // {y: 2}

// 可选链操作符
let obj5 = {
    user: {
        address: {
            city: "Beijing"
        }
    }
};

console.log(obj5.user?.address?.city);      // Beijing
console.log(obj5.user?.profile?.name);      // undefined (不报错)
console.log(obj5.user?.getName?.());        // undefined (安全调用方法)
```

### 1.3 基本类型和复合类型的区别

```javascript
// 基本类型：值存储在栈中，赋值是复制值
let a = 10;
let b = a;
b = 20;
console.log(a);  // 10 (a 不受影响)

// 复合类型：值存储在堆中，变量存储引用
let obj1 = {name: "Tom"};
let obj2 = obj1;  // 复制的是引用
obj2.name = "Jerry";
console.log(obj1.name);  // Jerry (obj1 也被改变了)

// 如何复制对象 (浅拷贝)
let original = {a: 1, b: {c: 2}};
let copy1 = {...original};
let copy2 = Object.assign({}, original);

copy1.a = 100;
console.log(original.a);  // 1 (第一层不受影响)

copy1.b.c = 200;
console.log(original.b.c);  // 200 (嵌套对象仍是引用)

// 深拷贝
let deep = JSON.parse(JSON.stringify(original));
deep.b.c = 300;
console.log(original.b.c);  // 200 (不受影响)

// 注意：JSON 方法不能处理 undefined、函数、Symbol、循环引用
// 可以使用 structuredClone (现代浏览器)
let deepCopy = structuredClone(original);
```

### 1.4 空类型

```javascript
// null - 表示"空"或"无"，是有意为之的空值
let empty = null;
console.log(typeof null);  // "object" (历史遗留 bug)
console.log(empty === null);  // true

// undefined - 表示"未定义"
let notDefined;
console.log(notDefined);        // undefined
console.log(typeof undefined);  // "undefined"

// null 和 undefined 的区别
console.log(null == undefined);   // true (宽松相等)
console.log(null === undefined);  // false (严格相等)

// 检查空值
function isNullOrUndefined(value) {
    return value == null;  // 同时检查 null 和 undefined
}

console.log(isNullOrUndefined(null));      // true
console.log(isNullOrUndefined(undefined)); // true
console.log(isNullOrUndefined(0));         // false

// 使用场景
let user = {
    name: "Tom",
    age: undefined,  // 属性存在但未赋值
    address: null    // 属性存在，明确表示没有地址
};
```

### 1.5 其他类型

#### 1.5.1 函数类型

```javascript
// 函数也是一种类型
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(typeof greet);  // "function"

// 函数可以赋值给变量
let sayHello = greet;
console.log(sayHello("Tom"));  // Hello, Tom!

// 函数可以作为参数
function execute(fn, value) {
    return fn(value);
}
console.log(execute(greet, "Jerry"));  // Hello, Jerry!

// 函数可以作为返回值
function createMultiplier(n) {
    return function(x) {
        return x * n;
    };
}
let double = createMultiplier(2);
console.log(double(5));  // 10
```

#### 1.5.2 Date

```javascript
// 创建日期
let now = new Date();
console.log(now);  // 当前时间

let specific = new Date(2024, 0, 15);  // 月份从 0 开始
console.log(specific);  // 2024-01-15

let fromString = new Date("2024-01-15T10:30:00");
console.log(fromString);

let fromTimestamp = new Date(1705312200000);
console.log(fromTimestamp);

// 获取日期部分
let date = new Date();
console.log(date.getFullYear());   // 年
console.log(date.getMonth());      // 月 (0-11)
console.log(date.getDate());       // 日
console.log(date.getDay());        // 星期几 (0-6, 0是周日)
console.log(date.getHours());      // 时
console.log(date.getMinutes());    // 分
console.log(date.getSeconds());    // 秒
console.log(date.getMilliseconds()); // 毫秒
console.log(date.getTime());       // 时间戳

// 设置日期部分
date.setFullYear(2025);
date.setMonth(5);  // 6月
date.setDate(20);
console.log(date);

// 格式化
console.log(date.toISOString());      // ISO 格式
console.log(date.toLocaleDateString()); // 本地日期
console.log(date.toLocaleTimeString()); // 本地时间
console.log(date.toLocaleString());     // 本地日期时间

// 日期计算
let start = new Date("2024-01-01");
let end = new Date("2024-12-31");
let diff = end - start;  // 毫秒差
console.log(diff / (1000 * 60 * 60 * 24));  // 天数

// 获取当前时间戳
console.log(Date.now());  // 毫秒时间戳
```

### 1.6 类型判断

```javascript
// typeof - 判断基本类型
console.log(typeof "hello");    // "string"
console.log(typeof 42);         // "number"
console.log(typeof true);       // "boolean"
console.log(typeof undefined);  // "undefined"
console.log(typeof Symbol());   // "symbol"
console.log(typeof 10n);        // "bigint"
console.log(typeof null);       // "object" (历史遗留问题)
console.log(typeof {});         // "object"
console.log(typeof []);         // "object" (数组也是对象)
console.log(typeof function(){}); // "function"

// Array.isArray - 判断数组
console.log(Array.isArray([]));      // true
console.log(Array.isArray({}));      // false
console.log(Array.isArray("hello")); // false

// instanceof - 判断是否是某个类的实例
console.log([] instanceof Array);    // true
console.log({} instanceof Object);   // true
console.log(new Date() instanceof Date); // true

// Object.prototype.toString - 最准确的类型判断
function getType(value) {
    return Object.prototype.toString.call(value).slice(8, -1);
}

console.log(getType("hello"));     // "String"
console.log(getType(42));          // "Number"
console.log(getType(true));        // "Boolean"
console.log(getType(null));        // "Null"
console.log(getType(undefined));   // "Undefined"
console.log(getType([]));          // "Array"
console.log(getType({}));          // "Object"
console.log(getType(new Date()));  // "Date"
console.log(getType(/abc/));       // "RegExp"
console.log(getType(new Map()));   // "Map"
console.log(getType(new Set()));   // "Set"

// 特殊值判断
console.log(Number.isNaN(NaN));        // true
console.log(Number.isFinite(100));     // true
console.log(Number.isInteger(10));     // true
console.log(Number.isInteger(10.5));   // false
```

### 1.7 类型转换

```javascript
// === 显式转换 ===

// 转为字符串
console.log(String(123));      // "123"
console.log(String(true));     // "true"
console.log(String(null));     // "null"
console.log(String(undefined)); // "undefined"
console.log(String([1, 2, 3])); // "1,2,3"
console.log(String({a: 1}));    // "[object Object]"

console.log((123).toString());  // "123"
console.log((255).toString(16)); // "ff"

// 转为数字
console.log(Number("123"));     // 123
console.log(Number("123.45"));  // 123.45
console.log(Number(""));        // 0
console.log(Number("abc"));     // NaN
console.log(Number(true));      // 1
console.log(Number(false));     // 0
console.log(Number(null));      // 0
console.log(Number(undefined)); // NaN
console.log(Number([1]));       // 1
console.log(Number([1, 2]));    // NaN

console.log(parseInt("123px"));   // 123
console.log(parseFloat("3.14m")); // 3.14
console.log(+"123");              // 123 (一元加号)

// 转为布尔
console.log(Boolean(1));         // true
console.log(Boolean(0));         // false
console.log(Boolean("hello"));   // true
console.log(Boolean(""));        // false
console.log(Boolean(null));      // false
console.log(Boolean(undefined)); // false
console.log(Boolean({}));        // true
console.log(Boolean([]));        // true

console.log(!!"hello");  // true (双重否定)
console.log(!!0);        // false

// === 隐式转换 ===

// 字符串拼接
console.log("3" + 2);       // "32"
console.log(3 + "2");       // "32"
console.log(1 + 2 + "3");   // "33" (先算 1+2=3，再拼接)
console.log("1" + 2 + 3);   // "123"

// 数学运算 (除 + 外)
console.log("6" - 2);       // 4
console.log("6" * "2");     // 12
console.log("6" / "2");     // 3

// 比较运算
console.log("10" > 9);      // true (字符串转数字)
console.log("10" > "9");    // false (字符串比较，按字符编码)

// 逻辑运算中的布尔转换
console.log(1 && 2);        // 2
console.log(0 || "default"); // "default"
console.log(!0);            // true

// == 的隐式转换
console.log(1 == "1");      // true
console.log(0 == false);    // true
console.log(null == undefined); // true
console.log([] == false);   // true
console.log([] == 0);       // true

// 建议：使用 === 避免隐式转换带来的困惑
console.log(1 === "1");     // false
console.log(0 === false);   // false
```

---

## 二、语法

### 2.1 声明

```javascript
// === var ===
// 函数作用域，有变量提升  variable
var x = 1;
var x = 2;  // 可以重复声明
console.log(x);  // 2

function testVar() {
    console.log(a);  // undefined (变量提升)
    var a = 10;
    console.log(a);  // 10
}
testVar();

// var 没有块级作用域
if (true) {
    var b = 20;
}
console.log(b);  // 20 (可以访问)

// === let ===
// 块级作用域，没有变量提升
let y = 1;
// let y = 2;  // 报错！不能重复声明

if (true) {
    let c = 30;
    console.log(c);  // 30
}
// console.log(c);  // 报错！c 不在作用域内

// 暂时性死区 (TDZ)
// console.log(d);  // 报错！不能在声明前访问
let d = 40;

// === const ===
// 块级作用域，必须初始化，不能重新赋值 constant
const PI = 3.14159;
// PI = 3.14;  // 报错！不能重新赋值

// 但 const 对象的属性可以修改
const person = {name: "Tom"};
person.name = "Jerry";  // 可以
person.age = 18;        // 可以
// person = {};         // 报错！不能重新赋值

// 使对象真正不可变
const frozen = Object.freeze({name: "Tom"});
// frozen.name = "Jerry";  // 严格模式报错

// === function 声明 ===
// 函数声明会被提升
sayHi();  // 可以在声明前调用
function sayHi() {
    console.log("Hi!");
}

// 函数表达式不会提升
// sayBye();  // 报错！
const sayBye = function() {
    console.log("Bye!");
};
sayBye();  // 正常调用

// === 最佳实践 ===
// 1. 优先使用 const
// 2. 需要重新赋值时使用 let
// 3. 避免使用 var
```

### 2.2 赋值

```javascript
// 基本赋值
let a = 10;

// 复合赋值
a += 5;   // a = a + 5
a -= 3;   // a = a - 3
a *= 2;   // a = a * 2
a /= 4;   // a = a / 4
a %= 3;   // a = a % 3
a **= 2;  // a = a ** 2
console.log(a);

// 解构赋值 - 数组
let [x, y, z] = [1, 2, 3];
console.log(x, y, z);  // 1 2 3

// 跳过元素
let [first, , third] = [1, 2, 3];
console.log(first, third);  // 1 3

// 默认值
let [p = 10, q = 20] = [5];
console.log(p, q);  // 5 20

// 剩余元素
let [head, ...tail] = [1, 2, 3, 4];
console.log(head);  // 1
console.log(tail);  // [2, 3, 4]

// 交换变量
let m = 1, n = 2;
[m, n] = [n, m];
console.log(m, n);  // 2 1

// 解构赋值 - 对象
let {name, age} = {name: "Tom", age: 18};
console.log(name, age);  // Tom 18

// 重命名
let {name: userName, age: userAge} = {name: "Jerry", age: 20};
console.log(userName, userAge);  // Jerry 20

// 默认值
let {city = "Unknown"} = {};
console.log(city);  // Unknown

// 嵌套解构
let user = {
    info: {
        firstName: "Tom",
        lastName: "Smith"
    },
    scores: [90, 85, 88]
};

let {info: {firstName}, scores: [firstScore]} = user;
console.log(firstName, firstScore);  // Tom 90

// 函数参数解构
function greet({name, age = 0}) {
    console.log(`${name} is ${age} years old`);
}
greet({name: "Tom", age: 18});  // Tom is 18 years old
greet({name: "Jerry"});         // Jerry is 0 years old
```

### 2.3 错误处理

```javascript
// try...catch...finally
try {
    // 可能出错的代码
    let result = someFunction();
    console.log(result);
} catch (error) {
    // 错误处理
    console.log("发生错误:", error.message);
} finally {
    // 无论是否出错都会执行
    console.log("清理工作");
}

// 抛出错误
function divide(a, b) {
    if (b === 0) {
        throw new Error("除数不能为0");
    }
    return a / b;
}

try {
    console.log(divide(10, 2));  // 5
    console.log(divide(10, 0));  // 抛出错误
} catch (e) {
    console.log("捕获错误:", e.message);
}

// 错误类型
try {
    // 语法错误 (不能被 try-catch 捕获，在解析阶段就报错)
    // eval("let a = ");

    // 引用错误
    // console.log(undeclaredVar);

    // 类型错误
    // null.toString();

    // 范围错误
    // new Array(-1);

    throw new TypeError("这是一个类型错误");
} catch (e) {
    if (e instanceof TypeError) {
        console.log("类型错误:", e.message);
    } else if (e instanceof ReferenceError) {
        console.log("引用错误:", e.message);
    } else {
        console.log("其他错误:", e.message);
    }
}

// 自定义错误
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = "ValidationError";
    }
}

function validateAge(age) {
    if (age < 0 || age > 150) {
        throw new ValidationError("年龄必须在 0-150 之间");
    }
    return true;
}

try {
    validateAge(200);
} catch (e) {
    if (e instanceof ValidationError) {
        console.log("验证错误:", e.message);
    }
}

// 异步错误处理
async function fetchData() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        return data;
    } catch (error) {
        console.log("请求失败:", error.message);
        return null;
    }
}
```

---

## 三、流程控制

### 3.1 条件语句

```javascript
// if 语句
let score = 85;

if (score >= 90) {
    console.log("优秀");
} else if (score >= 80) {
    console.log("良好");
} else if (score >= 60) {
    console.log("及格");
} else {
    console.log("不及格");
}
// 输出: 良好

// 三元运算符  

let status
if (age >= 18) {
    status = '成年'
} else {
    status = "未成年";
}

let age = 18;
let status = age >= 18 ? "成年" : "未成年";
console.log(status);  // 成年

// 嵌套三元
let num = 0;
let result = num > 0 
    ? "正数" 
    : num < 0 
        ? "负数" 
        : "零";
console.log(result);  // 零

// switch 语句
let day = 4;
switch (day) {
    case 1:
        console.log("星期一");
        break;
    case 2:
        console.log("星期二");
        break;
    case 3:
        console.log("星期三");
        break;
    case 4:
        console.log("星期四");
    case 5:
        console.log("星期五");
        break;
    case 6:
    case 7:
        console.log("周末");
        break;
    default:
        console.log("无效的日期");
}
// 输出: 星期三

// switch 也可以用于范围判断
let grade = 85;
switch (true) {
    case grade >= 90:
        console.log("A");
        break;
    case grade >= 80:
        console.log("B");
        break;
    case grade >= 70:
        console.log("C");
        break;
    default:
        console.log("D");
}
// 输出: B
```

### 3.2 循环语句

// i += 1;
// i = i + 1

```javascript
// for 循环
for (let i = 0; i < 3; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}

let i = 0
for (; ;) {
    if (i >= 5) {
        break
    }
    console.log(i);  // 0, 1, 2, 3, 4
    i++
}

// for...of (遍历可迭代对象的值)
let arr = ["a", "b", "c"];
for (let value of arr) {
    console.log(value);  // a, b, c
}



// for...in (遍历对象的键) key, value pair

let obj = {x: 1, y: 2, z: 3};
const keys = Object.keys(obj);
for (let i = 0; i < keys.length; i++) {
    const key = keys[i]
    console.log(`${key}: ${obj[key]}`)
}


let obj = {x: 1, y: 2, z: 3};
for (let key in obj) {
    console.log(`${key}: ${obj[key]}`);  // x: 1, y: 2, z: 3
}

// while 循环
let count = 0;
while (count < 3) {
    console.log(count);  // 0, 1, 2
    count++;
}

// do...while 循环 (至少执行一次)
let n = 0;
do {
    console.log(n);  // 0
    n++;
} while (n < 0);  // 条件为 false，但已经执行了一次
```

### 3.3 控制语句

```javascript
// break - 跳出循环
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break;  // 当 i 为 5 时跳出循环
    }
    console.log(i);  // 0, 1, 2, 3, 4
}

function test() {
    for (let j = 0; j < 10; j++) {
        for (let i = 0; i < 10; i++) {
            if (i === 11) {
                return [i, j];  // 当 i 为 5 时跳出循环
            }
            console.log(i);  // 0, 1, 2, 3, 4
        }
    }
    return 'not found'
}

// continue - 跳过当前迭代
for (let i = 0; i < 5; i++) {
    if (i === 2) {
        continue;  // 跳过 2
    }
    console.log(i);  // 0, 1, 3, 4
}

// 标签语句 (用于嵌套循环)
for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        if (i === 1 && j === 1) {
            break;  // 跳出外层循环
        }
        console.log(`i=${i}, j=${j}`);
    }
    break
}
// 输出:
// i=0, j=0
// i=0, j=1
// i=0, j=2
// i=1, j=0

// return - 从函数返回
function findFirst(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i;  // 找到后立即返回
        }
    }
    return -1;  // 未找到
}

console.log(findFirst([1, 2, 3, 4, 5], 3));  // 2
console.log(findFirst([1, 2, 3, 4, 5], 6));  // -1
```

---

## 四、作用域

```javascript
// 全局作用域
var globalVar = "我是全局变量";
let globalLet = "我也是全局变量";

function showGlobal() {
    console.log(globalVar);  // 可以访问
    console.log(globalLet);  // 可以访问
}
showGlobal();

// 函数作用域
function outer() {
    var functionVar = "函数内变量";
    let functionLet = "函数内 let";

    function inner() {
        console.log(functionVar);  // 可以访问外层函数的变量
        console.log(functionLet);
    }
    inner();
}
outer();
// console.log(functionVar);  // 报错！函数外无法访问

// 块级作用域 (let 和 const)
if (true) {
    var blockVar = "var 没有块级作用域";
    let blockLet = "let 有块级作用域";
    const blockConst = "const 有块级作用域";
}
console.log(blockVar);    // 可以访问
// console.log(blockLet);  // 报错！
// console.log(blockConst); // 报错！

// 作用域链
let a = 1;

function first() {
    let b = 2;

    function second() {
        let c = 3;
        console.log(a, b, c);  // 1, 2, 3 (沿作用域链向上查找)
    }
    second();
}
first();

// 变量遮蔽 (Shadowing)
let x = "外层";

function test() {
    let x = "内层";  // 遮蔽外层的 x
    console.log(x);  // 内层
}
test();
console.log(x);  // 外层

// 闭包 (Closure)
function createCounter() {
    let count = 0;  // 私有变量

    return {
        increment() {
            count++;
            return count;
        },
        decrement() {
            count--;
            return count;
        },
        getCount() {
            return count;
        }
    };
}

let counter = createCounter();
console.log(counter.increment());  // 1
console.log(counter.increment());  // 2
console.log(counter.decrement());  // 1
console.log(counter.getCount());   // 1
// console.log(count);  // 报错！外部无法直接访问 count

// 闭包的常见问题
// 问题代码
for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log("var:", i);  // 3, 3, 3 (都是 3)
    }, 100);
}

// 解决方案1：使用 let
for (let j = 0; j < 3; j++) {
    setTimeout(function() {
        console.log("let:", j);  // 0, 1, 2
    }, 100);
}

// 解决方案2：使用闭包
for (var k = 0; k < 3; k++) {
    (function(k) {
        setTimeout(function() {
            console.log("IIFE:", k);  // 0, 1, 2
        }, 100);
    })(k);
}
```

---

## 五、this

```javascript
// 1. 全局环境中的 this
console.log(this);  // 浏览器中是 window，Node.js 中是 global 或 {}

// 2. 普通函数中的 this
function showThis() {
    console.log(this);
}
showThis();  // 非严格模式: window/global，严格模式: undefined

// 3. 对象方法中的 this
let user = {
    name: "Tom",
    greet() {
        console.log(`Hello, I'm ${this.name}`);
    }
};
user.greet();  // Hello, I'm Tom

// 注意：方法赋值给变量后，this 会丢失
let greet = user.greet;
greet();  // Hello, I'm undefined

// 4. 构造函数中的 this
function Person(name) {
    this.name = name;
    this.sayHi = function() {
        console.log(`Hi, I'm ${this.name}`);
    };
}
let person = new Person("Jerry");
person.sayHi();  // Hi, I'm Jerry

// 5. 箭头函数中的 this (继承外层作用域)
let obj = {
    name: "Tom",
    regularFunc: function() {
        console.log("regular:", this.name);  // Tom
    },
    arrowFunc: () => {
        console.log("arrow:", this.name);    // undefined (继承全局)
    },
    nested: function() {
        // 普通函数嵌套
        setTimeout(function() {
            console.log("nested regular:", this.name);  // undefined
        }, 100);

        // 箭头函数嵌套
        setTimeout(() => {
            console.log("nested arrow:", this.name);    // Tom
        }, 100);
    }
};
obj.regularFunc();
obj.arrowFunc();
obj.nested();

// 6. 显式绑定 this

// call - 立即调用，参数逐个传递
function introduce(greeting, punctuation) {
    console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}
let person1 = {name: "Alice"};
introduce.call(person1, "Hello", "!");  // Hello, I'm Alice!

// apply - 立即调用，参数以数组传递
introduce.apply(person1, ["Hi", "?"]);  // Hi, I'm Alice?

// bind - 返回新函数，不立即调用
let boundIntroduce = introduce.bind(person1);
boundIntroduce("Hey", ".");  // Hey, I'm Alice.

// bind 可以预设参数
let boundHello = introduce.bind(person1, "Hello");
boundHello("!");  // Hello, I'm Alice!

// 7. Class 中的 this
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound`);
    }

    // 使用箭头函数保持 this
    delaySpeak = () => {
        setTimeout(() => {
            console.log(`${this.name} speaks after delay`);
        }, 100);
    }
}

let dog = new Animal("Dog");
dog.speak();       // Dog makes a sound
dog.delaySpeak();  // Dog speaks after delay

// 8. 事件处理中的 this
// 在浏览器中:
// button.addEventListener('click', function() {
//     console.log(this);  // button 元素
// });
//
// button.addEventListener('click', () => {
//     console.log(this);  // window (箭头函数)
// });
```

---

## 六、函数

### 6.1 函数声明方式

```javascript
// 1. 函数声明 (Function Declaration)
function add(a, b) {
    return a + b;
}
console.log(add(1, 2));  // 3

// 2. 函数表达式 (Function Expression)
const subtract = function(a, b) {
    return a - b;
};
console.log(subtract(5, 3));  // 2

// 3. 箭头函数 (Arrow Function)
const multiply = (a, b) => {
    return a * b;
};
console.log(multiply(3, 4));  // 12

// 箭头函数简写
const double = x => x * 2;  // 单参数可省略括号，单表达式可省略 return
console.log(double(5));  // 10

const getObject = () => ({name: "Tom"});  // 返回对象需要括号
console.log(getObject());  // {name: "Tom"}

// 4. 立即执行函数 (IIFE)
(function() {
    console.log("立即执行!");
})();

(() => {
    console.log("箭头函数也可以!");
})();

// 5. 构造函数
const divide = new Function('a', 'b', 'return a / b');
console.log(divide(10, 2));  // 5 (不推荐使用)
```

### 6.2 函数参数

```javascript
// 默认参数
function greet(name = "Guest", greeting = "Hello") {
    console.log(`${greeting}, ${name}!`);
}
greet();              // Hello, Guest!
greet("Tom");         // Hello, Tom!
greet("Tom", "Hi");   // Hi, Tom!

// 剩余参数 (Rest Parameters)
function sum(...numbers) {
    return numbers.reduce((acc, n) => acc + n, 0);
}
console.log(sum(1, 2, 3, 4, 5));  // 15

function logInfo(first, second, ...rest) {
    console.log("First:", first);
    console.log("Second:", second);
    console.log("Rest:", rest);
}
logInfo(1, 2, 3, 4, 5);
// First: 1
// Second: 2
// Rest: [3, 4, 5]

// 展开运算符 (Spread Operator)
let nums = [1, 2, 3];
console.log(Math.max(...nums));  // 3

function add3(a, b, c) {
    return a + b + c;
}
console.log(add3(...nums));  // 6

// arguments 对象 (非箭头函数)
function oldSum() {
    let total = 0;
    for (let i = 0; i < arguments.length; i++) {
        total += arguments[i];
    }
    return total;
}
console.log(oldSum(1, 2, 3));  // 6

// 参数解构
function createUser({name, age, city = "Unknown"}) {
    return `${name}, ${age}, ${city}`;
}
console.log(createUser({name: "Tom", age: 18}));  // Tom, 18, Unknown

function processArray([first, second, ...rest]) {
    console.log(first, second, rest);
}
processArray([1, 2, 3, 4, 5]);  // 1 2 [3, 4, 5]
```

### 6.3 箭头函数 vs 普通函数

```javascript
// 1. this 绑定不同
const obj = {
    name: "Tom",
    regular: function() {
        return this.name;
    },
    arrow: () => {
        return this.name;  // 继承外层 this
    }
};
console.log(obj.regular());  // Tom
console.log(obj.arrow());    // undefined

// 2. 没有 arguments 对象
const arrowFunc = () => {
    // console.log(arguments);  // 报错！
};

// 3. 不能作为构造函数
const ArrowClass = () => {};
// new ArrowClass();  // 报错！

// 4. 没有 prototype 属性
function RegularFunc() {}
const ArrowFunc = () => {};
console.log(RegularFunc.prototype);  // {}
console.log(ArrowFunc.prototype);    // undefined

// 5. 不能使用 yield (不能作为生成器)
```

### 6.4 高阶函数

```javascript
// 函数作为参数
function operate(a, b, operation) {
    return operation(a, b);
}

console.log(operate(5, 3, (x, y) => x + y));  // 8
console.log(operate(5, 3, (x, y) => x * y));  // 15

// 函数作为返回值
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const triple = createMultiplier(3);
console.log(triple(5));  // 15

// 函数柯里化 (Currying)
function curry(fn) {
    return function curried(...args) {
        if (args.length >= fn.length) {
            return fn.apply(this, args);
        }
        return function(...moreArgs) {
            return curried.apply(this, args.concat(moreArgs));
        };
    };
}

function add(a, b, c) {
    return a + b + c;
}

const curriedAdd = curry(add);
console.log(curriedAdd(1)(2)(3));     // 6
console.log(curriedAdd(1, 2)(3));     // 6
console.log(curriedAdd(1)(2, 3));     // 6

// 函数组合 (Composition)
const compose = (...fns) => x => fns.reduceRight((acc, fn) => fn(acc), x);
const pipe = (...fns) => x => fns.reduce((acc, fn) => fn(acc), x);

const addOne = x => x + 1;
const double = x => x * 2;
const square = x => x * x;

const composed = compose(square, double, addOne);
console.log(composed(2));  // 36: (2+1)*2=6, 6^2=36

const piped = pipe(addOne, double, square);
console.log(piped(2));  // 36: 2+1=3, 3*2=6, 6^2=36
```

### 6.5 内置函数和对象

```javascript
// === JSON ===
let user = {
    name: "Tom",
    age: 18,
    hobbies: ["reading", "gaming"]
};

// 对象转 JSON 字符串
let jsonStr = JSON.stringify(user);
console.log(jsonStr);  // {"name":"Tom","age":18,"hobbies":["reading","gaming"]}

// 格式化输出
console.log(JSON.stringify(user, null, 2));

// 自定义序列化
console.log(JSON.stringify(user, ["name", "age"]));  // 只包含指定属性

// JSON 字符串转对象
let parsed = JSON.parse(jsonStr);
console.log(parsed.name);  // Tom

// 深拷贝 (注意局限性)
let copy = JSON.parse(JSON.stringify(user));

// === 其他全局函数 ===
// 编码/解码 URI
let url = "https://example.com?name=张三&age=18";
let encoded = encodeURIComponent(url);
console.log(encoded);
console.log(decodeURIComponent(encoded));

// 编码/解码 URI (不编码特殊字符)
console.log(encodeURI(url));
console.log(decodeURI(encodeURI(url)));

// 定时器
let timeoutId = setTimeout(() => {
    console.log("延迟执行");
}, 1000);
clearTimeout(timeoutId);  // 取消

let intervalId = setInterval(() => {
    console.log("每秒执行");
}, 1000);
setTimeout(() => clearInterval(intervalId), 3000);  // 3秒后停止

// eval (不推荐使用，有安全风险)
// let result = eval("1 + 2");
// console.log(result);  // 3
```

---

## 七、Class

```javascript
// === 基本语法 ===
class Person {
    // 构造函数
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    // 实例方法
    greet() {
        console.log(`Hello, I'm ${this.name}`);
    }

    // Getter
    get info() {
        return `${this.name}, ${this.age} years old`;
    }

    // Setter
    set info(value) {
        [this.name, this.age] = value.split(", ");
    }

    // 静态方法 (通过类调用，不通过实例)
    static create(name, age) {
        return new Person(name, age);
    }

    // 静态属性
    static species = "Homo sapiens";
}

// 使用
let person = new Person("Tom", 18);
person.greet();              // Hello, I'm Tom
console.log(person.info);    // Tom, 18 years old

person.info = "Jerry, 20";
console.log(person.name);    // Jerry

let person2 = Person.create("Alice", 25);
console.log(Person.species); // Homo sapiens

// === 私有字段 (以 # 开头) ===
class BankAccount {
    #balance = 0;  // 私有属性

    constructor(initialBalance) {
        this.#balance = initialBalance;
    }

    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
        }
    }

    withdraw(amount) {
        if (amount > 0 && amount <= this.#balance) {
            this.#balance -= amount;
            return amount;
        }
        return 0;
    }

    get balance() {
        return this.#balance;
    }

    // 私有方法
    #validateAmount(amount) {
        return amount > 0;
    }
}

let account = new BankAccount(100);
account.deposit(50);
console.log(account.balance);  // 150
// console.log(account.#balance);  // 语法错误！无法访问私有属性

// === 继承 ===
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound`);
    }

    static info() {
        console.log("This is an Animal class");
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name);  // 调用父类构造函数
        this.breed = breed;
    }

    speak() {
        super.speak();  // 调用父类方法
        console.log(`${this.name} barks`);
    }

    fetch() {
        console.log(`${this.name} fetches the ball`);
    }
}

let dog = new Dog("Buddy", "Golden Retriever");
dog.speak();
// Buddy makes a sound
// Buddy barks

dog.fetch();  // Buddy fetches the ball

Dog.info();   // This is an Animal class (继承静态方法)

// 检查继承关系
console.log(dog instanceof Dog);     // true
console.log(dog instanceof Animal);  // true

// === 类表达式 ===
const MyClass = class {
    constructor(value) {
        this.value = value;
    }
};

// === Mixin 模式 (多重继承的替代方案) ===
let SpeakerMixin = {
    speak(text) {
        console.log(`Speaking: ${text}`);
    }
};

let WalkerMixin = {
    walk() {
        console.log("Walking...");
    }
};

class Robot {
    constructor(name) {
        this.name = name;
    }
}

// 混入方法
Object.assign(Robot.prototype, SpeakerMixin, WalkerMixin);

let robot = new Robot("R2D2");
robot.speak("Hello!");  // Speaking: Hello!
robot.walk();           // Walking...
```

---

## 八、Promise 和 async/await

### 8.1 回调地狱问题

```javascript
// 模拟异步操作
function fetchUser(userId, callback) {
    setTimeout(() => {
        callback({id: userId, name: "Tom"});
    }, 1000);
}

function fetchOrders(userId, callback) {
    setTimeout(() => {
        callback([{id: 1, item: "Book"}, {id: 2, item: "Pen"}]);
    }, 1000);
}

function fetchOrderDetails(orderId, callback) {
    setTimeout(() => {
        callback({id: orderId, price: 100, quantity: 2});
    }, 1000);
}

// 回调地狱 (Callback Hell)
fetchUser(1, user => {
    console.log("User:", user);
    fetchOrders(user.id, orders => {
        console.log("Orders:", orders);
        fetchOrderDetails(orders[0].id, details => {
            console.log("Details:", details);
            // 继续嵌套...
        });
    });
});
```

### 8.2 Promise 基础

```javascript
// 创建 Promise
let promise = new Promise((resolve, reject) => {
    // 异步操作
    setTimeout(() => {
        let success = true;
        if (success) {
            resolve("操作成功");
        } else {
            reject(new Error("操作失败"));
        }
    }, 1000);
});

// 使用 Promise
promise
    .then(result => {
        console.log("成功:", result);
    })
    .catch(error => {
        console.log("失败:", error.message);
    })
    .finally(() => {
        console.log("完成");
    });

// Promise 状态
// pending -> fulfilled (resolve)
// pending -> rejected (reject)

// 将回调改写为 Promise
function fetchUserPromise(userId) {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve({id: userId, name: "Tom"});
        }, 1000);
    });
}

function fetchOrdersPromise(userId) {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve([{id: 1, item: "Book"}, {id: 2, item: "Pen"}]);
        }, 1000);
    });
}

// 链式调用
fetchUserPromise(1)
    .then(user => {
        console.log("User:", user);
        return fetchOrdersPromise(user.id);
    })
    .then(orders => {
        console.log("Orders:", orders);
    })
    .catch(error => {
        console.log("Error:", error);
    });
```

### 8.3 Promise 静态方法

```javascript
// Promise.resolve / Promise.reject
let resolved = Promise.resolve("已完成");
let rejected = Promise.reject(new Error("已拒绝"));

resolved.then(console.log);  // 已完成
rejected.catch(e => console.log(e.message));  // 已拒绝

// Promise.all - 所有 Promise 都成功才成功
let p1 = Promise.resolve(1);
let p2 = Promise.resolve(2);
let p3 = Promise.resolve(3);

Promise.all([p1, p2, p3])
    .then(results => {
        console.log(results);  // [1, 2, 3]
    });

// 如果有一个失败，整体失败
let p4 = Promise.reject(new Error("失败"));
Promise.all([p1, p2, p4])
    .catch(error => {
        console.log("有一个失败了:", error.message);
    });

// Promise.allSettled - 等待所有 Promise 完成，无论成功失败
Promise.allSettled([p1, p2, p4])
    .then(results => {
        console.log(results);
        // [
        //   {status: "fulfilled", value: 1},
        //   {status: "fulfilled", value: 2},
        //   {status: "rejected", reason: Error}
        // ]
    });

// Promise.race - 返回第一个完成的 Promise
let slow = new Promise(resolve => setTimeout(() => resolve("慢"), 2000));
let fast = new Promise(resolve => setTimeout(() => resolve("快"), 1000));

Promise.race([slow, fast])
    .then(result => {
        console.log(result);  // 快
    });

// Promise.any - 返回第一个成功的 Promise
let fail1 = Promise.reject(new Error("失败1"));
let fail2 = Promise.reject(new Error("失败2"));
let success = Promise.resolve("成功");

Promise.any([fail1, fail2, success])
    .then(result => {
        console.log(result);  // 成功
    });

// 所有都失败则报错
Promise.any([fail1, fail2])
    .catch(error => {
        console.log(error);  // AggregateError
    });
```

### 8.4 async/await

```javascript
// async 函数自动返回 Promise
async function hello() {
    return "Hello";
}
hello().then(console.log);  // Hello

// await 等待 Promise 完成
async function fetchData() {
    console.log("开始获取数据...");

    let user = await fetchUserPromise(1);
    console.log("User:", user);

    let orders = await fetchOrdersPromise(user.id);
    console.log("Orders:", orders);

    return {user, orders};
}

fetchData().then(result => {
    console.log("最终结果:", result);
});

// 错误处理
async function fetchWithError() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        return data;
    } catch (error) {
        console.log("请求失败:", error.message);
        return null;
    }
}

// 并行执行
async function parallel() {
    // 串行执行 (慢)
    let result1 = await fetchUserPromise(1);
    let result2 = await fetchUserPromise(2);

    // 并行执行 (快)
    let [user1, user2] = await Promise.all([
        fetchUserPromise(1),
        fetchUserPromise(2)
    ]);

    console.log(user1, user2);
}

// 循环中使用 await
async function sequential() {
    let ids = [1, 2, 3];

    // 顺序执行
    for (let id of ids) {
        let user = await fetchUserPromise(id);
        console.log(user);
    }
}

async function concurrent() {
    let ids = [1, 2, 3];

    // 并发执行
    let promises = ids.map(id => fetchUserPromise(id));
    let users = await Promise.all(promises);
    console.log(users);
}

// 顶层 await (ES2022, 仅在模块中)
// let data = await fetch("https://api.example.com/data");

// async 箭头函数
const asyncArrow = async () => {
    let result = await Promise.resolve("done");
    return result;
};

// async 类方法
class DataFetcher {
    async fetch(url) {
        let response = await fetch(url);
        return response.json();
    }
}
```

### 8.5 实际应用示例

```javascript
// 带超时的请求
function fetchWithTimeout(url, timeout = 5000) {
    return Promise.race([
        fetch(url),
        new Promise((_, reject) =>
            setTimeout(() => reject(new Error("请求超时")), timeout)
        )
    ]);
}

// 重试机制
async function fetchWithRetry(url, retries = 3) {
    for (let i = 0; i < retries; i++) {
        try {
            let response = await fetch(url);
            return response.json();
        } catch (error) {
            console.log(`第 ${i + 1} 次尝试失败`);
            if (i === retries - 1) throw error;
            await new Promise(r => setTimeout(r, 1000 * (i + 1)));  // 递增延迟
        }
    }
}

// 并发限制
async function parallelLimit(tasks, limit) {
    let results = [];
    let executing = [];

    for (let task of tasks) {
        let p = Promise.resolve().then(() => task());
        results.push(p);

        if (limit <= tasks.length) {
            let e = p.then(() => executing.splice(executing.indexOf(e), 1));
            executing.push(e);

            if (executing.length >= limit) {
                await Promise.race(executing);
            }
        }
    }

    return Promise.all(results);
}

// 使用示例
let tasks = [
    () => fetchUserPromise(1),
    () => fetchUserPromise(2),
    () => fetchUserPromise(3),
    () => fetchUserPromise(4),
    () => fetchUserPromise(5)
];

// 同时最多执行 2 个任务
parallelLimit(tasks, 2).then(results => {
    console.log("所有任务完成:", results);
});
```

---

## 总结

这份教程涵盖了 JavaScript 的核心概念：

1. **类型** - 基本类型、复合类型、类型判断和转换
2. **语法** - 变量声明、解构赋值、错误处理
3. **流程控制** - 条件、循环、控制语句
4. **作用域** - 全局、函数、块级作用域和闭包
5. **this** - 不同场景下的 this 指向
6. **函数** - 声明方式、参数、箭头函数、高阶函数
7. **Class** - 类的基本语法、继承、私有字段
8. **异步** - Promise 和 async/await

所有示例代码都可以直接在浏览器控制台或 Node.js 环境中运行。
