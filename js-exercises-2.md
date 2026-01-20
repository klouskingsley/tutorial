# JavaScript 进阶练习题

> 这是第二套练习题，包含 16 道题目。前 8 道题目难度与第一套相当，后 8 道题目难度逐步提升，帮助你从基础过渡到更复杂的问题。

---

## 第一部分：基础巩固（与第一套难度相当）

### 题目 1：计算商品折后价格

**场景**：超市有不同的折扣规则，满 100 元打 9 折，满 200 元打 8 折，满 300 元打 7 折

**要求**：写一个函数 `calculateFinalPrice`，输入原价，返回折后价（保留两位小数，返回数字）

```javascript
// 在这里完成你的代码
function calculateFinalPrice(price) {

}

// 测试用例
const testCases = [
  { args: [50], expected: 50 },
  { args: [100], expected: 90 },
  { args: [150], expected: 135 },
  { args: [200], expected: 160 },
  { args: [300], expected: 210 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = calculateFinalPrice(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 2：判断奇偶数

**场景**：判断一个数字是奇数还是偶数

**要求**：写一个函数 `isEven`，输入一个整数，如果是偶数返回 `true`，否则返回 `false`

```javascript
// 在这里完成你的代码
function isEven(num) {

}

// 测试用例
const testCases = [
  { args: [2], expected: true },
  { args: [3], expected: false },
  { args: [0], expected: true },
  { args: [-4], expected: true },
  { args: [-7], expected: false }
]

