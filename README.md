# KernelSUExt

简体中文 | [English](#english)

---

## 简介

KernelSUExt 是为 KernelSU 管理器编写的 LSPosed/Xposed 模块，用来备份：

- **超级用户配置**：导出/导入 KernelSU Root列表。
- **模块文件**：按模块单独打包 ZIP 备份，可选择需要备份的模块。

浮动按钮常驻于 KernelSU 管理器界面左上角，点击即可调出功能弹窗。

## 功能

- 导出超级用户列表 → `Download/kernelsu_backup/` 下生成 `superusers-YYYY-MM-DD HH-mm-ss.json`
- 从文件导入超级用户列表（选择 JSON）
- 备份模块：多选模块，逐个生成 `<moduleId>_YYYY-MM-DD HH-mm-ss.zip`
- 任务进度：备份/恢复时显示 Loading，完成后自动关闭并提示
- 备份目录展示：功能弹窗中会显示当前备份目录路径

## 安装与要求

- Android 10+，已 Root
- 安装 KernelSU（目标包：`me.weishu.kernelsu`）
- 安装 LSPosed/EdXposed，并在作用域中勾选 KernelSU
- 安装并启用本模块后重启 KernelSU 应用（或设备）

## 使用步骤

1. 打开 KernelSU 管理器，左上角会出现拼图样式的浮动按钮（随明暗主题切换黑/白图标）。
2. 点击按钮，选择所需功能：导出/导入超级用户、备份模块。
3. 备份与导入文件默认路径：`/storage/emulated/0/Download/kernelsu_backup/`；若外置下载目录不可写，则退回应用私有目录。

## 备份文件说明

- 超级用户：`superusers-YYYY-MM-DD HH-mm-ss.json`
- 模块：`<moduleId>_YYYY-MM-DD HH-mm-ss.zip`（每个模块独立文件）
- 时间戳使用文件系统安全格式（不含冒号）

## 注意事项

- 需要 su 权限；若设备无 zip/unzip 命令，应用会使用内置打包/解压。
- 导入后会触发刷新，若未生效，可重启 KernelSU 管理器。
- 若浮动按钮缺失，请确认模块在 LSPosed 里已启用且作用域正确。
- 免责声明：仅供学习/测试/个人备份使用，风险自负。

---

## English

KernelSUExt is an LSPosed/Xposed module for KernelSU Manager that backs up:

- **Superuser config**: export/import allowlist & profiles (JSON).
- **Modules**: per-module ZIP backup with multi-selection.

A floating puzzle icon appears at the top-left of KernelSU Manager; tap it to open the actions dialog.

### Features

- Export superuser list → `Download/kernelsu_backup/superusers-YYYY-MM-DD HH-mm-ss.json`
- Import superuser list from JSON
- Backup modules: multi-select, create `<moduleId>_YYYY-MM-DD HH-mm-ss.zip` per module
- Restore modules from ZIP; falls back to in-app unzip + su copy if no system unzip
- Loading indicators during backup, auto-dismiss with toasts
- Backup directory path shown in the dialog

### Requirements & Install

- Android 10+, rooted
- KernelSU (`me.weishu.kernelsu`) installed
- LSPosed/EdXposed enabled with KernelSU in scope
- Install & enable this module, then restart KernelSU (or reboot)

### Usage

1. Open KernelSU Manager; the floating puzzle icon appears top-left (auto theme-aware).
2. Tap it and choose: export/import superuser or backup modules.
3. Default path: `/storage/emulated/0/Download/kernelsu_backup/`; falls back to app private dir if public downloads not writable.

### Backup Files

- Superuser JSON: `superusers-YYYY-MM-DD HH-mm-ss.json`
- Module ZIP: `<moduleId>_YYYY-MM-DD HH-mm-ss.zip`
- Timestamps are file-system safe (no colons).

### Notes

- su required; if zip/unzip binaries are missing, in-app zip/unzip is used.
- If changes don’t apply after import, restart KernelSU Manager.
- If the floating icon is missing, ensure the module is enabled and scoped in LSPosed.
- Disclaimer: For learning/testing/personal backup only. Use at your own risk.
