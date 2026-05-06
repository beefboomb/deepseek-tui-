# DeepSeek-TUI 学生部署教程（Windows）

本教程适合 Windows 电脑。你不需要安装 npm，也不需要安装 cargo，只需要下载两个运行文件。

## 1. 这是什么

DeepSeek-TUI 是一个在终端里运行的 AI 助手。它和网页端 DeepSeek 不完全一样：

- 网页端 DeepSeek：主要在浏览器里聊天。
- DeepSeek-TUI：可以在你指定的本地文件夹里运行，读取文件、整理文件、生成新文件。

本节课的重点不是学习编程，而是体验“AI 如何处理本地文件”。

## 2. 准备 DeepSeek API Key

1. 打开 DeepSeek 开放平台：

   <https://platform.deepseek.com>

2. 登录账号。

3. 找到：

   ```text
   API keys / API 密钥
   ```

4. 创建一个新的 API Key，名称可以写：

   ```text
   deepseek-tui
   ```

5. 复制生成的 API Key。

注意：API Key 相当于账号密码，不能发到群里，不能截图公开，也不能借给别人。

如果运行时提示 `Insufficient Balance`，说明 API 余额不足，需要在 DeepSeek 开放平台充值少量余额。

## 3. 下载 DeepSeek-TUI

打开发布页：

<https://github.com/Hmbown/DeepSeek-TUI/releases/latest>

在页面下方找到 Assets，下载这两个 Windows x64 文件：

```text
deepseek-windows-x64.exe
deepseek-tui-windows-x64.exe
```

不要下载 `Source code`，那是源码包。

## 4. 放到固定文件夹

新建一个文件夹，例如：

```text
C:\AI\deepseek
```

也可以放在 D 盘：

```text
D:\AI\deepseek
```

把两个 exe 文件放进去，然后改名：

```text
deepseek-windows-x64.exe      改成 deepseek.exe
deepseek-tui-windows-x64.exe  改成 deepseek-tui.exe
```

最后文件夹里应该是：

```text
C:\AI\deepseek\deepseek.exe
C:\AI\deepseek\deepseek-tui.exe
```

如果你使用 D 盘，就把路径里的 `C:` 换成 `D:`。

建议用 PowerShell 确认一次真实文件名：

```powershell
dir C:\AI\deepseek
```

如果你安装在 D 盘：

```powershell
dir D:\AI\deepseek
```

必须能看到这两个完整文件名：

```text
deepseek.exe
deepseek-tui.exe
```

注意：Windows 资源管理器有时会隐藏 `.exe` 扩展名。不要只看图标下面显示的名字，以 PowerShell 里 `dir` 显示的结果为准。

## 5. 第一次设置 API Key

打开 PowerShell，输入：

```powershell
cd C:\AI\deepseek
.\deepseek.exe --version
```

如果显示版本号，说明程序可以运行。

然后输入：

```powershell
.\deepseek.exe auth set --provider deepseek
```

看到提示后，粘贴你的 DeepSeek API Key，按回车。

如果看到类似下面的提示，说明设置成功：

```text
saved API key for deepseek
```

## 6. 启动 DeepSeek-TUI

继续输入：

```powershell
.\deepseek.exe
```

进入界面后，可以直接输入中文问题。

注意：普通问题不要以 `/` 开头。`/` 通常表示工具命令。

正确：

```text
你好，请介绍一下你能做什么。
```

错误：

```text
/你好，请介绍一下你能做什么。
```

## 7. 创建桌面快捷方式

如果每次都打开 PowerShell 再输入命令比较麻烦，可以创建一个桌面快捷方式。

### 方式一：启动 DeepSeek-TUI 主界面

1. 在桌面空白处点击右键。
2. 选择：

   ```text
   新建 -> 快捷方式
   ```

3. 在“请键入对象的位置”里输入：

   ```text
   powershell.exe -NoExit -Command "cd C:\AI\deepseek; .\deepseek.exe"
   ```

4. 点击“下一步”。
5. 名称填写：

   ```text
   DeepSeek-TUI
   ```

6. 点击“完成”。

以后双击这个快捷方式，就可以直接打开 DeepSeek-TUI。

