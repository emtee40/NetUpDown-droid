## FAQ


- 关于上行速的一些行为
> - 当上行速处于开启状态，会`开机自启`；关闭状态则不会。
> - 当上行速处于开启状态，会维护一个内存占用不大的`后台服务`来实时监测网速，刷新周期为`1500ms`；关闭状态则没有后台服务。

- 关于悬浮窗优先级
> `上行速`有`高`、`低`两种优先级，`高优先级`特征：可以显示在状态栏、通知栏、锁屏界面。`高优先级`可能带来一些问题，比如导致某些视频播放器调节亮度失效。
> 延伸：
> Android 的窗口被设计了几种优先级，`上行速`的高优先级对应`TYPE_SYSTEM_ERROR`，低优先级对应`TYPE_SYSTEM_ALERT`，了解更多请访问 [WindowManager.LayoutParams | Android Developers](https://developer.android.com/reference/android/view/WindowManager.LayoutParams.html#type)

- 如何切换悬浮窗优先级？
> 首次使用时会显示一次优先级选择对话框，在此处可作选择；当悬浮窗已显示，您随时可以通过`长按悬浮窗`来快速切换优先级。

- 为什么用了这个播放视频时调不了亮度了？
> 如果您正在使用`高优先级模式`，切换到`低优先级`可以解决这个问题。

- 如何切换网速/流量模式？
> `双击悬浮窗`即可。

- 为什么每次切换到流量模式都会清零？
> 设计如此。`流量模式`适合用于统计一段时间的流量消耗。场景举例：播放在线视频时，（双击悬浮窗）切换到流量模式，实时监测消耗的流量，避免流量“暴走”。

- 为什么流量模式统计的流量不准？
> 一般情况下，`上行速`统计的流量与运营商统计的实际流量出入不大；但在特殊情况偏差较大，甚至于数倍。那么什么是特殊情况？
> - 开启了`便携式 WLAN 热点`来共享流量
> - 使用了上网代理App，比如`ShadowSocks`、`Lantern`等
>
> 需要说明的是，这不算是一个BUG，但是是需要改进的地方。

- 为什么悬浮窗有时会消失？
> 后台服务被杀了。如果是系统调配所致（比如由于内存紧张而释放掉一些服务），那么不用担心，系统会随后自动将其恢复。