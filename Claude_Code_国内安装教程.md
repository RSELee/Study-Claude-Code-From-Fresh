# Claude Code 国内安装教程：从零到能用

> 面向人群：国内普通用户，无需编程基础，无需魔法，无需海外账号
>
> 阅读时间：约 10 分钟
>
> 最后更新：2026 年 5 月 28 日

---

## 前言：为什么是 Claude Code？

Claude Code 是 Anthropic 推出的 AI 编程助手，是目前公认的**上限最高的 AI 编程工具**。它可以直接读写你的项目文件、运行命令、理解整个代码库，相当于一个住在你电脑里的程序员。

但问题是——它原生只支持海外 API，国内用户装好了也用不了。

这篇教程用**四步走**的方案，帮你从零搞定：

| 步骤 | 内容 | 难度 |
|:----:|------|:----:|
| 第一步 | 用 AI Agent 帮你安装 Claude Code | ★☆☆ |
| 第二步 | 安装 CC Switch 切换工具 | ★★☆ |
| 第三步 | 接入国产模型（白嫖 16 元体验） | ★★☆ |
| 第四步 | 在 VS Code 中愉快使用 | ★☆☆ |

---

## 第一步：用 AI Agent 帮你安装 Claude Code

**思路很简单**：用魔法打败魔法——用 AI 来帮你安装 AI。

### 1.1 下载 WorkBuddy

WorkBuddy 是腾讯推出的 AI 桌面智能体（底层是 OpenClaw），安装即用，无需命令行折腾。

- **官网地址**：https://www.codebuddy.cn/work/
- 支持 Windows 和 macOS，双击安装包一路"下一步"即可
- 新用户注册赠送 **5000 Credits** 免费额度

### 1.2 让 WorkBuddy 帮你装 Claude Code

1. 打开 WorkBuddy，登录账号
2. 在对话框里直接输入：

```
帮我安装 Claude Code
```

3. WorkBuddy 会自动完成以下操作：
   - 检测 Node.js 环境（没有的话会帮你装）
   - 执行 `npm install -g @anthropic-ai/claude-code`
   - 配置相关依赖

4. 安装完成后，在终端输入以下命令验证：

```bash
claude --version
```

出现版本号就说明安装成功了。

> **为什么用这个方法？**
> 手动安装 Claude Code 需要配置 Node.js 环境、处理 npm 镜像源、解决各种依赖问题，新手很容易卡住。交给 AI Agent 来做，5 分钟搞定。

---

## 第二步：安装 CC Switch（核心工具）

装好了 Claude Code，但你打开会发现——没法用。因为它默认连的是 Anthropic 海外服务器，国内直连不通。

**CC Switch** 就是用来解决这个问题的。它可以把 Claude Code 的 API 指向国内可用的模型服务。

### 2.1 下载 CC Switch

- **GitHub 地址**：https://github.com/farion1231/cc-switch/releases/latest
- Windows 用户下载 `CC-Switch-vX.X.X-Windows.msi`（推荐 MSI 安装包）
- macOS 用户下载 `CC-Switch-vX.X.X-macOS.zip`

> **没有魔法访问不了 GitHub？**
> 可以联系我免费获取 CC Switch 安装包，直接本地安装。

### 2.2 安装 CC Switch

**Windows**：双击 MSI 文件，按向导安装，完成后在开始菜单搜索"CC Switch"启动。

**macOS**：
1. 解压 zip 文件
2. 将 `CC Switch.app` 拖入「应用程序」文件夹
3. 首次打开如果提示"未知开发者"，前往「系统设置 → 隐私与安全性 → 仍要打开」

### 2.3 系统要求

| 系统 | 最低版本 | 架构 |
|------|---------|------|
| Windows | Windows 10+ | x64 |
| macOS | macOS 10.15+ | Intel / Apple Silicon |
| Linux | 各发行版 | x64 / arm64 |

---

## 第三步：接入国产模型

现在 CC Switch 装好了，接下来要给它配置一个能用的模型供应商。推荐使用**硅基流动（SiliconFlow）**，新用户注册送 16 元代金券，够你先体验一阵子。

### 3.1 注册硅基流动

1. 打开硅基流动官网：https://cloud.siliconflow.cn
2. 用手机号注册账号
3. **完成实名认证**（上传身份证或扫脸）—— 不认证领不到 16 元券
4. 认证完成后，前往「余额充值」或「优惠券」页面确认 16 元代金券已到账

### 3.2 创建 API 密钥

1. 登录硅基流动控制台
2. 点击左侧「API 密钥」
3. 点击「新建 API 密钥」
4. 描述随意填写（比如 "Claude Code 使用"）
5. 生成后**立即复制并保存**（sk- 开头的字符串，只显示一次）

### 3.3 在 CC Switch 中配置供应商

