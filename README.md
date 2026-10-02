# 七草荠记账挂件（dsh-qicaoji-widget）

> 住在 DSH 界面右下角的七草荠（七草なずな / 《彻夜之歌》），帮你盯着 DeepSeek 账户余额。
> 基于 [dsh-whale-widget](https://github.com/MeteorNOX/DeepSeek-Balance-Whale-Widget) 二次皮肤改造。

## 安装

在 DSH 会话里让它自己装（本地 link 方式）：

```bash
dsh plugin --profile web add link:D:\编程\DeepSeek Balance qicaoji Widget\dsh-qicaoji-widget
```

然后重启 / 刷新 DSH Web 界面，七草荠就会出现在右下角。

## 目录结构

```
dsh-qicaoji-widget/
├── package.json          # 插件元数据（dsh.bundle.patch 指向 cordis.patch.yml）
├── cordis.patch.yml       # DSH bundle 挂载声明
├── lib/
│   ├── index.js           # 宿主侧插件本体（路由 + 记账 + 余额查询）
│   └── accounting.mjs      # 记账内核（定点金额运算）
└── assets/
    ├── whale-widget.js    # 前端挂件本体（前端文件名保留 whale-widget.js，路由 /dsh-whale/* 不变）
    ├── DSniang1.png       # 默认角色：黑色高领邪气笑七草荠
    ├── DSniang02.png      # 备用：水手服正面
    ├── DSniang03.png      # 备用：女仆装
    └── DSniang04.png      # 备用：修女装
```

## 特性

继承自 dsh-whale-widget 全部能力：

- 💰 余额 60 秒自动刷新 + 点击手动刷新，数字滚动动画
- 📊 今日已用记账（余额下降累计消费，上升/充值单独记录）
- 💬 每轮对话消耗泡泡（按真实 usage 换算金额）
- ⛰️ 峰谷定价（工作日高峰 9-12/14-18，周末全天谷价）
- 🖱️ 拖拽 + 四边吸附 + 左吸附水平翻转 + 按压 Q 弹
- 🧩 泡泡系统：点击序列、随机语句/图片、模块化排版、逐行样式
- 🔊 音效、余额预警、今日预算、多厂商余额

## 已做的皮肤改造

- 默认角色图 → 七草荠（4 套服装，去背透明 PNG）
- UI 文案「小鲸鱼记账」→「荠荠记账」
- 角色按钮标签「小鲸鱼」→「七草荠」
- 插件 id → `dsh-qicaoji-widget`

## 自定义

插件安装后，右键/长按七草荠打开菜单，所有内容都可在设置里改：

- **角色**：可上传自己的七草荠图（资源管理 → 角色）
- **泡泡文案**：菜单 → 按压泡泡设置，可改成《彻夜之歌》台词
  （比如「不行哦，这是我的特别」「一起度过夜晚吧」）
- **音效**：可导入七草梓的语音片段
- **吸附位置/大小**：菜单 → 吸附设置 / 大小滑块

## 备注

- 路由前缀仍为 `/dsh-whale/*`（前端硬编码，改了会断），不影响使用
- 原仓库的内置音效（小黄鸭 mp3、minecraft 经验球 wav）和泡泡 gif 未随包分发，
  首次安装按压无声效属正常，可在「音效与提示」里自行导入音频片段
- 运行时数据存在 `~/.dsh/` 下（.dshw-bubble.json / .dshw-usage.json 等）
