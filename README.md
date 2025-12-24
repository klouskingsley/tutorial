# CSS 选择器完全指南

这个项目包含了 CSS 选择器的完整示例和使用指南。

## 文件说明

- `css-selectors-demo.html` - 包含所有 CSS 选择器类型的交互式演示

## 内联样式详解

### 什么是内联样式？

**内联样式（Inline Styles）** 是直接写在 HTML 元素上的样式，使用 `style` 属性定义。

### 基本语法

```html
<div style="color: red; font-size: 16px; margin: 10px;">
    这是一个使用内联样式的元素
</div>
```

### 内联样式的特点

#### 1. **最高优先级**
内联样式的权重为 `(1,0,0,0)`，比任何选择器都高（除了 `!important`）

```html
<!-- 即使有 ID 选择器，内联样式也会生效 -->
<style>
    #text { color: blue; }      /* 权重: (0,1,0,0) */
    .highlight { color: green; } /* 权重: (0,0,1,0) */
</style>

<p id="text" class="highlight" style="color: red;">
    文字颜色是红色（内联样式优先级最高）
</p>
```

#### 2. **直接作用于元素**
不需要选择器，样式直接应用到当前元素

```html
<button style="background: blue; color: white; padding: 10px 20px;">
    点击我
</button>
```

#### 3. **只影响当前元素**
内联样式不能被复用，仅对单个元素生效

```html
<!-- 每个按钮都需要重复写样式 -->
<button style="background: blue; color: white;">按钮1</button>
<button style="background: blue; color: white;">按钮2</button>
<button style="background: blue; color: white;">按钮3</button>
```

---

### 内联样式的使用场景

#### ✅ **适合使用的场景**

1. **JavaScript 动态修改样式**
   ```javascript
   // 动态改变元素样式
   element.style.backgroundColor = 'yellow';
   element.style.display = 'none';
   ```

2. **快速测试和调试**
   ```html
   <!-- 临时测试某个样式效果 -->
   <div style="border: 1px solid red;">测试边框</div>
   ```

3. **邮件 HTML（Email Templates）**
   ```html
   <!-- 邮件客户端通常需要内联样式 -->
   <table style="width: 100%; border-collapse: collapse;">
       <tr style="background: #f0f0f0;">
           <td style="padding: 10px;">内容</td>
       </tr>
   </table>
   ```

4. **动态生成的内容**
   ```javascript
   // 服务端渲染或模板中动态插入样式
   const color = user.favoriteColor;
   html = `<div style="color: ${color};">欢迎 ${user.name}</div>`;
   ```

5. **覆盖第三方库样式**（临时方案）
   ```html
   <!-- 紧急覆盖某个难以修改的样式 -->
   <div class="third-party-widget" style="width: 100% !important;">
   ```

---

#### ❌ **不推荐使用的场景**

1. **常规组件样式**
   ```html
   <!-- ❌ 不好：难以维护 -->
   <button style="background: blue; color: white; padding: 10px;">按钮</button>

   <!-- ✅ 好：使用类 -->
   <button class="btn-primary">按钮</button>
   ```

2. **需要复用的样式**
   ```html
   <!-- ❌ 不好：代码重复 -->
   <div style="margin: 10px; padding: 20px; border: 1px solid #ddd;">卡片1</div>
   <div style="margin: 10px; padding: 20px; border: 1px solid #ddd;">卡片2</div>

   <!-- ✅ 好：使用类 -->
   <div class="card">卡片1</div>
   <div class="card">卡片2</div>
   ```

3. **响应式设计**
   ```html
   <!-- ❌ 内联样式无法使用媒体查询 -->
   <div style="width: 800px;">内容</div>

   <!-- ✅ 使用 CSS 类可以响应式 -->
   <style>
   .container {
       width: 800px;
   }
   @media (max-width: 768px) {
       .container { width: 100%; }
   }
   </style>
   ```

