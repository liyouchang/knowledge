qt 开发浏览器插件
============================

1. 对winID的使用，不可以在构造函数中调用QWidget::winID，因为在构造函数中qt5还没有显示初始化，调用winID会强制分配一个id，界面的父窗口会未知。
2. 需要使用regsvr32注册生成的com，否则EventInterface不会写入注册表