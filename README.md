## 基础 View 动画（View Animations）

### 创建动画

通过调用 UIView 的类方法 `animate(withDuration:animations:)`，来创建最基础的动画效果,还可以设置动画的延时，参数，结束回调等，使用 `animate(withDuration:delay:options:animations:completion)` 方法，其中：

* `withDuration`：动画的时长

* `delay`：动画的延时

* `options`：动画的参数，当参数为空时，传入空数组 `[]`

* `completion`：动画完成时执行的回调，传入一个闭包

示例：

```swift
UIView.animate(withDuration: 0.5,
  delay: 0.3,
  options: [],
  animations: {
    // 记得闭包里要使用 self
    self.myView.center.x += self.view.bounds.width
  },
  completion: nil
)
```

### 动画参数

* `.repeat`：从头开始动画，无限循环

* `.autoreverse`：完成后倒退一次，相当于从头到尾一次，然后从尾到头回去，接着终止在动画的尾处

两者搭配可以创建出不断来回的循环动画

还可以设置动画曲线：`.curveLinear`，`.curveEaseIn`，`.curveEaseOut`，`.curveEaseInOut`（默认）

## 弹性动画（Springs）

### 创建弹性动画

创建带弹性的动画，需要调用 UIView 的类方法 `animate(withDuration:delay:usingSpringWithDamping:initialSpringVelocity:optio ns:animations:completion:)`，其中：

* `usingSpringWithDamping`：取值 0 到 1，越大则弹性动画越“生硬”，越小则越“有弹性”

* `initialSpringVelocity`：控制弹性动画的速度，假设取值为 1，对于移动的动画，则在 1 秒内完成整个位移

## 过渡动画（Transitons）

* `transition(with:duration:options:animations:completion:)`：`with` 为过渡的 View，如果效果为显示一个 View，则 `with` 可以是这个要“出现”的 View 的父 View，通过 `superView.addSubView(subView)` 来实现动画效果

* View 的“出现”效果，除了上面的方法，在不改变 View 的布局结构的情况下，也可以通过 `transitionView.isHidden` 属性的改变来实现

* `transition(from:to:duration:options:animations:completion:)`：效果为一个 View 切换到另一个 View，可以使用该方法 ，其中 `from` 与 `to` 分别为过渡的两个 View