4. **伪类和伪元素**
   ```html
   <!-- ❌ 内联样式无法使用 :hover -->
   <button style="background: blue;">无法设置 hover 效果</button>

   <!-- ✅ 需要使用样式表 -->
   <style>
   .btn:hover { background: darkblue; }
   </style>
   ```

---

### 内联样式的优缺点

#### 优点 ✅

| 优点 | 说明 |
|-----|------|
| **最高优先级** | 可以快速覆盖其他样式 |
| **即时生效** | 不需要额外的 CSS 文件 |
| **适合动态样式** | JavaScript 可以轻松修改 |
| **无选择器冲突** | 直接作用于元素 |

#### 缺点 ❌

| 缺点 | 说明 |
|-----|------|
| **难以维护** | 修改样式需要逐个元素修改 |
| **代码重复** | 无法复用，增加 HTML 体积 |
| **无法使用伪类** | 不支持 `:hover`、`:focus` 等 |
| **无法使用媒体查询** | 不支持响应式设计 |
| **HTML/CSS 混合** | 违反关注点分离原则 |
| **性能问题** | 大量内联样式增加页面大小 |

---

### 内联样式 vs CSS 类

```html
<!-- 场景：创建 3 个相同样式的按钮 -->

<!-- ❌ 内联样式方式（不推荐）-->
<button style="background: #007bff; color: white; padding: 10px 20px; border: none; border-radius: 4px;">
    按钮1
</button>
<button style="background: #007bff; color: white; padding: 10px 20px; border: none; border-radius: 4px;">
    按钮2
</button>
<button style="background: #007bff; color: white; padding: 10px 20px; border: none; border-radius: 4px;">
    按钮3
</button>

<!-- ✅ CSS 类方式（推荐）-->
<style>
.btn-primary {
    background: #007bff;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
}
.btn-primary:hover {
    background: #0056b3;
}
</style>

<button class="btn-primary">按钮1</button>
<button class="btn-primary">按钮2</button>
<button class="btn-primary">按钮3</button>
```

**对比结果：**
- 内联样式：约 300 字符（重复 3 次）
- CSS 类：约 150 字符（样式定义一次）+ 60 字符（HTML）
- CSS 类还支持 hover 效果，更易维护

---

### JavaScript 操作内联样式

```javascript
// 获取元素
const box = document.getElementById('myBox');

// 设置单个样式
box.style.backgroundColor = 'blue';
box.style.width = '200px';
box.style.fontSize = '16px';

// 设置多个样式（CSS 文本）
box.style.cssText = 'background: blue; width: 200px; font-size: 16px;';

// 使用 setAttribute
box.setAttribute('style', 'background: blue; width: 200px;');

// 读取内联样式
console.log(box.style.backgroundColor); // 'blue'

// 移除样式
box.style.backgroundColor = '';

// 注意：style 只能读取内联样式，不能读取 CSS 类的样式
// 要读取计算后的样式，使用 getComputedStyle
const computedStyle = window.getComputedStyle(box);
console.log(computedStyle.backgroundColor);
```

---

### 实际示例对比

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* CSS 类方式 */
        .card {
            border: 1px solid #ddd;
            padding: 20px;
            margin: 10px;
            border-radius: 8px;
            background: #f9f9f9;
        }

        .card:hover {
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transform: translateY(-2px);
            transition: all 0.3s;
        }
    </style>
</head>
<body>
    <!-- ❌ 内联样式：无法实现 hover 效果 -->
    <div style="border: 1px solid #ddd; padding: 20px; margin: 10px; border-radius: 8px; background: #f9f9f9;">
        <h3>内联样式卡片</h3>
        <p>无法实现 hover 效果和过渡动画</p>
    </div>

    <!-- ✅ CSS 类：支持完整功能 -->
    <div class="card">
        <h3>CSS 类卡片</h3>
        <p>支持 hover 效果和过渡动画</p>
    </div>
