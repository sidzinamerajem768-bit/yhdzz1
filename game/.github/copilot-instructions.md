# Copilot Instructions for AI Agents

## 项目概览
本项目为基于 Ren'Py 引擎的视觉小说游戏，主要脚本和资源均位于根目录下。核心文件包括：
- `script.rpy`、`screens.rpy`、`options.rpy`：游戏主流程、界面与配置脚本
- `gui/`、`images/`、`audio/`：美术与音频资源
- `tl/None/`：本地化翻译脚本
- `libs/`：第三方库或依赖

## 架构与数据流
- 游戏逻辑、UI、配置均通过 `.rpy` 脚本实现，遵循 Ren'Py 官方脚本结构。
- 资源通过 `gui/`、`images/`、`audio/` 目录引用，路径需与脚本一致。
- 本地化采用 `tl/None/` 目录下的 `.rpym` 文件，按 Ren'Py 约定进行翻译。

## 关键开发流程
- **构建与发布**：
  - 构建配置在 `options.rpy`，通过 `build.classify` 控制资源打包与排除。
  - 常见排除模式：`*.bak`、`~`、隐藏文件、`thumbs.db` 等。
  - 可通过注释的 `build.classify('game/**.png', 'archive')` 控制资源归档。
- **调试与运行**：
  - 直接用 Ren'Py 启动根目录即可进入开发模式。
  - 修改 `.rpy` 文件后无需重启，Ren'Py 支持热加载。
- **本地化**：
  - 翻译文本位于 `tl/None/common.rpym`，格式为 `old`/`new` 对。

## 项目约定与注意事项
- 所有脚本文件均为 UTF-8 编码。
- 资源引用路径区分大小写，需与实际文件名一致。
- 不要直接修改 `.rpyc`、`.rpyb` 等编译文件，始终编辑 `.rpy` 源文件。
- 构建时如需排除/归档新类型资源，需同步更新 `options.rpy` 中的 `build.classify` 规则。

## 典型模式示例
- 排除所有备份文件：`build.classify('**.bak', None)`
- 归档所有图片资源：`build.classify('game/**.png', 'archive')`
- 添加文档到构建包：`build.documentation('*.txt')`

## 参考文件
- `options.rpy`：构建与资源管理规则
- `script.rpy`、`screens.rpy`：主流程与 UI
- `tl/None/common.rpym`：本地化翻译

---
如需补充开发流程、特殊约定或遇到不明确的结构，请在此文档补充说明。