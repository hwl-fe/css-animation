# CSS 动画基础使用

## 整体结构介绍

### 1. 动画属性

### 2. 性能优化

### 3. 应用场景

### 4. 总结

## 常用动画属性介绍

### 6 种实现动画的方式

- js+定时器
- requestAnimationFrame
- svg
- canvas
- css+transition
- css+animation

### transform

- translate
- scale
- rotate
- skew

### transform 3d

- transform-style: flat | preserve-3d;
- perspective: 800px; （透视视距）

	- perspective取值为none或不设置，就没有真3D空间。
	- perspective取值越小，3D效果就越明显，也就是你的眼睛越靠近真3D。
	- perspective的值无穷大，或值为0时与取值为none效果一样（效果不明显）。

### transition

- transition-property

	- 属性名
	- all（所有值变化的属性均参与）

- transition-duration
- transition-timing-function
- transition-delay

	- 默认0，立即执行动画
	- 正值，延迟指定时间再执行
	- 负值，跳过指定时间开始执行

### animation

- @keyframes

	- from...to...
	- 0%...10%...50%...100%

- animation-name
- animation-duration
- animation-delay
- animation-iteration-count

	- number
	- infinite

- animation-direction

	- normal
	- alertnate

- animation-play-state

	- paused
	- running

- animation-fill-mode

	- none
	- forwards
	- backwards
	- both(向前和向后填充模式都被应用)

- animation-timing-function

    - cubic-bezier

		- ease
		- linear
		- ease-in
		- ease-out
		- ease-in-out
		- google浏览器调试方法
		- 贝塞尔曲线原理 https://www.cnblogs.com/hnfxs/p/3148483.html

    - steps
		- step-start（跳过第一个帧）
		- step-end（跳过最后一个帧）
		- https://designmodo.com/steps-css-animations/
		- 学习如何使用 steps - https://designmodo.com/demo/stepscss/car.html

## css 动画实践

### 巧用 border 实现 loading 图

### 巧用伪元素实现开门动效

### 巧用 box-shadow 实现多种天气动效

- 一个元素可以设置多个 box-shadow

### css 动画在项目中的应用

- 点赞动效
- 气球上升效果
- tab 切换动效

## 动画性能优化

### 为什么会出现卡顿

- 丢帧

  浏览器绘制某一帧的时长超过了平均时长（帧超时），为了完成整个动画不得不丢弃 后面的 动画帧，造成丢帧现象。 就出现了所谓的闪烁，卡顿。
  导致帧超时的原因有很多，最主要的原因是 layout、paint 带来的性能开销

- 主线程 和 合成线程 的调度不合理

	- 主线程

		主线程负责：运行 JavaScript；计算 HTML 元素的 CSS 样式；页面的布局；将元素绘制到一个或多个位图中；将这些位图交给合成线程。

	- 合成线程

		合成线程负责：通过 GPU 将位图绘制到屏幕上；通知主线程更新页面中可见或即将变成可见的部分的位图；计算出页面中哪部分是可见的；计算出当你在滚动页面时哪部分是即将变成可见的；当你滚动页面时将相应位置的元素移动到可视区域。

### 如何优化

- 优先选择 transform
- transform-3d 变换开启 GPU 加速
- transition 性能好于 animation
- 加速属性

	- transform
	- opacity
	- filter

## 总结

### transition 和 animation 的不同点

- 触发条件不同
- 关键帧数量不同
- animation 可以设定循环次数
- animation 可控性强

### transition 和 animation 适用场景

- transition

	- 通常和hover等事件配合使用，由事件触发
	- 简单的from to 过渡效果

- animation

	- 灵活定制多个关键帧
	- 可重复，可正反向播放
	- 多个动作组合

### 动效网站分享

- Hover.css 悬停效果集合 http://ianlunn.github.io/Hover/
- Easing Functions 缓动函数 https://easings.net/en
- cubic-bezier 贝塞尔曲线在线编辑 https://cubic-bezier.com/
- animate.css 多种动效 demo https://daneden.github.io/animate.css/