</body>
</html>
```

---

### 最佳实践建议

1. **优先使用 CSS 类**，避免滥用内联样式
2. **仅在以下情况使用内联样式**：
   - JavaScript 动态修改
   - 邮件模板
   - 快速调试
3. **避免在生产代码中使用内联样式**作为主要样式方案
4. **使用构建工具**：某些框架（如 React 的 CSS-in-JS）会自动处理样式注入
5. **关注点分离**：保持 HTML 结构、CSS 样式、JS 行为分离

---

## 什么时候使用什么选择器？

### 1. **元素选择器** (`div`, `p`, `h1`)
**使用场景：**
- 设置全局默认样式
- 重置浏览器默认样式
- 对某类元素统一设置基础样式

**示例：**
```css
/* 适合：为所有段落设置默认行高 */
p { line-height: 1.6; }

/* 适合：重置所有标题的 margin */
h1, h2, h3 { margin: 0; }
```

**注意：** 避免过度使用，可能导致样式难以覆盖。

---

### 2. **类选择器** (`.button`, `.card`)
**使用场景：**
- 可复用的样式组件（最常用）
- 创建样式变体（`.button-primary`, `.button-secondary`）
- 大多数常规样式需求

**示例：**
```css
/* 推荐：可复用的按钮样式 */
.button { padding: 10px 20px; }
.button-primary { background: blue; }
.button-large { font-size: 18px; }
```

**优点：** 灵活、可复用、优先级适中

---

### 3. **ID 选择器** (`#header`, `#main`)
**使用场景：**
- 页面唯一元素（header, footer, main）
- JavaScript 钩子（但推荐用 data 属性）
- 页面锚点跳转

**示例：**
```css
/* 适合：唯一的页面头部 */
#header { position: fixed; top: 0; }

/* 不推荐：普通组件不要用 ID */
#button1 { color: red; } /* ❌ 应该用 class */
```

**注意：** 优先级太高，难以覆盖，现代开发中尽量少用于样式。

---

### 4. **属性选择器** (`[type="text"]`, `[data-state]`)
**使用场景：**
- 根据属性值设置样式
- 表单元素样式
- 链接类型区分
- 自定义数据属性

**示例：**
```css
/* 适合：不同类型的输入框 */
input[type="text"] { border: 1px solid gray; }
input[type="email"] { border: 1px solid blue; }

/* 适合：外部链接 */
a[href^="http"] { color: blue; }
a[target="_blank"]::after { content: " ↗"; }

/* 适合：状态样式 */
[data-status="error"] { color: red; }
```

---

### 5. **后代选择器** (`.nav a`)
**使用场景：**
- 限定样式作用范围
- 组件内部样式隔离

**示例：**
```css
/* 适合：导航栏内的链接样式 */
.nav a { text-decoration: none; }

/* 适合：卡片内的标题 */
.card h3 { font-size: 1.2em; }
```

**注意：** 不要嵌套过深（建议 ≤3 层）

---

### 6. **子选择器** (`.menu > li`)
**使用场景：**
- 只选择直接子元素
- 避免影响嵌套结构

**示例：**
```css
/* 适合：只选择第一层列表项 */
.menu > li { display: inline-block; }

/* 不会影响到嵌套的 li */
.menu > li > ul > li { display: block; }
```

---

### 7. **相邻兄弟选择器** (`h2 + p`)
**使用场景：**
- 紧跟在某元素后的样式
- 段落首行特殊处理

**示例：**
```css
/* 适合：标题后第一段的样式 */
h2 + p { font-weight: bold; color: gray; }

/* 适合：表单标签后的间距 */
label + input { margin-top: 5px; }
```

---

### 8. **通用兄弟选择器** (`h2 ~ p`)
**使用场景：**
- 选择某元素后所有同级元素

**示例：**
```css
/* 适合：选中状态后的所有段落 */
.selected ~ p { opacity: 0.5; }
```

---

### 9. **伪类选择器**

