# 项目：MFC的窗口自绘美化

## 项目背景
- MFC 对话框自绘美化示例：以“登录窗口”风格为目标，用图片资源实现背景皮肤、自绘按钮与输入框图标。
- 面向传统桌面程序 UI 美化需求，体现 OwnerDraw 控件绘制链路与资源皮肤化的组织方式。

## 技术介绍
- 窗口背景通过重载 OnEraseBkgnd 接管擦除流程，并把背景位图拉伸铺满，实现随窗口尺寸变化的自适应背景皮肤。
- 按钮与图标控件使用 OwnerDraw：在资源中把 Button/Static 设置为 BS_OWNERDRAW/SS_OWNERDRAW，由 WM_DRAWITEM 回调统一绘制。
- 按钮根据按下状态切换两套图片资源（up/down），从而实现按压反馈；输入框旁的账号/密码图标也通过同一套绘制机制贴图显示。
- 绘制采用内存 DC + CImage 的方式把资源绘制到目标 DC，逻辑集中且便于后续扩展更多皮肤元素（边框、阴影、hover 等）。

## 技术栈
- 语言：C++（Unicode）
- GUI：MFC
- 绘制：GDI + CImage
- 构建：Visual Studio/MSBuild
- 代码位置：`MFC的窗口自绘美化`
