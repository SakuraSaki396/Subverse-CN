# Subverse 1.2.0 汉化补丁（完整增强版）使用说明

本发布包提供两种安装方式，**任选其一即可**。

---

## 方式一（推荐）：图形化安装器 `SubverseCNInstaller.exe`

双击运行 `SubverseCNInstaller.exe`，会出现一个图形界面（窗口标题为 **“Subverse 汉化补丁安装器”**）。首次运行会弹出 UAC 请求管理员权限，用于写入游戏目录，请点击 **“是”**。

### 界面说明
- 顶部 **“检测信息”** 面板显示：Steam 路径、游戏目录、游戏版本（buildid）、当前汉化状态、内嵌汉化文件大小。
- 启动后安装器会自动检测游戏并填充上述信息；右上角 **“当前状态”** 用颜色区分：
  - 🔵 蓝色 = 未安装
  - 🟢 绿色 = 已装增强版
  - 🟠 橙色 = 可升级 / 其它

### 按钮功能
| 按钮 | 作用 |
| --- | --- |
| **开始安装汉化** | 一键安装（先自动备份原文件 → 写入汉化 → SHA256 校验）。点击后会弹确认框。 |
| **重新检测** | 手动刷新游戏检测结果。 |
| **浏览游戏目录…** | 若自动定位失败，手动选择游戏根目录（即包含 `Subverse` 子目录的那个文件夹）。 |
| **恢复备份** | 把之前自动备份的 `.bak` 文件还原，回到无汉化的原版状态。 |

运行日志框会实时显示每一步进度与结果；安装成功后会弹出提示。

> ⚠️ 运行前请先**完全退出游戏**（安装器也会检测并拦截）。

### 命令行参数（高级用户）
```
SubverseCNInstaller.exe --check          仅检测与校验，不做任何修改
SubverseCNInstaller.exe --dry-run        模拟安装（不实际写入）
SubverseCNInstaller.exe --game-path=X:\路径   手动指定游戏根目录
```

---

## 方式二：手动复制

1. **完全退出游戏。**
2. 进入游戏 Paks 目录：
   ```
   E:\SteamLibrary\steamapps\common\Subverse\Subverse\Content\Paks\
   ```
   （Steam 库不在 E 盘时，请按实际情况调整为 `Steam\steamapps\common\Subverse\Subverse\Content\Paks\`）
3. 把目录里原有的 `pakchunk0_t0-WindowsNoEditor.pak` 改名备份（例如改成 `.bak`），以便回退。
4. 把本包里的 `pakchunk0_t0-WindowsNoEditor.pak` 复制到该目录覆盖。
5. 启动游戏，语言保持 **“English”**（中文通过英文语言表注入）。

---

## 启动与语言

- 游戏内语言**务必保持 English**，否则中文不会生效。
- 若 Steam 校验完整性或更新，可能还原该 t0 文件，重新安装一次即可。

---

## 卸载 / 回退

- 删除或移走本补丁的 `pakchunk0_t0-WindowsNoEditor.pak`；
- 把备份的 `.bak` 文件（方式一会自动生成）改回原名即可恢复原汉化补丁；
- 也可直接用图形界面里的 **【恢复备份】** 按钮完成此操作。

---

## 重要提醒

- ⚠️ 请勿修改 Paks 目录里约 **598MB** 的 `pakchunk0-WindowsNoEditor.pak`（Steam 原版基础包），也不要改动 `pakchunk0_s1` ~ `s32` 等资源包。**汉化补丁只涉及 1.5MB 的 t0 文件。**

---

## 汉化内容概览

| 类别 | 内容 |
| --- | --- |
| 设置页（CommonTermsUI 字符串表） | 全量翻译 129 项，覆盖画面 / 音频 / 控制 / 语言等；修正 CREDITS→制作人员、WEBSITE→官网、TEMPORALAA→TAA、GRAPHICS→画面 等 |
| 图鉴（CodexEntries） | 补全 180 个标题（原表缺失 key 导致回退英文） |
| 退出主菜单确认弹窗（PauseScreen.uexp） | 5 句：确定吗？ / 所有未保存的更改都将丢失。 / 上次存档于 / 小时 / 分钟前 |
| 对话控制栏（DialogueUIControls.uexp） | 5 项：Tab=自动播放 / L=下一张 / M=跳过本段 / C=切换日志 / =控制栏开关 |
| 其他可见 UI 与 EULA | 57 条散落界面文案与用户协议段落 |

本地化表共 17,684 条，其中 17,405 条含中文；剩余 276 条纯英文条目多为角色名、专有名词、内部标识符与技术术语，非可翻译界面文案，故保留原文。

> 完整清单详见同目录 `汉化内容清单.txt`。
