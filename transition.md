# CSS Transition 详解

## 什么是 Transition

CSS `transition` 属性用于在元素的样式发生变化时创建**平滑的过渡动画**，而不是瞬间改变。

## 基本语法

```css
/* 完整语法 */
transition: property duration timing-function delay;

/* 简写示例 */
transition: all 0.3s ease 0s;
```

## 四个参数详解

### 1. transition-property（属性名）
指定要过渡的 CSS 属性

```css
transition-property: width;          /* 单个属性 */
transition-property: width, height;  /* 多个属性 */
transition-property: all;            /* 所有可过渡属性 */
```

### 2. transition-duration（持续时间）
过渡动画的持续时间

```css
transition-duration: 0.3s;   /* 秒 */
transition-duration: 300ms;  /* 毫秒 */
```

### 3. transition-timing-function（速度曲线）
控制过渡的速度变化

| 值 | 说明 |
|---|---|
| `ease` | 默认值，慢-快-慢 |
| `linear` | 匀速运动 |
| `ease-in` | 慢速开始，加速 |
| `ease-out` | 快速开始，减速 |
| `ease-in-out` | 慢速开始和结束 |
| `cubic-bezier(n,n,n,n)` | 自定义贝塞尔曲线 |

### 4. transition-delay（延迟时间）
延迟开始过渡的时间（可选）

```css
transition-delay: 0.1s;   /* 延迟 0.1 秒开始 */
```

## 可过渡的属性

### ✅ 可以过渡
- **尺寸**: `width`, `height`, `padding`, `margin`
- **颜色**: `color`, `background-color`, `border-color`
- **透明度**: `opacity`
- **变换**: `transform` (translate, rotate, scale, skew)
- **边框**: `border-width`, `border-radius`
- **阴影**: `box-shadow`, `text-shadow`
- **位置**: `top`, `right`, `bottom`, `left`
- **字体**: `font-size`, `letter-spacing`, `line-height`

### ❌ 不可以过渡
- `display` - 只能瞬间切换
- `font-family` - 字体名称无法插值
- `position` - 定位类型无法过渡
- `visibility` - 需特殊处理

## 使用示例

### 单个属性过渡
```css
.button {
  background-color: blue;
  transition: background-color 0.3s;
}

.button:hover {
  background-color: red;
}
```

### 多个属性过渡
```css
.box {
  width: 100px;
  height: 100px;
  background: blue;
  transition: width 0.3s, height 0.5s, background 0.3s;
}

.box:hover {
  width: 200px;
  height: 200px;
  background: red;
}
```

### 所有属性过渡
```css
.card {
  transition: all 0.3s ease-in-out;
}
```

### 带延迟的过渡
```css
.element {
  opacity: 0;
  transition: opacity 0.3s ease 0.2s;
}

.element.show {
  opacity: 1;
}
```

## 常见应用场景

1. **按钮悬停效果**
```css
.button {
  background: blue;
  transform: scale(1);
  transition: all 0.2s;
}

.button:hover {
  background: darkblue;
  transform: scale(1.1);
}
```

2. **卡片展开**
```css
.card {
  height: 100px;
  transition: height 0.4s ease-out;
}

.card.expanded {
  height: 300px;
}
```

3. **图片放大**
```css
.image {
  transform: scale(1);
  transition: transform 0.3s;
}

.image:hover {
  transform: scale(1.2);
}
```

4. **菜单滑入**
```css
.menu {
  transform: translateX(-100%);
  transition: transform 0.3s ease-out;
}

.menu.open {
  transform: translateX(0);
}
```

## Display 的替代方案

由于 `display` 不能直接过渡，可以使用以下组合：

```css
/* 方案1: opacity + visibility */
.modal {
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.3s, visibility 0.3s;
}

.modal.show {
  opacity: 1;
  visibility: visible;
}

/* 方案2: height + overflow */
.dropdown {
  height: 0;
  overflow: hidden;
  transition: height 0.3s;
}

.dropdown.open {
  height: 200px;
}
```

## 性能优化建议

1. **优先过渡 transform 和 opacity**
   - 这些属性不会触发重排（reflow），性能最好

2. **避免过渡 layout 属性**
   - `width`, `height`, `margin`, `padding` 会触发重排，性能较差

3. **指定具体属性而非 all**
   ```css
   /* 不推荐 */
   transition: all 0.3s;

   /* 推荐 */
   transition: opacity 0.3s, transform 0.3s;
   ```

4. **使用 will-change 提示浏览器**
   ```css
   .element {
     will-change: transform, opacity;
   }
   ```

## 与 Animation 的区别

| Transition | Animation |
|---|---|
| 需要触发条件（hover, class 等） | 可以自动播放 |
| 只有开始和结束两个状态 | 可以定义多个关键帧 |
| 简单的状态变化 | 复杂的动画序列 |
| 不能循环播放 | 可以循环播放 |

## 浏览器兼容性

现代浏览器全面支持，无需前缀：
- Chrome 26+
- Firefox 16+
- Safari 9+
- Edge 12+

旧版浏览器可能需要 `-webkit-` 前缀。
