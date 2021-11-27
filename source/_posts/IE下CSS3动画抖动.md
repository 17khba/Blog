---
title: IE下CSS3动画抖动
date: 2019-05-02 16:42:46
tags: [ie, CSS3]
---

**问题记录：IE11中执行淡入动画时出现抖动效果，效果如下：**

![shake_before](/IE下CSS3动画抖动/img/shake_before.gif)

<!--more-->

### 解决此问题需理解一些概念：
---
1. 重排：重新生成布局
2. 重绘：重新绘制(颜色、阴影等）

<div class="tip">注意：重排必定导致重绘，重绘不一定  需要重排；比如改变背景色，就只会触发重绘</div>



### 原始代码：
---
```javascript
// >>>>> js部分 <<<<<
listEl.show();
timer = requestAnimationFrame(function () {
  listEl.removeClass('out').addClass('in');
})

// >>>>> css部分 <<<<<
.dropDown_list.in {
   animation-name: in;
   animation-duration: 2s;
   animation-fill-mode: both;
 }
@keyframes in {
  0% {
    opacity: 0;
    filter:alpha(opacity=0);
    transform-origin: 0% 0%;
    transform: scaleY(0.8);
  }
  100% {
    opacity: 1;
    filter:alpha(opacity=100);
    transform-origin: 0% 0%;
    transform: scaleY(1);
  }
}
```



**执行步骤：**

1. 点击按钮，控制 `ul` 标签 `display` 属性让其显示
2. 给ul标签追加 `in` 类名，让其 `opacity` 树形从0到1，实现淡入

**动画抖动剖析：**
1. 执行 `display: block` 时会单独触发重排;

2. 执行动画 `opacity` 时也会单独触发重排

  也就是 `ul` 标签刚显示出来，又重新应用上了 `opacity: 0 和 transform: scaleY(.8)`，导致抖动的发生



### 解决方案：
---
既然是因为两次重排导致动画抖动，那合并起来触发一次重排就可以了，优化后的代码如下：
```javascript
// >>>>> js部分 <<<<<
timer = requestAnimationFrame(function () {
  listEl.show();
  listEl.removeClass('out').addClass('in');
})
```



**使用 `requestAnimationFrame` 的原因在于浏览器可以优化并行的动画动作，更合理的重新排列动作序列，并把能够合并的动作放在一个渲染周期内完成，从而呈现出更流畅的动画效果**



优化后的效果：

![shake_after](/IE下CSS3动画抖动/img/shake_after.gif)

**demo：**

<iframe height="265" style="width: 100%;" scrolling="no" title="下拉组件封装" src="//codepen.io/17khba/embed/aEjjxK/?height=265&theme-id=dark&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/17khba/pen/aEjjxK/'>下拉组件封装</a> by 17khba
  (<a href='https://codepen.io/17khba'>@17khba</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>