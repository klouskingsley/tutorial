# JavaScript 初学者练习题

> 这些题目专为编程初学者设计，不涉及复杂的数据结构，每道题都有现实场景对应，帮助你锻炼将问题转化为代码的思维。
>
> 每道题都提供了函数定义和测试用例，你只需要填写函数体，然后运行代码验证答案是否正确。

---

## 第一部分：变量与基础运算

### 题目 1：计算购物总价

**场景**：你去超市买了 3 个苹果（每个 5 元）和 2 瓶牛奶（每瓶 8 元）

**要求**：计算总价，并输出结果

```javascript
// 在这里完成你的代码
const applePrice = 5
const appleCount = 3
const milkPrice = 8
const milkCount = 2

// 计算总价
const total = // 你的代码

console.log(total) // 应该输出 31
```

---

### 题目 2：温度转换

**场景**：天气预报显示今天气温是 30 摄氏度，你的外国朋友问你这是多少华氏度

**要求**：写一个函数 `celsiusToFahrenheit`，输入摄氏度，返回华氏度

**公式**：华氏度 = 摄氏度 × 9/5 + 32

```javascript
// 在这里完成你的代码
function celsiusToFahrenheit(celsius) {

}

// 测试用例
const testCases = [
  { args: [30], expected: 86 },
  { args: [0], expected: 32 },
  { args: [100], expected: 212 },
  { args: [-40], expected: -40 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = celsiusToFahrenheit(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 3：计算折扣价

**场景**：商店搞活动，所有商品打 8 折

**要求**：写一个函数 `calculateDiscount`，输入原价，返回折后价（保留两位小数，返回字符串）

```javascript
// 在这里完成你的代码
function calculateDiscount(originalPrice) {

}