testCases.forEach(({ args, expected }, index) => {
  const result = isEven(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 3：计算阶乘

**场景**：计算一个数的阶乘（5! = 5 × 4 × 3 × 2 × 1 = 120）

**要求**：写一个函数 `factorial`，输入一个非负整数 n，返回 n 的阶乘

```javascript
// 在这里完成你的代码
function factorial(n) {

}

// 测试用例
const testCases = [
  { args: [0], expected: 1 },
  { args: [1], expected: 1 },
  { args: [5], expected: 120 },
  { args: [6], expected: 720 },
  { args: [10], expected: 3628800 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = factorial(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 4：找出数组中的最小值

**场景**：找出一组数字中的最小值

**要求**：写一个函数 `findMin`，输入数组，返回最小值（不使用 `Math.min`）

```javascript
// 在这里完成你的代码
function findMin(arr) {

}

// 测试用例
const testCases = [
  { args: [[5, 2, 8, 1, 9]], expected: 1 },
  { args: [[10, 20, 30]], expected: 10 },
  { args: [[-5, -2, -10]], expected: -10 },
  { args: [[100]], expected: 100 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = findMin(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 5：统计数组中某个元素出现的次数

**场景**：统计数组中某个特定元素出现了多少次

**要求**：写一个函数 `countOccurrences`，输入数组和目标元素，返回该元素出现的次数

```javascript
// 在这里完成你的代码
function countOccurrences(arr, target) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 3, 2, 4, 2], 2], expected: 3 },
  { args: [['a', 'b', 'a', 'c', 'a'], 'a'], expected: 3 },
  { args: [[1, 2, 3], 5], expected: 0 },
  { args: [[], 1], expected: 0 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = countOccurrences(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 6：判断字符串是否包含某个子串

**场景**：检查一个字符串中是否包含另一个字符串

**要求**：写一个函数 `contains`，输入两个字符串，判断第一个字符串是否包含第二个字符串（不使用 `includes` 方法）

```javascript
// 在这里完成你的代码
function contains(str, substr) {

}

// 测试用例
const testCases = [
  { args: ['hello world', 'world'], expected: true },
  { args: ['javascript', 'script'], expected: true },
  { args: ['hello', 'bye'], expected: false },
  { args: ['test', 'test'], expected: true },
  { args: ['abc', 'abcd'], expected: false }
]

testCases.forEach(({ args, expected }, index) => {
  const result = contains(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 7：数组求和

**场景**：计算数组中所有数字的总和

**要求**：写一个函数 `sumArray`，输入数字数组，返回所有元素的和

```javascript
// 在这里完成你的代码
function sumArray(arr) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 3, 4, 5]], expected: 15 },
  { args: [[10, 20, 30]], expected: 60 },
  { args: [[-5, 5]], expected: 0 },
  { args: [[]], expected: 0 },
  { args: [[100]], expected: 100 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = sumArray(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 8：移除数组中的指定元素

**场景**：从数组中删除所有等于指定值的元素

**要求**：写一个函数 `removeElement`，输入数组和目标值，返回一个新数组，不包含目标值

```javascript
// 在这里完成你的代码
function removeElement(arr, target) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 3, 2, 4], 2], expected: [1, 3, 4] },
  { args: [['a', 'b', 'c', 'b'], 'b'], expected: ['a', 'c'] },
  { args: [[1, 2, 3], 5], expected: [1, 2, 3] },
  { args: [[1, 1, 1], 1], expected: [] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = removeElement(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 第二部分：进阶挑战（难度逐步提升）

### 题目 9：两数之和

**场景**：在数组中找到两个数，它们的和等于目标值

**要求**：写一个函数 `twoSum`，输入数组和目标值，返回这两个数的下标（数组形式）。如果找不到，返回空数组。

**提示**：假设每个输入只有一个答案，且同一个元素不能使用两次

```javascript
// 在这里完成你的代码
function twoSum(nums, target) {

}

// 测试用例
const testCases = [
  { args: [[2, 7, 11, 15], 9], expected: [0, 1] },
  { args: [[3, 2, 4], 6], expected: [1, 2] },
  { args: [[3, 3], 6], expected: [0, 1] },
  { args: [[1, 2, 3], 10], expected: [] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = twoSum(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 10：合并两个有序数组

**场景**：将两个已排序的数组合并成一个有序数组

**要求**：写一个函数 `mergeSortedArrays`，输入两个升序数组，返回合并后的升序数组

```javascript
// 在这里完成你的代码
function mergeSortedArrays(arr1, arr2) {

}

// 测试用例
const testCases = [
  { args: [[1, 3, 5], [2, 4, 6]], expected: [1, 2, 3, 4, 5, 6] },
  { args: [[1, 2, 3], [4, 5, 6]], expected: [1, 2, 3, 4, 5, 6] },
  { args: [[], [1, 2, 3]], expected: [1, 2, 3] },
  { args: [[1, 2, 3], []], expected: [1, 2, 3] },
  { args: [[1, 5, 9], [2, 3, 8]], expected: [1, 2, 3, 5, 8, 9] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = mergeSortedArrays(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 11：找出数组中的第二大值

**场景**：找出数组中第二大的数字

**要求**：写一个函数 `findSecondMax`，输入数组，返回第二大的数。如果不存在第二大的数，返回 `null`

```javascript
// 在这里完成你的代码
function findSecondMax(arr) {

}

// 测试用例
const testCases = [
  { args: [[1, 5, 3, 9, 2]], expected: 5 },
  { args: [[10, 10, 9]], expected: 9 },
  { args: [[5, 5, 5]], expected: null },
  { args: [[1]], expected: null },
  { args: [[3, 1, 4, 1, 5, 9, 2, 6]], expected: 6 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = findSecondMax(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 12：字符串压缩

**场景**：将字符串中连续重复的字符压缩成"字符+次数"的形式

**要求**：写一个函数 `compressString`，输入字符串，返回压缩后的字符串。如果压缩后的字符串不比原字符串短，则返回原字符串

**示例**：`"aabbbcccc"` → `"a2b3c4"`，`"abc"` → `"abc"`

```javascript
// 在这里完成你的代码
function compressString(str) {

}

// 测试用例
const testCases = [
  { args: ['aabbbcccc'], expected: 'a2b3c4' },
  { args: ['abc'], expected: 'abc' },
  { args: ['aaa'], expected: 'a3' },
  { args: [''], expected: '' },
  { args: ['aabbcc'], expected: 'aabbcc' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = compressString(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 13：数组去重

**场景**：移除数组中的重复元素，保留第一次出现的元素

**要求**：写一个函数 `removeDuplicates`，输入数组，返回去重后的新数组（保持原顺序）

```javascript
// 在这里完成你的代码
function removeDuplicates(arr) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 2, 3, 4, 4, 5]], expected: [1, 2, 3, 4, 5] },
  { args: [['a', 'b', 'a', 'c', 'b']], expected: ['a', 'b', 'c'] },
  { args: [[1, 1, 1]], expected: [1] },
  { args: [[]], expected: [] },
  { args: [[1, 2, 3]], expected: [1, 2, 3] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = removeDuplicates(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 14：找出缺失的数字

**场景**：给定一个包含 0 到 n 中 n 个数的数组，找出缺失的那个数字

**要求**：写一个函数 `findMissingNumber`，输入数组，返回缺失的数字

**示例**：`[0, 1, 3]` 缺失 `2`，`[0, 1, 2, 3, 4, 6]` 缺失 `5`

```javascript
// 在这里完成你的代码
function findMissingNumber(arr) {

}

// 测试用例
const testCases = [
  { args: [[0, 1, 3]], expected: 2 },
  { args: [[0, 1, 2, 3, 4, 6]], expected: 5 },
  { args: [[1, 2, 3, 4]], expected: 0 },
  { args: [[0]], expected: 1 },
  { args: [[0, 1, 2, 3, 4, 5, 6, 7, 9]], expected: 8 }
]

testCases.forEach(({ args, expected }, index) => {
  const result = findMissingNumber(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 15：旋转数组

**场景**：将数组向右旋转 k 个位置

**要求**：写一个函数 `rotateArray`，输入数组和旋转次数 k，返回旋转后的新数组

**示例**：`[1, 2, 3, 4, 5]` 向右旋转 2 次 → `[4, 5, 1, 2, 3]`

```javascript
// 在这里完成你的代码
function rotateArray(arr, k) {

}

// 测试用例
const testCases = [
  { args: [[1, 2, 3, 4, 5], 2], expected: [4, 5, 1, 2, 3] },
  { args: [[1, 2, 3], 1], expected: [3, 1, 2] },
  { args: [[1, 2, 3], 4], expected: [3, 1, 2] },
  { args: [[1], 0], expected: [1] },
  { args: [[1, 2, 3, 4], 0], expected: [1, 2, 3, 4] }
]

testCases.forEach(({ args, expected }, index) => {
  const result = rotateArray(...args)
  if (JSON.stringify(result) !== JSON.stringify(expected)) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${JSON.stringify(expected)}, 实际 ${JSON.stringify(result)}`)
  }
})
console.log('所有测试用例通过!')
```

---

### 题目 16：最长公共前缀

**场景**：找出字符串数组中所有字符串的最长公共前缀

**要求**：写一个函数 `longestCommonPrefix`，输入字符串数组，返回最长公共前缀。如果不存在公共前缀，返回空字符串

**示例**：`["flower", "flow", "flight"]` → `"fl"`

```javascript
// 在这里完成你的代码
function longestCommonPrefix(strs) {

}

// 测试用例
const testCases = [
  { args: [['flower', 'flow', 'flight']], expected: 'fl' },
  { args: [['dog', 'racecar', 'car']], expected: '' },
  { args: [['test', 'test', 'test']], expected: 'test' },
  { args: [['a']], expected: 'a' },
  { args: [['ab', 'a']], expected: 'a' }
]

testCases.forEach(({ args, expected }, index) => {
  const result = longestCommonPrefix(...args)
  if (result !== expected) {
    throw new Error(`测试用例 ${index + 1} 失败: 输入 ${JSON.stringify(args)}, 期望 ${expected}, 实际 ${result}`)
  }
})
console.log('所有测试用例通过!')
```

---

## 提示

1. 前 8 道题目是基础巩固，如果遇到困难，可以回顾第一套练习题
2. 后 8 道题目难度逐步提升，需要综合运用多个知识点
3. 遇到困难时，先在纸上画出解题思路，再写代码
4. 可以先用简单的例子手动模拟一遍算法过程
5. 双重循环、数组操作、字符串处理是这些题目的重点