#### 状态伪类 (`:hover`, `:focus`, `:active`)
**使用场景：**
- 交互反馈
- 用户体验优化

```css
/* 必须：所有可点击元素 */
button:hover { background: darkblue; }
a:focus { outline: 2px solid blue; }
input:focus { border-color: green; }
```

#### 结构伪类 (`:first-child`, `:nth-child()`)
**使用场景：**
- 列表样式
- 表格斑马纹
- 特定位置元素

```css
/* 适合：列表第一项 */
li:first-child { font-weight: bold; }

/* 适合：表格斑马纹 */
tr:nth-child(even) { background: #f0f0f0; }

/* 适合：选择前3项 */
li:nth-child(-n+3) { color: red; }
```

#### 表单伪类 (`:checked`, `:disabled`, `:valid`)
**使用场景：**
- 表单状态样式
- 无障碍提示

```css
/* 适合：表单验证 */
input:invalid { border-color: red; }
input:valid { border-color: green; }
input:disabled { opacity: 0.5; }

/* 适合：自定义复选框 */
input:checked + label { color: green; }
```

#### `:not()` 伪类
**使用场景：**
- 排除特定元素

```css
/* 适合：除了最后一项都有边框 */
li:not(:last-child) { border-bottom: 1px solid #ddd; }

/* 适合：除了禁用的按钮 */
button:not(:disabled):hover { cursor: pointer; }
```

---

### 10. **伪元素选择器** (`::before`, `::after`)
**使用场景：**
- 装饰性内容
- 图标插入
- 清除浮动

**示例：**
```css
/* 适合：添加图标 */
.icon-user::before { content: "👤"; }

/* 适合：引用标记 */
blockquote::before { content: """; }
blockquote::after { content: """; }

/* 适合：清除浮动 */
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```

---

### 11. **分组选择器** (`h1, h2, h3`)
**使用场景：**
- 多个元素共享相同样式
- 减少代码重复

**示例：**
```css
/* 适合：统一设置标题字体 */
h1, h2, h3, h4, h5, h6 {
    font-family: Georgia, serif;
}

/* 适合：统一按钮样式基础 */
.btn-primary, .btn-secondary, .btn-danger {
    padding: 10px 20px;
    border: none;
}
```

---

## CSS 选择器优先级（权重）

### 优先级计算规则

CSS 使用 **特异性（Specificity）** 来决定哪个样式生效。可以用四位数表示：

```
(内联样式, ID, Class/属性/伪类, 元素/伪元素)
```

### 权重值对照表

| 选择器类型 | 权重值 | 示例 |
|----------|--------|------|
| 内联样式 `style=""` | (1,0,0,0) | `<div style="color: red">` |
| ID 选择器 | (0,1,0,0) | `#header` |
| 类选择器 | (0,0,1,0) | `.button` |
| 属性选择器 | (0,0,1,0) | `[type="text"]` |
| 伪类 | (0,0,1,0) | `:hover` |
| 元素选择器 | (0,0,0,1) | `div` |
| 伪元素 | (0,0,0,1) | `::before` |
| 通配符 `*` | (0,0,0,0) | `*` |
| 组合符 `>`, `+`, `~` | (0,0,0,0) | 不增加权重 |

### 优先级计算示例

```css
/* (0,0,0,1) */
p { color: black; }

/* (0,0,1,0) */
.text { color: blue; }

/* (0,0,1,1) */
p.text { color: green; }

/* (0,1,0,0) */
#main { color: red; }

/* (0,1,1,1) */
#main p.text { color: purple; }

/* (0,0,2,1) */
.container .text.highlight { color: orange; }

/* (1,0,0,0) */
<p style="color: yellow;">内联样式最高优先级</p>
```

### 优先级规则

1. **!important 最高**（但尽量避免使用）
   ```css
   p { color: red !important; } /* 强制优先 */
   ```

2. **内联样式** > **ID** > **类/属性/伪类** > **元素**

