# 优惠券弹窗禁用状态复盘

## 问题/目标

优惠券入口在某些状态下看起来已经禁用，但用户点击后仍然可以打开弹窗。目标是让页面展示状态和真实交互行为保持一致。

## 设计思路

这个模块不能只依赖样式禁用。页面需要用同一个状态同时控制禁用样式、展示文案和点击拦截。

整体流程是：先计算当前是否允许打开弹窗，再在模板里展示对应样式，最后在点击函数里做真正拦截。

## 实现讲解

关键位置是优惠券入口组件。

这段代码解决的是：样式禁用无法阻止用户点击的问题。

```ts
const openCouponPopup = () => {
  if (!canOpenCouponPopup.value) return
  couponPopupRef.value?.open()
}
```

`if (!canOpenCouponPopup.value) return` 是真正的交互拦截。不能打开优惠券弹窗时，函数会提前结束，后面的 `open()` 不会执行，所以弹窗不会出现。

模板层可以继续用动态 class 做视觉反馈：

```vue
<view :class="{ disabled: !canOpenCouponPopup }" @click="openCouponPopup">
```

`:class` 是动态 class 绑定。对象里的 `disabled` 是要追加的 class 名，后面的值为真时才会追加。这里的 `!canOpenCouponPopup` 表示不能打开弹窗时才显示禁用样式。

## 复盘点

- 视觉禁用和点击拦截是两个层次，不能只做样式。
- 点击函数里的提前 `return` 才是真正阻止后续逻辑执行的地方。
- 像 `canOpenCouponPopup` 这种状态最好同时驱动样式、文案和行为，避免页面表现不一致。