### 方式二：直接进入课堂实验文件夹

如果你想每次都直接进入课堂实验文件夹 `D:\AI-demo`，快捷方式的位置可以填写：

```text
powershell.exe -NoExit -Command "cd D:\AI-demo; C:\AI\deepseek\deepseek.exe"
```

这样双击快捷方式后，它会直接在 `D:\AI-demo` 里启动，适合做课堂任务。

如果你的 DeepSeek-TUI 安装在 D 盘，请把命令里的：

```text
C:\AI\deepseek\deepseek.exe
```

改成：

```text
D:\AI\deepseek\deepseek.exe
```

## 8. 课堂体验任务：整理一次班级活动资料


### 第一步：创建实验文件夹

新建文件夹：

```text
D:\AI-demo
```

### 第二步：新建资料文件

在 `D:\AI-demo` 里新建一个文本文件：

```text
activity-notes.txt
```

复制下面的内容进去：

```text
活动名称：校园图书角整理
时间：周三下午
参与人员：第一小组、第二小组
完成情况：
第一小组负责整理图书，把文学类、科普类、工具书分开放好。
第二小组负责擦拭书架，检查破损图书，并登记需要修补的书。
发现的问题：
1. 有些图书没有编号。
2. 部分同学借书后没有及时归还。
3. 科普类图书数量较少。
同学建议：
可以制作借阅登记表。
可以每周安排一名图书管理员。
可以向班级征集闲置图书。
```

### 第三步：先体验网页端

打开网页端 DeepSeek：

<https://chat.deepseek.com>

输入：

```text
请读取我电脑里 D:\AI-demo\activity-notes.txt，并帮我生成一份班级活动总结。
```

观察：网页端通常不能直接读取你电脑里的本地文件。你需要手动复制文件内容。

### 第四步：再体验 DeepSeek-TUI

打开 PowerShell，输入：

```powershell
cd D:\AI-demo
C:\AI\deepseek\deepseek.exe
```

进入 DeepSeek-TUI 后输入：

```text
请查看当前文件夹里的 activity-notes.txt，帮我生成一份班级活动总结，并保存为 activity-summary.md。总结要包括：活动概况、完成情况、发现的问题、改进建议。
```

### 第五步：检查结果

退出 TUI 后，在 PowerShell 输入：

```powershell
dir D:\AI-demo
```

看看是否多了：

```text
activity-summary.md
```

可以打开查看：

```powershell
notepad D:\AI-demo\activity-summary.md
```

## 9. 思考问题

1. 网页端 DeepSeek 和 DeepSeek-TUI 最大的区别是什么？
2. 如果只是问知识问题，哪个更方便？
3. 如果要整理本地文件夹里的资料，哪个更适合？
4. 为什么 API Key 不能发给别人？

## 10. 常见问题

### Companion deepseek-tui binary not found

原因：`deepseek.exe` 旁边没有 `deepseek-tui.exe`。

解决办法：用 PowerShell 确认真实文件名：

```powershell
dir D:\AI\deepseek
```

或者：

```powershell
dir C:\AI\deepseek
```

同一个文件夹里必须有：

```text
deepseek.exe
deepseek-tui.exe
```

如果看到的是 `deepseek-tui-windows-x64.exe`，说明还没有改名。

如果看到的是 `deepseek-tui.exe.exe`，说明 Windows 隐藏扩展名时重复加了一次 `.exe`。

如果看到的是 `deepseek-tui` 但没有 `.exe`，说明扩展名可能被删掉了。

### HTTP 402 Payment Required / Insufficient Balance

原因：DeepSeek API 余额不足。

解决办法：进入 DeepSeek 开放平台充值：

<https://platform.deepseek.com>

### Unknown command

原因：普通问题前面加了 `/`。

解决办法：普通问题直接输入文字，不要加 `/`。

### 想看可用命令

在 TUI 里输入：

```text
/help
```

## 11. 安全提醒

- API Key 不要发给别人。
- API Key 不要写进作业。
- API Key 不要截图公开。
- 如果 API Key 泄露，立刻去 DeepSeek 开放平台删除旧 key，重新创建新 key。