3. **相同权重时，后面的覆盖前面的**
   ```css
   p { color: red; }
   p { color: blue; } /* blue 生效 */
   ```

4. **权重相加规则**
   ```css
   /* (0,0,2,0) */
   .nav.active { }

   /* (0,0,1,1) */
   div.nav { }

   /* 第一个权重更高 */
   ```

### 优先级对比示例

```css
/* 从低到高排序 */
div                          /* (0,0,0,1) */
div p                        /* (0,0,0,2) */
.text                        /* (0,0,1,0) */
div.text                     /* (0,0,1,1) */
.nav .text                   /* (0,0,2,0) */
#header                      /* (0,1,0,0) */
#header .text                /* (0,1,1,0) */
#header div.text             /* (0,1,1,1) */
#header .nav .text           /* (0,1,2,0) */
style="color: red"           /* (1,0,0,0) */
color: red !important        /* 最高优先级 */
```

---

## 最佳实践建议

### ✅ 推荐做法

1. **优先使用类选择器**
   ```css
   /* 好 */
   .button { }
   .button-primary { }
   ```

2. **保持选择器简短（≤3层）**
   ```css
   /* 好 */
   .card .title { }

   /* 避免 */
   .container .wrapper .card .header .title { }
   ```

3. **使用语义化的类名**
   ```css
   /* 好 */
   .btn-submit, .card-header

   /* 避免 */
   .blue-button, .big-text
   ```

4. **利用伪类优化交互**
   ```css
   .button:hover { }
   .input:focus { }
   .checkbox:checked + label { }
   ```

5. **使用属性选择器处理状态**
   ```css
   [data-status="error"] { color: red; }
   [aria-expanded="true"] { }
   ```

### ❌ 避免做法

1. **过度使用 ID 选择器**
   ```css
   /* 避免 */
   #header #nav #menu li { }
   ```

2. **滥用 !important**
   ```css
   /* 避免 */
   .text { color: red !important; }
   ```

3. **选择器嵌套过深**
   ```css
   /* 避免 */
   .a .b .c .d .e .f { }
   ```

4. **过度使用通配符**
   ```css
   /* 避免 */
   * * * { } /* 性能差 */
   ```

---

## 性能考虑

### 选择器性能排序（从快到慢）

1. ID 选择器：`#header`
2. 类选择器：`.button`
3. 元素选择器：`div`
4. 相邻选择器：`div + p`
5. 子选择器：`div > p`
6. 后代选择器：`div p`
7. 通配符选择器：`*`
8. 属性选择器：`[type="text"]`
9. 伪类/伪元素：`:hover`

**注意：** 现代浏览器性能优化很好，通常不需要过度担心选择器性能，代码可读性和可维护性更重要。

---

## 常见应用场景总结

| 场景 | 推荐选择器 | 示例 |
|------|-----------|------|
| 全局样式重置 | 元素选择器 | `body, h1, p { margin: 0; }` |
| 组件样式 | 类选择器 | `.card { }` |
| 页面布局 | ID/类选择器 | `#main`, `.container` |
| 按钮变体 | 类选择器 | `.btn-primary`, `.btn-large` |
| 表单样式 | 属性选择器 | `input[type="text"]` |
| 交互效果 | 伪类 | `.btn:hover`, `input:focus` |
| 列表样式 | 结构伪类 | `li:first-child`, `tr:nth-child(odd)` |
| 装饰内容 | 伪元素 | `.icon::before` |
| 状态管理 | 数据属性 | `[data-state="active"]` |

---

## 学习建议

1. 从常用的类选择器开始
2. 理解优先级计算规则
3. 多使用浏览器开发者工具查看实际权重
4. 实践中总结最适合项目的选择器策略
5. 关注可维护性而非过度优化

---

## 参考资源

- [MDN CSS 选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Selectors)
- [CSS 特异性计算器](https://specificity.keegan.st/)
- [Can I Use - 浏览器兼容性](https://caniuse.com/)

---

**Happy Coding! 🎨**