1. 打开 CC Switch，顶部选择 **Claude Code** 图标
2. 点击**右上角「+」按钮**
3. 在列表中选择 **SiliconFlow**
4. 在配置页面中找到 `API KEY` 字段，粘贴刚才创建的密钥
5. 点击「获取模型列表」，等待加载（会出现 99+ 个可用模型）
6. 找到 `deepseek-ai/DeepSeek-V4-PRO`，点击「一键设置」
7. 最后点击「添加」完成配置

> **关于模型选择**：
> - 体验期用硅基流动的 16 元券，先跑通流程
> - 正式使用推荐接入 **DeepSeek V4 Pro**，性价比极高，编程能力在国内模型中名列前茅
> - 也可以尝试 GLM-5.1、DeepSeek-V4-Flash 等其他模型

 **不想一直被询问许可？**
 > - 可以复制以下代码贴到编辑通用配置里
{
  "permissions": {
    "defaultMode": "bypassPermissions"
  }
}


### 3.4 验证配置

在 CC Switch 中点击「健康检查」按钮，发送测试请求验证 API Key 和网络是否正常。

---

## 第四步：在 VS Code 中使用 Claude Code

配置完成后，推荐在 VS Code 中使用 Claude Code，体验远超纯命令行。

### 4.1 安装 Claude Code 扩展

1. 打开 VS Code（没有的话去 https://code.visualstudio.com 免费下载）
2. 按 `Ctrl+Shift+X`（Mac: `Cmd+Shift+X`）打开扩展商店
3. 搜索 **"Claude Code"**
4. 安装**第一个带官方蓝 V 标识**的扩展

### 4.2 开始使用

1. 安装完成后，点击 VS Code **左侧边栏**的 Claude Code 图标
2. 如果配置正确，聊天框会直接出现
3. 你可以开始对话了：

```
帮我写一个 Python 爬虫
```

```
解释一下这段代码的逻辑
```

```
帮我重构这个函数
```

### 4.3 如果没有出现聊天框（手动修复）

极少数情况下 CC Switch 的配置没有自动同步到 VS Code，需要手动设置：

1. 打开 VS Code 设置：左下角齿轮 → 「打开设置」（或 `Ctrl + ,`）
2. 搜索 `claudeCode.environmentVariable`
3. 在中括号内添加：

```json
{
  "claudeCode.environmentVariable": [
    { "name": "ANTHROPIC_BASE_URL", "value": "你的代理地址" },
    { "name": "ANTHROPIC_AUTH_TOKEN", "value": "你的API密钥" }
  ]
}
```

> `ANTHROPIC_BASE_URL` 和 `ANTHROPIC_AUTH_TOKEN` 的值可以在 CC Switch 的配置详情中找到。

4. 保存后重新打开 Claude Code 即可。

---

## 常见问题

### Q：安装 Claude Code 时报错怎么办？
**A**：确保 Node.js 版本 >= 18。在终端运行 `node -v` 检查版本。如果版本过低，让 WorkBuddy 帮你升级。

### Q：claude 命令提示 "command not found"？
**A**：重启终端，或检查 Node.js 全局包路径是否已加入系统环境变量。

### Q：CC Switch 配置后 Claude Code 还是连不上？
**A**：在 CC Switch 中点击「健康检查」验证连通性。确认 API Key 没有过期或用完余额。

### Q：硅基流动的 16 元用完了怎么办？
**A**：可以在硅基流动官网充值，价格非常实惠。DeepSeek-V4-Flash 价格极低，日常编程足够。

### Q：能直接用 DeepSeek 官方 API 吗？
**A**：可以。在 CC Switch 中选择 DeepSeek 预设，填入 DeepSeek 官方的 API Key 即可。

---

## 全流程速查

```
下载 WorkBuddy → 让它帮你装 Claude Code
        ↓
下载 CC Switch → 安装
        ↓
注册硅基流动 → 实名认证 → 领 16 元券 → 创建 API Key
        ↓
CC Switch 添加 SiliconFlow → 填入 API Key → 选择 DeepSeek V4 Pro → 一键设置
        ↓
VS Code 安装 Claude Code 扩展 → 开始对话
```

恭喜你，现在你已经拥有了一个能直接理解你项目代码的 AI 编程助手。

---

## 工具下载汇总

| 工具 | 地址 | 说明 |
|------|------|------|
| WorkBuddy | https://www.codebuddy.cn/work/ | AI 桌面智能体，帮你装 Claude Code |
| Claude Code | `npm install -g @anthropic-ai/claude-code` | Anthropic 官方 AI 编程 CLI |
| CC Switch | https://github.com/farion1231/cc-switch/releases/latest | API 切换工具 |
| 硅基流动 | https://cloud.siliconflow.cn | 国产模型 API 平台，新用户送 16 元 |
| VS Code | https://code.visualstudio.com | 代码编辑器（免费） |

---

*有问题？欢迎交流。祝编码愉快！*
