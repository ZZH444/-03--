# 实验3 CSS布局实战——导航菜单

## 文件说明

- `一级菜单.html` —— 一级水平导航菜单（HTML 结构未改，全部效果由 CSS 完成）
- `二级菜单.html` —— 二级水平导航菜单（悬停展开下拉，HTML 结构未改）

## 实现要点

1. **水平排列**：一级菜单用 `table` 自带的行内表格布局 + `margin: 0 auto` 居中；二级菜单用 `display: flex` 让 `li` 水平排列并 `flex: 1` 均分宽度（等价方案 `inline-block + font-size: 0` 已在注释中给出）。
2. **盒模型**：`* { box-sizing: border-box }` 统一盒模型；菜单链接用 `display: block` + `padding: 16px 22px` 撑开整个可点击区域，`border-bottom: 3px solid transparent` 预留高亮条避免悬停抖动。
3. **选择器综合**：通配选择器 `*` 清默认边距；元素/后代选择器（`table td a`、`ul > li > a`）设置菜单样式；并集选择器让"当前页首项"与 `:hover` 共用高亮样式。
4. **:hover 伪类**：一级项悬停变背景色、文字变白并显示底部高亮条；二级项悬停背景变色且 `padding-left` 增大形成右移反馈。
5. **二级菜单定位**：一级 `li` 设 `position: relative` 作为定位父元素，二级 `ul` 设 `position: absolute; top: 100%; left: 0` 紧贴其下边缘，默认 `display: none`，悬停时 `li:hover > ul { display: block }` 展开，`z-index: 999` 保证浮在上层。
6. **CSS 三角箭头**：有子菜单的一级项用 `::after` + `border` 三角绘制 ▾ 提示符。

## 运行方式

直接用 Chrome 打开两个 HTML 文件即可，鼠标悬停"教学院(部)"可查看二级菜单下拉效果。
