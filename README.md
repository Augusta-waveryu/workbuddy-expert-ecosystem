# WorkBuddy 专家技能生态 · 拆解仓库

> 把 WorkBuddy 专家市场「打开看看」：440 位专家、609 个私有技能、108 个连接器的真实构成拆解。
> 配套：**[公众号长文](公众号长文.md)** · **[自查网站](https://augusta-waveryu.github.io/workbuddy-expert-ecosystem/)** · **[网页版速查报告](拆解报告/)**

---

## 这是什么

本仓库是对 WorkBuddy 专家市场的一次**纯客户端逆向**：在不借助任何特权、不上传任何数据的前提下，把 440 位专家的展示清单、真实构件、调用关系、运行差异全部摊开来看清。

数据基准：**2026-08-19**，基于 421 个已安装插件包的真实文件系统扫描。

## 核心数字

| 维度 | 数量 |
|---:|---|
| 专家总数 | 440（市场公开 421 + 内部 19） |
| 已装到本地 | 421（48 秒批量） |
| 唯一私有 skill | 609（共享 78 / 独家 531） |
| 私有 skill 目录 | 801 |
| 全局 skill 池 | 664 |
| agent 提示词 | 712 |
| 总体积 / 文件 | 1.57 GB / 16,485 |
| 连接器 | 108 |

> 「标签 = 能力」是错觉。同名 skill 被不同专家调用，因为外层 prompt 不同，产出形态可能天差地别。

## 目录

```
workbuddy-expert-ecosystem/
├── README.md                  ← 你在这里
├── 公众号长文.md                ← 配套长文（首发平台：公众号）
├── docs/                      ← GitHub Pages 站点源（自查网站）
│   ├── index.html
│   └── data.js
├── 拆解报告/                  ← 8 份 Markdown 报告（含网页版 index.html）
│   ├── 00-连接器清单.md        （108 个连接器）
│   ├── 01-全局概览.md          （数据基准 / 路径 / 调用模型）
│   ├── 02-专家构件映射.md      （440 位专家的标签→实际构件）
│   ├── 03-Skill拆解.md         （801 私有 + 664 全局 详细清单）
│   ├── 04-关键实现学习.md      （典型 skill 实现机制深度复盘）
│   ├── 05-差异分析.md          （同标签/同 skill 差异四层模型）
│   ├── 06-安装机制逆向.md      （召唤 = 真安装，公开 COS 源）
│   └── 07-Skill排行榜.md       （谁被 12+ 专家同时引用）
└── scripts/                   ← 仓库维护脚本（可选）
```

## 三分钟自助

### 1. 想知道你装了多少专家？
直接打开 [自查网站](https://augusta-waveryu.github.io/workbuddy-expert-ecosystem/)，上传本机：
```
~/.workbuddy/plugins/marketplaces/experts/.codebuddy-plugin/marketplace.json
```
1 秒内算出覆盖率、缺哪些分类、持有的技能包数。**所有解析在浏览器本地完成，不会上传。**

### 2. 想自己批量装 421 个专家？
```bash
# 拉清单
curl -o /tmp/expert_center.json \
  https://acc-1258344699.cos.accelerate.myqcloud.com/workbuddy/expert-marketplace/expert_center.json

# 下载单个示例
curl -O https://acc-1258344699.cos.accelerate.myqcloud.com/workbuddy/expert-marketplace/bundles/content-creator.tar.gz
```
完整并发脚本可参考 `拆解报告/06-安装机制逆向.md` 第 6.4 节。

### 3. 想找最值得复用的 skill？
看 `拆解报告/07-Skill排行榜.md` 的 TOP 30。被 12+ 专家同时引用的 skill，**就是生态里的「标准工具」**，装上它等于补齐 12 位专家的公共需求。

## 几个反直觉的发现

- **87% 的 skill 是独家**——大部分专家是「带专精工具的人」，不是「共用公共库」的角色。
- **「点击召唤」是真的下载**——你的硬盘已经悄悄涨了 1.5GB，可能你只召唤过 5 个。
- **19 位内部专家无法经公开源安装**——他们走的是运营平台预签名 URL，只能 GUI 召唤。
- **同标签 ≠ 同能力**——同样的「数据分析」标签下，藏着 5 种完全不同的 prompt 范式。

## 致谢

数据完全来自本地公开文件系统扫描，未对 WorkBuddy 服务器做任何主动攻击或未授权访问。公开 COS 源是官方客户端的默认降级地址，本项目只是将其工程化复用。

## 许可

本仓库文档采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)；代码脚本采用 [MIT](https://opensource.org/licenses/MIT)。引用本仓库数据请注明出处。

---

> 如果你是 WorkBuddy 重度用户，强烈建议**先自查再决定要不要召唤**——你会发现自己真正缺的，往往不是某位专家，而是一个被 12 个专家同时引用的 `market-researcher` skill。
