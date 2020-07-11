---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: true

print_background: false

---

# Git 风格指南

## 提交信息

### 信息结构

提交信息由空行分隔的三个不同部分组成：`标题`、`正文`（可选）和`页脚`（可选）。布局如下：

```shell
type: subject

body

footer
```

标题由信息类型和标题组成。

### 类型

类型包含在标题中，可以是这些类型之一:

- **feat:** 新功能（feature）
- **fix:** 修复bug
- **docs:** 文档
- **style:** 格式（不影响代码运行的变动）e.g. 分号缺失，统一缩进
- **refactor:** 重构（即不是新增功能，也不是修改bug的代码变动）
- **test:** 添加测试
- **chore:** 构建任务，包管理器配置或辅助工具的变动

### 主题

commit 目的的简短描述，最好不超过50个字符，结尾不加句号。

### 正文

对本次 commit 的详细描述。用来解释提交的内容和原因。

正文是可选部分，因为并不是所有提交都复杂到需要正文来详细描述。

写正文时，标题和正文之间必须有空白行，每行的长度不能超过72个字符。

### 页脚

页脚是可选的，用来记录当前 commit 针对的是哪个 issue。

### 示例

```shell
feat: 50个字符以内的简短描述

如过有必要，可以在正文部分添加更详细的说明文本。字数大约为72个字符。写正文时，标题和正文之间必须有空白行；如果同时运行 `log`、`shortlog` 和 `rebase` 等工具，可能会混淆。

解释此提交要解决的问题。重点关注为什么要进行此更改，而不是如何进行更改(代码对此进行了解释)。这种变化是否有副作用或其他不直观的结果？在这里解释一下。


如果想要记录当前 commit 针对的是哪个issue，可以这样编写：

Resolves: #123
```