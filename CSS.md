## VNSS

VNSS(Video Native Style Sheets)是一套样式语言，用于描述 VNML 的组件样式。

VNSS 用来决定 VNML 的组件应该怎么显示。

为了适应广大的前端开发者，VNSS 具有 CSS 大部分特性。同时为了更适合开发微信小程序，VNSS 对 CSS 进行了扩充以及修改。

与 CSS 相比，WXSS 扩展的特性有：

### 尺寸单位

-rpx（responsive pixel）: 可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。如在 iPhone6 上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素。

设备 | rpx换算px (屏幕宽度/750) |px换算rpx (750/屏幕宽度)
--- | --- | ---
iPhone5 | 1rpx = 0.42px | 1px = 2.34rpx
iPhone6 | 1rpx = 0.5px | 1px = 2rpx
iPhone6 Plus | 1rpx = 0.552px | 1px = 1.81rpx

**建议：** 开发微信小程序时设计师可以用 iPhone6 作为视觉稿的标准。

**注意：**在较小的屏幕上不可避免的会有一些毛刺，请在开发时尽量避免这种情况。

### 内联样式

框架组件上支持使用 style、class 属性来控制组件的样式。

-style：静态的样式统一写到 class 中。style 接收动态的样式，在运行时会进行解析，请尽量避免将静态的样式写进 style 中，以免影响渲染速度。

```html
<!--test.vnml-->
<view style="color:{{color}};" />
```

-class：用于指定样式规则，其属性值是样式规则中类选择器名(样式类名)的集合，样式类名不需要带上.，样式类名之间用空格分隔。

```html
<!--test.vnml-->
<view class="normal_view" />
```

### 选择器

目前支持的选择器有：

选择器 | 样例 | 样例描述
--- | --- | ---
\* | \* | 选择所有组件
element | view | 选择所有 view 组件
.class | .intro | 选择所有拥有 class="intro" 的组件
:pseudoclass | :active | 伪类选择器，目前普通组件只支持:active伪类，input组件还支持:focus,:disable
\#id | #firstname | 选择拥有 id="firstname" 的组件
element, element | view, checkbox | 选择所有文档的 view 组件和所有的 checkbox 组件

**注意：**选择器还可以使用集联操作如:"#id1 text"可以匹配id1下面左右的text组件(包含嵌套多层的子组件)

**注意：**选择器的优先集为 #id > .class > element > *

更多CSS的规范请参看[W3C标准](https://developer.mozilla.org/en-US/docs/Web/CSS)

更多Flex属性介绍清参看[Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)