// 测试用例
const testCases = [
  { args: [100], expected: '80.00' },
  { args: [75], expected: '60.00' },
  { args: [99.99], expected: '79.99' },
  { args: [0], expected: '0.00' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = calculateDiscount(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第二部分：条件判断

### 题目 4：判断成绩等级

**场景**：老师需要根据分数给学生评等级

**要求**：写一个函数 `getGrade`，输入分数（0-100），返回等级

**规则**：
- 90 及以上：A
- 80-89：B
- 70-79：C
- 60-69：D
- 60 以下：F

```javascript
// 在这里完成你的代码
function getGrade(score) {

}

// 测试用例
const testCases = [
  { args: [95], expected: 'A' },
  { args: [90], expected: 'A' },
  { args: [82], expected: 'B' },
  { args: [75], expected: 'C' },
  { args: [65], expected: 'D' },
  { args: [55], expected: 'F' },
  { args: [0], expected: 'F' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = getGrade(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 5：判断闰年

**场景**：你想知道某一年是不是闰年（闰年 2 月有 29 天）

**要求**：写一个函数 `isLeapYear`，输入年份，返回 `true` 或 `false`

**规则**：能被 4 整除但不能被 100 整除，或者能被 400 整除的年份是闰年

```javascript
// 在这里完成你的代码
function isLeapYear(year) {

}

// 测试用例
const testCases = [
  { args: [2024], expected: true },
  { args: [2023], expected: false },
  { args: [2000], expected: true },
  { args: [1900], expected: false },
  { args: [2100], expected: false }
]

testCases.forEach(({ args, expected }, index) => {
  const result = isLeapYear(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 6：电影票价计算

**场景**：电影院票价规则如下：
- 普通票：50 元
- 学生票：半价
- 周二会员日：所有票再打 8 折

**要求**：写一个函数 `calculateTicketPrice`，输入是否学生（boolean）、是否周二（boolean），返回最终票价

```javascript
// 在这里完成你的代码
function calculateTicketPrice(isStudent, isTuesday) {

}

// 测试用例
const testCases = [
  { args: [false, false], expected: 50 },
  { args: [true, false], expected: 25 },
  { args: [false, true], expected: 40 },
  { args: [true, true], expected: 20 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = calculateTicketPrice(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第三部分：循环

### 题目 7：计算 1 到 N 的和

**场景**：小明想知道从 1 加到 100 等于多少

**要求**：写一个函数 `sumToN`，输入 N，返回 1+2+3+...+N 的结果

```javascript
// 在这里完成你的代码
function sumToN(n) {

}

// 测试用例
const testCases = [
  { args: [5], expected: 15 },
  { args: [10], expected: 55 },
  { args: [100], expected: 5050 },
  { args: [1], expected: 1 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = sumToN(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 8：找出所有能被 3 整除的数

**场景**：老师让你找出 1 到 50 之间所有能被 3 整除的数

**要求**：写一个函数 `findDivisibleByThree`，输入范围上限 N，返回一个数组，包含 1 到 N 中所有能被 3 整除的数

```javascript
// 在这里完成你的代码
function findDivisibleByThree(n) {

}

// 测试用例
const testCases = [
  { args: [10], expected: [3, 6, 9] },
  { args: [15], expected: [3, 6, 9, 12, 15] },
  { args: [2], expected: [] },
  { args: [3], expected: [3] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = findDivisibleByThree(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 9：生成乘法表结果

**场景**：生成一个九九乘法表的计算结果

**要求**：写一个函数 `multiplicationTable`，返回一个二维数组，`result[i][j]` 表示 `i × j` 的结果（i 和 j 从 0 到 9）

```javascript
// 在这里完成你的代码
function multiplicationTable() {

}

// 测试用例
const table = multiplicationTable()
const testCases = [
  { i: 2, j: 3, expected: 6 },
  { i: 7, j: 8, expected: 56 },
  { i: 9, j: 9, expected: 81 },
  { i: 0, j: 5, expected: 0 },
  { i: 1, j: 1, expected: 1 }
]

testCases.forEach(({ i, j, expected }, index) => {
  const result = table[i][j]
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: table[${i}][${j}] 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第四部分：数组操作

### 题目 10：找出最高分

**场景**：班级考试成绩出来了，成绩列表是 `[78, 92, 85, 67, 95, 88]`

**要求**：写一个函数 `findMax`，输入成绩数组，返回最高分

**限制**：不使用 `Math.max`，自己用循环实现

```javascript
// 在这里完成你的代码
function findMax(arr) {

}

// 测试用例
const testCases = [
  { args: [[78, 92, 85, 67, 95, 88]], expected: 95 },
  { args: [[60, 70, 80]], expected: 80 },
  { args: [[100]], expected: 100 },
  { args: [[-5, -2, -10]], expected: -2 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = findMax(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 11：计算平均分

**场景**：需要计算班级平均分

**要求**：写一个函数 `calculateAverage`，输入成绩数组，返回平均分（保留一位小数，返回字符串）

```javascript
// 在这里完成你的代码
function calculateAverage(arr) {

}

// 测试用例
const testCases = [
  { args: [[80, 90, 100]], expected: '90.0' },
  { args: [[78, 92, 85, 67, 95, 88]], expected: '84.2' },
  { args: [[100]], expected: '100.0' },
  { args: [[0, 0, 0]], expected: '0.0' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = calculateAverage(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 12：筛选及格的学生

**场景**：老师想知道哪些学生及格了（60 分及以上）

**要求**：写一个函数 `filterPassed`，输入成绩数组，返回一个新数组，只包含及格的成绩

```javascript
// 在这里完成你的代码
function filterPassed(scores) {

}

// 测试用例
const testCases = [
  { args: [[78, 55, 92, 48, 60, 85]], expected: [78, 92, 60, 85] },
  { args: [[30, 40, 50]], expected: [] },
  { args: [[60, 70, 80]], expected: [60, 70, 80] },
  { args: [[59, 60, 61]], expected: [60, 61] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = filterPassed(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 13：统计投票结果

**场景**：班级投票选班长，投票结果是 `['小明', '小红', '小明', '小华', '小红', '小明']`

**要求**：写一个函数 `countVotes`，输入投票数组，返回一个对象，统计每个人的得票数

```javascript
// 在这里完成你的代码
function countVotes(votes) {

}

// 测试用例
const testCases = [
  {
    args: [['小明', '小红', '小明', '小华', '小红', '小明']],
    expected: { '小明': 3, '小红': 2, '小华': 1 }
  },
  {
    args: [['A', 'B', 'A', 'A', 'C']],
    expected: { 'A': 3, 'B': 1, 'C': 1 }
  },
  {
    args: [['X']],
    expected: { 'X': 1 }
  }
]

testCases.forEach(({ args, expected }, index) => {
  const result = countVotes(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第五部分：字符串操作

### 题目 14：统计字符出现次数

**场景**：统计一句话中某个字符出现了多少次

**要求**：写一个函数 `countChar`，输入字符串和目标字符，返回该字符出现的次数

```javascript
// 在这里完成你的代码
function countChar(str, char) {

}

// 测试用例
const testCases = [
  { args: ['hello world', 'l'], expected: 3 },
  { args: ['javascript', 'a'], expected: 2 },
  { args: ['test', 'x'], expected: 0 },
  { args: ['aaa', 'a'], expected: 3 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = countChar(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 15：反转字符串

**场景**：把一个单词倒过来写

**要求**：写一个函数 `reverseString`，输入字符串，返回反转后的字符串

```javascript
// 在这里完成你的代码
function reverseString(str) {

}

// 测试用例
const testCases = [
  { args: ['hello'], expected: 'olleh' },
  { args: ['javascript'], expected: 'tpircsavaj' },
  { args: ['a'], expected: 'a' },
  { args: ['12345'], expected: '54321' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = reverseString(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 16：判断回文

**场景**：有些词正着读和倒着读一样，比如 "level"、"noon"

**要求**：写一个函数 `isPalindrome`，判断输入的字符串是否是回文，返回 `true` 或 `false`

```javascript
// 在这里完成你的代码
function isPalindrome(str) {

}

// 测试用例
const testCases = [
  { args: ['level'], expected: true },
  { args: ['noon'], expected: true },
  { args: ['hello'], expected: false },
  { args: ['a'], expected: true },
  { args: ['ab'], expected: false }
]

testCases.forEach(({ args, expected }, index) => {
  const result = isPalindrome(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第六部分：综合应用

### 题目 17：简易购物车

**场景**：实现一个简单的购物车计算功能

**要求**：写一个函数 `calculateCartTotal`，输入商品列表（每个商品有名称、单价、数量），计算购物车总价

```javascript
// 在这里完成你的代码
function calculateCartTotal(cart) {

}

// 测试用例
const testCases = [
  {
    args: [[
      { name: '苹果', price: 5, quantity: 3 },
      { name: '牛奶', price: 8, quantity: 2 },
      { name: '面包', price: 10, quantity: 1 }
    ]],
    expected: 41
  },
  {
    args: [[{ name: '可乐', price: 3, quantity: 10 }]],
    expected: 30
  },
  {
    args: [[]],
    expected: 0
  }
]

testCases.forEach(({ args, expected }, index) => {
  const result = calculateCartTotal(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 18：查找重复元素

**场景**：检查一个数组中是否有重复的元素

**要求**：写一个函数 `hasDuplicate`，输入数组，返回 `true`（有重复）或 `false`（无重复）

```javascript
// 在这里完成你的代码
function hasDuplicate(arr) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 3, 2]], expected: true },
  { args: [[1, 2, 3, 4]], expected: false },
  { args: [['a', 'b', 'a']], expected: true },
  { args: [[1]], expected: false },
  { args: [[]], expected: false }
]

testCases.forEach(({ args, expected }, index) => {
  const result = hasDuplicate(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 19：生成随机密码

**场景**：生成一个指定长度的随机密码（只包含数字和大小写字母）

**要求**：写一个函数 `generatePassword`，输入密码长度，返回随机密码字符串

**提示**：可以用 `Math.random()` 和字符串拼接

```javascript
// 在这里完成你的代码
function generatePassword(length) {

}

// 测试用例（由于结果随机，只验证长度和字符范围）
const testLengths = [4, 8, 12, 16]
const validChars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'

testLengths.forEach((len, index) => {
  const result = generatePassword(len)
  if (result.length !== len) {
    throw new Error(`测试用例 ${index + 1} 失败: 期望长度 ${len}, 实际长度 ${result.length}`)
  }
  for (let i = 0; i < result.length; i++) {
    if (!validChars.includes(result[i])) {
      throw new Error(`测试用例 ${index + 1} 失败: 包含非法字符 "${result[i]}"`)
    }
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 20：简易日期格式化

**场景**：把日期对象格式化成 "YYYY-MM-DD" 格式

**要求**：写一个函数 `formatDate`，输入包含 year、month、day 的对象，返回格式化的日期字符串（月份和日期要补零）

```javascript
// 在这里完成你的代码
function formatDate(date) {

}

// 测试用例
const testCases = [
  { args: [{ year: 2024, month: 3, day: 15 }], expected: '2024-03-15' },
  { args: [{ year: 2024, month: 12, day: 5 }], expected: '2024-12-05' },
  { args: [{ year: 2024, month: 1, day: 1 }], expected: '2024-01-01' },
  { args: [{ year: 2000, month: 10, day: 20 }], expected: '2000-10-20' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = formatDate(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 提示

1. 每道题先想清楚解题思路，再动手写代码
2. 复制代码到你的编辑器中，填写函数体后运行
3. 如果测试失败，仔细阅读错误信息，找出问题所在
4. 遇到困难时，把问题分解成更小的步骤
5. 不要怕出错，调试是学习编程的重要部分
