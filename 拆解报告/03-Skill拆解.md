# 03 · Skill 全量拆解

> 两个池子：**全局 skill 池 1165 个**（独立安装，所有专家共用） + **专家私有 skill 801 个目录 / 609 个不同名**（随插件包分发，仅该专家可见）。

## 3.1 两类 skill 的本质区别

| 维度 | 全局 skill | 专家私有 skill |
|---|---|---|
| 存放位置 | `~/.workbuddy/skills/`、`plugins/marketplaces/workbuddy-builtin/` 等 | `experts/plugins/<plugin>/skills/` |
| 分发方式 | 独立安装/预装 | 随专家包 tar.gz 一起下发 |
| 可见范围 | 全局，任何会话 | 仅激活该专家的会话 |
| 命名冲突 | 全局唯一 | 可与全局同名，**专家包内优先** |
| 典型用途 | 通用能力（文档、表格、浏览器、搜索） | 专业方法论（DCF 模型、CIM 拆解、投行清单） |

> **关键**：专家私有 skill 可与全局 skill 同名（如 `humanizer`、`github`、`deep-research`），此时加载的是专家包内那份 —— 这是「同名 skill 执行差异」的根因之一，详见 05。

## 3.2 形态分布

| 形态 | 数量 | 判定依据 |
|---|---:|---|
| 代码型（带 `scripts/`） | 247 | 目录内有 `scripts/`，可执行真实逻辑 |
| 提示型（纯 SKILL.md） | 554 | 只有 `SKILL.md`，靠提示词约束流程 |

## 3.3 跨专家复用的私有 skill（78 个）

被 ≥2 位专家携带的同名 skill，是「同一技能不同执行」的观察样本。

| 复用数 | skill 名 | 携带该 skill 的专家 |
|---:|---|---|
| 15 | `minimax-docx` | 文博凯 · 关德豪 · 文档达 · 策必中 · 图说说 · 流畅畅 · 探真真 · 律守正 · 文通通 · 闪造造 · 方案通 · 掘需需 · 救火队 · 合规规 · 政通通 |
| 12 | `market-researcher` | 卖得好 · 裂变变 · 播旺旺 · 暖心心 · 策必中 · 风向标 · 探真真 · 文通通 · 拓客客 · 掘需需 · 听声声 · 链优优 |
| 12 | `neodata-financial-search` | 财数数 · 投资大师专家团 · A股研究团队 · 季明辨 · 严研行 · 莫百炼 · 白必得 · 顾估衡 · 回测明算 · 刺桐说Pro-投资社群嘉宾团 · 基金投研分析师 · 丁笃行 |
| 10 | `anti-distill` | 文博凯 · 斗音音 · 单必成 · 剪神神 · 搜霸霸 · 郝文昌 · 度优优 · 著书书 · 助推推 · 剧本本 |
| 9 | `browser-use` | 像素君 · 海跨洋 · 策必中 · 体验达 · 风向标 · 探真真 · 吴八哥 · 像素匠 · 链优优 |
| 8 | `xlsx-author` | 季明辨 · 钱对齐 · 查本源 · 莫百炼 · 关月结 · 白必得 · 审细明 · 顾估衡 |
| 7 | `humanizer` | 文博凯 · 斗音音 · 盾卫卫 · 薛红笙 · 点睛睛 · 郝文昌 · 全域内容分发专家团 |
| 7 | `westock` | A股研究团队 · 季明辨 · 严研行 · 莫百炼 · 白必得 · 顾估衡 · 丁笃行 |
| 6 | `audit-xls` | 季明辨 · 钱对齐 · 莫百炼 · 关月结 · 白必得 · 审细明 |
| 6 | `deep-research` | 深网网 · 文通通 · 合规规 · 选品品 · 政通通 · 插件达 |
| 6 | `fullstack-dev` | 深网网 · 吴八哥 · 像素匠 · 磐石石 · 架构通 · 小程达 |
| 6 | `github` | 像素匠 · 火眼眼 · 分支通 · 调度达 · 看板达 · 析测测 |
| 6 | `multi-search-engine` | 卖得好 · 简明明 · 搜霸霸 · 文通通 · 关卡卡 · 门头沟营商顾问 |
| 6 | `wechat-article-search` | 简明明 · 郝文昌 · 方案通 · 深研研 · 析数数 · 全域内容分发专家团 |
| 5 | `frontend-dev` | 像素君 · 吴八哥 · 像素匠 · 磐石石 · 规范范 |
| 5 | `marketing-skills` | 薛红笙 · 裂变变 · 播旺旺 · 弹幕幕 · 度优优 |
| 4 | `cloudq` | CloudQ · 腾讯云技术支持 · 腾讯云行业 SRE · CloudQ |
| 4 | `comps-analysis` | 建模模 · 严研行 · 莫百炼 · 白必得 |
| 4 | `dcf-model` | 建模模 · 银拓远 · 莫百炼 · 白必得 |
| 4 | `fbs-bookwriter` | 搜霸霸 · 著书书 · 听声声 · 助推推 |
| 4 | `impeccable` | 像素君 · 像素匠 · 小程达 · 规范范 |
| 4 | `lbo-model` | 建模模 · 银拓远 · 莫百炼 · 白必得 |
| 4 | `pdb-viewer-skill` | 腾讯组学生信分析专家 · 腾讯IgGM抗体药物研发专家 · 腾讯ORI蛋白设计专家 · 腾讯tFold抗体结构预测专家 |
| 3 | `competitive-analysis` | 产品通 · 建模模 · 严研行 |
| 3 | `ima-skills` | 裂变变 · 风向标 · 律守正 |
| 3 | `online-search` | 终端老兵专家（陈丰伟） · 新闻资讯专家 · 热点猎手 |
| 3 | `pptx-author` | 严研行 · 周备全 · 白必得 |
| 3 | `sector-overview` | 严估深 · 严研行 · 白必得 |
| 3 | `xlsx` | 析数数 · 理文文 · 生辰命理大师 |
| 2 | `3-statement-model` | 莫百炼 · 白必得 |
| 2 | `agent-browser-core` | 深网网 · 一键达 |
| 2 | `agent-team-orchestration` | 流畅畅 · 深网网 |
| 2 | `ai-shifu-course-creator` | AI师傅 · AI师傅 |
| 2 | `andonq` | 腾讯云技术支持 · AndonQ |
| 2 | `brand-guidelines` | 盾卫卫 · 点睛睛 |
| 2 | `cantian-bazi` | 运势分析师 · 生辰命理大师 |
| 2 | `client-report` | 理财财 · 周备全 |
| 2 | `client-review` | 理财财 · 周备全 |
| 2 | `company-tearsheet` | 严估深 · 银拓远 |
| 2 | `comps-valuation` | 严估深 · 银拓远 |
| 2 | `data-visualization` | 舒明析 · 探数数 |
| 2 | `databrain-competitor-events` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `databrain-game-content-trend` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `databrain-opinion-alert` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `databrain-opinion-hotposts` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `databrain-opinion-metrics` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `databrain-opinion-summary` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `docx` | 理文文 · 生辰命理大师 |
| 2 | `earnings-analysis` | 严估深 · 季明辨 |
| 2 | `earnings-preview` | 严估深 · 季明辨 |
| 2 | `ic-memo` | 募资资 · 顾估衡 |
| 2 | `idea-generation` | 严估深 · 严研行 |
| 2 | `ihr-base` | 利唐智语AI面谈官 · 利唐智语AI面试官 |
| 2 | `ihr-conference` | 利唐智语AI面谈官 · 利唐智语AI面试官 |
| 2 | `ihr-shared` | 利唐智语AI面谈官 · 利唐智语AI面试官 |
| 2 | `investment-proposal` | 理财财 · 周备全 |
| 2 | `invoice-verify` | 智能发票专家团 · 票证核验专家 |
| 2 | `jiaozhen-factcheck` | 方案通 · 合规规 |
| 2 | `libtv-skill` | 拓刻刻 · 全域内容分发专家团 |
| 2 | `lucide-icons` | 速构构 · 动画画 |
| 2 | `memo-builder` | 严估深 · 银拓远 |
| 2 | `migraq` | 腾讯云技术支持 · 腾讯云上云迁移专家团 |
| 2 | `model-update` | 严估深 · 季明辨 |
| 2 | `morning-note` | 严估深 · 季明辨 |
| 2 | `mp-draft-push` | 郝文昌 · 全域内容分发专家团 |
| 2 | `novel-writing` | 文博凯 · 剧本本 |
| 2 | `omics-run-diagnosis` | 腾讯组学生信分析专家 · 腾讯组学任务分析智能诊断专家 |
| 2 | `opinions-crawler` | DataBrain舆情分析专家 · DataBrain X TideRider |
| 2 | `pdf` | 理文文 · 生辰命理大师 |
| 2 | `pitch-deck` | 银拓远 · 白必得 |
| 2 | `portfolio-monitoring` | 募资资 · 顾估衡 |
| 2 | `returns-analysis` | 募资资 · 顾估衡 |
| 2 | `skill-creator` | 建模模 · 技术公益专家团 |
| 2 | `tencent-rce-skill` | 天御营销保护 · 天御账号保护 |
| 2 | `uae-corpus` | 阿联酋公共事务专家 · 阿联酋战略顾问专家 |
| 2 | `westock-data` | 腾讯自选股股票投研专家团 · 回测明算 |
| 2 | `westock-tool` | 腾讯自选股股票投研专家团 · 回测明算 |
| 2 | `xiaohongshu` | 薛红笙 · 全域内容分发专家团 |

## 3.4 专家私有 skill 全表

按专家分组，列出全部 801 个私有 skill 目录及其 `description`（skill 路由的唯一依据）。

### 银拓远 `InvestmentBankingExpert` — 22 个

插件包 `investment-banking` ｜ agents: `investment-banking-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `buyer-list` | 提示型 | 1 | Build and organize a universe of potential acquirers for sell-side M&A processes. Identifies strategic and financial buyers, assesses fit, and prioritizes outre |
| `capital-markets` | 提示型 | 1 | \| |
| `cim-builder` | 提示型 | 1 | Structure and draft a Confidential Information Memorandum for sell-side M&A processes. Organizes company information into a professional, investor-ready documen |
| `cim-teardown` | 提示型 | 1 | \| |
| `company-tearsheet` | 提示型 | 1 | \| |
| `comps-valuation` | 提示型 | 1 | \| |
| `datapack-builder` | 提示型 | 1 | Build professional financial services data packs from various sources including CIMs, offering memorandums, SEC filings, web search, or MCP servers. Extract, no |
| `dcf-model` | 提示型 | 1 | \| |
| `deal-tracker` | 提示型 | 1 | Track multiple live deals with milestones, deadlines, action items, and status updates. Maintains a deal pipeline view and surfaces upcoming deadlines and overd |
| `lbo-model` | 提示型 | 1 | \| |
| `meeting-prep` | 提示型 | 1 | \| |
| `memo-builder` | 提示型 | 1 | \| |
| `merger-model` | 提示型 | 1 | Build accretion/dilution analysis for M&A transactions. Models pro forma EPS impact, synergy sensitivities, and purchase price allocation. Use when evaluating a |
| `model-audit` | 提示型 | 1 | \| |
| `pitch-deck` | 提示型 | 5 | Populates investment banking pitch deck templates with data from source files. Use when: user provides a PowerPoint template to fill in, user has source data (E |
| `private-credit` | 提示型 | 1 | \| |
| `process-letter` | 提示型 | 1 | Draft process letters and bid instructions for sell-side M&A processes. Covers initial indication of interest (IOI) instructions, final bid procedures, and mana |
| `restructuring` | 提示型 | 1 | \| |
| `scenario-sensitivity` | 提示型 | 1 | \| |
| `strip-profile` | 提示型 | 1 | \| |
| `teaser` | 提示型 | 1 | Draft anonymous one-page company teasers for sell-side M&A processes. Creates a compelling summary without revealing the company's identity, designed to gauge b |
| `three-statement-model` | 提示型 | 1 | \| |

### 同舟股市投研专家 `FinResearchExpert` — 18 个

插件包 `fin-research-expert` ｜ agents: `fin-research-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `fin-mcp-gateway` | 提示型 | 9 | \| |
| `layer1-doc-search` | 提示型 | 7 | Use when you need structured retrieval for news, company news, events, announcements, research reports, meeting minutes, morning briefings, timelines, or docume |
| `layer1-fin-data` | 提示型 | 6 | Use when you need structured financial data such as prices, rankings, limit-up/limit-down screening, stock pattern counts, ETF/industry constituents, valuation  |
| `layer1-fin-graph` | 提示型 | 6 | Use when you need industry/theme identity resolution, industry graph nodes/public factors, industry-chain graph overview/tree/node/map access, industry viewpoin |
| `layer1-same-boat` | 提示型 | 2 | Use for read-only Chinese investment research / 投研知识库 queries: 行业/板块/概念研究目录, 分析师资料, 研报观点, 市场要闻, 分析师解读, 行情异动归因, 行业观点, market news, analyst viewpoints, sector vie |
| `layer2-announcement-brief` | 提示型 | 1 | 当用户询问某条公告的内容或含义时——如'帮我看一下这条股权激励公告''腾亚精工最近公告说了什么''这条业绩预告主要说了什么'。必须先获取公告原文再展开分析，不是泛新闻或研报综述。 |
| `layer2-evidence-ledger` | 提示型 | 1 | 当用户需要把已取证的公开股市投研材料整理成证据台账、信源审计、证据强弱表或结论依据清单时使用。只整理和校验已有证据，不负责新增取数、认证、预测、账户诊断或生成新事实。 |
| `layer2-html-research-playbook` | 提示型 | 2 | Render an already-evidenced public equity research brief into a standalone WorkBuddy-ready HTML artifact. Use as the shared presentation dependency after a Laye |
| `layer2-industry-brief` | 提示型 | 1 | 当用户询问某个具体行业的近况、景气、估值或政策影响时——如'白酒最近怎么看''动力煤行业发生了什么''半导体景气如何'。聚焦单一具体行业；跨多行业找方向时先收窄到具体行业、事件或研报证据；个股问题用 stock-brief。 |
| `layer2-policy-event-brief` | 提示型 | 1 | 当用户问具体政策事件、官方会议表态或监管动向时——如'这次降准对市场意味着什么''最近重要会议释放了什么信号''这个行业政策变化影响哪些方向'。侧重政府/监管发布的具体政策解读；宏观国际风险只在有明确公开事件证据时做有限背景说明。 |
| `layer2-research-digest` | 提示型 | 1 | 当用户明确询问研报内容或分析师/机构观点时——如'最近茅台有哪些研报''券商怎么看白酒''最近策略研究在关注什么'。主角是研究观点和报告共识，不是行情或新闻综述（那用 stock-brief 或 industry-brief）。 |
| `layer2-research-red-team` | 提示型 | 1 | 当用户需要对公开股市投研结论做反方审查、证伪检查、风险透视、叙事漏洞排查或多空证据拆分时使用。只基于已取证材料进行批判性复核，不负责新增取数、预测、回测、账户诊断或交易建议。 |
| `layer2-research-visuals` | 代码型 | 12 | 当用户明确要求K线、走势图、事件收益图、数据对比图、研报图片，或已取证数据用图形更易理解时使用。负责普通问答中的可复核可视化、WorkBuddy内联显示和跨客户端表格降级；不新增数据权限、不生成预测、不替代HTML Playbook。 |
| `layer2-stock-brief` | 提示型 | 1 | 当用户明确提到某个具体股票或上市公司时——如'保隆科技最近怎么了''帮我快速看一下600519''茅台最近有什么重要信息'。整合行情、公告、新闻和研报。行业整体问题用 industry-brief，研报专项用 research-digest，公告专项用 announcement-brief。 |
| `layer2-stock-narrative-valuation` | 代码型 | 2 | 当用户已经点名某个具体股票或上市公司，并希望做深度个股叙事、估值隐含预期、股价为何涨跌、是否透支、历史主升浪复盘、商业模式/护城河或反方证伪时使用。基于公开资料、行情、财务指标、研报和产业空间假设，分析市场当前可能隐含了什么终局预期。仅做公开投研推演，不输出买卖、仓位、目标价或个人账户建议；最近新闻/公告快查仍用 la |
| `layer2-transmission-chain-builder` | 提示型 | 1 | 当用户需要把公开事件、行业异动、政策或主题行情拆成事件到机制到产业链上下游的传导链路时使用。适用于 MLCC、新能源、AI 算力、半导体等行业/板块解释，不负责预测、回测、账户诊断或生成新事实。 |
| `layer3-event-interpretation` | 提示型 | 2 | Generate the complete 事件因子解读 user story as one evidence-backed HTML file. Use when the user asks to turn a policy, announcement, news, company, or industry even |
| `layer3-industry-windvane` | 提示型 | 2 | Generate the complete 行业多空风向标 user story as one evidence-backed HTML file. Use when the user names a dynamic industry or theme and asks for an industry bull/bea |

### 严估深 `EquityResearchExpert` — 16 个

插件包 `equity-research` ｜ agents: `equity-research-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `catalyst-calendar` | 提示型 | 1 | Build and maintain a calendar of upcoming catalysts across a coverage universe — earnings dates, conferences, product launches, regulatory decisions, and macro  |
| `company-tearsheet` | 提示型 | 1 | \| |
| `comps-valuation` | 提示型 | 1 | \| |
| `dcf-model-builder` | 提示型 | 1 | \| |
| `earnings-analysis` | 提示型 | 4 | \| |
| `earnings-preview` | 提示型 | 1 | [DEPRECATED] Merged into earnings-analysis skill. Use earnings-analysis for both pre-earnings preview and post-earnings analysis. |
| `event-scenario-analyzer` | 提示型 | 1 | \| |
| `idea-generation` | 提示型 | 1 | Systematic stock screening and investment idea sourcing. Combines quantitative screens, thematic research, and pattern recognition to surface new long and short |
| `initiating-coverage` | 提示型 | 9 | Create institutional-quality equity research initiation reports through a 5-task workflow. Tasks 1 & 2 can run in parallel. Tasks 3-5 have sequential dependenci |
| `long-short-pitch` | 提示型 | 1 | \| |
| `memo-builder` | 提示型 | 1 | \| |
| `model-update` | 提示型 | 1 | Update financial models with new data — quarterly earnings, management guidance, macro changes, or revised assumptions. Adjusts estimates, recalculates valuatio |
| `morning-note` | 提示型 | 1 | Draft concise morning meeting notes summarizing overnight developments, trade ideas, and key events for coverage stocks. Designed for the 7am morning meeting fo |
| `portfolio-risk` | 提示型 | 1 | \| |
| `sector-overview` | 提示型 | 1 | Create comprehensive industry and sector landscape reports covering market dynamics, competitive positioning, key players, and thematic trends. Use for client r |
| `thesis-tracker` | 提示型 | 1 | Maintain and update investment theses for portfolio positions and watchlist names. Track key data points, catalysts, and thesis milestones over time. Use when u |

### HR数智专家 `HrDigitalExpert` — 15 个

插件包 `hr-digital-expert` ｜ agents: `hr-digital-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-boost` | 代码型 | 37 | Analyze any deployed web application and add a smart Agent layer to it. Triggered by /agent-boost. Scans the project, recommends an Agent + Skills combo, asks t |
| `auth-code-checker` | 提示型 | 1 | > |
| `auth-code-developer` | 代码型 | 2 | > |
| `auth-code-tester` | 提示型 | 1 | > |
| `data-table-permission-checker` | 提示型 | 1 | 查询用户的HR数仓数据权限信息。当用户想了解自己是否有某张表或某些字段的访问权限、或想确认SQL查询结果中某些异常值是否因权限不足被脱敏时，使用本Skill。使用场景：1.用户询问自己有哪些表的数据权限。2.用户想确认是否有某张表的访问权限。3.用户想了解自己对某张表的行权限和列权限范围。4.查询结果中出现疑似脱敏值（ |
| `data-warehouse-api-codegen` | 提示型 | 2 | 提供标准化的数仓 HTTP 查询接口调用能力。当用户需要从数据仓库获取数据时，根据接口规范生成正确的前端调用代码。⚠️严格限制：数仓接口只能在前端页面（浏览器端）中调用，严禁在任何后端代码（Node.js、Python、Go、Java等后端服务）中调用，因为后端环境没有用户的SSO身份信息，调用会报错。使用场景：1.用 |
| `hr-ai-knowledge` | 提示型 | 6 | HR AI 知识检索。基于 hr-ai-knowledge MCP 的 knowledge_search 工具，支持多来源语义检索（团队空间、HR 知识库、企微文档）。触发短语："查HR"、"HR知识"、"搜索知识库"、"政策查询"、"检索文档"、"search knowledge"、"查公司制度"。 |
| `hr-common-llm` | 提示型 | 3 | \| |
| `hr-data-sql-builder` | 提示型 | 1 | 生成HR数仓StarRocks查询SQL。覆盖员工信息/人员异动/绩效/梯队等查询，含术语映射、业务规则和SQL模板。表结构从MCP resources动态获取。用户提出数据查询需求时必须使用本Skill。指标类查询（涉及率/比/占比/平均值/趋势等计算指标）必须使用indicator-query Skill。 |
| `hr-right` | 提示型 | 9 | 权限中台最全面的权限的查询、申请、变更、续期、删除，以及权限到期提醒。 适用场景：用户提出权限查询、申请（新增/变更/续期）、清理（删除/撤销/取消授权）、到期情况。 |
| `hr-vue-next` | 提示型 | 22 | This skill provides guidance for using the hr-vue-next component library via UMD. It should be used when building HR-related web pages that require employee sel |
| `hrclaw-message` | 提示型 | 1 | 当用户在自己搭建的 AI 生成网页（前端页面）中需要集成"发送邮件"或"发送企业微信 Tips"能力时使用。只要用户提到在页面里想要发邮件、发企微消息、通知同事、给某某同学发通知、一键给团队群发邮件、页面上加一个"发送"按钮、集成消息推送、调用 HR 消息通道等需求，就应当触发本 skill。即便用户没有明确说"HRC |
| `indicator-api-codegen` | 提示型 | 2 | 提供标准化的指标 HTTP 查询接口调用能力。当用户需要在前端页面查询预置指标数据（如比率、占比、平均值、人均、趋势对比、流入流出率等）时，根据接口规范生成正确的前端调用代码。⚠️严格限制：指标接口只能在前端页面（浏览器端）中调用，严禁在任何后端代码（Node.js、Python、Go、Java等后端服务）中调用，因为 |
| `indicator_query` | 提示型 | 1 | 通过预置指标API查询HR数据。当用户需要查询涉及计算逻辑的数据（如比率、占比、平均值、人均、趋势对比、流入流出率等）时优先使用本Skill。指标口径经过业务验证，比手写SQL更准确。 |
| `page-deliver` | 提示型 | 40 | You MUST use this skill for ANY task involving code generation, page creation, publishing, deployment, or going live. 触发词：HRClaw、部署、发布、生成看板、生成页面、page-deliver、上线 |

### 一站式视频创作专家 `ChatcutVideoEditor` — 13 个

插件包 `chatcut-video-editor` ｜ agents: `chatcut-video-editor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `asset-import` | 代码型 | 2 | Import local or attached media files, readable user-provided paths, existing ChatCut assets, and public media URLs into a ChatCut project from WorkBuddy. |
| `export` | 提示型 | 1 | Export, render, download, or deliver a ChatCut timeline from WorkBuddy as video, audio, subtitles, Premiere Pro or DaVinci Resolve-compatible project files, or  |
| `image-gen` | 提示型 | 3 | \| |
| `known-errors` | 提示型 | 1 | Use when a ChatCut plugin tool call fails or returns an unexpected shape. |
| `motion-graphics` | 提示型 | 1 | Add, directly author, edit, and place editable Motion Graphics in ChatCut from WorkBuddy using inline JSX, existing library assets, and timeline tools. |
| `music` | 提示型 | 1 | \| |
| `shader-gen` | 提示型 | 6 | \| |
| `talking-head-guide` | 提示型 | 1 | \| |
| `transcription` | 提示型 | 1 | Use when a video/audio task needs ChatCut transcription, captions, subtitles, subtitle styling, transcript search, transcript readiness checks, or enabling capt |
| `verification` | 提示型 | 1 | Verify that ChatCut edits made from WorkBuddy are present in project state and, when possible, visually correct in the editor or rendered frames. |
| `video-gen` | 提示型 | 3 | \| |
| `voice` | 提示型 | 3 | Create and place ChatCut voiceover, narration, and custom sound effects from WorkBuddy while keeping timing, voice choice, and credit confirmation explicit. |
| `widget-forms` | 提示型 | 1 | Use when ChatCut work in WorkBuddy requires structured user choices or clarification through ordinary chat or a host-native question surface. |

### 白必得 `PitchAgent` — 13 个

插件包 `pitch-agent` ｜ agents: `pitch-agent`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `3-statement-model` | 提示型 | 4 | Complete, populate and fill out 3-statement financial model templates (Income Statement, Balance Sheet, Cash Flow Statement) . Use when asked to fill out model  |
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `comps-analysis` | 提示型 | 1 | \| |
| `dcf-model` | 代码型 | 4 | Real DCF (Discounted Cash Flow) model creation for equity valuation. Retrieves financial data from SEC filings and analyst reports, builds comprehensive cash fl |
| `deck-refresh` | 提示型 | 1 | Updates a presentation with new numbers — quarterly refreshes, earnings updates, comp rolls, rebased market data. Use whenever the user asks to "update the deck |
| `ib-check-deck` | 代码型 | 4 | Investment banking presentation quality checker. Reviews a pitch deck or client-ready presentation for (1) number consistency across slides, (2) data-narrative  |
| `lbo-model` | 提示型 | 1 | This skill should be used when completing LBO (Leveraged Buyout) model templates in Excel for private equity transactions, deal materials, or investment committ |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `pitch-deck` | 提示型 | 5 | Populates investment banking pitch deck templates with data from source files. Use when: user provides a PowerPoint template to fill in, user has source data (E |
| `pptx-author` | 代码型 | 59 | Use this skill any time a .pptx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or presentations; rea |
| `sector-overview` | 提示型 | 1 | Create comprehensive industry and sector landscape reports covering market dynamics, competitive positioning, key players, and thematic trends. Use for client r |
| `westock` | 代码型 | 11 | \| |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### DataBrain `DatabrainAgentV2` — 11 个

插件包 `databrain-agent-v2` ｜ agents: `databrain-agent-v2`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `colorful-dark-style-html` | 提示型 | 1 | Generate dark-tech colorful HTML pages for presentations, PPT-style pages, feature introductions, and workflow comparisons. Keywords: dark theme, deep color pag |
| `databrain-ai-gallery-upload` | 代码型 | 10 | >- |
| `databrain-analysis` | 提示型 | 20 | >- |
| `databrain-dashboard-service` | 代码型 | 61 | Query first-party (经分) game metrics (active users, revenue, sales, retention, ARPU, CCU/PCU, ASP, refund, LTV, wishlist, game-specific feature data, ua impressi |
| `databrain-datalab-analyst` | 代码型 | 15 | >- |
| `databrain-entity-resolver` | 代码型 | 2 | Resolve game/company names to canonical DataBrain entities + per-system permissions. Run once per query before any data skill when the user names games or compa |
| `databrain-intelligence` | 代码型 | 60 | DataBrain intelligence data query assistant. Translates natural language questions into executable BigQuery SQL for the intelligence domain: market data (Sensor |
| `databrain-mgmt-service` | 代码型 | 35 | Query DataBrain Management (MGMT/管理) data for users with MGMT permission — IEGG / publishing / studio / project commercialization and management metrics includi |
| `databrain-opinion-metrics-service` | 代码型 | 31 | DataBrain 舆情指标查询助手。把游戏舆情/口碑/声量/情感/评分/KOL/直播/新闻/热门视频/热门帖子/Hashtag/热梗/竞品/官号 等问题，以及**游戏广告投放素材/创意取数**（创意数·素材数·素材类型·渠道·国家维度·素材明细列表）翻译成可执行的 BigQuery SQL，覆盖 opinion /  |
| `databrain-opinion-service` | 代码型 | 89 | Generate qualitative public opinion deliverables for games — packaged summary reports, topic deep-dive with representative player comments and URLs, single YouT |
| `databrain-summarize` | 提示型 | 3 | >- |

### 懒人出游规划师 `LazyTravelPlanner` — 11 个

插件包 `lazy-travel-planner` ｜ agents: `travel-planner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `accommodation-pick` | 代码型 | 2 | 住宿选型 · 美团连接器一手房态价格为主，xhs-explore skill 拉真实住客评价识别水军，online-search（地理搜索） 评估位置。三维评分（位置 × 价位 × 口碑），输出 3-5 个酒店候选给用户挑。 |
| `budget-balance` | 代码型 | 2 | 预算平衡与取舍 · 按总预算分配交通/住宿/餐饮/门票/购物/备用六大类，超支时主动给"砍哪天/降哪档/换地点"的取舍建议。基于 price_benchmark.json 城市价格基准做合理性校验。 |
| `destination-research` | 代码型 | 2 | 目的地调研 · 把"江西附近游玩"或"成都"这类输入，转成结构化的目的地候选清单（含特色/季节性/必玩/避雷）。完全调用 search-orchestrator 编排底座，不重复造检索逻辑。 |
| `intake-clarify` | 提示型 | 1 | 出游需求澄清 · 只问 3 件事（目的地/日期/人数），其余靠 agent 思考-调工具-给选项-必要追问。绝不一次问 10 个问题，绝不静默用默认值。老用户从 user_profile 默认沿用。 |
| `itinerary-optimize` | 代码型 | 5 | ⭐ 行程运筹核心壁垒 · 把 Top N POI 池转成"地理顺路 + 体力分配 + 时间窗匹配"的可执行行程。三步走：K-Means 地理聚类分天 → TSP 贪心+2-opt 排顺路 → 体力/营业/用时窗适配。这是通用 AI 完全做不好的事。 |
| `poi-curate` | 代码型 | 2 | POI 多维加权打分 · 基于美团/online-search的 POI 详情 + 小红书评论 + 用户偏好画像，按 scoring_rules.json 多维度打分，输出每天可塞入的 Top N POI 清单。是 itinerary-optimize 的输入。 |
| `preference-load` | 代码型 | 4 | 用户偏好画像加载与增量学习 · 加载 user_profile.json / 首次走 BOOTSTRAP 极简 3 题问卷 / 每次对话后从对话内容自动抽取增量 / 顺便做数据源体检。这是 agent 跨次复用的护城河。 |
| `report-render` | 代码型 | 13 | ⭐ HTML 行程书生成 · 把上游所有 JSON（itinerary/transport/hotel/budget/risk）渲染成单文件 HTML，含 Leaflet 地图（每天分色路线）+ 时间轴 + POI 卡片 + 预算饼图 + 风险面板 + 行前清单。写到 output/，preview_url 打开。 |
| `risk-check` | 代码型 | 2 | 出行风险体检 · 天气预警 / 限行 / 节假日人流 / 当地骗局 / 应急联系。结合 risk_knowledge.json 静态知识 + online-search 实时天气 + xhs-explore skill"避雷"搜索。按置信度绿/黄/灰输出。 |
| `search-orchestrator` | 代码型 | 8 | 搜索编排底座 · 把"江西附近游玩"这类模糊地理意图转成结构化查询矩阵，调度online-search / 美团连接器 / xhs-explore skill 做 fan-out → fan-in 多源混合检索，输出带置信度的候选地点 + 内容证据池。是 03/04/06/09 的共用底座。 |
| `transport-plan` | 代码型 | 2 | 交通方案规划 · 大交通（高铁/飞机推荐+备选）+ 市内交通（地铁/打车/公交）。美团连接器 + online-search（火车票查询） 双源校验高铁，机票走 WebSearch 兜底。永远标注"参考价 + 查询时间"。 |

### 小花创意 `DesignPrototypeExpert` — 10 个

插件包 `design-prototype-expert` ｜ agents: `design-prototype-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `aesthetic-starter-kits` | 提示型 | 1 | 10 prebuilt aesthetic templates, each a complete design system. When the user has no brand assets and needs a fast start, show these kits first — selecting one  |
| `design-system-extract` | 提示型 | 1 | 从用户提供的截图/URL/代码库/品牌资料中提取设计 Token（配色、字体、间距、圆角、阴影、卡片样式），并细化所有可复用组件的完整规范（变体、状态、尺寸）。一个技能覆盖 Token 抽取与组件细化两个阶段。 |
| `discovery-questions` | 提示型 | 1 | Structured discovery questionnaire for new design tasks. Asks minimum necessary questions covering product, audience, page goal, output format, existing assets, |
| `frontend-aesthetic-direction` | 提示型 | 1 | Generates 3-4 distinct aesthetic directions after starter kits have been rejected or when the user explicitly requests custom directions. Each direction has a c |
| `generate-variations` | 提示型 | 1 | Explores variations on an existing prototype. After a prototype exists, generates hi-fi variants along 2-3 design dimensions (warmth vs cold vs playful, loose v |
| `make-a-deck` | 提示型 | 1 | Generates an HTML slide deck following the design system. One core message per slide, max 6 lines, clear visual hierarchy, keyboard navigation, 0.2-0.3s transit |
| `make-prototype` | 提示型 | 1 | Generates high-fidelity HTML prototypes strictly following the DesignSystemManifest. Uses defined colors, fonts, spacing, and components. Includes all interacti |
| `make-tweakable` | 提示型 | 1 | Overlays a floating control panel on the prototype allowing real-time adjustment of color tokens, type scale, font weight, spacing multiplier, radius, and shado |
| `qa-review` | 提示型 | 1 | 交付前五道质量检查合为一体：AI 味检测、可访问性审查、层级与节奏审查、交互状态审查、终检汇总。前四项独立检测，第五项引用前四项结果做汇总判定，不重复检测。产出最终 QAReport（含 P0/P1/P2 优先级和交付判定）。 |
| `wireframe` | 提示型 | 1 | Low-fidelity wireframe exploration to test layout and information hierarchy before committing to hi-fi. Produces 3+ layout variants using ASCII art, each annota |

### Makers 开发专家团 `EdgeoneMakersExperts` — 10 个

插件包 `edgeone-makers-experts` ｜ agents: `agent-specialist`, `backend-specialist`, `edgeone-makers-team-lead`, `frontend-specialist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `makers-agents` | 提示型 | 23 | >- |
| `makers-cli` | 提示型 | 1 | >- |
| `makers-cloud-functions` | 提示型 | 5 | >- |
| `makers-deploy` | 提示型 | 2 | >- |
| `makers-edge-functions` | 提示型 | 1 | >- |
| `makers-env-adaption` | 提示型 | 1 | >- |
| `makers-middleware` | 提示型 | 1 | >- |
| `makers-migration` | 提示型 | 7 | >- |
| `makers-recipes` | 提示型 | 1 | >- |
| `makers-storage` | 提示型 | 3 | >- |

### 创迪 `IndieFounderCoach` — 10 个

插件包 `indie-founder-coach` ｜ agents: `indie-founder-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `company-values` | 提示型 | 1 | \| |
| `find-community` | 提示型 | 1 | \| |
| `first-customers` | 提示型 | 1 | \| |
| `founder-review` | 提示型 | 1 | \| |
| `grow-sustainably` | 提示型 | 1 | \| |
| `marketing-plan` | 提示型 | 1 | \| |
| `mvp` | 提示型 | 1 | \| |
| `pricing` | 提示型 | 1 | \| |
| `processize` | 提示型 | 1 | \| |
| `validate-idea` | 提示型 | 1 | \| |

### DataBrain X TideRider `TideriderSentiment` — 10 个

插件包 `tiderider-sentiment` ｜ agents: `tiderider-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `bigquery-sentiment` | 代码型 | 11 | \| |
| `bug-radar` | 代码型 | 12 | \| |
| `databrain-competitor-events` | 代码型 | 21 | 游戏竞品活动报告生成工具。当用户需要对某款游戏生成官媒发帖内容和官方活动报告时使用，依次执行数据获取、活动聚合、联网搜索、总结分析四个主要工作模块，最终保存并展示指定格式的竞品报告。触发示例："帮我做一份 XXX 的竞品活动分析"、"生成 XXX 游戏官帖分析报告"、"最近 XXX 有什么官方活动？"。 |
| `databrain-game-content-trend` | 代码型 | 13 | 游戏创意灵感引擎。融合 TikTok/YouTube 热门视频和行业热梗数据，为游戏运营/市场团队提供社媒内容制作灵感和端内资源跟进建议。当用户询问"今日热门"、"游戏内容灵感"、"素材方向"、"官号整活"、"趋势情报"、"热梗"、"热点借势"、"KOL 合作方向"、"端内动作"、"做进游戏"时触发。也应在用户用模糊表 |
| `databrain-opinion-alert` | 代码型 | 26 | 游戏舆情告警 Skill。监控游戏口碑指标并推送企业微信告警。当前主推「商店评分告警 v2」（Steam / Google Play / App Store 三渠道，P0/P1/P2 三级，支持分语种/分国家全切片自动评估、四维触发条件、静默期、归因），保留向后兼容的 KOL 热帖告警与关键词声量告警。当用户需要「设置 |
| `databrain-opinion-hotposts` | 代码型 | 17 | 按订阅游戏生成「过去 N 小时各平台热帖日报」，分平台（Reddit / X / YouTube / Steam / TikTok / Discord / 官方论坛 / Instagram / Facebook）出榜、每榜 Top 1-10 可配，输出 markdown / html 并可一键投递到 AI Galler |
| `databrain-opinion-metrics` | 代码型 | 15 | 查询游戏舆情核心指标。支持声量、情绪分布、Brand Health、互动量、分渠道/分语种分布、Steam 评论评分、社区指标等。当用户询问游戏的"舆情"、"口碑"、"声量"、"情绪"、"评分"、"社媒表现"、"正负面评价"、"玩家讨论"、"Brand Health"时触发。 |
| `databrain-opinion-summary` | 代码型 | 7 | 通过 Databrain 生成指定游戏、时段的舆情 AI 总结报告，快速掌握玩家讨论的核心观点与口碑趋势。在用户需要「舆情总结」「口碑摘要」「玩家讨论总结」「AI 解读评论」「一段时间内的舆情报告」时使用；需先解析游戏名得到 game_id 与平台类型。 |
| `opinions-crawler` | 代码型 | 5 | \| |
| `steam-deep-analysis` | 提示型 | 2 | \| |

### 林正刚 `EntrepreneurshipCoach` — 9 个

插件包 `chuangye-manor` ｜ agents: `chuangye-manor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `commitment-tracker` | 提示型 | 1 | 创业伙伴的轻量承诺追踪 Skill。不使用文件持久化，只在当前对话上下文中自然追问用户上次承诺、复述本次承诺、埋下回访锚点。当用户提到"我总是忘了做""执行力差""上次说要做""承诺"等时由 manor-judge 调用。 |
| `knowledge-business` | 提示型 | 2 | 创业社区知识模块·商业财务。包含商业模型约束、财务仪表盘、现金流、预算。对应《创业可以学》第5-6章。知识模块，由判断层在需要商业/财务相关知识时读取参考。当用户问题涉及"商业模式/财务/现金流/预算/模型太重/盈利/成本"时由 manor-judge 读取本 skill。 |
| `knowledge-growth` | 提示型 | 4 | 创业社区知识模块·成长转型。包含手艺磨练、实战环境、转型观、三阶段人生。对应《创业可以学》第11-12章 + 创能量 + 创业的盲点。知识模块，由判断层在需要成长/转型相关知识时读取参考。当用户问题涉及"成长/转型/手艺/学习/阶段/倦怠/职业发展/创能量"时由 manor-judge 读取本 skill。 |
| `knowledge-gtm` | 提示型 | 7 | 创业社区知识模块·客户GTM与敢见客户。包含情绪层判断、客户心路GPS、三合一的人、客户选择、GTM框架、销售阶段、客户资产管理、关键活动。对应《创业可以学》第3-4章及《敢见客户》v9.6。知识模块，由判断层在需要客户/GTM相关知识时读取参考。当用户问题涉及"客户/目标人群/GTM/销售阶段/钩子/客户选择/切入点 |
| `knowledge-org` | 提示型 | 5 | 创业社区知识模块·人执行组织。包含人是结果、系统自运转、环境设计、舞台交付、沟通、猴子管理。对应《创业可以学》第7-10章。知识模块，由判断层在需要组织/执行相关知识时读取参考。当用户问题涉及"团队/招人/执行/管理/沟通/环境/舞台/系统/盯人"时由 manor-judge 读取本 skill。 |
| `knowledge-sequence` | 提示型 | 3 | 创业社区知识模块·顺序判断。包含顺序框架、判断能力、关口识别。对应《创业可以学》第1-2章。知识模块，由判断层在需要顺序相关知识时读取参考。当用户问题涉及"顺序/判断/关口/为什么忙没结果/先后"时由 manor-judge 读取本 skill。 |
| `manor-host` | 提示型 | 3 | 创业伙伴的接待与人设层。负责身份识别、新用户接待、接待流程、灯塔五步前两步（识别+接住）。触发场景：(1)新用户第一次来 (2)用户打招呼/寒暄/自我介绍 (3)不确定对方身份时 (4)用户主动问"你是谁""创业社区是什么地方" (5)用户只聊天不涉及具体创业问题。与 manor-judge 互斥触发：本 skill  |
| `manor-judge` | 提示型 | 2 | 创业伙伴的判断与回答层。负责具体创业问题的识别、回答组织、一语道破、追问收尾。触发场景:(1)用户提出具体创业问题(明确痛点、场景、困惑) (2)用户问体系根概念(OPC/GTM/目标人群/销售阶段等) (3)用户描述经营现状(忙没结果、客户模糊、销售难、模型重、执行靠盯、团队弱、转型难等)。与 manor-host  |
| `references` | 提示型 | 2 | — |

### 建模模 `FinancialModelingExpert` — 9 个

插件包 `financial-analysis` ｜ agents: `financial-modeling-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `3-statements` | 提示型 | 4 | Complete, populate and fill out 3-statement financial model templates (Income Statement, Balance Sheet, Cash Flow Statement) . Use when asked to fill out model  |
| `check-deck` | 代码型 | 4 | \| |
| `check-model` | 提示型 | 1 | Debug and audit financial models for errors — circular references, broken formulas, hardcoded overrides, balance sheet imbalances, cash flow mismatches, and log |
| `competitive-analysis` | 提示型 | 3 | Framework for competitive landscape analysis across any industry. Use when creating competitor analysis, market positioning assessments, investment memos, strat |
| `comps-analysis` | 提示型 | 1 | \| |
| `dcf-model` | 代码型 | 4 | Real DCF (Discounted Cash Flow) model creation for equity valuation. Retrieves financial data from SEC filings and analyst reports, builds comprehensive cash fl |
| `lbo-model` | 提示型 | 1 | This skill should be used when completing LBO (Leveraged Buyout) model templates in Excel for private equity transactions, deal materials, or investment committ |
| `ppt-template-creator` | 提示型 | 1 | Creates self-contained PPT template SKILLS (not presentations) from user-provided PowerPoint templates. Use ONLY when a user wants to create a reusable skill fr |
| `skill-creator` | 代码型 | 7 | Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends CodeBuddy's capa |

### 一人公司专家团 `OpcTeam` — 9 个

插件包 `opc-team` ｜ agents: `opc-asset-strategist`, `opc-conversion-designer`, `opc-dashboard-reviewer`, `opc-model-architect`, `opc-mvp-designer`, `opc-niche-strategist`, `opc-resource-auditor`, `opc-team-lead`, `opc-value-designer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `opc-asset-ops` | 提示型 | 3 | Turn repeatable outputs of a one-person company into compounding assets. Use when Codex needs to explain asset-compounding concepts when needed, verify prerequi |
| `opc-business-model-design` | 提示型 | 4 | Design a viable business model for a one-person company using Lean Canvas and a simplified Business Model Canvas. Use when Codex needs to explain the business-m |
| `opc-conversion-loop` | 提示型 | 3 | Design a conversion loop for a one-person company from reach to lead capture to purchase. Use when Codex needs to explain conversion concepts when needed, verif |
| `opc-dashboard-review` | 提示型 | 4 | Review the operating health of a one-person company using lightweight metrics, bottleneck analysis, and stop-loss logic. Use when Codex needs to explain review  |
| `opc-mvp-designer` | 提示型 | 3 | Define the smallest viable experiment and MVP for a selected one-person company opportunity. Use when Codex needs to explain what MVP means when needed, verify  |
| `opc-niche-positioning` | 提示型 | 4 | Find and position a viable niche market for a one-person company by combining market mapping and customer segmentation. Use when Codex needs to explain niche co |
| `opc-orchestrator` | 提示型 | 4 | Orchestrate the full one-person company workflow across all OPC skills. Use when Codex needs to start, continue, or review the complete 一人企业方法论流程, read prior ou |
| `opc-resource-audit` | 提示型 | 3 | Inventory all founder resources across 8 categories for a one-person company. Use when Codex needs to systematically confirm what resources the founder has — ex |
| `opc-value-proposition` | 提示型 | 3 | Design value propositions for candidate customer segments and help the user choose the strongest one. Use when Codex needs to explain jobs, pains, and gains whe |

### 募资资 `PrivateEquityExpert` — 9 个

插件包 `private-equity` ｜ agents: `private-equity-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `dd-checklist` | 提示型 | 1 | Generate and track comprehensive due diligence checklists tailored to the target company's sector, deal type, and complexity. Covers all major workstreams with  |
| `dd-meeting-prep` | 提示型 | 1 | Prepare for due diligence meetings — management presentations, expert network calls, customer references, and advisor sessions. Generates targeted question list |
| `deal-screening` | 提示型 | 1 | Quickly screen inbound deal flow — CIMs, teasers, and broker materials — against the fund's investment criteria. Extracts key deal metrics, runs a pass/fail fra |
| `deal-sourcing` | 提示型 | 1 | PE deal sourcing workflow — discover target companies, check CRM for existing relationships, and draft personalized founder outreach emails. Use when sourcing n |
| `ic-memo` | 提示型 | 1 | Draft a structured investment committee memo for PE deal approval. Synthesizes due diligence findings, financial analysis, and deal terms into a professional IC |
| `portfolio-monitoring` | 提示型 | 1 | Track and analyze portfolio company performance against plan. Ingests monthly/quarterly financial packages (Excel, PDF), extracts KPIs, flags variances to budge |
| `returns-analysis` | 提示型 | 1 | Build quick IRR/MOIC sensitivity tables for PE deal evaluation. Models returns across entry multiple, leverage, exit multiple, growth, and hold period scenarios |
| `unit-economics` | 提示型 | 1 | Analyze unit economics for PE targets — ARR cohorts, LTV/CAC, net retention, payback periods, revenue quality, and margin waterfall. Essential for software/SaaS |
| `value-creation-plan` | 提示型 | 1 | Structure post-acquisition value creation plans with revenue, cost, and operational levers mapped to an EBITDA bridge. Includes 100-day priorities, KPI targets, |

### 路小鲜 `TripStarAgent` — 9 个

插件包 `tripstar-agent` ｜ agents: `trip-planner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `12306-train-assistant` | 提示型 | 2 | 12306 查询与订票辅助技能，支持余票查询、经停站查询、中转换乘、候补查询与提交/取消、登录状态检查、密码登录与二维码登录、下单与支付链接获取；当用户提到火车票、高铁票、经停站、中转、候补或 12306 查票时触发。 |
| `airbnb` | 提示型 | 1 | Search Airbnb listings with prices, ratings, and direct links. No API key required. Use when user asks to search Airbnb, find vacation rentals, look for short-t |
| `aviation-weather` | 代码型 | 2 | Fetch aviation weather data (METAR, TAF, PIREPs) from aviationweather.gov. Use for flight planning, weather briefings, checking airport conditions, or any pilot |
| `flight-tracker` | 代码型 | 3 | Flight tracking and scheduling. Track live flights in real-time by region, callsign, or airport using OpenSky Network. Search flight schedules between airports. |
| `flights-search` | 提示型 | 1 | Search flights via Google Flights. Find nonstop/connecting flights, filter by time and cabin class, get booking links. Supports city names (NYC, London, Tokyo)  |
| `flyai` | 提示型 | 9 | Search flights, hotels, attractions, concerts, and travel deals with natural language. FlyAI connects to Fliggy MCP for real-time search and booking across hote |
| `globepilot-ai-agent-2` | 提示型 | 1 | AI-powered global travel assistant providing visa info, currency conversion, airport status, events, cultural tips, emergency contacts, and travel recommendatio |
| `meituan-coupon-workbuddy` | 代码型 | 10 | 【美团官方】美团红包助手，支持外卖、餐饮团购、酒店住宿、门票度假、休闲娱乐、闪购、医药等多品类优惠券/红包/神券的一键领取与历史领取记录查询。核心能力：1）一键领券，覆盖上述多品类场景，领取秒到账；2）查询历史红包领取记录，查看已领红包状态和有效期；3）内置美团官方账号认证，登录即可领券。重要说明：如存在多个美团红包助 |
| `travel-planning` | 提示型 | 6 | Plan trips with itineraries, multi-city routing, budget optimization, family logistics, packing lists, and visa timelines. Use when user asks to plan a trip, cr |

### 车赢赢 `AutoConsultant` — 8 个

插件包 `auto-consultant` ｜ agents: `auto-consultant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `audience-campaign` | 提示型 | 1 | Audience segmentation strategy, vehicle messaging, and campaign planning for automotive marketing. Use when users ask for target audience analysis, vehicle sell |
| `buyer-needs-direction` | 提示型 | 1 | Use when users ask for car selection, first-car advice, budget direction, EV/hybrid/fuel choice, family commute scenarios, charging constraints, or a 3-5 model  |
| `marketing-content-creation` | 提示型 | 1 | Generate automotive marketing content by invoking Xinling AI marketing agents via MCP agent_invoke. Covers Xiaohongshu seeding posts, WeChat Moments copy, sales |
| `marketing-diagnosis-review` | 提示型 | 1 | Use when OEM or dealer teams ask to diagnose marketing funnel bottlenecks, review campaign/channel/store results, compare against benchmark ranges, allocate mar |
| `model-comparison-cost` | 提示型 | 1 | Use when users compare models, trims, configurations, version value, ownership cost, insurance, energy, maintenance, depreciation, or family-fit tradeoffs. Lock |
| `oem-dealer-ops` | 提示型 | 1 | Use for OEM/brand-side work: brand building, official communications, new vehicle national launch GTM, dealer network planning, dealer enablement, commercial po |
| `test-drive-transaction` | 提示型 | 1 | Use when users prepare test drives, showroom visits, price negotiation, deposits, financing, insurance, contract review, delivery inspection, or vehicle handove |
| `used-sell-tradein` | 提示型 | 1 | Used-car buying checks (accident, flood, mileage fraud, transfer safety), selling a private car, trade-in decisions, channel choice, and family car-buying decis |

### 丁笃行 `ConsultingPartners` — 8 个

插件包 `consulting-partners` ｜ agents: `consulting-partner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deck-design` | 代码型 | 60 | \| |
| `evidence-analysis` | 提示型 | 3 | \| |
| `hypothesis-framing` | 提示型 | 2 | \| |
| `memo-writing` | 提示型 | 2 | \| |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `quality-audit` | 提示型 | 1 | \| |
| `valuation-modeling` | 代码型 | 4 | \| |
| `westock` | 代码型 | 11 | \| |

### 何同守 `ContractExpert` — 8 个

插件包 `contract-expert` ｜ agents: `contract-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `contract-drafting-engine` | 提示型 | 1 | Draft contracts, build template libraries, and write supplementary agreements (scenarios C3/C4/C9). Use this skill after intake and research to deconstruct the  |
| `contract-intake` | 提示型 | 1 | Collect, through conversational Q&A (and questionnaire-style checklists when many fields are needed), the key transaction facts required before any contract dra |
| `contract-legal-research` | 提示型 | 2 | Retrieve the legal basis and due-diligence facts that contract work depends on — supporting statutes and their effectiveness status, regulatory requirements, ma |
| `contract-lifecycle-advisor` | 提示型 | 1 | Handle contract management-system design, negotiation support, and performance-stage dispute resolution (scenarios C1/C2/C7/C8). Use this skill to design a cont |
| `contract-output-formatter` | 提示型 | 2 | Format contract work products into the delivery shape that best matches the hit scenario (C1-C9) and the reading audience. Use this skill as the LAST step befor |
| `contract-review-engine` | 提示型 | 4 | Review contracts for risk (scenarios C5/C6) — background assessment before signing (counterparty qualification, transaction-mode legality, contract-form fit, sp |
| `contract-scenario-router` | 提示型 | 2 | Identify the user's true contract-work intent and route it to the correct scenario (C1-C9). Use this skill FIRST for every contract request to determine scenari |
| `contract-standards-ingest` | 提示型 | 2 | Ingest and standardize user-provided contract assets — existing template libraries, sample contracts, clause banks, rule/standard libraries, review playbooks, c |

### 探数数 `DataExplorationExpert` — 8 个

插件包 `data` ｜ agents: `data-exploration-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `data-analysis-workflows` | 提示型 | 1 | > |
| `data-context-extractor` | 代码型 | 6 | > |
| `data-exploration` | 提示型 | 1 | Profile and explore datasets to understand their shape, quality, and patterns before analysis. Use when encountering a new dataset, assessing data quality, disc |
| `data-validation` | 提示型 | 1 | QA an analysis before sharing with stakeholders — methodology checks, accuracy verification, and bias detection. Use when reviewing an analysis for errors, chec |
| `data-visualization` | 提示型 | 1 | Create effective data visualizations with Python. 优先使用 plotly（交互式图表），seaborn 和 matplotlib 作为备选（静态图表）。Use when building charts, choosing the right chart type for |
| `interactive-dashboard-builder` | 提示型 | 1 | Build self-contained interactive HTML dashboards with Chart.js, dropdown filters, and professional styling. Use when creating dashboards, building interactive r |
| `sql-queries` | 提示型 | 1 | Write correct, performant SQL across all major data warehouse dialects (Snowflake, BigQuery, Databricks, PostgreSQL, etc.). Use when writing queries, optimizing |
| `statistical-analysis` | 提示型 | 1 | Apply statistical methods including descriptive stats, trend analysis, outlier detection, and hypothesis testing. Use when analyzing distributions, testing for  |

### 季明辨 `EarningsReviewer` — 8 个

插件包 `earnings-reviewer` ｜ agents: `earnings-reviewer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `earnings-analysis` | 提示型 | 4 | Create professional equity research earnings update reports (8-12 pages, 3,000-5,000 words) analyzing quarterly results for companies already under coverage. Fa |
| `earnings-preview` | 提示型 | 1 | Build pre-earnings analysis with estimate models, scenario frameworks, and key metrics to watch. Use before a company reports quarterly earnings to prepare posi |
| `model-update` | 提示型 | 1 | Update financial models with new data — quarterly earnings, management guidance, macro changes, or revised assumptions. Adjusts estimates, recalculates valuatio |
| `morning-note` | 提示型 | 1 | Draft concise morning meeting notes summarizing overnight developments, trade ideas, and key events for coverage stocks. Designed for the 7am morning meeting fo |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `westock` | 代码型 | 11 | \| |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 生辰命理大师 `FortuneMaster` — 8 个

插件包 `fortune-master` ｜ agents: `fortune-master`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cantian-bazi` | 代码型 | 10 | 以命理场景为主的八字排盘、黄历查询与大运/流年/流月/流日/流时区间查询技能。用于用户请求“算八字”“四柱排盘”“阳历/农历转八字”“查黄历/宜忌”“查未来10年流年”“查下个月流日/流时”等场景；关键词包括：八字、四柱、命理、大运、流年、流月、流日、流时、时辰、阳历转八字、农历转八字、黄历、宜忌、干支日期。真太阳时换 |
| `cloud-upload-backup` | 代码型 | 5 | Cloud file upload and backup tool. Upload local files to Tencent SMH cloud storage, viewable in QClaw Mini Program. |
| `docx` | 代码型 | 61 | Use this skill whenever the user wants to create, read, edit, or manipulate Word documents (.docx files). Triggers include: any mention of \"Word doc\", \"word  |
| `email-skill` | 提示型 | 1 | 邮件统一入口（纯路由层），自身不执行任何脚本与接口，识别用户意图后用 read 工具读取下游 skill 的 SKILL.md 路由到下游。【路由决策必读】两步决策：L0 用户是否显式指定邮箱通道？L1 若未指定，是发给自己/结果留存还是发给别人/完整收发？L0 显式：'Agent/AI 邮箱'→读取 agent-em |
| `fortune-master-ultimate` | 代码型 | 42 | \| |
| `mcporter` | 提示型 | 1 | Use the mcporter CLI to list, configure, auth, and call MCP servers/tools directly (HTTP or stdio), including ad-hoc servers, config edits, and CLI/type generat |
| `pdf` | 代码型 | 13 | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combining or merging multiple P |
| `xlsx` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 门头沟营商顾问 `MentougouBusinessGuide` — 8 个

插件包 `mentougou-business-guide` ｜ agents: `mentougou-business-guide`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `address-registration` | 代码型 | 3 | 门头沟注册地址申请。当用户需要门头沟区注册地址、免费地址、挂靠地址时使用。通过开放API提交申请并查询审核状态。 |
| `beijing-policy` | 提示型 | 5 | 北京市级政策知识库。当用户涉及北京市级小微企业、OPC创业、科技创新、人才引进等政策查询时使用。门头沟区是北京市下辖区，市级政策同样适用。 |
| `case-research` | 提示型 | 2 | 中国财税法律案例与法规检索助手。当用户需要检索税务相关判例、行政复议决定、税收法规政策、国家税务总局公告、各地税务实践案例，或需要查找类似税务争议案例时，应使用本 Skill。适用于税务争议应对、税务筹划合规性验证、法律研究等场景。 |
| `china-tax-law` | 提示型 | 4 | 中国财税法律专业知识助手。当用户涉及中国税法咨询、税务筹划分析、税务合规审查、税收政策解读、税务争议处理等任务时，应使用本 Skill。适用场景包括但不限于：增值税、企业所得税、个人所得税、印花税、土地增值税等税种分析，税务筹划方案设计，税务稽查应对，以及涉税法律法规查询。 |
| `entrepreneurship-can-be-learned` | 提示型 | 2 | 创业方法论知识库。基于林正刚《创业可以学》（ver 0.0.3），当用户咨询创业方向、经营顺序、GTM策略、商业模型、团队搭建、财务管理、系统执行等创业相关问题时使用。核心框架：创业成功的首要原则是"守住顺序"——客户→GTM→商业模型→财务→团队→系统→舞台。 |
| `mentougou-policy` | 提示型 | 8 | 门头沟区级政策知识库。当用户涉及门头沟区招商引资、税收优惠、人才政策、场地补贴、注册流程、园区入驻等政策查询时使用。内置门头沟区政策文件，命中即停，不依赖搜索引擎临时检索。 |
| `multi-search-engine` | 提示型 | 8 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |
| `tax-agency` | 提示型 | 2 | 代办税务服务（建设中）。当用户涉及代办税务、代账、报税、记账等需求时触发。当前状态：建设中，暂不提供服务。记录用户需求，待服务上线后跟进。 |

### 莫百炼 `ModelBuilder` — 8 个

插件包 `model-builder` ｜ agents: `model-builder`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `3-statement-model` | 提示型 | 4 | Complete, populate and fill out 3-statement financial model templates (Income Statement, Balance Sheet, Cash Flow Statement) . Use when asked to fill out model  |
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `comps-analysis` | 提示型 | 1 | \| |
| `dcf-model` | 代码型 | 4 | Real DCF (Discounted Cash Flow) model creation for equity valuation. Retrieves financial data from SEC filings and analyst reports, builds comprehensive cash fl |
| `lbo-model` | 提示型 | 1 | This skill should be used when completing LBO (Leveraged Buyout) model templates in Excel for private equity transactions, deal materials, or investment committ |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `westock` | 代码型 | 11 | \| |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 鹅厂职业经纪人 `CareerBroker` — 7 个

插件包 `career-broker` ｜ agents: `career-broker`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-career-agent` | 代码型 | 5 | \| |
| `career-broker-core` | 代码型 | 24 | Internal-only shared references, setup guides, and helper scripts for the Tencent Career Broker expert. Do not invoke directly for user tasks; other skills and  |
| `career-development-consultant` | 代码型 | 25 | \| |
| `career-qa` | 代码型 | 6 | 回答腾讯员工关于「活水 / 职业 / HR / IT / 行政 / 财经 / 新人融入 / 学习成长」相关问询。双路由：活水/招聘类走 recruit-mcp 招聘问询知识库，其他走学堂小Q MCP。 |
| `liveflow-job-recommender` | 代码型 | 6 | \| |
| `profile-perception` | 代码型 | 11 | 为腾讯员工自动构建职业画像，输出三轴结构化结果——技能（能干什么）/ 经历（干过什么）/ 软性素质（是个怎样的人）。主数据源是「自评 MCP」的全部历史自评（近 3 期完整 + 更早期 LLM 汇总）；如果员工尚无自评（入职 < 半年），引导上传简历附件作为经历补充。画像最终沉淀到 ~/.workbuddy/caree |
| `resume-generator` | 提示型 | 1 | 基于用户的自评原文，为用户生成一段「在职经历」的简历描述（动宾结构 + 量化结果 + 能力关键词）。主要在活水岗位推荐完成后引导用户使用：拿自评MCP获取用户自评原文，提炼成可直接放进简历的在职经历段落。当用户说「帮我生成简历 / 写一段在职简历 / 根据自评写简历 / 我的在职经历怎么写 / 把我的经历写成简历」时激 |

### DataBrain舆情分析专家 `DatabrainOpinionExpert` — 7 个

插件包 `databrain-opinion-expert` ｜ agents: `databrain-opinion-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `databrain-competitor-events` | 代码型 | 20 | 游戏竞品活动报告生成工具。当用户需要对某款游戏生成官媒发帖内容和官方活动报告时使用，依次执行数据获取、活动聚合、联网搜索、总结分析四个主要工作模块，最终保存并展示指定格式的竞品报告。触发示例："帮我做一份 XXX 的竞品活动分析"、"生成 XXX 游戏官帖分析报告"、"最近 XXX 有什么官方活动？"。 |
| `databrain-game-content-trend` | 代码型 | 12 | 游戏创意灵感引擎。融合 TikTok/YouTube 热门视频和行业热梗数据，为游戏运营/市场团队提供社媒内容制作灵感和端内资源跟进建议。当用户询问"今日热门"、"游戏内容灵感"、"素材方向"、"官号整活"、"趋势情报"、"热梗"、"热点借势"、"KOL 合作方向"、"端内动作"、"做进游戏"时触发。也应在用户用模糊表 |
| `databrain-opinion-alert` | 代码型 | 25 | 游戏舆情告警 Skill。监控游戏口碑指标并推送企业微信告警。当前主推「商店评分告警 v2」（Steam / Google Play / App Store 三渠道，P0/P1/P2 三级，支持分语种/分国家全切片自动评估、四维触发条件、静默期、归因），保留向后兼容的 KOL 热帖告警与关键词声量告警。当用户需要「设置 |
| `databrain-opinion-hotposts` | 代码型 | 17 | 按订阅游戏生成「过去 N 小时各平台热帖日报」，分平台（Reddit / X / YouTube / Steam / TikTok / Discord / 官方论坛 / Instagram / Facebook）出榜、每榜 Top 1-10 可配，输出 markdown / html 并可一键投递到 AI Galler |
| `databrain-opinion-metrics` | 代码型 | 14 | 查询游戏舆情核心指标。支持声量、情绪分布、Brand Health、互动量、分渠道/分语种分布、Steam 评论评分、社区指标等。当用户询问游戏的"舆情"、"口碑"、"声量"、"情绪"、"评分"、"社媒表现"、"正负面评价"、"玩家讨论"、"Brand Health"时触发。 |
| `databrain-opinion-summary` | 代码型 | 6 | 通过 Databrain 生成指定游戏、时段的舆情 AI 总结报告，快速掌握玩家讨论的核心观点与口碑趋势。在用户需要「舆情总结」「口碑摘要」「玩家讨论总结」「AI 解读评论」「一段时间内的舆情报告」时使用；需先解析游戏名得到 game_id 与平台类型。 |
| `opinions-crawler` | 代码型 | 5 | \| |

### 记账账 `FinanceAccountingExpert` — 7 个

插件包 `finance` ｜ agents: `finance-accounting-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `audit-support` | 提示型 | 1 | Support SOX 404 compliance with control testing methodology, sample selection, and documentation standards. Use when generating testing workpapers, selecting au |
| `close-management` | 提示型 | 1 | Manage the month-end close process with task sequencing, dependencies, and status tracking. Use when planning the close calendar, tracking close progress, ident |
| `finance-workflows` | 提示型 | 1 | Comprehensive finance workflows including income statements, journal entries, reconciliations, SOX testing, and variance analysis |
| `financial-statements` | 提示型 | 1 | Generate income statements, balance sheets, and cash flow statements with GAAP presentation and period-over-period comparison. Use when preparing financial stat |
| `journal-entry-prep` | 提示型 | 1 | Prepare journal entries with proper debits, credits, and supporting documentation for month-end close. Use when booking accruals, prepaid amortization, fixed as |
| `reconciliation` | 提示型 | 1 | Reconcile accounts by comparing GL balances to subledgers, bank statements, or third-party data. Use when performing bank reconciliations, GL-to-subledger recs, |
| `variance-analysis` | 提示型 | 1 | Decompose financial variances into drivers with narrative explanations and waterfall analysis. Use when analyzing budget vs. actual, period-over-period changes, |

### 运势分析师 `FortuneConsultant` — 7 个

插件包 `fortune-consultant` ｜ agents: `fortune-consultant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-mbti` | 提示型 | 6 | AI Agent personality diagnosis and configuration system based on MBTI framework. Use when users want to (1) test/diagnose an Agent's personality type, (2) under |
| `cantian-bazi` | 代码型 | 9 | 以命理场景为主的八字排盘、黄历查询与大运/流年/流月/流日/流时区间查询技能。用于用户请求“算八字”“四柱排盘”“阳历/农历转八字”“查黄历/宜忌”“查未来10年流年”“查下个月流日/流时”等场景；关键词包括：八字、四柱、命理、大运、流年、流月、流日、流时、时辰、阳历转八字、农历转八字、黄历、宜忌、干支日期。真太阳时换 |
| `fortune-master` | 代码型 | 38 | \| |
| `lunar-calendar` | 代码型 | 10 | \| |
| `meihua-yijing` | 提示型 | 2 | 梅花易数占卜，基于时间、数字、方位起卦，解读吉凶祸福 |
| `tarot-reading` | 提示型 | 5 | \| |
| `ziwei-doushu` | 代码型 | 5 | Professional Ziwei Doushu consultation skill with offline, Beijing-standard calculation rules. Use when the user wants a polished Ziwei report from birth date a |

### 严研行 `FsiMarketResearcher` — 7 个

插件包 `market-researcher` ｜ agents: `market-researcher`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `competitive-analysis` | 提示型 | 3 | Framework for building competitive landscape decks — market positioning, competitor deep-dives, comparative analysis, strategic synthesis. Use when the user ask |
| `comps-analysis` | 提示型 | 1 | \| |
| `idea-generation` | 提示型 | 1 | Systematic stock screening and investment idea sourcing. Combines quantitative screens, thematic research, and pattern recognition to surface new long and short |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `pptx-author` | 代码型 | 59 | Use this skill any time a .pptx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or presentations; rea |
| `sector-overview` | 提示型 | 1 | Create comprehensive industry and sector landscape reports covering market dynamics, competitive positioning, key players, and thematic trends. Use for client r |
| `westock` | 代码型 | 11 | \| |

### 权知明 `IpExpert` — 7 个

插件包 `ip-expert` ｜ agents: `ip-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ip-analysis-engine` | 提示型 | 2 | The core研判 engine for intellectual-property work — after intake confirms the user's standpoint (right-holder vs accused/freedom-to-operate) and ip-legal-researc |
| `ip-drafting-engine` | 提示型 | 1 | The drafting & strategy engine for intellectual-property work — after intake/research/analysis, this skill produces the concrete IP deliverables: application-or |
| `ip-intake` | 提示型 | 1 | Collect the concrete facts an IP task depends on before any substantive work — right type (copyright / patent / trademark / trade secret / domain), rights crede |
| `ip-legal-research` | 提示型 | 2 | Retrieve the legal basis and professional-database facts that intellectual-property work depends on — supporting statutes/司法解释 and their effectiveness status, s |
| `ip-output-formatter` | 提示型 | 8 | Format IP analysis/drafting results into the deliverable shape the routed scenario requires, following the house style distilled from real IP work-product templ |
| `ip-scenario-router` | 提示型 | 2 | Identify the user's true intellectual-property intent and route it to the correct scenario (IP-A~IP-F across copyright, patent, trademark, trade secret, domain  |
| `ip-verification-workbench` | 代码型 | 19 | 知识产权检索核验工作台。任务单出现【核验工作台：必用】、【输出档位：重量】或输出形态属于专利/商标/著作权检索报告、布局全景分析、侵权风险/侵权认定分析（FTO）、无效宣告/驳回复审策略、商业秘密认定、尽职调查、诉讼管辖方案、企业IP战略等成体系交付物时必须使用。本 skill 执行脚本化动作：保存 answer/so |

### 求职陪跑团 `JobCompanionTeam` — 7 个

插件包 `job-companion-team` ｜ agents: `job-companion-interview`, `job-companion-negotiation`, `job-companion-reflection`, `job-companion-resume`, `job-companion-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `interview-prep` | 提示型 | 1 | Stage 4 of the Job Companion Team flow. Builds a STAR story bank and behavioral interview question set tailored to a target role, equipping the user with struct |
| `mock-interview` | 提示型 | 1 | Stage 5 of the Job Companion Team flow. Runs role-play mock interviews (behavioral / technical / case) with per-question scoring and three concrete improvement  |
| `onboarding-reflection` | 提示型 | 1 | Stage 7 of the Job Companion Team flow. Converts a chosen offer into a 90-day onboarding plan, runs monthly probation reflections, and projects 3-5 year career  |
| `resume-polish` | 提示型 | 1 | Stage 3 of the Job Companion Team flow. Turns a candidate direction plus raw experience into ATS-friendly resume versions, one-line self-introductions, and 90-s |
| `salary-negotiation` | 提示型 | 1 | Stage 6 of the Job Companion Team flow. Calibrates salary against public benchmarks, drafts negotiation scripts for counter-offers, and runs weighted multi-offe |
| `self-inventory` | 提示型 | 1 | Stage 1 of the Job Companion Team flow. A four-card self-inventory system that helps job seekers turn fuzzy self-knowledge into a clear self-portrait card cover |
| `target-positioning` | 提示型 | 1 | Stage 2 of the Job Companion Team flow. Turns a completed self-portrait into 1-3 candidate directions, each with industry image, typical role profiles, market t |

### 产品通 `ProductManagementExpert` — 7 个

插件包 `product-management` ｜ agents: `product-management-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `competitive-analysis` | 提示型 | 1 | Analyze competitors with feature comparison matrices, positioning analysis, and strategic implications. Use when researching a competitor, comparing product cap |
| `feature-spec` | 提示型 | 1 | Write structured product requirements documents (PRDs) with problem statements, user stories, requirements, and success metrics. Use when speccing a new feature |
| `metrics-tracking` | 提示型 | 1 | Define, track, and analyze product metrics with frameworks for goal setting and dashboard design. Use when setting up OKRs, building metrics dashboards, running |
| `product-management-workflows` | 提示型 | 1 | Complete product management workflows including feature specs, roadmap management, stakeholder updates, user research synthesis, competitive analysis, and metri |
| `roadmap-management` | 提示型 | 1 | Plan and prioritize product roadmaps using frameworks like RICE, MoSCoW, and ICE. Use when creating a roadmap, reprioritizing features, mapping dependencies, ch |
| `stakeholder-comms` | 提示型 | 1 | Draft stakeholder updates tailored to audience — executives, engineering, customers, or cross-functional partners. Use when writing weekly status updates, month |
| `user-research-synthesis` | 提示型 | 1 | Synthesize qualitative and quantitative user research into structured insights and opportunity areas. Use when analyzing interview notes, survey responses, supp |

### 热点猎手 `TrendHunter` — 7 个

插件包 `trend-hunter` ｜ agents: `trend-hunter`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-research-radar` | 代码型 | 4 | 定时任务：每日研究简报。漏掉重要论文和行业报告？每天帮你盯着，关键信息一条不漏 This skill should be used when the user asks about 定时任务：每日研究简报. Keywords: 每日简报, 研究简报. |
| `competitor-monitoring` | 提示型 | 5 | Track competitors with pricing alerts, feature changes, positioning analysis, and strategic dossiers. |
| `content-calendar` | 提示型 | 3 | Plan, schedule, and track content across channels — newsletters, social media, blog posts, and videos. Manages pipeline stages, publishing cadence, and repurpos |
| `online-search` | 代码型 | 2 | \| |
| `social-copywriter` | 提示型 | 4 | Social media copywriter. 社交媒体文案、朋友圈文案、朋友圈怎么发、微博文案、微博段子、Twitter文案、tweet、Instagram文案、IG caption、社交媒体文案生成、节日祝福、生日祝福文案、美食文案、旅行文案、心灵鸡汤、日常文案、晒照文案、show off、心情文案、搞笑文案、高 |
| `social-media-poster` | 提示型 | 2 | 社媒内容自动发布 - 支持多平台内容一键发布、定时推送、效果追踪。适用于自媒体、运营，品牌方。 |
| `video-editing` | 提示型 | 2 | 该技能介绍如何通过视频剪辑实现变现；当你计划从事或优化视频剪辑时调用。 |

### 小法同学 `XiaofaLitigationAssistant` — 7 个

插件包 `xiaofa-litigation-assistant` ｜ agents: `xiaofa-litigation-assistant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `docx-writer` | 提示型 | 1 | \| |
| `element-lawsuit-generato` | 代码型 | 17 | 要素式文书一键生成——个人提效利器：以前律师对着模板逐项手动填写要素式文书，一份半小时起步；现在上传传统起诉状，自动识别案由、匹配模板、提取要素、填充输出，9类文书58个案由一键搞定。单人执业无需助理团队，文书格式转换从手工活变成秒级自动化。支持11大领域104份模板，区域定位精确填充，勾选框智能处理。 |
| `enforcement` | 提示型 | 2 | \| |
| `legal-calculator` | 提示型 | 1 | \| |
| `legal-epistemology` | 提示型 | 1 | \| |
| `legal-hallucination-check` | 提示型 | 1 | \| |
| `litigation-timeline` | 提示型 | 5 | \| |

### 全域内容分发专家团 `ContentDistributionTeam` — 6 个

插件包 `content-distribution-team` ｜ agents: `content-distribution-team-lead`, `distribution-analyst`, `domestic-platform-expert`, `international-platform-expert`, `scheduling-specialist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |
| `libtv-skill` | 代码型 | 7 | agent-im 会话技能 - 通过 liblib.tv 的 AI 能力生成和编辑图片/视频。覆盖场景包括：生成（文生图、文生视频、图生视频、做动画、画一个xxx、来段xxx）、编辑修改（把xxx换成yyy、去掉xxx、加上xxx、改成xxx、调整xxx、局部修改、改镜头）、风格转换（风格迁移、转绘、换风格）、视频续写 |
| `mp-draft-push` | 提示型 | 2 | 将现成的文章内容发布到微信公众号草稿箱。当用户说"发布文章"、"发布到草稿箱"、"publish to draft"、"推送到公众号"时触发。 |
| `multi-platform-distribution` | 提示型 | 5 | \| |
| `wechat-article-search` | 代码型 | 3 | 搜索微信公众号文章技能。通过微信搜索获取文章列表，覆盖科技/AI、社会热点、财经、教育、职场等各类中文资讯；可按关键词检索并返回标题、概要、发布时间、来源公众号与链接。当用户需要查找微信公众号文章、整理参考资料或快速获取文章信息时使用此技能。 |
| `xiaohongshu` | 提示型 | 1 | \| |

### 小Q `QingflowHrExpert` — 6 个

插件包 `qingflow-hr-expert` ｜ agents: `qingflow-hr-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-recruiting-engine` | 提示型 | 1 | \| |
| `hr-analytics-dashboard` | 提示型 | 1 | \| |
| `hr-performance-assistant` | 提示型 | 1 | \| |
| `ida-instructional-design-agent` | 提示型 | 1 | \| |
| `onboarding-flow-builder` | 提示型 | 1 | \| |
| `qingflow-build` | 提示型 | 3 | \| |

### 动画画 `RemotionVideoExpert` — 6 个

插件包 `remotion-video-generator` ｜ agents: `remotion-video-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `bgm-library` | 代码型 | 6 | Search, filter, and download royalty-free background music from ccMixter for Remotion videos. Supports keyword search, tag presets, license filtering (CC BY / C |
| `environment-setup` | 提示型 | 1 | Automatically detects and configures the Remotion video generation environment. Use when user requests video creation and dependencies (Node.js, FFmpeg, Remotio |
| `lucide-icons` | 代码型 | 5 | Search, download, and customize Lucide icons (1000+ beautiful SVG icons). Supports SVG and TypeScript React component generation with full customization options |
| `remotion-best-practices` | 提示型 | 34 | Best practices for Remotion - Video creation in React |
| `scene-planner` | 提示型 | 1 | Creates detailed video storyboards and scene breakdowns for Remotion video generation. Analyzes user requirements, determines video type, selects appropriate te |
| `video-generator` | 提示型 | 1 | Orchestrates complete Remotion video generation workflow from user request to MP4 output. Automatically activates when user mentions creating videos, animations |

### 单必成 `SalesCoach` — 6 个

插件包 `sales-coach` ｜ agents: `sales-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `business-case` | 提示型 | 1 | \| |
| `call-debrief` | 提示型 | 1 | \| |
| `competitive-brief` | 提示型 | 1 | \| |
| `deal-strategy` | 提示型 | 1 | \| |
| `prepare-meeting` | 提示型 | 1 | \| |

### 顾估衡 `ValuationReviewer` — 6 个

插件包 `valuation-reviewer` ｜ agents: `valuation-reviewer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ic-memo` | 提示型 | 1 | Draft a structured investment committee memo for PE deal approval. Synthesizes due diligence findings, financial analysis, and deal terms into a professional IC |
| `neodata-financial-search` | 代码型 | 4 | >- |
| `portfolio-monitoring` | 提示型 | 1 | Track and analyze portfolio company performance against plan. Ingests monthly/quarterly financial packages (Excel, PDF), extracts KPIs, flags variances to budge |
| `returns-analysis` | 提示型 | 1 | Build quick IRR/MOIC sensitivity tables for PE deal evaluation. Models returns across entry multiple, leverage, exit multiple, growth, and hold period scenarios |
| `westock` | 代码型 | 11 | \| |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 理财财 `WealthManagementExpert` — 6 个

插件包 `wealth-management` ｜ agents: `wealth-management-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `client-report` | 提示型 | 1 | Generate professional client-facing performance reports with portfolio returns, allocation breakdowns, and market commentary. Suitable for quarterly or annual d |
| `client-review` | 提示型 | 1 | Prepare for client review meetings with portfolio performance summary, allocation analysis, talking points, and action items. Pulls together account data into a |
| `financial-plan` | 提示型 | 1 | Build or update a comprehensive financial plan covering retirement projections, education funding, estate planning, and cash flow analysis. Use for new client o |
| `investment-proposal` | 提示型 | 1 | Create professional investment proposals for prospective clients. Covers the firm's approach, proposed allocation, expected outcomes, and fee structure. Use whe |
| `portfolio-rebalance` | 提示型 | 1 | Analyze portfolio allocation drift and generate rebalancing trade recommendations across accounts. Considers tax implications, transaction costs, and wash sale  |
| `tax-loss-harvesting` | 提示型 | 1 | Identify tax-loss harvesting opportunities across taxable accounts. Finds positions with unrealized losses, suggests replacement securities, and tracks wash sal |

### 天御金融反诈 `AntiScamAgent` — 5 个

插件包 `anti-scam-agent` ｜ agents: `anti-scam-agent`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `dark-grey-intel` | 提示型 | 3 | 黑灰产情报MCP，面向卡商、料商、四件套、非法数据交易、黑卡资源、社媒引流和黑灰产生态链分析。。通过 amcpcli 二进制对接 |
| `debt-runner` | 提示型 | 3 | 背债人/职业背债专题MCP，面向背债资源、房企信、企业信、包装贷款、法人背债、车贷背债、征信包装等专题情报。。通过 amcpcli |
| `fraud-laundering` | 提示型 | 3 | 涉诈洗钱MCP，面向涉诈银行卡、黑卡交易、代办卡、跑分水房、卡U、洗钱交易、非法数据交易和资金风险链路分析。通过 amcpcli |
| `knowledge` | 提示型 | 3 | 知识库MCP，面向电诈术语、黑话、TTPs、链路角色、业务方案和风控方案查询。。通过 amcpcli 二进制对接 MCP |
| `victim` | 提示型 | 3 | 受害者MCP，面向潜在受害者统计、号码反查、实时新增预警、预警明细摘录和脱敏画像。通过 amcpcli 二进制对接 MCP |

### 文博凯 `ContentCreator` — 5 个

插件包 `content-creator` ｜ agents: `content-creator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |
| `minimax-docx` | 代码型 | 75 | > |
| `novel-writer` | 代码型 | 3 | 章节正文生成器 - 根据章节大纲、Voice Profile 和角色档案构建 LLM 提示词，用于生成章节正文。当需要根据大纲创作具体章节时使用。 |
| `novel-writing` | 代码型 | 3 | AI长篇网文创作技能包。用于解决长篇网络小说创作中的核心痛点：上下文丢失、文风不一致、设定冲突、节奏失控、多线混乱、质量不稳、读者反馈无法内化。触发场景包括：开始新书、规划大纲、撰写章节、管理伏笔、检测冲突、读者反馈分析、批量创作质量控制。 |

### 舒明析 `DataAnalyticsReporter` — 5 个

插件包 `data-analytics-reporter` ｜ agents: `data-analytics-reporter`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `analytics-reporting` | 提示型 | 1 | Build polished analytical reports, dashboards, and product/business analyses. Use when the user needs a durable report (executive or technical), an analytical d |
| `data-quality-assessment` | 提示型 | 1 | Assess whether datasets are trustworthy for analysis, modeling, dashboards, or pipelines; and validate finished analyses before sharing. Use for data quality ch |
| `data-visualization` | 提示型 | 1 | Design, specify, implement, revise, and QA quantitative visuals and chart choices. Use when an analytical answer needs visual judgment—comparing values, showing |
| `kpi-design` | 提示型 | 1 | Design KPI frameworks, set targets, develop measurement plans, and estimate market/opportunity sizes (TAM/SAM/SOM). Use when success metrics, drivers, guardrail |
| `metric-diagnostics` | 提示型 | 1 | Diagnose why a metric changed or differs from expectation, and produce leadership-ready KPI updates. Use when the user needs to understand what drove a metric m |

### 像素匠 `FrontendDeveloper` — 5 个

插件包 `frontend-developer` ｜ agents: `frontend-developer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `frontend-dev` | 代码型 | 98 | \| |
| `fullstack-dev` | 提示型 | 9 | \| |
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |
| `impeccable` | 提示型 | 31 | \| |

### PPT大纲、生成、视频、演示与交付专家团 `HumanizePptTeam` — 5 个

插件包 `humanize-ppt-team` ｜ agents: `frontend-slides-renderer`, `guizang-renderer`, `html-ppt-presenter`, `humanize-ppt-team-lead`, `outline-director`, `qa`, `video-motion-agent`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `frontend-slides` | 代码型 | 10 | Create stunning, animation-rich HTML presentations from scratch or by converting PowerPoint files. Use when the user wants to build a presentation, convert a PP |
| `guizang-ppt-skill` | 提示型 | 13 | 生成"电子杂志 × 电子墨水"风格的横向翻页网页 PPT（单 HTML 文件），含 WebGL 流体背景、衬线标题 + 非衬线正文、章节幕封、数据大字报、图片网格等模板。当用户需要制作分享 / 演讲 / 发布会风格的网页 PPT，或提到"杂志风 PPT"、"horizontal swipe deck"、"editori |
| `html-ppt` | 代码型 | 224 | HTML PPT Studio — author professional static HTML presentations in many styles, layouts, and animations, all driven by templates. Use when the user asks for a p |
| `humanize-ppt` | 代码型 | 42 | AST-based outline director for human-centered AI presentation workflows. Use before generating PPT/HTML slides from raw material. |
| `remotion-video-toolkit` | 提示型 | 34 | Complete toolkit for programmatic video creation with Remotion + React. Covers animations, timing, rendering (CLI/Node.js/Lambda/Cloud Run), captions, 3D, chart |

### 福帮手 `IndustrialParkInvestmentAttractionExpert` — 5 个

插件包 `industrial-park-investment-attraction-expert` ｜ agents: `industrial-park-investment-attraction-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `artifact-renderer` | 提示型 | 1 | 将已经通过质量门的园区、证据、任务验收或候选组合结果渲染为用户需要的聊天、Markdown、JSON、CSV或其他受支持工件。仅在确有结构化交付、导出、跨会话续作或外部动作草稿需要时使用；只改格式，不得修改事实、判断、排序、状态或语义。 |
| `entity-evidence-audit` | 提示型 | 1 | 审计公开材料中的主体和关键主张，把事实绑定到可回看的来源、日期与原文位置，并记录冲突、不利信息和未知。既可用于企业身份与候选证据，也可用于政策、园区材料、方法论和一般公开事实；没有企业对象时不得虚构实体或候选资产。唯一写来源、主张及证据台账，不决定业务优先级。 |
| `fit-portfolio` | 提示型 | 1 | 在实体与证据审计完成后，按本次任务目标、硬约束和适用判断项生成当前批次、累计企业组合、替补、排除与目标进度。仅在用户明确或确认优先标准时生成业务优先批次。用于首次编排、约束或关键来源变化后重算、继续下一批或复核现有清单；唯一写 TargetPortfolio，不改实体或证据。 |
| `park-brief-builder` | 提示型 | 1 | 将自然语言、园区官网或用户粘贴的公开材料规范为当前会话的 ParkBrief 和 TaskGoal。用于首次找企业、切换园区、园区硬约束变化或候选组合需要回溯约束时；是 ParkBrief 与 TaskGoal 的唯一写者，不搜索企业或排序。 |
| `public-target-research` | 提示型 | 1 | 根据 ParkBrief 使用公开搜索、公开网页或用户粘贴的公开材料发现候选企业并记录 QueryLedger。用于首次宽召回、补齐候选、指定链节/区域搜索或证据不足时扩展来源；只写发现账本，不做最终主体结论或排名。 |

### 金山文档知识收藏助手 `KdocsKnowledgeCollector` — 5 个

插件包 `kdocs-knowledge-collector` ｜ agents: `kdocs-knowledge-collector`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `doc-writer` | 提示型 | 11 | 搜索多份云文档，提取信息并自动生成总结报告或新文档内容。可浏览目录定位目标文档。 当用户要求「汇总报告」、「多文档总结」、「定期播报」、「内容整合」时使用。 若只需读取单篇文档，请使用 doc-to-markdown 技能。 |
| `fragment-organize` | 提示型 | 11 | 从多份云文档中提取碎片内容，整合生成结构化的汇总文档。可浏览目录定位源文件和目标文件。 当用户要求「整理碎片笔记」、「合并文档」、「整合分散内容」、「汇总资料」时使用。 若需要在知识库中整理，请使用 knowledge-format 技能。 |
| `knowledge-format` | 提示型 | 21 | 对知识库中的零散内容进行智能化整理和结构化重组。支持读取文档内容、调整格式与排版、规范化标题层级，可浏览目录批量处理多个文档。 当用户要求「整理知识库」、「重组笔记」、「知识库内容整理」、「结构化知识」、「格式化文档」时使用。 若需要将内容存入知识库，请使用 knowledge-save 技能。 |
| `knowledge-save` | 提示型 | 13 | 将各类内容（网页、文件、云文档）一键保存到个人知识库。支持按时间筛选批量归档和自动分类，可浏览目录选择保存位置。 当用户要求「存入知识库」、「保存到知识库」、「归档到知识库」、「放到知识库」时使用。 若需要整理知识库已有内容，请使用 knowledge-format 技能。 |
| `web-clipper` | 提示型 | 3 | 将网页内容剪藏并自动保存为金山文档智能文档（.otl）。 当用户提供 URL 并要求「保存网页」、「收藏网页」、「剪藏」、「网页存到文档」时使用。 若需要存入知识库，请使用 knowledge-save 技能。 |

### 法检 Pro `LegalSearchPro` — 5 个

插件包 `legal-search-pro` ｜ agents: `legal-search-pro`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `case-retrieval` | 提示型 | 1 | 当用户需要查找与当前法律问题相关的类似案例、相关判决、裁判规则时触发。典型场景：查找类似案例或判例、通过裁判支撑法律论点、案件预判、分析司法实践趋势、对比不同法院/时期的裁判立场。关键词包括：类似案例、相关判决、判例检索、裁判规则、同类案件、指导性案例、典型案例、司法观点、裁判要旨等。 |
| `legal-output-formatter` | 提示型 | 2 | Format legal-retrieval results into the output shape required by the routed scenario. Use after retrieval to draft the final answer text and citation style. If  |
| `legal-scenario-router` | 提示型 | 2 | Identify the user's true legal-search intent and route it to the correct retrieval scenario. Use this skill FIRST for every legal-search request to determine sc |
| `legal-search-engine` | 提示型 | 3 | Execute the multi-layer legal retrieval pipeline once a scenario is identified - extract legal facts, locate the legal issue, judge source effectiveness hierarc |
| `legal-verification-workbench` | 代码型 | 19 | 法律检索核验工作台。任务单出现【核验工作台：必用】、【输出档位：重量】或输出形态属于全面合规检索、文书引用素材、诉讼仲裁支撑、非诉文书检索、企业合规体检、案例专题分析、刑事量刑参考、行政复议证据时必须使用。本 skill 执行脚本化动作：保存 answer/sources/claims，运行 legal-verify  |

### 关月结 `MonthEndCloser` — 5 个

插件包 `month-end-closer` ｜ agents: `month-end-closer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `accrual-schedule` | 提示型 | 1 | Build the period-end accrual schedule — for each accrual, compute the entry, cite the support, and draft the JE. Use during month-end close; the JE is a draft f |
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `roll-forward` | 提示型 | 1 | Build a roll-forward schedule for a balance-sheet account — beginning balance plus activity less reversals equals ending balance, with each component tied to GL |
| `variance-commentary` | 提示型 | 1 | Write flux commentary for every P&L and balance-sheet line over threshold — current vs prior period and vs budget, with the driver explained from underlying act |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 技术公益专家团 `SkillhubCharityExpertTeam` — 5 个

插件包 `skillhub-charity-expert-team` ｜ agents: `skillhub-icon-designer`, `skillhub-manager`, `skillhub-operation-expert`, `skillhub-ops-expert`, `skillhub-security-tester`, `skillhub-social-value-evaluator`, `skillhub-solution-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `expert-creator` | 提示型 | 3 | \| |
| `expert-reviewer` | 代码型 | 7 | 审查外部提交的 Expert Marketplace 专家包（agent/team/plugin）合规性与质量，输出对外可交付的 Markdown 审查报告。触发场景：审查专家、检查专家包、专家合规审查、专家质量评估、review expert、check expert package。重点覆盖 plugin.json |
| `skill-creator` | 提示型 | 5 | 专家团内部技能编写工具。按 WorkBuddy Skill 规范自动推导生成完整的 Skill 技能包（SKILL.md + README.md + GUIDE.md + CASES.md + Prompt.md + references/）。由专家团解决方案专家（帅帅/SY）调用，基于任务卡用户需求和已确认设计方向自 |
| `skill-tester` | 提示型 | 3 | 分析目标 Skill 并设计全方位自测流程，验证其完整性、易用性、安全性（含 allowed-tools 一致性、7 项通用质量原则）、兼容性、性能（含深度思考与 Token 消耗）、效果增益（含无技能对照组 A/B 实验）的多维度测评，全面对齐 TRACE（Trust/Reliability/Adaptability |
| `wenjuan-fallback-submit` | 代码型 | 3 | \| |

### 钱守通 `SmbFinance` — 5 个

插件包 `smb-finance` ｜ agents: `smb-finance`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cash-flow` | 提示型 | 1 | Cash flow forecasting and payroll planning. Generate 4-13 week cash projections, assess payroll feasibility, chase overdue invoices to close gaps, and provide n |
| `invoice-chase` | 提示型 | 1 | Overdue invoice chasing with AR aging report, escalation templates, and priority scoring. Triggers on: overdue, chase invoice, accounts receivable, late payment |
| `margin-analysis` | 提示型 | 1 | Product/service margin analysis with pricing recommendations. Calculate gross margin per line, diagnose problem items, model price increase scenarios. Triggers  |
| `month-end-close` | 提示型 | 1 | Complete month-end close workflow: pre-close checks, bank reconciliation, accruals, trial balance, financial statements, P&L narrative with margin summary. Trig |
| `tax-preparation` | 提示型 | 1 | 中国小企业税务申报准备工作流：发票合规、增值税与企业所得税申报、社保公积金、可抵扣项梳理、汇算清缴交接。触发词：报税、税务申报、汇算清缴、增值税、企税、个税、社保、发票、税务交接。 |

### 小程达 `WeChatMiniProgramDeveloper` — 5 个

插件包 `we-chat-mini-program-developer` ｜ agents: `we-chat-mini-program-developer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `fullstack-dev` | 提示型 | 9 | \| |
| `impeccable` | 提示型 | 31 | \| |
| `skyline` | 提示型 | 59 | WeChat Mini Program Skyline rendering engine. Use when developing with Skyline renderer, including components (scroll-view, swiper, draggable-sheet), WXSS style |
| `tdesign-miniprogram` | 提示型 | 76 | TDesign WeChat Mini Program UI component library by Tencent. Use when building WeChat mini apps with TDesign components (Button, Dialog, Input, Tabs, Chat, etc. |
| `wechat-miniprogram` | 提示型 | 10 | WeChat Mini Program (微信小程序) development framework. Use when building WeChat mini apps with WXML templates, WXSS styles, WXS scripting, component development, We |

### 深网网 `AiEngineer` — 4 个

插件包 `ai-engineer` ｜ agents: `ai-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-browser-core` | 提示型 | 6 | OpenClaw skill for the agent-browser CLI (Rust-based with Node.js fallback) enabling AI-friendly web automation with snapshots, refs, and structured commands. |
| `agent-team-orchestration` | 提示型 | 6 | Orchestrate multi-agent teams with defined roles, task lifecycles, handoff protocols, and review workflows. Use when: (1) Setting up a team of 2+ agents with di |
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |
| `fullstack-dev` | 提示型 | 9 | \| |

### 盾卫卫 `BrandGuardian` — 4 个

插件包 `brand-guardian` ｜ agents: `brand-guardian`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `brand-consistency-check` | 提示型 | 2 | Audits creative assets and channels for brand consistency across visual identity (logo, color, typography, imagery), voice, and messaging. Use to review deliver |
| `brand-guidelines` | 提示型 | 6 | Applies Anthropic's official brand colors and typography to any sort of artifact that may benefit from having Anthropic's look-and-feel. Use it when brand color |
| `brand-voice-messaging` | 提示型 | 3 | Defines and applies a brand's verbal identity — voice, tone, and messaging architecture. Use when establishing brand personality, adapting tone across contexts, |
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |

### 天御对公信贷 `CorpCreditDueDiligence` — 4 个

插件包 `corp-credit-due-diligence` ｜ agents: `corp-credit-due-diligence`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `auth-permission` | 提示型 | 3 | 业务Skill执行前的权限检查服务，这是系统安全基础步骤。如果业务Skill中添加了前置条件指向这里，必须在执行其他业务 Skill 前先调用本Skill，做认证和鉴权操作。同时，auth-permission也支持重置登录态操作（清除当前Agent身份）。 |
| `credit-industry-research` | 提示型 | 6 | > |
| `due-diligence` | 提示型 | 3 | 对公尽调 Agent 服务。提供尽调会话查询上报能力，用于审计追踪、意图分析、成本核算和性能监控。。通过 amcpcli 二进制对接 MCP 服务，自动完成 Agent 鉴权、会话管理、工具调用全流程，同时支持重置本地登录态、清除当前 Agent 身份缓存。 |
| `md2pdf` | 代码型 | 2 | 将 Markdown 文档转换为带专业排版和中文支持的 PDF。流程为 Markdown → 带样式 HTML → PDF（用无头 Chromium 打印）。适用于把报告、文档等 .md 文件导出为可交付的 PDF，环境无需 pandoc/wkhtmltopdf/latex。 |

### 理文文 `DocumentProcessingExpert` — 4 个

插件包 `document-skills` ｜ agents: `document-processing-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `docx` | 代码型 | 61 | Use this skill whenever the user wants to create, read, edit, or manipulate Word documents (.docx files). Triggers include: any mention of \"Word doc\", \"word  |
| `pdf` | 代码型 | 12 | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combining or merging multiple P |
| `pptx` | 代码型 | 59 | Use this skill any time a .pptx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or presentations; rea |
| `xlsx` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 马滢老师 `FamilyEducationMa` — 4 个

插件包 `family-education-ma` ｜ agents: `family-education-ma`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `family-education-expert` | 提示型 | 56 | \| |
| `outreach-communication` | 提示型 | 7 | \| |
| `res-family-intervention` | 提示型 | 2 | \| |
| `risk-assessment-referral` | 提示型 | 4 | \| |

### 专业高考顾问 `GaokaoAdvisor` — 4 个

插件包 `gaokao-advisor` ｜ agents: `gaokao-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `gaokao-search` | 代码型 | 5 | > |
| `gaokao-zhiyuan-assistant` | 提示型 | 9 | 高考志愿填报的逐步引导助手，帮用户梳理出最适合自己的志愿填报名单。通过对话分阶段进行：收集个人信息与选科，解读感兴趣的专业，探讨城市与院校，产出带“冲稳保”的候选志愿草表，最终生成可直接对照官方系统填报的志愿表与报告；全程产物沉淀为腾讯文档。只要用户提到高考、报志愿、填志愿、选专业、选大学、冲稳保、平行志愿、选科能报什 |
| `tencent-yuanbao-gaokao-regional-passing-scores` | 提示型 | 18 | 高考地区分数线信息检索助手。当用户询问各省份历年高考录取分数线、录取批次或对应排名时使用，支持按地区、年份、选科和批次查询，自动适配新老高考政策差异。 |
| `tencent-yuanbao-gaokao-score-to-rank-lookup` | 提示型 | 5 | 高考一分一段信息检索助手，帮助考生根据分数查询全省排名位次，或根据位次估算对应分数区间，或提供一分一段表。 |

### 钱对齐 `GlReconciler` — 4 个

插件包 `gl-reconciler` ｜ agents: `gl-reconciler`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `break-trace` | 提示型 | 1 | Root-cause a reconciliation break to its source transaction or posting — follow the audit trail from the break row back to the originating entry on each side an |
| `gl-recon` | 提示型 | 1 | Reconcile general ledger to subledger for a trade date or period — match at the position or transaction level, surface breaks, and classify each break by likely |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 金山文档文档管家助手 `KdocsDocButler` — 4 个

插件包 `kdocs-doc-butler` ｜ agents: `kdocs-doc-butler`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `create-doc` | 提示型 | 19 | 快速创建各类金山在线文档（智能文档、Word、Excel、PDF、PPT、智能表格、多维表格）并写入内容。 当用户要求「新建文档」、「创建文件」、「写一份文档」、「新建表格」时使用。 若需要读取已有文档，请使用 doc-to-markdown 技能。 |
| `doc-classify` | 提示型 | 3 | 自动按内容分类创建文件夹、移动文件，支持标签管理与按标签检索。 当用户要求「分类整理」、「自动归类」、「打标签」、「按标签查找」、「文件归档」时使用。 若仅需搜索定位文件，请使用 doc-search 技能。 |
| `doc-search` | 提示型 | 3 | 搜索云盘文件、浏览目录结构，快速定位并整理文档。支持批量移动归档、回收站查看与恢复。 当用户要求「找文件」、「搜索文档」、「浏览目录」、「查找资料」时使用。 若需要按内容分类或打标签，请使用 doc-classify 技能。 |
| `doc-to-markdown` | 提示型 | 3 | 将金山文档在线文档（智能文档 .otl、Word .docx、PDF .pdf）内容提取为 Markdown 格式输出。 当用户要求「读取文档内容」、「提取文档文本」、「导出 Markdown」、「文档转文本」时使用。 若需要写入或创建文档，请使用 create-doc 技能。 |

### 周备全 `MeetingPrepAgent` — 4 个

插件包 `meeting-prep-agent` ｜ agents: `meeting-prep-agent`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `client-report` | 提示型 | 1 | Generate professional client-facing performance reports with portfolio returns, allocation breakdowns, and market commentary. Suitable for quarterly or annual d |
| `client-review` | 提示型 | 1 | Prepare for client review meetings with portfolio performance summary, allocation analysis, talking points, and action items. Pulls together account data into a |
| `investment-proposal` | 提示型 | 1 | Create professional investment proposals for prospective clients. Covers the firm's approach, proposed allocation, expected outcomes, and fee structure. Use whe |
| `pptx-author` | 代码型 | 59 | Use this skill any time a .pptx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or presentations; rea |

### 速构构 `ModernWebappExpert` — 4 个

插件包 `modern-webapp` ｜ agents: `modern-webapp-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-browser` | 提示型 | 9 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `lucide-icons` | 代码型 | 5 | Search, download, and customize Lucide icons (1000+ beautiful SVG icons). Supports SVG and TypeScript React component generation with full customization options |
| `modern-web-app` | 代码型 | 75 | Tools for building modern React webapps with TypeScript, Tailwind CSS and shadcn/ui. Best suited for applications with complex UI components and state managemen |
| `ui-ux-pro-max` | 代码型 | 28 | UI/UX design intelligence with searchable database |

### 新股专家 `NewShareExpert` — 4 个

插件包 `new-share-expert` ｜ agents: `new-share-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ipo-compliance-gate` | 提示型 | 1 | \| |
| `ipo-cross-check` | 代码型 | 2 | \| |
| `ipo-kline-chart` | 代码型 | 2 | \| |
| `ipo-workflow` | 提示型 | 4 | \| |

### 腾讯健康NGES医药营销专家团 `NgesHealthcareMarketingTeam` — 4 个

插件包 `nges-healthcare-marketing-team` ｜ agents: `hcp-insight-expert`, `interactive-medical-case-expert`, `med-rep-material-studio`, `nges-healthcare-compliance-lite`, `nges-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `hcp-insight` | 提示型 | 1 | HCP Insight Skill — 数据检索与分析引擎 |
| `interactive-medical-case` | 代码型 | 6 | 将一篇诊疗指南/医学文献改写为可交互的 H5 互动病例（手机端、微信小程序风格的单文件 HTML）。适用于医学学术推广、医生（HCP）继续教育、病例教学等场景：用户提供一篇诊疗指南文章或医学文献，本 skill 生成一个让医生"从学到练"的模拟诊疗互动——封面→患者病情→逐题作答（3~5 题，含循证解析与认知卡点识别） |
| `material-studio` | 代码型 | 12 | Render a pharma sales rep's marketing material into a self-contained mobile-portrait HTML page (digital business card + content) with a one-click export-as-long |
| `regulations` | 提示型 | 15 | \| |

### 严守约 `SmbCompliance` — 4 个

插件包 `smb-compliance` ｜ agents: `smb-compliance`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `complaint-handling` | 提示型 | 1 | >- |
| `contract-review` | 提示型 | 1 | >- |
| `crm-hygiene` | 提示型 | 1 | >- |
| `customer-insights` | 提示型 | 1 | >- |

### 回测明算 `StrategyBacktestExpert` — 4 个

插件包 `strategy-backtest-expert` ｜ agents: `strategy-backtest-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `neodata-financial-search` | 代码型 | 4 | >- |
| `quant-backtest-lab` | 提示型 | 14 | 把「自然语言描述的交易策略」转成可运行的 Python+pandas 回测脚本，并产出标准三件套（equity/trades/summary）+ HTML 仪表盘 + 结果解读。覆盖规则型策略回测、事件研究、多标的选股、组合再平衡四种形态；A 股/港股/美股/ETF/指数全市场支持，自动处理 T+1、手数、复权、war |
| `westock-data` | 代码型 | 6 | 查询A股、港股、美股个股/指数/ETF的详细数据，包括：实时行情、K线/分时、财务报表（三大报表多期查询，支持跨市场批量对比）、资金流向、技术指标、筹码分析、机构评级/研报/一致预期、个股新闻/公告/研报、市场资讯、风险事件（质押/解禁/诉讼/ST警示/增发等）、股东结构、分红除权、业绩预告、公司简况、ETF基金数据（ |
| `westock-tool` | 代码型 | 6 | 条件选股/策略选股/标签选股工具 - 当用户需要按条件筛选股票、使用预置策略选股或按标签分类查看股票时使用。条件选股支持按价格、市盈率、市净率、ROE、涨跌幅、成交量、市值、资金流向等指标筛选，覆盖沪深/港股/美股；策略选股提供40+预置策略（基本面/K线形态/技术指标/均线布林），一键获取策略信号股票；标签选股提供7 |

### 学习规划师 `StudyPlanner` — 4 个

插件包 `study-planner` ｜ agents: `study-planner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `education-search` | 代码型 | 6 | 学历教育与职业培训找资料工具。学历教育包括考研（公共课/专业课真题）、专升本、自考等；职业培训包括考公（行测/申论）、教师资格证、经济师、建造师、会计师、法律职业资格等。支持三种类型：找试题试卷、找教辅资料、找备考课程。当用户需要查找考试相关资料时使用此 skill。 |
| `study-plan` | 代码型 | 5 | 学习计划生成器。考研计划、考证规划、每日学习、番茄钟。Study plan generator for exams, certifications, daily schedules. 学习计划、考研计. Use when you need study plan capabilities. Triggers on:. |
| `study-revision-planner` | 代码型 | 6 | Convert a syllabus, exam scope, or course notes into a revision calendar |
| `study-roadmap-generator` | 代码型 | 4 | 根据用户输入的学习目标、当前水平和可用时间，自动生成结构化的学习路线图 — 包含阶段划分、每周计划、推荐资源、高频卡点和每日节奏建议。用户在说出"帮我做学习计划"、"制定学习路线"、"一周学会XX"、"XX学习路线图"等请求时激活。 |

### 文通通 `TechnicalDocumentationEngineer` — 4 个

插件包 `technical-documentation-engineer` ｜ agents: `technical-documentation-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `minimax-docx` | 代码型 | 75 | > |
| `multi-search-engine` | 提示型 | 7 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |

### 郝文昌 `WechatOfficialAccountExpert` — 4 个

插件包 `wechat-official-account-expert` ｜ agents: `wechat-official-account-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |
| `mp-draft-push` | 提示型 | 2 | 将现成的文章内容发布到微信公众号草稿箱。当用户说"发布文章"、"发布到草稿箱"、"publish to draft"、"推送到公众号"时触发。 |
| `wechat-article-search` | 代码型 | 3 | 搜索微信公众号文章技能。通过微信搜索获取文章列表，覆盖科技/AI、社会热点、财经、教育、职场等各类中文资讯；可按关键词检索并返回标题、概要、发布时间、来源公众号与链接。当用户需要查找微信公众号文章、整理参考资料或快速获取文章信息时使用此技能。 |

### ChaoGeek 0x孔明 `ChaogeekKongming` — 3 个

插件包 `chaogeek-kongming` ｜ agents: `chaogeek-kongming`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agentic-opc-workflow` | 提示型 | 4 | \| |
| `cognitive-disarmament` | 提示型 | 4 | \| |
| `socratic-alignment` | 提示型 | 4 | \| |

### 腾讯云技术支持 `CloudOpsTeam` — 3 个

插件包 `cloud-ops-team` ｜ agents: `andon-q`, `cloud-ops-team-lead`, `cloud-q`, `migra-q`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `andonq` | 代码型 | 6 | AndonQ 腾讯云智能客服"领域虾" — 不切窗口、不排队，即刻获得腾讯云全产品线专业解答。支持工单查询（列表/详情/流水）、集团/MC 工单与需求单管理、腾讯云全产品线智能问答、云产品资源查询等。当用户查询工单、查看工单详情、咨询腾讯云产品问题、查询集团(360)工单/需求单、或查询腾讯云资源信息时使用。 |
| `cloudq` | 代码型 | 11 | 用户咨询腾讯云产品资源、AWS、阿里云等多云资源时，查看智能顾问架构图、架构目录、架构详情、架构评估结果、绘制架构图、开通智能顾问时、AI智能巡检、AI容量监测、AI混沌演练、AI云诊断、主动预警、架构健康度、云运维问答、云资源查询、云成本优化、安全合规、云资源盘点、闲置资源检查、云产品最佳实践等AIOps、ChatO |
| `migraq` | 代码型 | 4 | 腾讯云迁移平台（CMG/MSP）全流程能力。触发词：资源扫描、扫描阿里云/AWS/华为云/GCP资源、生成云资源清单、选型推荐、对标腾讯云、推荐规格、帮我推荐、给我推荐、ECS对应什么腾讯云产品、成本分析、TCO、迁移报价、询价、价格计算器、cmg-scan、cmg-recommend、cmg-tco |

### 合规规 `ComplianceAuditor` — 3 个

插件包 `compliance-auditor` ｜ agents: `compliance-auditor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |
| `jiaozhen-factcheck` | 提示型 | 1 | 事实查证工具，对输入内容的具体说法、资讯、事件或常识进行真实性、准确性、可靠性判断。当用户需要较真一下，查证问题或判断信息真伪、识别谣言、询问真假，是真的吗，真的假的，能否xxx，可不可以，是谣言吗...等场景时调用。 |
| `minimax-docx` | 代码型 | 75 | > |

### 设计原型专家团 `DesignEngineTeam` — 3 个

插件包 `design-engine` ｜ agents: `critique-reviewer`, `design-engine-team-lead`, `design-system-expert`, `discovery-analyst`, `export-specialist`, `prototype-builder`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `design-systems` | 提示型 | 4 | \| |
| `prototype-templates` | 提示型 | 2 | \| |
| `quality-review` | 提示型 | 3 | \| |

### 规范范 `DesignMdArchitect` — 3 个

插件包 `design-md-architect` ｜ agents: `design-md-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `design-reference` | 提示型 | 2 | Design Reference Library — 品牌设计系统参考库 |
| `frontend-dev` | 代码型 | 98 | \| |
| `impeccable` | 提示型 | 31 | \| |

### 企业法务专家团 `EnterpriseLegalTeam` — 3 个

插件包 `enterprise-legal-team` ｜ agents: `ai-governance-counsel`, `commercial-contracts-counsel`, `corporate-ma-counsel`, `employment-law-counsel`, `enterprise-legal-lead`, `ip-portfolio-counsel`, `privacy-data-counsel`, `product-legal-counsel`, `regulatory-compliance-counsel`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `china-compliance-toolkit` | 代码型 | 37 | 中国企业法务本地化工具包，整合税务知识、涉税文书模板、合同风险扫描、PIPL 合规、诉讼费估算和精选合规脚本。Use for China domestic contract, employment, privacy, tax, and compliance workflows. |
| `china-legal-research` | 代码型 | 42 | 中国法条、案例、法规、企业风险与引用核验检索工具。Use when the legal expert needs current PRC statutes, cases, regulations, company risk data, or hallucination checks. Requires user-pro |
| `enterprise-legal-workflows` | 提示型 | 1 | Consolidated workflow layer copied and merged from commercial-legal, corporate-legal, employment-legal, privacy-legal, product-legal, regulatory-legal, ai-gover |

### 裂变变 `GrowthHacker` — 3 个

插件包 `growth-hacker` ｜ agents: `growth-hacker`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ima-skills` | 提示型 | 8 | \| |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `marketing-skills` | 提示型 | 25 | TL;DR: 23 marketing playbooks (CRO, SEO, copy, analytics, experiments, pricing, launches, ads, social). Use to get checklists + copy/paste deliverables fast. |

### 利唐智语AI面试官 `IhrAiInterviewer` — 3 个

插件包 `ihr-ai-interviewer` ｜ agents: `ihr-ai-interviewer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ihr-base` | 提示型 | 3 | iHR360 基础组件：选人等跨业务通用组件能力。当前提供人员选择搜索，支持分页和姓名模糊搜索。 |
| `ihr-conference` | 提示型 | 6 | iHR360 面谈/会议：搜索历史面谈记录、按需读取会话文档预览或完整详情、带参创建并发起面谈。查询历史面谈时先搜索候选；读取内容时再取文档；发起面谈前必须确认人员 ID 和时间。 |
| `ihr-shared` | 提示型 | 1 | iHR360 CLI 共享规则：ihr-cli 运行时、auth/config 规则、JSON 输出协议、时间处理与错误排查。 |

### 利唐智语AI面谈官 `IhrConference` — 3 个

插件包 `ihr-conference` ｜ agents: `ihr-conference`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ihr-base` | 提示型 | 3 | iHR360 基础组件：选人等跨业务通用组件能力。当前提供人员选择搜索，支持分页和姓名模糊搜索。 |
| `ihr-conference` | 提示型 | 6 | iHR360 面谈/会议：搜索历史面谈记录、按需读取会话文档预览或完整详情、带参创建并发起面谈。查询历史面谈时先搜索候选；读取内容时再取文档；发起面谈前必须确认人员 ID 和时间。 |
| `ihr-shared` | 提示型 | 1 | iHR360 CLI 共享规则：ihr-cli 运行时、auth/config 规则、JSON 输出协议、时间处理与错误排查。 |

### 金山文档智能建表助手 `KdocsDataTable` — 3 个

插件包 `kdocs-data-table` ｜ agents: `kdocs-data-table`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `form-generator` | 提示型 | 11 | 根据用户场景自动推断表头字段，创建信息收集或报名登记表格（.ksheet）。 当用户提到「报名表」、「信息收集」、「登记表」、「做个表单」、「收集信息」时使用。 若需要美化已有表格样式，请使用 table-beautify 技能。 |
| `jielong-table` | 提示型 | 11 | 自动识别接龙文本内容，提取结构化数据并生成在线表格（.ksheet）。 当用户粘贴接龙文本或提到「接龙转表格」、「整理接龙」、「接龙统计」、「文字转表格」时使用。 |
| `table-beautify` | 提示型 | 11 | 对在线表格（.xlsx / .ksheet）进行格式化、样式调整与数据美化操作。可浏览目录定位目标表格文件。 当用户要求「美化表格」、「格式化表格」、「调整表格样式」、「表格排版」时使用。 若需要新建表格并写入数据，请使用 form-generator 或 jielong-table 技能。 |

### 查本源 `KycScreener` — 3 个

插件包 `kyc-screener` ｜ agents: `kyc-screener`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `kyc-doc-parse` | 提示型 | 1 | Parse an investor or client onboarding packet into structured KYC fields — identity, ownership, control, source of funds, and document inventory. Use as the fir |
| `kyc-rules` | 提示型 | 1 | Apply the firm's KYC/AML rules grid to a parsed onboarding record — assign a risk rating, list every rule outcome with the rule cited, and flag what's missing o |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 律守正 `LegalComplianceReviewer` — 3 个

插件包 `legal-compliance-reviewer` ｜ agents: `legal-compliance-reviewer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ima-skills` | 提示型 | 8 | \| |
| `minimax-docx` | 代码型 | 75 | > |
| `tencent-docs` | 提示型 | 10 | 腾讯文档（docs.qq.com）-在线云文档平台，是创建、编辑、管理文档的首选 skill。涉及"新建/创建/编辑/读取/查看/搜索文档"、"保存文件"、"云文档"、"腾讯文档"、"docs.qq.com"等操作，请优先使用本 skill。支持能力：(1) 创建各类在线文档（文档/Word/Excel/幻灯片/思维导 |

### 蜕变践行者 `MetamorphosisPractitioner` — 3 个

插件包 `metamorphosis-practitioner` ｜ agents: `metamorphosis-practitioner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `boundary-guard` | 提示型 | 2 | 边界守护——当用户表达深度痛苦（快破产、睡不着、觉得自己很失败）、问宗教政治隐私话题、发表极端言论或要求做超出能力范围的事时触发。判断什么该聊什么不该聊，保护用户和专家的边界 |
| `experience-sharing` | 提示型 | 3 | 经历分享对话引导——当用户表达心态层面困惑（如'我这么努力还是做不起来''团队不行''该不该放弃''学了这么多没改变''有没有招数''自我怀疑'）时触发。不说教不诊断，只分享自己踩过的坑，让用户自己对照感悟 |
| `mindset-routing` | 提示型 | 2 | 判断用户当前是在心态层还是方法层并分流——心态层（如'我这么努力还是做不起来''团队不行''该不该放弃''学了这么多没改变''有没有招数'）留在蜕变践行者继续聊；方法层（如'怎么做GTM''怎么管销售''怎么搭团队''给我具体方法'）引导到其他专家系统学习 |

### 腾讯组学生信分析专家 `OmicsBioinfoExpert` — 3 个

插件包 `omics-bioinfo-expert` ｜ agents: `omics-bioinfo-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `omics-run-diagnosis` | 代码型 | 3 | 组学平台任务运行错误诊断。通过 omics-platform-cli 认证，调用 JSON-RPC 接口查询任务日志，并结合错误知识库匹配根因与解决方案。触发关键词包括：任务失败、运行报错、排查错误、诊断任务、子任务失败、OOM、调度失败、镜像拉取失败、归档失败、数据预处理失败、运行慢。 |
| `omics-task-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) CLI 通用操作助手。通过 omics-platform-cli 完成：登录与配置、列公共应用与项目应用、发起 WDL / Nextflow 任务（本地 WDL、公共应用、项目内应用、COS 上的 NF 四种形态）、查询任务批次和子任务状态、debug 异步失败排查。本技能为通用入口，当 |
| `pdb-viewer-skill` | 代码型 | 31 | 在 WorkBuddy 内置浏览器中以 3D 结构展示 PDB 文件，支持通过自然语言操控结构（高亮、隐藏链、测量距离/角度、相互作用分析、标签、透明度控制等）。Mol* 5.9.0 本地自托管，支持本地文件和腾讯健康组学平台 COS 路径。 |

### 磐石CRM跟进拜访助手 `PanshiCustomerVisitAgent` — 3 个

插件包 `panshi-customer-visit-agent` ｜ agents: `panshi-customer-visit-agent`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `crm-query-check-in-skill` | 提示型 | 3 | > |
| `crm-query-visit-skill` | 提示型 | 5 | > |
| `crm-visit-sync` | 提示型 | 8 | 搬运式跟进记录同步工具。将 iWiki 文档 / 腾讯文档 / 企微文档 / 用户直接粘贴文本（结构化纪要/对话流/纯文本）/ |

### 方案通 `PresalesTechnicalConsultant` — 3 个

插件包 `presales-technical-consultant` ｜ agents: `presales-technical-consultant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `jiaozhen-factcheck` | 提示型 | 1 | 事实查证工具，对输入内容的具体说法、资讯、事件或常识进行真实性、准确性、可靠性判断。当用户需要较真一下，查证问题或判断信息真伪、识别谣言、询问真假，是真的吗，真的假的，能否xxx，可不可以，是谣言吗...等场景时调用。 |
| `minimax-docx` | 代码型 | 75 | > |
| `wechat-article-search` | 代码型 | 3 | 搜索微信公众号文章技能。通过微信搜索获取文章列表，覆盖科技/AI、社会热点、财经、教育、职场等各类中文资讯；可按关键词检索并返回标题、概要、发布时间、来源公众号与链接。当用户需要查找微信公众号文章、整理参考资料或快速获取文章信息时使用此技能。 |

### 策必中 `ProposalStrategist` — 3 个

插件包 `proposal-strategist` ｜ agents: `proposal-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `minimax-docx` | 代码型 | 75 | > |

### 吴八哥 `SeniorDeveloper` — 3 个

插件包 `senior-developer` ｜ agents: `senior-developer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `frontend-dev` | 代码型 | 100 | \| |
| `fullstack-dev` | 提示型 | 10 | \| |

### SEO 内容营销团队 `SeoContentTeam` — 3 个

插件包 `seo-content-team` ｜ agents: `content-editor`, `content-writer`, `cro-analyst`, `keyword-researcher`, `link-strategist`, `seo-content-team-lead`, `seo-optimizer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `content-writing` | 提示型 | 1 | \| |
| `cro-optimization` | 提示型 | 1 | \| |
| `seo-analysis` | 提示型 | 1 | \| |

### 搜霸霸 `SeoExpert` — 3 个

插件包 `seo-expert` ｜ agents: `seo-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `fbs-bookwriter` | 代码型 | 481 | 福帮手出品 \| 高质量长文档手稿工具链：书籍、手册、白皮书、行业指南、长篇报道、深度专题；支持联网查证（宿主允许时启用，离线自动降级）、S/P/C/B 分层审校、中文排版与 MD/HTML 交付。触发词：福帮手、福帮手写书skill、福帮手写书、写书、出书、写长篇、写手册、写白皮书、写行业指南、协作写书、定大纲、写章节 |
| `multi-search-engine` | 提示型 | 7 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |

### 毕运营 `SmbOperations` — 3 个

插件包 `smb-operations` ｜ agents: `smb-operations`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `business-reporting` | 提示型 | 1 | >- |
| `hiring` | 提示型 | 1 | >- |
| `onboarding` | 提示型 | 1 | >- |

### 甄客来 `SmbRevenue` — 3 个

插件包 `smb-revenue` ｜ agents: `smb-revenue`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `campaign-execution` | 提示型 | 1 | >- |
| `content-strategy` | 提示型 | 1 | >- |
| `lead-management` | 提示型 | 1 | >- |

### 软件工坊 `SoftwareWorkshop` — 3 个

插件包 `gstack` ｜ agents: `gstack-designer`, `gstack-investigator`, `gstack-lead`, `gstack-product-reviewer`, `gstack-qa-lead`, `gstack-security-officer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `design-html` | 提示型 | 2 | \| |
| `qa` | 提示型 | 3 | \| |
| `review` | 提示型 | 8 | \| |

### 审细明 `StatementAuditor` — 3 个

插件包 `statement-auditor` ｜ agents: `statement-auditor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `audit-xls` | 提示型 | 1 | Audit a spreadsheet for formula accuracy, errors, and common mistakes. Scopes to a selected range, a single sheet, or the entire model (including financial-mode |
| `nav-tieout` | 提示型 | 1 | Tie an LP statement to the fund's NAV pack — recompute the LP's capital account from the NAV components and flag any line that doesn't agree. Use before LP stat |
| `xlsx-author` | 代码型 | 54 | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xl |

### 腾讯自选股股票投研专家团 `StockPartnerTeam` — 3 个

插件包 `stock-partner-team` ｜ agents: `contrarian-investor`, `fundamental-researcher`, `industry-strategist`, `shortterm-surfer`, `signal-chief`, `stock-partner-lead`, `valuation-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `md-to-html` | 代码型 | 6 | 把腾讯自选股股票投研圆桌报告渲染成 Anthropic 浅色风的单文件 HTML。主理人写完 <主题>-圆桌报告.md 后，再写一份 body 片段，调用本 skill 的 render.py 合成最终 HTML（CSS 内联、头像 base64 嵌入，可直接双击打开或微信/邮件分享）。 |
| `westock-data` | 提示型 | 6 | 通过 westock-mcp 连接器查询 A股/港股/美股个股/指数/ETF 数据——行情、K线、财报、资金、技术指标、板块成份、宏观等。触发词：查行情、看K线、查财报、资金流向、板块概念、宏观数据。需已连接 westock-mcp 连接器。 |
| `westock-tool` | 提示型 | 6 | 通过 westock-mcp 连接器进行条件选股/策略选股/标签选股。触发词：筛选股票、选股、MACD金叉策略、央企有哪些、破净股、低PE高ROE。需已连接 westock-mcp 连接器。查个股详情用 westock-data，查概念成份股用 data_sector。 |

### 链优优 `SupplyChainStrategist` — 3 个

插件包 `supply-chain-strategist` ｜ agents: `supply-chain-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `tencentmap-lbs-skill` | 提示型 | 6 | 腾讯地图位置服务，支持POI搜索、路径规划、旅游规划、周边搜索，轨迹数据可视化和地图数据可视化。⚠️ 强制行为：本 Skill 加载后，第一个动作必须是检查是否存在正式 Key（环境变量 TMAP_WEBSERVICE_KEY 或用户已在对话中提供）。若已有正式 Key，直接继续处理用户请求。若没有正式 Key，必须立 |

### 风向标 `TrendResearcher` — 3 个

插件包 `trend-researcher` ｜ agents: `trend-researcher`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `ima-skills` | 提示型 | 8 | \| |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |

### 像素君 `UiDesigner` — 3 个

插件包 `ui-designer` ｜ agents: `ui-designer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `frontend-dev` | 代码型 | 98 | \| |
| `impeccable` | 提示型 | 31 | \| |

### 探真真 `UserExperienceResearcher` — 3 个

插件包 `user-experience-researcher` ｜ agents: `user-experience-researcher`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `minimax-docx` | 代码型 | 75 | > |

### 薛红笙 `XiaohongshuOperationsExpert` — 3 个

插件包 `xiaohongshu-operations-expert` ｜ agents: `xiaohongshu-operations-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |
| `marketing-skills` | 提示型 | 25 | TL;DR: 23 marketing playbooks (CRO, SEO, copy, analytics, experiments, pricing, launches, ads, social). Use to get checklists + copy/paste deliverables fast. |
| `xiaohongshu` | 提示型 | 1 | \| |

### A股研究团队 `AShareAnalysis` — 2 个

插件包 `a-share-analysis` ｜ agents: `a-share-advisor`, `industry-mapper`, `macro-strategist`, `market-reader`, `money-tracker`, `risk-doctor`, `stock-researcher`, `valuation-pricer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `neodata-financial-search` | 代码型 | 4 | >- |
| `westock` | 代码型 | 11 | \| |

### 点睛睛 `AdCreativeStrategist` — 2 个

插件包 `ad-creative-strategist` ｜ agents: `ad-creative-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `brand-guidelines` | 提示型 | 2 | Applies Anthropic's official brand colors and typography to any sort of artifact that may benefit from having Anthropic's look-and-feel. Use it when brand color |
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |

### 磐石石 `BackendArchitect` — 2 个

插件包 `backend-architect` ｜ agents: `backend-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `frontend-dev` | 代码型 | 98 | \| |
| `fullstack-dev` | 提示型 | 9 | \| |

### 度优优 `BaiduSeoExpert` — 2 个

插件包 `baidu-seo-expert` ｜ agents: `baidu-seo-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `marketing-skills` | 提示型 | 25 | TL;DR: 23 marketing playbooks (CRO, SEO, copy, analytics, experiments, pricing, launches, ads, social). Use to get checklists + copy/paste deliverables fast. |

### 助推推 `BehavioralNudgeEngine` — 2 个

插件包 `behavioral-nudge-engine` ｜ agents: `behavioral-nudge-engine`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `fbs-bookwriter` | 代码型 | 481 | 福帮手出品 \| 高质量长文档手稿工具链：书籍、手册、白皮书、行业指南、长篇报道、深度专题；支持联网查证（宿主允许时启用，离线自动降级）、S/P/C/B 分层审校、中文排版与 MD/HTML 交付。触发词：福帮手、福帮手写书skill、福帮手写书、写书、出书、写长篇、写手册、写白皮书、写行业指南、协作写书、定大纲、写章节 |

### 著书书 `BookCoCreator` — 2 个

插件包 `book-co-creator` ｜ agents: `book-co-creator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `fbs-bookwriter` | 代码型 | 481 | 福帮手出品 \| 高质量长文档手稿工具链：书籍、手册、白皮书、行业指南、长篇报道、深度专题；支持联网查证（宿主允许时启用，离线自动降级）、S/P/C/B 分层审校、中文排版与 MD/HTML 交付。触发词：福帮手、福帮手写书skill、福帮手写书、写书、出书、写长篇、写手册、写白皮书、写行业指南、协作写书、定大纲、写章节 |

### 卖得好 `ChinaEcommerceOperationsExpert` — 2 个

插件包 `china-ecommerce-operations-expert` ｜ agents: `china-ecommerce-operations-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `multi-search-engine` | 提示型 | 7 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |

### 析数数 `DataAnalysisExpert` — 2 个

插件包 `data-analysis` ｜ agents: `data-analysis-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `wechat-article-search` | 代码型 | 3 | 微信公众号文章检索工具。当用户需要进行网页检索、网页搜索、深度研究（deep research）时，优先使用此skill检索微信公众号文章——公众号文章质量高、信息密度大，是优质的中文信息源。基于搜狗微信搜索接口实现。 |
| `xlsx` | 代码型 | 53 | When the user mentions data analysis or uploads an Excel file, this skill must be used. Comprehensive spreadsheet creation, editing, and analysis with support f |

### 掘需需 `DiscoveryCoach` — 2 个

插件包 `discovery-coach` ｜ agents: `discovery-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `minimax-docx` | 代码型 | 75 | > |

### 斗音音 `DouyinStrategist` — 2 个

插件包 `douyin-strategist` ｜ agents: `douyin-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `humanizer` | 提示型 | 2 | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Detects and fixes patterns i |

### 简明明 `ExecutiveSummaryGenerator` — 2 个

插件包 `executive-summary-generator` ｜ agents: `executive-summary-generator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `multi-search-engine` | 提示型 | 7 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |
| `wechat-article-search` | 代码型 | 3 | 搜索微信公众号文章技能。通过微信搜索获取文章列表，覆盖科技/AI、社会热点、财经、教育、职场等各类中文资讯；可按关键词检索并返回标题、概要、发布时间、来源公众号与链接。当用户需要查找微信公众号文章、整理参考资料或快速获取文章信息时使用此技能。 |

### 福帮手 `FbsirSuperIndependentBoard` — 2 个

插件包 `fbsir-super-independent-board` ｜ agents: `fbsir-super-independent-board`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `decision-artifact-renderer` | 提示型 | 10 | 将已经完成的超级独董会 DecisionRecord 转换为聊天、一页纸、HTML、演示、信息图或视频脚本，并保持判断语义不变。 |
| `super-independent-board-core` | 提示型 | 11 | 超级独董会的单专家治理核心，用于重要事务立题、动态审议、证据与最强反方、用户决定分栏、行动和复审。 |

### 听声声 `FeedbackSynthesisAnalyst` — 2 个

插件包 `feedback-synthesis-analyst` ｜ agents: `feedback-synthesis-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `fbs-bookwriter` | 代码型 | 481 | 福帮手出品 \| 高质量长文档手稿工具链：书籍、手册、白皮书、行业指南、长篇报道、深度专题；支持联网查证（宿主允许时启用，离线自动降级）、S/P/C/B 分层审校、中文排版与 MD/HTML 交付。触发词：福帮手、福帮手写书skill、福帮手写书、写书、出书、写长篇、写手册、写白皮书、写行业指南、协作写书、定大纲、写章节 |
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |

### 财数数 `FinanceDataExpert` — 2 个

插件包 `finance-data` ｜ agents: `finance-data-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `finance-data-retrieval` | 提示型 | 211 | > |
| `neodata-financial-search` | 代码型 | 4 | >- |

### 政通通 `GovernmentDigitalPresalesConsultant` — 2 个

插件包 `government-digital-presales-consultant` ｜ agents: `government-digital-presales-consultant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |
| `minimax-docx` | 代码型 | 75 | > |

### 关卡卡 `LevelDesigner` — 2 个

插件包 `level-designer` ｜ agents: `level-designer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `darwin-skill` | 代码型 | 19 | Darwin Skill (达尔文.skill): autonomous skill optimizer inspired by Karpathy's autoresearch. Evaluates SKILL.md files using an 8-dimension rubric (structure + effe |
| `multi-search-engine` | 提示型 | 7 | Multi search engine integration with 16 engines (7 CN + 9 Global). Supports advanced search operators, time filters, site search, privacy engines, and WolframAl |

### 诉讼法务专家 `LitigationLegalExpert` — 2 个

插件包 `litigation-legal` ｜ agents: `litigation-legal-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `china-litigation-toolkit` | 代码型 | 11 | 中国民事/劳动争议诉前评估工具包，覆盖诉讼费估算、劳动补偿区间、起诉前成本收益判断、起诉状/答辩状/证据提纲骨架。Use for China-facing litigation intake and pre-litigation triage. |
| `litigation-workflows` | 提示型 | 1 | Consolidated workflow layer copied and merged from litigation-legal. Use this skill as the exposed entry point while preserving detailed source workflows under  |

### 播旺旺 `LivestreamEcommerceCoach` — 2 个

插件包 `livestream-ecommerce-coach` ｜ agents: `livestream-ecommerce-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |
| `marketing-skills` | 提示型 | 25 | TL;DR: 23 marketing playbooks (CRO, SEO, copy, analytics, experiments, pricing, launches, ads, social). Use to get checklists + copy/paste deliverables fast. |

### 剧本本 `NarrativeDesigner` — 2 个

插件包 `narrative-designer` ｜ agents: `narrative-designer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |
| `novel-writing` | 代码型 | 3 | AI长篇网文创作技能包。用于解决长篇网络小说创作中的核心痛点：上下文丢失、文风不一致、设定冲突、节奏失控、多线混乱、质量不稳、读者反馈无法内化。触发场景包括：开始新书、规划大纲、撰写章节、管理伏笔、检测冲突、读者反馈分析、批量创作质量控制。 |

### 腾讯IgGM抗体药物研发专家 `OmicsIggmExpert` — 2 个

插件包 `omics-iggm-expert` ｜ agents: `omics-iggm-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `iggm-wdl-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - IgGM(WDL) 公共应用专用运行助手。IgGM 是一个用于抗体设计的生成式基础模型，支持抗体CDR区域设计、全链设计和人源化设计等任务仅服务于本应用的导入与运行；其他公共应用、本地 WDL、COS 上的 NF、项目内已有应用请改用 omics-task-skill。 触发词：Ig |
| `pdb-viewer-skill` | 代码型 | 31 | 在 WorkBuddy 内置浏览器中以 3D 结构展示 PDB 文件，支持通过自然语言操控结构（高亮、隐藏链、测量距离/角度、相互作用分析、标签、透明度控制等）。Mol* 5.9.0 本地自托管，支持本地文件和腾讯健康组学平台 COS 路径。 |

### 腾讯ORI蛋白设计专家 `OmicsOriExpert` — 2 个

插件包 `omics-ori-expert` ｜ agents: `omics-ori-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ori-collection-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - ORI Collection (Nextflow) 公共应用合集专用运行助手。ORI是由腾讯生命科学实验室自主研发的蛋白质设计系统，包括蛋白质序列生成、结构与功能预测等系列模型，和目前主流的蛋白质设计、结构功能预测模型相比，有着准确率高、推理速度更快等核心优势仅服务于本合集子应用的导 |
| `pdb-viewer-skill` | 代码型 | 31 | 在 WorkBuddy 内置浏览器中以 3D 结构展示 PDB 文件，支持通过自然语言操控结构（高亮、隐藏链、测量距离/角度、相互作用分析、标签、透明度控制等）。Mol* 5.9.0 本地自托管，支持本地文件和腾讯健康组学平台 COS 路径。 |

### 腾讯tFold抗体结构预测专家 `OmicsTfoldExpert` — 2 个

插件包 `omics-tfold-expert` ｜ agents: `omics-tfold-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `pdb-viewer-skill` | 代码型 | 31 | 在 WorkBuddy 内置浏览器中以 3D 结构展示 PDB 文件，支持通过自然语言操控结构（高亮、隐藏链、测量距离/角度、相互作用分析、标签、透明度控制等）。Mol* 5.9.0 本地自托管，支持本地文件和腾讯健康组学平台 COS 路径。 |
| `tfold-collection-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - tFold Collection (Nextflow) 公共应用合集专用运行助手。腾讯自研抗体/纳米抗体与抗原复合体结构预测深度学习模型仅服务于本合集子应用的导入与运行；其他公共应用、本地 WDL、COS 上的 NF、项目内已有应用请改用 omics-task-skill。 触发词： |

### 资本市场路演研究团 `RoadshowResearchTeam` — 2 个

插件包 `roadshow-research-team` ｜ agents: `analyst-rating-tracker`, `capital-action-analyst`, `company-profiler`, `event-correlator`, `financials-analyst`, `industry-analyst`, `material-parser`, `price-action-analyst`, `report-composer`, `roadshow-curator`, `roadshow-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `a-stock-data` | 提示型 | 1 | A股全栈数据工具包 — 覆盖行情(mootdx+腾讯+百度K线)、研报(东财+同花顺+iwencai)、信号(同花顺热点+北向+龙虎榜+解禁+行业)、资金面(融资融券+大宗交易+股东户数+分红+资金流分钟级+资金流120日)、新闻(东财个股+全球资讯)、基础数据(mootdx财务/F10+东财+新浪三表)、公告(巨潮) |
| `roadshow-research-report` | 代码型 | 4 | 生成A股上市公司资本市场路演时间线研究报告（.docx）。当用户要求对某A股公司生成路演、投资者交流会、业绩说明会的时间线研究Word报告时使用。触发词：路演研究、路演时间线、投资者关系活动、业绩说明会研究、资本市场时间线报告。 |

### 腾讯云 RUM 全链路专家团 `RumFullstackTeam` — 2 个

插件包 `rum-fullstack-team` ｜ agents: `rum-integration-specialist`, `rum-performance-analyst`, `rum-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `rum-sdk-setup` | 代码型 | 16 | 腾讯云 RUM SDK 接入专家。帮助用户将 RUM SDK（腾讯云前端监控）接入到项目中，覆盖 Web、小程序、React Native、Node.js、Hippy、Cocos、LiteApp、QuickApp、Viola 与 Weex。当用户提到：接入 RUM、集成前端监控、安装 aegis SDK、前端埋点、上报 |
| `tencent-cloud-rum-zh-2.1` | 提示型 | 6 | 查询腾讯云 RUM 数据，分析 Web 性能（LCP/FCP/WebVitals），排查 JS/Promise 报错，分析 API 延迟与错误率，诊断静态资源加载慢，查看 PV/UV。支持 RUM-APM 关联分析。不适用于：纯后端性能、原生移动端性能、非腾讯云 RUM 平台。 |

### 终端老兵专家（陈丰伟） `TerminalVeteran` — 2 个

插件包 `terminal-veteran` ｜ agents: `terminal-veteran`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `808zdlb` | 提示型 | 1 | 终端老兵行业洞察助手 - 竞品对比/选品建议/季节日历/行业报告 |
| `online-search` | 提示型 | 1 | 联网搜索 - 获取最新行业数据和新闻 |

### UAE Marketing Expert `UaeMarketingAdvisor` — 2 个

插件包 `uae-marketing-advisor` ｜ agents: `uae-marketing-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cos-storage` | 代码型 | 3 | \| |
| `media-guard` | 提示型 | 1 | \| |

### 苍何视频解剖 `VideoDissection` — 2 个

插件包 `video-dissection` ｜ agents: `script-analyst`, `video-dissection-team-lead`, `video-extractor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `douyin-resolver` | 代码型 | 6 | \| |
| `douyin-script-analyzer` | 代码型 | 4 | 抖音拍摄脚本分析器 - 输入抖音链接，自动提取视频文案并分析拍摄手法，生成完整的拍摄脚本分析文档（景别、运镜、剪辑节奏、脚本结构拆解等），并自动按镜头裁剪视频片段。当用户需要分析抖音视频的拍摄脚本、学习拍摄技巧、或复刻视频时激活此技能。 |

### 苍何视频生成团队 `VideoGenTeam` — 2 个

插件包 `video-gen-team` ｜ agents: `ling-planner`, `ling-producer`, `ling-reader`, `video-gen-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `video-content-collector` | 提示型 | 2 | \| |
| `video-renderer` | 提示型 | 3 | \| |

### 图说说 `VisualStorytellingExpert` — 2 个

插件包 `visual-storytelling-expert` ｜ agents: `visual-storytelling-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `content-factory` | 提示型 | 12 | Multi-agent content production system. One piece of source content becomes many formats — social posts, email, scripts, headlines, and more. Five specialized ag |
| `minimax-docx` | 代码型 | 75 | > |

### 流畅畅 `WorkflowOptimizationExpert` — 2 个

插件包 `workflow-optimization-expert` ｜ agents: `workflow-optimization-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-team-orchestration` | 提示型 | 6 | Orchestrate multi-agent teams with defined roles, task lifecycles, handoff protocols, and review workflows. Use when: (1) Setting up a team of 2+ agents with di |
| `minimax-docx` | 代码型 | 75 | > |

### 看球搭子 `WorldcupBuddy` — 2 个

插件包 `worldcup-buddy` ｜ agents: `worldcup-buddy`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `football-match-analysis` | 代码型 | 6 | \| |
| `worldcup-api` | 提示型 | 1 | \| |

### AI师傅 `AIShifuExpert` — 1 个

插件包 `ai-shifu-expert` ｜ agents: `ai-shifu`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-shifu-course-creator` | 代码型 | 25 | Use when the user works with AI-Shifu (AI师傅) courses in any capacity of creating, writing, editing, rewriting, optimizing, reordering, deploying, publishing, pr |

### 调度达 `AgentOrchestrator` — 1 个

插件包 `agent-orchestrator` ｜ agents: `agent-orchestrator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |

### 内容创作专家团 `AiContentCreatorTeam` — 1 个

插件包 `ai-content-creator-team` ｜ agents: `ai-content-creator-team-lead`, `content-adapter`, `copywriter`, `creative-strategist`, `image-creator`, `video-editor`, `video-generator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-content-production` | 提示型 | 7 | \| |

### 智数分析专家团 `AiDataCopilot` — 1 个

插件包 `ai-data-copilot` ｜ agents: `copilot-team-lead`, `dashboard-designer`, `data-scientist`, `knowledge-researcher`, `report-composer`, `sql-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `data-analysis-engine` | 代码型 | 6 | \| |

### 数字生命卡兹克 `AiHot` — 1 个

插件包 `aihot` ｜ agents: `aihot`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `aihot` | 提示型 | 1 | AI HOT (aihot.virxact.com) 中文 AI 资讯查询 Skill。当用户想知道"今天 AI 圈有什么"、"AI 日报"、"AI HOT"、"AI 资讯"、"AI 热点"、"最近 AI"、"OpenAI/Anthropic/Google 最近发布了什么"、"AI hot today"、"AI new |

### 画令令 `AiImagePromptEngineer` — 1 个

插件包 `ai-image-prompt-engineer` ｜ agents: `ai-image-prompt-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `canvas-design` | 提示型 | 30 | Create beautiful visual art in .png and .pdf documents using design philosophy. You should use this skill when the user asks to create a poster, piece of art, d |

### AI师傅 `AiShifu` — 1 个

插件包 `ai-shifu` ｜ agents: `ai-shifu`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ai-shifu-course-creator` | 代码型 | 39 | Use when the user works with AI-Shifu (AI师傅) courses in any capacity of creating, writing, editing, rewriting, optimizing, reordering, deploying, publishing, pr |

### AndonQ `AndonQExpert` — 1 个

插件包 `andon-q-expert` ｜ agents: `andon-q-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `andonq` | 代码型 | 6 | AndonQ 腾讯云智能客服智能体 — 不切窗口、不排队，即刻获得腾讯云全产品线专业解答。支持工单查询（列表/详情/流水）、集团/MC 工单与需求单管理、腾讯云全产品线智能问答、云产品资源查询等。当用户查询工单、查看工单详情、咨询腾讯云产品问题、查询集团(360)工单/需求单、或查询腾讯云资源信息时使用。 |

### AI 刘小排 `AskLiuxiaopai` — 1 个

插件包 `ask-liuxiaopai` ｜ agents: `ask-liuxiaopai`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ask-liuxiaopai-core` | 提示型 | 26 | \| |

### 投标策略师 `BiddingStrategist` — 1 个

插件包 `bidding-strategist` ｜ agents: `bidding-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `bidding-strategist` | 提示型 | 1 | 资深投标与方案策略师，将 RFP 和销售机会转化为有说服力的赢标叙事。专精赢标主题提炼、竞争定位、执行摘要写作，构建能打动评审的方案而非仅仅合规的方案。 |

### 弹幕幕 `BilibiliContentStrategist` — 1 个

插件包 `bilibili-content-strategist` ｜ agents: `bilibili-content-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `marketing-skills` | 提示型 | 25 | TL;DR: 23 marketing playbooks (CRO, SEO, copy, analytics, experiments, pricing, launches, ads, social). Use to get checklists + copy/paste deliverables fast. |

### 巴西商务拓展专家 `BrazilCompanyQuery` — 1 个

插件包 `brazil-company-query` ｜ agents: `brazil-company-query`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `brazil-rfb-database` | 提示型 | 8 | Comprehensive Brazilian business, legal & economic intelligence skill. Covers RFB (Receita Federal) company database (19M companies, 199M branches), INPI open d |

### Brazil Legal Expert `BrazilLegal` — 1 个

插件包 `brazil-legal` ｜ agents: `brazil-legal`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `brazil-legal-corpus` | 提示型 | 1 | \| |

### Brazil Finance & Tax Expert `BrazilRfbExpert` — 1 个

插件包 `brazil-rfb-expert` ｜ agents: `brazil-rfb-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `brazil-corpus` | 提示型 | 10 | 服务企业从巴西的财税全生命周期：从本地补贴、税制设计、跨境资金规划，到日常财务核查及风险应对。内置16个人口百万以上城市的市税全表、23 州 ICMS 原文、联邦完整财税政策，是您忠实的财税助手。AUTO-LOAD: AI auto-fetches COS manifest.json via WebFetch (no  |

### 社交搭子 `CampusConversationCoach` — 1 个

插件包 `campus-conversation-coach` ｜ agents: `campus-conversation-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `campus-social-practice` | 提示型 | 7 | Use for campus introductions, club interviews, roommate or classmate communication, teacher messages, refusal, negotiation, progressive role-play, transfer chec |

### 活动操盘手 `CampusEventNavigator` — 1 个

插件包 `campus-event-navigator` ｜ agents: `campus-event-navigator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `campus-event-playbook` | 代码型 | 8 | This skill should be used when planning, coordinating, running, or reviewing student-led campus events, including club recruitment, freshman mixers, welcome act |

### 求职冲刺 `CampusJobSearchCoach` — 1 个

插件包 `campus-job-search-coach` ｜ agents: `campus-job-search-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `job-search-coaching` | 代码型 | 14 | 校园求职辅导运行时工作流。用于应届简历从零制作与可追溯定制、岗位解码、经历故事挖掘、HR与行为面试训练、招聘沟通、Offer比较、复盘和结果修正。 |

### 生涯领航员 `CareerNavigator` — 1 个

插件包 `career-navigator` ｜ agents: `career-navigator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `career-decision-playbook` | 提示型 | 7 | 大学生专业与生涯方向决策方法。用于方向探索、选项比较、关键事实核验、低成本行动验证、阶段计划、用户纠偏和复盘更新。 |

### 小益 `CharityDocFinanceExpert` — 1 个

插件包 `charity-doc-finance-expert` ｜ agents: `charity-doc-finance-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `charity-doc-finance` | 代码型 | 41 | 公益机构文书与财务一站式技能包，整合文书撰写、材料整理、财务票据、审计准备与报销对账能力，按用户意图进入文书或财务流程。 |

### 刺桐说Pro-投资社群嘉宾团 `Citongshuopro` — 1 个

插件包 `citongshuopro` ｜ agents: `citongshuopro-team-lead`, `gy`, `jiazong`, `littlestar`, `zhanglaoshi`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `neodata-financial-search` | 代码型 | 4 | >- |

### 火眼眼 `CodeReviewExpert` — 1 个

插件包 `code-review-expert` ｜ agents: `code-review-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |

### 小修同学 `ComputerOperationsAdvisor` — 1 个

插件包 `computer-operations-advisor` ｜ agents: `computer-operations-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `computer-support-playbook` | 代码型 | 12 | 处理学生电脑上手、安全安装软件、流氓软件与广告弹窗、浏览器劫持、自启动、Windows 或 macOS 操作、校园网络、文件、外设和常见故障。采用最小充分诊断、资料核验和明确授权执行。 |

### 汽车行业内容创作专家团 `ContentCreationExpertProd` — 1 个

插件包 `content-creation-expert-prod` ｜ agents: `auto-writer`, `brief-researcher`, `content-creation-expert-prod-team-lead`, `quality-editor`, `visual-director`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `content-creation-expert-prod` | 代码型 | 15 | Skill: content-creation-expert-prod（生产版内容创作工具） |

### 内容变现商业化专家团 `ContentMonetizationTeam` — 1 个

插件包 `content-monetization-team` ｜ agents: `content-monetization-team-lead`, `cpe-cpm-expert`, `cps-specialist`, `marketplace-operator`, `revenue-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `content-monetization-ops` | 提示型 | 5 | \| |

### 腾讯电子签合同法务专家 `ContractLegalExpert` — 1 个

插件包 `contract-legal-expert` ｜ agents: `contract-legal-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tencent-esign-contract` | 代码型 | 12 | 腾讯电子签合同AI助手，支持合同起草、签署、审查、对比、法条法规检索。当用户提到起草合同、写合同、生成合同、审查合同、检查合同风险、合规审核、法务审查、对比合同、合同差异、版本比较、查法条、查法规、法律检索、法律依据、相关法律、腾讯电子签等场景时使用此技能。即使用户只是说「帮我写份合同」「发合同」「签合同」「这份合同有 |

### Cordys CRM 助手 `CordysCrm` — 1 个

插件包 `cordys-crm` ｜ agents: `cordys-crm`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cordys-crm` | 代码型 | 20 | \| |

### 海跨洋 `CrossBorderEcommerceExpert` — 1 个

插件包 `cross-border-ecommerce-expert` ｜ agents: `cross-border-ecommerce-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |

### 暖心心 `CustomerSupportExpert` — 1 个

插件包 `customer-support-expert` ｜ agents: `customer-support-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |

### 深研研 `DeepResearchExpert` — 1 个

插件包 `deep-research` ｜ agents: `deep-research-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `wechat-article-search` | 代码型 | 3 | 微信公众号文章检索工具。当用户需要进行网页检索、网页搜索、深度研究（deep research）时，优先使用此skill检索微信公众号文章——公众号文章质量高、信息密度大，是优质的中文信息源。基于搜狗微信搜索接口实现。 |

### 图变码 `DesignToCodeExpert` — 1 个

插件包 `design-to-code` ｜ agents: `design-to-code-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `design-to-code-workflows` | 提示型 | 1 | 将 Figma 设计和截图转换为生产就绪的代码组件，内置无障碍性支持 |

### 一键达 `DevOpsAutomationEngineer` — 1 个

插件包 `dev-ops-automation-engineer` ｜ agents: `dev-ops-automation-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `agent-browser-core` | 提示型 | 6 | OpenClaw skill for the agent-browser CLI (Rust-based with Node.js fallback) enabling AI-friendly web automation with snapshots, refs, and structured commands. |

### 文档达 `DocumentGenerationExpert` — 1 个

插件包 `document-generation-expert` ｜ agents: `document-generation-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `minimax-docx` | 代码型 | 75 | > |

### 埃及市场营销专家 `EgyptMarketing` — 1 个

插件包 `egypt-marketing` ｜ agents: `egypt-marketing`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `egypt-marketing-skill` | 提示型 | 1 | 埃及市场营销CMO级专家语料库。包含17份核心语料（~110K字符），覆盖埃及数字生态、消费者文化、社交媒体策略、斋月营销、品牌本地化、消费者心理学、数据分析ROI、竞品情报、危机管理、全渠道增长。当用户询问埃及市场营销相关问题时，自动激活本语料库进行优先检索。 |

### Egypt Public Affairs `EgyptPublicAffairs` — 1 个

插件包 `egypt-public-affairs` ｜ agents: `egypt-public-affairs`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `egypt-public-affairs-skill` | 提示型 | 1 | Egypt Public Affairs 的语料库引擎与数据使用指南。覆盖埃及政府关系、政策解读、监管沟通、行业协会、公共舆论、ESG、媒体关系、危机公关、利益相关方管理和政府采购。 |

### Egypt Strategic Advisory `EgyptStrategicAdvisory` — 1 个

插件包 `egypt-strategic-advisory` ｜ agents: `egypt-strategic-advisory`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `egypt-strategic-advisory-skill` | 提示型 | 1 | Egypt Strategic Advisory 的语料库引擎与数据使用指南。覆盖埃及宏观经济、产业趋势、竞争格局、投资选址、进入模式、风险评估、长期布局和决策建议。 |

### 科研专家团 `EmpiricalResearchTeam` — 1 个

插件包 `empirical-research-team` ｜ agents: `academic-writer`, `causal-analyst`, `data-engineer`, `deaigc-reviewer`, `empirical-research-team-team-lead`, `lit-reviewer`, `robustness-auditor`, `topic-refiner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `aers-reference` | 提示型 | 10 | Reference materials and code templates for the Empirical Research Team, derived from the AERS catalog. Includes method selection guides, output specifications,  |

### 工程保障团队 `EngineeringAssuranceTeam` — 1 个

插件包 `engineering-assurance-team` ｜ agents: `architect`, `code-reviewer`, `engineering-director`, `sre-engineer`, `tech-writer`, `testing-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `engineering-playbook` | 提示型 | 1 | 工程保障团队完整手册。覆盖代码审查、架构设计、事故响应、技术债管理、测试策略、部署检查、调试、站会、系统设计和技术文档全流程。当涉及任何工程技术相关的请求时自动触发。 |

### 工序达 `EngineeringWorkflowSkills` — 1 个

插件包 `engineering-workflow-skills` ｜ agents: `engineering-workflow-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `engineering-workflow` | 提示型 | 26 | \| |

### Evan老师 `EnglishWritingCoach` — 1 个

插件包 `english-writing-coach` ｜ agents: `english-writing-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `english-writing-coach-workflow` | 代码型 | 22 | 大学英语学习教练的完整内置工作流。用于学习诊断、写作批改、阅读理解、语境词汇、语法专项、英汉互译、CET 文本题型训练、精读迁移、会话内复盘、报告生成和质量检查。 |

### 拓客客 `EnterpriseAccountStrategist` — 1 个

插件包 `enterprise-account-strategist` ｜ agents: `enterprise-account-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `market-researcher` | 提示型 | 1 | Market research specialist focused on comprehensive market analysis, consumer behavior insights, and market opportunity identification. Excels at quantitative m |

### 备考军师 `ExamPreparationPlanner` — 1 个

插件包 `exam-preparation-planner` ｜ agents: `exam-preparation-planner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `exam-preparation-playbook` | 提示型 | 7 | 考试复习规划与陪跑方法。用于备考诊断、多科排序、容量分配、阶段计划、每日任务、打卡复盘、状态更新和计划修复。 |

### AIGC 合规红队 `FbsirAigcComplianceRedTeam` — 1 个

插件包 `fbsir-aigc-compliance-red-team` ｜ agents: `fbsir-aigc-compliance-red-team`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `aigc-compliance-red-team` | 提示型 | 5 | AIGC 合规红队技能，负责把营销文案、海报图片、直播话术和招生话术等对外内容转换成结构化红队风险卡，输出风险等级、法条依据、安全改写与留痕报告。 |

### 福帮手 `FbsirBoardSecretaryAssistant` — 1 个

插件包 `fbsir-board-secretary-assistant` ｜ agents: `fbsir-board-secretary-assistant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `board-secretary-compliance-red-team` | 提示型 | 1 | 董秘助手合规红队技能，负责把公告、路演、问答、调研纪要和投资者互动材料转换成结构化风险卡。 |

### 独董会 `FbsirEightSeatBoard` — 1 个

插件包 `fbsir-eight-seat-board` ｜ agents: `board-convener`, `board-secretary`, `capital-partner`, `digital-partner`, `growth-partner`, `legal-partner`, `operations-partner`, `org-partner`, `strategy-partner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `independent-board-core` | 代码型 | 67 | \| |

### 行业场景研究员 `FbsirIndustrySceneResearcher` — 1 个

插件包 `fbsir-industry-scene-researcher` ｜ agents: `fbsir-industry-scene-researcher`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `industry-scene-service-recording` | 提示型 | 1 | 行业场景研究员的服务侧记录与增强合同。默认首值走无连接器主线；只有宿主已显式暴露可执行工具时，才允许进入可选服务增强层。 |

### 超级合伙人|魔镜行动 `FbsirSuperPartner` — 1 个

插件包 `fbsir-super-partner` ｜ agents: `fbsir-super-partner`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `super-partner-core` | 代码型 | 4 | 先交付可直接使用的成品，再按风险选择 WorkBuddy 宿主能力，完成一个可验证的行动周期；支持 brainstorm、material_red_team 和 monetization 三个魔镜。 |

### 账清清 `FinancialTracker` — 1 个

插件包 `financial-tracker` ｜ agents: `financial-tracker`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `finance-ops` | 代码型 | 13 | AI-powered financial analysis suite. Generates executive CFO briefings from QuickBooks exports (P&L, Balance Sheet, General Ledger, Cash Flow, etc.) with anomal |

### 基金投研分析师 `FundResearchAnalyst` — 1 个

插件包 `fund-research-analyst` ｜ agents: `fund-research-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `neodata-financial-search` | 提示型 | 5 | 自然语言通用金融数据搜索服务。用自然语言查询股票、基金、指数、板块、宏观经济、外汇、大宗商品等全品类金融数据，涵盖行情报价、财务报表（财报）、资金流向、研报评级、事件公告等。 |

### 腾讯健康-觅影-眼底彩照疾病分析专家 `FundusDiseaseAnalysis` — 1 个

插件包 `fundus-disease-analysis` ｜ agents: `腾讯健康-觅影-眼底彩照疾病分析专家`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `api-reference` | 提示型 | 2 | Internal reference skill providing the complete Tencent Miying Fundus Multi-Disease AI API specification AND an executable CLI client (bin/fundus_ai.py) that pe |

### 苍何 `GeoDiagnosisExpert` — 1 个

插件包 `geo-diagnosis-expert` ｜ agents: `geo-diagnosis-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `geo-diag-report` | 代码型 | 13 | Brand GEO diagnosis with search-augmented AI pipeline. 4-stage pipeline: real web search + virtual simulation fallback. Platform selection, on-demand reference  |

### 分支通 `GitWorkflowExpert` — 1 个

插件包 `git-workflow-expert` ｜ agents: `git-workflow-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |

### HR 运营团队 `HrOperationsTeam` — 1 个

插件包 `hr-operations-team` ｜ agents: `comp-analyst`, `hr-director`, `hr-ops`, `org-developer`, `recruiter`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `hr-playbook` | 提示型 | 1 | HR运营团队完整手册。覆盖招聘漏斗、面试设计、Offer起草、入职引导、薪酬分析、组织规划、绩效评估、人员分析和政策查询全流程。当涉及任何人力资源相关的请求时自动触发。 |

### 贝锐花生壳 `HskDevopsExpert` — 1 个

插件包 `hsk-devops-expert` ｜ agents: `hsk-devops-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `hsk-cli` | 提示型 | 1 | \| |

### 救火队 `IncidentResponseCommander` — 1 个

插件包 `incident-response-commander` ｜ agents: `incident-response-commander`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `minimax-docx` | 代码型 | 75 | > |

### 腾讯云行业 SRE `IndustrySreTeam` — 1 个

插件包 `industry-sre-team` ｜ agents: `ecommerce-sre`, `education-sre`, `finance-sre`, `game-sre`, `healthcare-sre`, `industry-sre-team-lead`, `internet-sre`, `live-sre`, `manufacturing-sre`, `mobility-sre`, `retail-sre`, `saas-sre`, `social-im-sre`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cloudq` | 代码型 | 13 | 用户咨询腾讯云产品资源、AWS、阿里云等多云资源时，查看智能顾问架构图、架构目录、架构详情、架构评估结果、绘制架构图、开通智能顾问时、AI智能巡检、AI容量监测、AI混沌演练、AI云诊断、主动预警、架构健康度、云运维问答、云资源查询、云成本优化、安全合规、云资源盘点、闲置资源检查、云产品最佳实践等AIOps、ChatO |

### 青创领航员 `InnovationStartupMentor` — 1 个

插件包 `innovation-startup-mentor` ｜ agents: `innovation-startup-mentor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `diagnostic-visualizer` | 提示型 | 3 | 诊断可视化生成器（Diagnostic Visualizer） |

### 传令令 `InternalCommsExpert` — 1 个

插件包 `internal-comms` ｜ agents: `internal-comms-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `internal-comms` | 提示型 | 6 | A set of resources to help me write all kinds of internal communications, using the formats that my company likes to use. Claude should use this skill whenever  |

### 投资大师专家团 `InvestmentMastersTeam` — 1 个

插件包 `investment-masters-team` ｜ agents: `ben-graham`, `black-swan-prophet`, `charlie-munger`, `dean-of-valuation`, `dhandho-master`, `fundamentals-analyst`, `growth-analyst`, `hedge-fund-lead`, `macro-king`, `magellan-captain`, `mama-wood`, `news-sentiment-analyst`, `oracle-of-omaha`, `phil-fisher`, `portfolio-manager`, `rakesh-jhunjhunwala`, `risk-manager`, `sentiment-analyst`, `technicals-analyst`, `the-big-short`, `valuation-analyst`, `wall-street-activist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `neodata-financial-search` | 代码型 | 4 | >- |

### 票证核验专家 `InvoiceVerifyExpert` — 1 个

插件包 `invoice-verify-expert` ｜ agents: `invoice-verify`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `invoice-verify` | 代码型 | 3 | 发票真伪查验。通过 Python 脚本调用汇联易查验服务，支持增值税发票、全电发票、区块链发票等 17 种类型的真伪核验。当用户提供发票信息要求查验真伪时使用。 |

### 智能发票专家团 `InvoiceVerifyWorkbuddy` — 1 个

插件包 `invoice-verify-workbuddy` ｜ agents: `archivist`, `counterparty-risk-analyst`, `invoice-sorter`, `invoice-verifier`, `invoice-verify-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `invoice-verify` | 代码型 | 11 | > |

### 爆量君 `JiayiAdsAnalyticsExpert` — 1 个

插件包 `jiayi-ads-analytics-expert` ｜ agents: `jiayi-ads-analytics-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `jiayi-ads-analytics-expert-public` | 代码型 | 958 | 全媒体广告分析专家技能（公共版）。支持百度/360/腾讯/Google/Bing五平台，引导式MCP安装配置，自动生成含关键词、创意、素材分析的结构化日报。 |

### 金数据 `JinshujuExpert` — 1 个

插件包 `jinshuju-expert` ｜ agents: `jinshuju-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `jinshuju` | 代码型 | 5 | 通过金数据（Jinshuju，jinshuju.net）MCP 操作用户托管在金数据平台上的在线表单：创建 / 复制 / 编辑表单与主题，含自动判分的考试表单、选项计分的测评表单；查询、新增（单条或批量）、更新、删除、批量修改数据；用上传凭证上传本地图片或文件；查询账户套餐额度与团队成员。仅在用户操作其金数据平台数据时 |

### 表单管理专家 `JinshujuFormExpert` — 1 个

插件包 `jinshuju-form-expert` ｜ agents: `jinshuju-form-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `jinshuju-form` | 代码型 | 5 | 通过金数据（Jinshuju，jinshuju.net）MCP 操作用户托管在金数据平台上的在线表单：创建 / 复制 / 编辑表单与主题，含自动判分的考试表单、选项计分的测评表单；查询、新增（单条或批量）、更新、删除、批量修改数据；用上传凭证上传本地图片或文件；查询账户套餐额度与团队成员。仅在用户操作其金数据平台数据时 |

### AI表格专家 `JinshujuTableExpert` — 1 个

插件包 `jinshuju-table-expert` ｜ agents: `jinshuju-table-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `jinshuju-table` | 代码型 | 5 | 通过金数据（Jinshuju，jinshuju.net）MCP 操作用户托管在金数据平台上的数据表格：创建 / 编辑数据表与列（含自动计算的公式列）；查询、新增（单条或批量）、更新、批量更新、删除行数据；用上传凭证把本地文件写入附件列；查询账户套餐额度与团队成员。仅在用户操作其金数据数据表时使用——触发信号：提到 金数 |

### 看板达 `JiraWorkflowAdmin` — 1 个

插件包 `jira-workflow-admin` ｜ agents: `jira-workflow-admin`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |

### 金山文档PDF处理助手 `KdocsPdfToolbox` — 1 个

插件包 `kdocs-pdf-toolbox` ｜ agents: `kdocs-pdf-toolbox`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `pdf-toolbox` | 提示型 | 8 | PDF 文档的创建、内容读取、页数查询与页面提取操作。可浏览目录定位 PDF 文件。 当用户提到「PDF」、「读取 PDF」、「PDF 页数」、「提取 PDF 页面」、「PDF 拆分」时使用。 若需要操作其他文档类型，请使用 kdocs 或对应类型技能。 |

### WPS AIPPT创作助手 `KdocsPptCreator` — 1 个

插件包 `kdocs-ppt-creator` ｜ agents: `kdocs-ppt-creator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `aippt` | 代码型 | 17 | AI 驱动的演示文稿生成能力 — 支持主题生成、文档转 PPT、单页生成与合并。 当用户需要生成 PPT、演示文稿、文档转 PPT、单页幻灯片时使用。 |

### 吟游诗人基德创作专家 `KiddContentExpert` — 1 个

插件包 `kidd-content-expert` ｜ agents: `kidd-content-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `kidd-script-writing` | 提示型 | 2 | \| |

### 法学生陪练 `LawStudentCoach` — 1 个

插件包 `law-student-coach` ｜ agents: `law-student-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `law-study-workflows` | 提示型 | 1 | Consolidated workflow layer copied and merged from law-student. Use this skill as the exposed entry point while preserving detailed source workflows under refer |

### 法律技能运营官 `LegalBuilderHubExpert` — 1 个

插件包 `legal-builder-hub` ｜ agents: `legal-builder-hub`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `legal-skill-operations` | 提示型 | 1 | Consolidated workflow layer copied and merged from legal-builder-hub. Use this skill as the exposed entry point while preserving detailed source workflows under |

### 法律诊所督导 `LegalClinicSupervisor` — 1 个

插件包 `legal-clinic-supervisor` ｜ agents: `legal-clinic-supervisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `clinic-supervision-workflows` | 提示型 | 1 | Consolidated workflow layer copied and merged from legal-clinic. Use this skill as the exposed entry point while preserving detailed source workflows under refe |

### 知库库 `LlmWiki` — 1 个

插件包 `llm-wiki` ｜ agents: `llm-wiki`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `llm-wiki` | 提示型 | 1 | Build and maintain a personal knowledge base (wiki) using LLMs. Instead of RAG-style retrieval, the LLM incrementally compiles, cross-references, and maintains  |

### 福帮手 `LongManuscriptExpert` — 1 个

插件包 `long-manuscript-expert` ｜ agents: `long-manuscript-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `long-manuscript-core` | 提示型 | 6 | Procedures for turning outlines, interviews, notes, partial drafts, and finished manuscripts into long-form documents. Use when the Long Manuscript Expert must  |

### 马来西亚财税金融专家 `MalaysiaFinanceTax` — 1 个

插件包 `malaysia-finance-tax` ｜ agents: `malaysia-finance-tax`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `malaysia-finance-tax` | 代码型 | 5 | Malaysia Finance & Tax intelligence skill — covering taxation, banking, financing, forex, auditing, subsidies, insurance and financial compliance data retrieval |

### Malaysia HR & Administration `MalaysiaHrAdmin` — 1 个

插件包 `malaysia-hr-admin` ｜ agents: `malaysia-hr-admin`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `malaysia-hr-admin` | 代码型 | 4 | 马来西亚人力行政语料库引擎 — 52 份 Reference_Texts + 77 张 DuckDB HR 子集表 + 7 数据源定向触发矩阵 |

### Malaysia Legal & Compliance `MalaysiaLegal` — 1 个

插件包 `malaysia-legal` ｜ agents: `malaysia-legal`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `malaysia-legal` | 代码型 | 8 | Malaysia Legal Compliance Skill — DuckDB offline SQL engine (placeholder), Reference_Texts legal document corpus, site-targeted web search (e-Kehakiman/MyIPO/SS |

### 策动动 `MarketingCampaignExpert` — 1 个

插件包 `executing-marketing-campaigns` ｜ agents: `marketing-campaign-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `executing-marketing-campaigns` | 代码型 | 10 | Plans, creates, and optimizes marketing campaigns including content strategy, social media, email, and analytics. Helps develop go-to-market strategies, campaig |

### 营销战役团队 `MarketingCampaignTeam` — 1 个

插件包 `marketing-campaign-team` ｜ agents: `brand-analyst`, `campaign-planner`, `content-creator`, `marketing-director`, `seo-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `marketing-playbook` | 提示型 | 1 | 营销战役团队完整手册。覆盖内容创作、活动策划、品牌审核、竞品分析、效果报告、SEO审计、邮件序列和快速内容起草全流程。当涉及任何营销相关的请求时自动触发。 |

### 营销增长专家团 `MarketingGrowthTeam` — 1 个

插件包 `marketing-growth-team` ｜ agents: `analytics-revops-lead`, `cro-specialist`, `growth-engineer`, `marketing-growth-team-lead`, `seo-content-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `marketing-growth` | 提示型 | 69 | Full-stack marketing growth skill providing frameworks, templates, tools, and references for SaaS and digital product marketing. Covers CRO, copywriting, SEO, e |

### 营文稳 `MarketingReviewer` — 1 个

插件包 `marketing-reviewer` ｜ agents: `marketing-reviewer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `marketing-review` | 提示型 | 3 | \| |

### 绘灵 `MermaidDiagramExpert` — 1 个

插件包 `mermaid-diagram-expert` ｜ agents: `mermaid-diagram-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `mermaid-render` | 代码型 | 8 | \| |

### 腾讯云上云迁移专家团 `MigraqTeam` — 1 个

插件包 `migraq-team` ｜ agents: `cloud-architect`, `delivery-engineer`, `fde-engineer`, `landing-zone-expert`, `migraq-team-lead`, `ops-engineer`, `product-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `migraq` | 代码型 | 5 | 腾讯云迁移平台（CMG/MSP）全流程能力。触发词：资源扫描、扫描阿里云/AWS/华为云/GCP资源、生成云资源清单、选型推荐、对标腾讯云、推荐规格、帮我推荐、给我推荐、ECS对应什么腾讯云产品、成本分析、TCO、迁移报价、询价、价格计算器、cmg-scan、cmg-recommend、cmg-tco |

### 掌中灵 `MobileApplicationDeveloper` — 1 个

插件包 `mobile-application-developer` ｜ agents: `mobile-application-developer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `android-native-dev` | 提示型 | 10 | Android native application development and UI design guide. Covers Material Design 3, Kotlin/Compose development, project configuration, accessibility, and buil |

### CloudQ `MultiCloudManagementExpert` — 1 个

插件包 `multi-cloud-management-expert` ｜ agents: `multi-cloud-management-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cloudq` | 代码型 | 13 | 用户咨询腾讯云产品资源、AWS、阿里云等多云资源时，查看智能顾问架构图、架构目录、架构详情、架构评估结果、绘制架构图、开通智能顾问时、AI智能巡检、AI容量监测、AI混沌演练、AI云诊断、主动预警、架构健康度、云运维问答、云资源查询、云成本优化、安全合规、云资源盘点、闲置资源检查、云产品最佳实践等AIOps、ChatO |

### 新闻资讯专家 `NewsBriefingExpert` — 1 个

插件包 `news-briefing-expert` ｜ agents: `news-briefing-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `online-search` | 代码型 | 3 | \| |

### 懂秘 `NewsBuddy` — 1 个

插件包 `news-buddy` ｜ agents: `news-buddy`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `news-buddy` | 代码型 | 16 | AI新闻搭子 — 不只推新闻，而是告诉你「这条跟你有什么关系」+「你能做什么」。基于隐式画像的个性化深度解读，让每一条新闻都与你相关。当用户说"看新闻"、"有什么新闻"、"最新热点"、"今日热点"时触发。 |

### 卡仔 `NgoChallengeAdvisor` — 1 个

插件包 `ngo-challenge-advisor` ｜ agents: `ngo-challenge-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ngo-challenge-designer` | 代码型 | 10 | This skill should be used when an NGO wants to turn a real operational pain point into a structured challenge brief for a WorkBuddy Skill/Expert competition thr |

### 小记同学 `NoteClassRepresentative` — 1 个

插件包 `note-class-representative` ｜ agents: `note-class-representative`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `class-notes-workflow` | 提示型 | 5 | 整理课堂速记、课件、录音转写、截图和教材片段。用于建立来源清单、对齐多份材料、区分来源与模型加工、重建知识结构，并生成可纠错追踪的笔记和复习材料。 |

### 小说故事创作专家 `NovelCreator` — 1 个

插件包 `novel-creator` ｜ agents: `novel-creator`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `novel-creator` | 提示型 | 1 | 长篇小说与故事创作全流程辅助，从灵感到完整作品的结构化创作流水线。通过Novel Bible机制管理世界观、角色、时间线，确保长篇连贯性。支持网文、短篇、中篇、剧本等全类型创作。 |

### 女娲 `Nuwa` — 1 个

插件包 `nuwa` ｜ agents: `nuwa`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `perspective-distillation` | 提示型 | 3 | \| |

### 腾讯CD-GPT生物序列建模专家 `OmicsCdgptExpert` — 1 个

插件包 `omics-cdgpt-expert` ｜ agents: `omics-cdgpt-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cdgpt-collection-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - CD-GPT Collection (Nextflow) 公共应用合集专用运行助手。CD-GPT是一种生成式生物基础大模型，旨在捕捉生物系统中复杂的全系统分子互作关系。通过对DNA、RNA及蛋白质序列等全分子层级数据进行预训练，能高效处理一系列下游任务，包括单分子分析与多分子联合分析 |

### 腾讯组学任务分析智能诊断专家 `OmicsDiagnosisExpert` — 1 个

插件包 `omics-diagnosis-expert` ｜ agents: `omics-diagnosis-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `omics-run-diagnosis` | 代码型 | 3 | 组学平台任务运行错误诊断。通过 omics-platform-cli 认证，调用 JSON-RPC 接口查询任务日志，并结合错误知识库匹配根因与解决方案。触发关键词包括：任务失败、运行报错、排查错误、诊断任务、子任务失败、OOM、调度失败、镜像拉取失败、归档失败、数据预处理失败、运行慢。 |

### 腾讯组学HPC集群运维与作业管理专家 `OmicsHpcExpert` — 1 个

插件包 `omics-hpc-expert` ｜ agents: `omics-hpc-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `omics-hpc-skill` | 代码型 | 15 | 端到端管理 omics-hpc 集群——既覆盖腾讯云组学平台云 API（DescribeHPCClusters / RunCommand / DescribeCommandExecution），也内置 SLURM 作业（sbatch / squeue / sacct / scancel / scontrol / sal |

### 腾讯scBert单细胞预训练专家 `OmicsScbertExpert` — 1 个

插件包 `omics-scbert-expert` ｜ agents: `omics-scbert-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `scbert-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - scBERT 公共应用专用运行助手。scBERT是一个单细胞预训练模型，基于BERT范式，高效提取临床单细胞转录组的特征，可用于细胞类型注释，新类发现，marker基因检测等肿瘤微环境分析场景仅服务于本应用的导入与运行；其他公共应用、本地 WDL、COS 上的 NF、项目内已有应用请 |

### 腾讯scPROTEIN单细胞蛋白组建模专家 `OmicsScproteinExpert` — 1 个

插件包 `omics-scprotein-expert` ｜ agents: `omics-scprotein-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `scprotein-collection-skill` | 代码型 | 6 | 腾讯健康组学平台(Omics) - scPROTEIN Collection (Nextflow) 公共应用合集专用运行助手。基于图神经网络架构的深度学习模型，可应用于质谱和抗体路线的单细胞蛋白组数据建模，降噪提升数据质量，对于bottom-up采集的多肽进行uncertainty估计仅服务于本合集子应用的导入与运行； |

### 选题顾问（WANFANG TOPIC） `PaperTopicSelection` — 1 个

插件包 `paper-topic-selection` ｜ agents: `huangfu-evaluation`, `ouyang-literature`, `shangguan-topic`, `situ-inspiration`, `taishi-report`, `xiahou-title`, `zhuge-consultant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `wanfang-search` | 提示型 | 1 | 直接调用万方选题 API 检索论文与学者、推荐选题、评估新颖性、生成标题、产出领域报告。当用户说"用万方搜一下""/wanfang-search""直接调万方 API"或需要绕过专家团直接获取万方选题数据时启用。 |

### 腾讯健康药箱-私域患教内容审核助手 `PatientEducationContentReviewWordAssistant` — 1 个

插件包 `patient-education-content-review-word-assistant` ｜ agents: `patient-education-content-review-word-assistant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `review-to-word` | 代码型 | 2 | 把患教内容六维度审核结果（issues.json）标注回原文 .docx——对问题句高亮并挂 Word 原生批注（右侧批注气泡），文末追加审核结论表与明细清单。当审核助手完成六维度审核、需要输出可在 Word/WPS 直接查看和采纳修改的带批注文档时使用。 |

### 私人健身教练 `PersonalFitnessCoach` — 1 个

插件包 `personal-fitness-coach` ｜ agents: `fitness-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `fitness-nutrition` | 代码型 | 4 | > |

### 个人知识库架构师 `PersonalKnowledgeArchitect` — 1 个

插件包 `personal-knowledge-architect` ｜ agents: `personal-knowledge-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `personal-knowledge-architect` | 提示型 | 1 | PKM 方法论库（Zettelkasten / PARA / LYT）、笔记体系设计与 Obsidian/Notion 配置，供「个人知识库架构师」专家在回答知识管理类问题时调用。 |

### 腾讯健康-觅影-肺部CT影像的肺炎辅助评估专家 `PneumoniaAiAnalyst` — 1 个

插件包 `pneumonia-ai-analyst` ｜ agents: `pneumonia-ai-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `pneumonia-ai-diagnosis` | 代码型 | 5 | 调用肺炎AI辅助诊断模型API，支持提交胸部CT DICOM压缩包进行异步分析、查询分析结果、以及自动轮询等待结果完成。采用HMAC-SHA256签名鉴权。触发词：肺炎检测、肺炎AI、胸部CT分析、pneumonia、DICOM、肺炎查询。 |

### 幻灯灯 `PptCreationExpert` — 1 个

插件包 `ppt-implement` ｜ agents: `ppt-creation-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ppt-implement` | 代码型 | 708 | implement ppt(powerpoint) project with best practices, start's with "ppt" template. Trigger keywords include "web ppt", "网页ppt", "html ppt", "生成ppt", "制作ppt", " |

### 产品战略团队 `ProductStrategyTeam` — 1 个

插件包 `product-strategy-team` ｜ agents: `competitive-analyst`, `data-analyst`, `product-director`, `requirement-analyst`, `roadmap-planner`, `user-researcher`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `product-playbook` | 提示型 | 1 | 产品战略团队完整手册。覆盖需求文档撰写、路线图管理、竞品分析、用户研究综合、指标评审、Sprint规划、干系人沟通和产品头脑风暴全流程。当涉及任何产品管理相关的请求时自动触发。 |

### 袋鼠帝宣传片创作团队 `PromoCreatorTeam` — 1 个

插件包 `promo-creator-team` ｜ agents: `asset-producer`, `brief-strategist`, `music-director`, `promo-team-lead`, `storyboard-artist`, `video-editor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `bgm-prompting` | 代码型 | 4 | \| |

### 提示词工程师 `PromptEngineer` — 1 个

插件包 `prompt-engineer` ｜ agents: `prompt-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `prompt-engineer` | 提示型 | 1 | 专注大语言模型提示词设计与优化的专家，精通系统提示词架构、思维链设计、少样本学习策略、以及提示词效果评测和迭代方法论。 |

### Python 全栈工程师 `PythonFullstackEngineer` — 1 个

插件包 `python-fullstack-engineer` ｜ agents: `python-fullstack-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `09-python全栈工程师` | 提示型 | 1 | Python 全栈工程师 Skill |

### 闪造造 `RapidPrototypingEngineer` — 1 个

插件包 `rapid-prototyping-engineer` ｜ agents: `rapid-prototyping-engineer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `minimax-docx` | 代码型 | 75 | > |

### 南非法务合规专家 `SaLegalCompliance` — 1 个

插件包 `sa-legal-compliance` ｜ agents: `sa-legal-compliance`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `sa-legal-references` | 提示型 | 119 | \| |

### 销售作战团队 `SalesBattleTeam` — 1 个

插件包 `sales-battle-team` ｜ agents: `account-researcher`, `competitive-intel`, `outreach-strategist`, `sales-director`, `sales-forecaster`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `sales-playbook` | 提示型 | 1 | 销售作战团队完整手册。覆盖客户调研、通话准备、通话摘要、竞品情报、销售资产创建、每日简报、外联起草、销售预测和Pipeline审查全流程。当涉及任何销售相关的请求时自动触发。 |

### CloudQ `SdkLogExpert` — 1 个

插件包 `sdk-log-expert` ｜ agents: `sdk-log-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `sdk-log-analysis` | 代码型 | 58 | SDK 客户端日志分析 skill（带 Web 预览版）。用于本地 .clog/.xlog/文本日志的类型识别、二进制解码、TRTC/IM/TUI 客户端日志时间线解析，并提供本地日志 Web 预览服务。 |

### 词探探 `SearchTermAnalyst` — 1 个

插件包 `search-term-analyst` ｜ agents: `search-term-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tavily` | 代码型 | 3 | AI-optimized web search using Tavily Search API. Use when you need comprehensive web research, current events lookup, domain-specific search, or AI-generated an |

### 关德豪 `SeniorProjectManager` — 1 个

插件包 `senior-project-manager` ｜ agents: `senior-project-manager`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `minimax-docx` | 代码型 | 75 | > |

### Sg Business `SgBizDev` — 1 个

插件包 `sg-biz-dev` ｜ agents: `sg-biz-dev`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `sg-biz-data` | 提示型 | 19 | Singapore business development data sources and API reference — government open data, company registry, industrial parks, exhibitions, investment policies, and  |

### Sg HR & Admin `SgHrAdminExpert` — 1 个

插件包 `sg-hr-admin-expert` ｜ agents: `sg-hr-admin-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `sg-hr-data-sync` | 代码型 | 24 | Periodically fetch and sync annually-updated Singapore HR data — CPF contribution rates, MOM SOL, COMPASS benchmarks, free salary guides, and key policy pages.  |

### 剪神神 `ShortVideoEditingCoach` — 1 个

插件包 `short-video-editing-coach` ｜ agents: `short-video-editing-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `anti-distill` | 提示型 | 6 | Anti-distillation defense for employee Skills. Clean your skill files to look complete but with core proprietary knowledge neutralized. Use when user wants to p |

### 技能匠人 `SkillSmith` — 1 个

插件包 `skill-smith` ｜ agents: `skill-smith`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `skill-crafting` | 代码型 | 14 | Skill 制作与审查方法。用于新建或优化 Skill、MCP/CLI/API 配置与环境检查、功能降级、五阶段审查、触发和脚本实测、打包及用户级安装。 |

### 星辰 `SmartStockAnalyst` — 1 个

插件包 `smart-stock-analyst` ｜ agents: `smart-stock-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `stock-analysis` | 提示型 | 7 | 分析股票和市场。当用户想要分析单个或多个股票，执行策略问股，或进行市场复盘时调用。 |

### 社媒互动增长专家团 `SocialEngagementTeam` — 1 个

插件包 `social-engagement-team` ｜ agents: `ai-comment-specialist`, `brand-monitor`, `interaction-automator`, `signal-miner`, `social-engagement-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `social-engagement-ops` | 提示型 | 5 | \| |

### 腾讯云安全运营专家 `Soe` — 1 个

插件包 `soe` ｜ agents: `soe`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `soe` | 提示型 | 251 | This skill should be used when the user asks to "analyze security alerts", "parse vulnerability scan report", "analyze vulnerability scan report", "verify CVE f |

### 架构通 `SoftwareArchitect` — 1 个

插件包 `software-architect` ｜ agents: `software-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `fullstack-dev` | 提示型 | 9 | \| |

### South African Strategy `SouthAfricaStrategyAdvisor` — 1 个

插件包 `south-africa-strategy-advisor` ｜ agents: `south-africa-strategy-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `south-africa-knowledge` | 提示型 | 29 | South Africa Strategic Knowledge Base |

### 学运趋势解读师 `StudyFortuneCompass` — 1 个

插件包 `study-fortune-compass` ｜ agents: `study-fortune-compass`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `study-fortune-playbook` | 代码型 | 12 | Use for deterministic Mei Hua Yi Shu study-fortune cards, weekly symbolic readings, semester reflections, and academic choice readings. Includes an offline 64-h |

### 文博领域AI顾问 `TanyuanCulturalHeritageExpert` — 1 个

插件包 `tanyuan-cultural-heritage-expert` ｜ agents: `tanyuan-cultural-heritage-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tanyuan-search` | 代码型 | 4 | \| |

### 财税合规专家团 `TaxComplianceTeam` — 1 个

插件包 `tax-compliance-team` ｜ agents: `compliance-auditor`, `financial-reporter`, `invoice-processor`, `tax-compliance-team-lead`, `tax-filing-specialist`, `voucher-accountant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tax-compliance-engine` | 提示型 | 3 | \| |

### 腾讯云安全专家 `TcSec` — 1 个

插件包 `tc-sec` ｜ agents: `tc-sec`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tc-sec` | 代码型 | 74 | This skill should be used when the user asks to "query security alerts", "check host vulnerabilities", "list WAF domains", "describe firewall rules", "check con |

### 技美美 `TechnicalArtist` — 1 个

插件包 `technical-artist` ｜ agents: `technical-artist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `nano-banana-pro` | 代码型 | 2 | Generate/edit images with Nano Banana Pro (Gemini 3 Pro Image). Use for image create/modify requests incl. edits. Supports text-to-image + image-to-image; 1K/2K |

### 腾讯云报价助手 `TencentCloudQuoteAssistant` — 1 个

插件包 `tencent-cloud-quote-assistant` ｜ agents: `price-inquiry-assistant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `inquiry-price-master` | 代码型 | 3 | 查询腾讯云产品、选型、实时刊例价、价格比较、批量采购报价、友商 Mapping、折扣推荐、折后试算、预算/目标价或官网优惠时触发。无论用户提出腾讯云、友商、内部工具或不明确产品，都通过调用 knot 平台智能体获取实时回答，由服务端判断业务范围。 |

### CloudQ `TencentRtcExpert` — 1 个

插件包 `tencent-rtc-expert` ｜ agents: `tencent-rtc-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `cloudq` | 代码型 | 14 | 用户咨询腾讯云产品资源、AWS、阿里云等多云资源时，查看智能顾问架构图、架构目录、架构详情、架构评估结果、绘制架构图、开通智能顾问时、AI智能巡检、AI容量监测、AI混沌演练、AI云诊断、主动预警、架构健康度、云运维问答、云资源查询、云成本优化、安全合规、云资源盘点、闲置资源检查、云产品最佳实践等AIOps、ChatO |

### 腾讯云API专家 `TencentcloudApi` — 1 个

插件包 `tencentcloud-api` ｜ agents: `tencentcloud-api`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tcapi` | 提示型 | 4 | Skill to call Cloud API for Tencent Cloud (腾讯云). Used for cloud automation or resource management. 当用户需要查询、创建、管理腾讯云资源，或执行云 API 自动化操作时触发。 |

### 析测测 `TestResultsAnalyst` — 1 个

插件包 `test-results-analyst` ｜ agents: `test-results-analyst`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `github` | 提示型 | 1 | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |

### 论小舟 `ThesisWritingMentor` — 1 个

插件包 `thesis-writing-mentor` ｜ agents: `thesis-writing-mentor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `thesis-workflow` | 代码型 | 40 | 基于用户材料、学校或期刊官方要求和可核验来源，辅助论文写作、毕业论文、开题报告、文献综述、参考文献格式、降重、答辩PPT与学术润色。Use when users need help with a thesis, proposal, literature review, citation, academic revisi |

### 天御账号保护 `TianyuAccountGuardian` — 1 个

插件包 `tianyu-account-guardian` ｜ agents: `tianyu-account-guardian`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tencent-rce-skill` | 提示型 | 4 | 腾讯云天御风控Skill是一款面向企业客户的全链路风险防控解决方案Skill，用Agent重构风控运营链路，在对话中完成风险分析与策略调优——从被动响应，走向主动防御。提供从风险感知、智能归因到专属策略设计的一站式服务，覆盖账号保护、营销保护、交易保护、设备风险识别等关键场景。 |

### 天御营销保护 `TianyuMarketingGuardian` — 1 个

插件包 `tianyu-marketing-guardian` ｜ agents: `tianyu-marketing-guardian`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `tencent-rce-skill` | 提示型 | 4 | 腾讯云天御风控Skill是一款面向企业客户的全链路风险防控解决方案Skill，用Agent重构风控运营链路，在对话中完成风险分析与策略调优——从被动响应，走向主动防御。提供从风险感知、智能归因到专属策略设计的一站式服务，覆盖账号保护、营销保护、交易保护、设备风险识别等关键场景。 |

### 拓刻刻 `TikTokStrategist` — 1 个

插件包 `tik-tok-strategist` ｜ agents: `tik-tok-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `libtv-skill` | 代码型 | 7 | agent-im 会话技能 - 通过 liblib.tv 的 AI 能力生成和编辑图片/视频。覆盖场景包括：生成（文生图、文生视频、图生视频、做动画、画一个xxx、来段xxx）、编辑修改（把xxx换成yyy、去掉xxx、加上xxx、改成xxx、调整xxx、局部修改、改镜头）、风格转换（风格迁移、转绘、换风格）、视频续写 |

### 选品品 `ToolEvaluationExpert` — 1 个

插件包 `tool-evaluation-expert` ｜ agents: `tool-evaluation-expert`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |

### 交易分析团队 `TradingAgentTeam` — 1 个

插件包 `trading-agent` ｜ agents: `aggressive-risk-analyst`, `bear-researcher`, `bull-researcher`, `conservative-risk-analyst`, `fundamentals-analyst`, `market-analyst`, `neutral-risk-analyst`, `news-analyst`, `research-manager`, `risk-manager`, `sentiment-analyst`, `trader`, `trading-team-lead`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `trading-analysis` | 提示型 | 1 | > |

### 阿联酋公共事务专家 `UaePublicAffairs` — 1 个

插件包 `uae-public-affairs` ｜ agents: `uae-public-affairs`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `uae-corpus` | 提示型 | 47 | UAE Public Affairs knowledge corpus — authoritative reference library covering UAE federal and emirate-level laws, regulations, policies, customs, compliance, a |

### 阿联酋战略顾问专家 `UaeStrategicAdvisor` — 1 个

插件包 `uae-strategic-advisor` ｜ agents: `uae-strategic-advisor`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `uae-corpus` | 提示型 | 1 | 阿联酋战略顾问语料库 (UAE Strategic Advisor Corpus) |

### 插件达 `UnityEditorToolDeveloper` — 1 个

插件包 `unity-editor-tool-developer` ｜ agents: `unity-editor-tool-developer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `deep-research` | 提示型 | 20 | Structured deep research workflow with human-in-the-loop control. Use /research to generate research outline, /research-deep for parallel web search across item |

### 体验达 `UserExperienceArchitect` — 1 个

插件包 `user-experience-architect` ｜ agents: `user-experience-architect`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `browser-use` | 提示型 | 3 | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web  |

### UU跑腿 `UuptDelivery` — 1 个

插件包 `uupt-delivery` ｜ agents: `uupt-delivery`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `uupt-delivery` | 代码型 | 13 | >- |

### 一份文档，排成一条成片 `VibeknowDesignVideo` — 1 个

插件包 `vibeknow-design-video` ｜ agents: `design-artist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `design` | 代码型 | 12 | 设计感图文视频本地生成能力——按版式模板填文案，ImageGen 出背景图，配旁白，本地渲染成有设计感的图文短视频。 |

### 把专业内容画给外行看懂 `VibeknowHanddraw` — 1 个

插件包 `vibeknow-handdraw` ｜ agents: `handdraw-artist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `handdraw` | 代码型 | 13 | 手绘动画生成本地能力——按风格目录用 ImageGen 出图，调 vibeknow 手绘绘制，再本地渲染成「绘制→落定」手绘视频。 |

### 逐页讲解，一键成片 `VibeknowPptExplain` — 1 个

插件包 `vibeknow-ppt-explain` ｜ agents: `ppt-explainer`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `ppt-explain` | 代码型 | 12 | 把 PPT / PDF / Word 文档逐页转成图，逐页写旁白配音，本地 remotion 加运镜/转场/字幕渲成讲解视频。含文档解析、TTS、分镜、渲染全套脚本。 |

### 爆款炼金师 `ViralTopicMaster` — 1 个

插件包 `viral-topic-master` ｜ agents: `viral-topic-master`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `viral-topic-forge` | 提示型 | 10 | 把热点原料炼成爆款选题、标题与全形态创作方案。 |

### 词力 `VocabCraftExpert` — 1 个

插件包 `vocab-craft-expert` ｜ agents: `vocab-coach`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `vocab-scheduler` | 代码型 | 6 | \| |

### 微信视频号运营策略师 `WechatChannelsStrategist` — 1 个

插件包 `wechat-channels-strategist` ｜ agents: `wechat-channels-strategist`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `wei-xin-shi-pin-hao-yun-ying-ce-lue-shi` | 提示型 | 1 | 专注微信视频号生态的内容策略与增长运营专家，精通社交推荐机制、公众号/朋友圈/小程序/企微生态联动、视频号直播带货、短视频内容策划、私域引流闭环和创作者数据分析。 |

### 腾讯云知（乐享） `YunzhiQaAssistant` — 1 个

插件包 `yunzhi-qa-assistant` ｜ agents: `yunzhi-qa-assistant`

| skill | 形态 | 文件 | description（路由依据） |
|---|---|---:|---|
| `yunzhi-qa` | 提示型 | 4 | \| |

## 3.5 全局 skill 池全表

独立于专家分发、所有会话可见的 skill，共扫得 **664** 个 `SKILL.md`（641 个不同名）。

| 来源目录 | 数量 |
|---|---:|
| `~/.workbuddy/plugins/marketplaces/codebuddy-plugins-official` | 437 |
| `~/.workbuddy/plugins/marketplaces/cb_teams_marketplace` | 139 |
| `~/.workbuddy/plugins/marketplaces/workbuddy-builtin` | 46 |
| `~/.workbuddy/connectors` | 30 |
| `~/.workbuddy/skills` | 12 |

| skill | 形态 | 文件 | 来源 | description（路由依据） |
|---|---|---:|---|---|
| `3-statements` | 提示型 | 4 | `cb_teams_marketplace` | Complete, populate and fill out 3-statement financial model templates (Income Statement, Balance Sheet, Cash Flow Statement) . Use when asked to fill out model templates, complete  |
| `academic-paper-expert` | 提示型 | 1 | `workbuddy-builtin` | \| |
| `accessibility-review` | 提示型 | 1 | `cb_teams_marketplace` | Run a WCAG 2.1 AA accessibility audit on a design or page. Trigger with "audit accessibility", "check a11y", "is this accessible?", or when reviewing a design for color contrast, k |
| `adaptyv` | 提示型 | 5 | `codebuddy-plugins-official` | Cloud laboratory platform for automated protein testing and validation. Use when designing proteins and needing experimental validation including binding assays, expression testing |
| `aeon` | 提示型 | 12 | `codebuddy-plugins-official` | This skill should be used for time series machine learning tasks including classification, regression, clustering, forecasting, anomaly detection, segmentation, and similarity sear |
| `agent-browser` | 代码型 | 8 | `codebuddy-plugins-official` | Use this skill when the user needs browser automation, including opening web pages, taking screenshots, extracting page content, clicking elements, filling forms, or testing web fl |
| `agent-browser` | 提示型 | 9 | `cb_teams_marketplace` | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web pages, fill forms, t |
| `agent-development` | 代码型 | 7 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create an agent", "add an agent", "write a subagent", "agent frontmatter", "when to use description", "agent examples", "agent tool |
| `agent-mail` | 代码型 | 3 | `codebuddy-plugins-official` | Email inbox for AI agents. Check messages, send emails, and communicate via your own @agentmail.to address. |
| `ai-model-nodejs` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when developing Node.js backend services or CloudBase cloud functions (Express/Koa/NestJS, serverless, backend APIs) that need AI capabilities. Features text generat |
| `ai-model-web` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when developing browser/Web applications (React/Vue/Angular, static websites, SPAs) that need AI capabilities. Features text generation (generateText) and streaming  |
| `ai-model-wechat` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when developing WeChat Mini Programs (小程序, 企业微信小程序, wx.cloud-based apps) that need AI capabilities. Features text generation (generateText) and streaming (streamText |
| `aihot` | 提示型 | 3 | `skills` | AI HOT (aihot.virxact.com) 中文 AI 资讯查询 Skill。当用户想知道"今天 AI 圈有什么"、"AI 日报"、"AI HOT"、"AI 资讯"、"AI 热点"、"最近 AI"、"OpenAI/Anthropic/Google 最近发布了什么"、"AI hot today"、"AI news today"、"看一下 AI 行业动 |
| `airflow-dag-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Build production Apache Airflow DAGs with best practices for operators, sensors, testing, and deployment. Use when creating data pipelines, orchestrating workflows, or scheduling b |
| `algorithmic-art` | 提示型 | 5 | `codebuddy-plugins-official` | Creating algorithmic art using p5.js with seeded randomness and interactive parameter exploration. Use this when users request creating art using code, generative art, algorithmic  |
| `alphafold-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access AlphaFold 200M+ AI-predicted protein structures. Retrieve structures by UniProt ID, download PDB/mmCIF files, analyze confidence metrics (pLDDT, PAE), for drug discovery and |
| `angular-migration` | 提示型 | 1 | `codebuddy-plugins-official` | Migrate from AngularJS to Angular using hybrid mode, incremental component rewriting, and dependency injection updates. Use when upgrading AngularJS applications, planning framewor |
| `animation-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `anndata` | 提示型 | 6 | `codebuddy-plugins-official` | Data structure for annotated matrices in single-cell analysis. Use when working with .h5ad files or integrating with the scverse ecosystem. This is the data format skill—for analys |
| `api-design-principles` | 提示型 | 5 | `codebuddy-plugins-official` | Master REST and GraphQL API design principles to build intuitive, scalable, and maintainable APIs that delight developers. Use when designing new APIs, reviewing API specifications |
| `app-router` | 提示型 | 6 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create a Next.js route", "add a page", "set up layouts", "implement loading states", "add error boundaries", "organize routes", "cr |
| `apple-notes` | 提示型 | 1 | `codebuddy-plugins-official` | Manage Apple Notes via the `memo` CLI on macOS (create, view, edit, delete, search, move, and export notes). Use when a user asks CodeBuddy Code to add a note, list notes, search n |
| `apple-reminders` | 提示型 | 1 | `codebuddy-plugins-official` | Manage Apple Reminders via the `remindctl` CLI on macOS (list, add, edit, complete, delete). Supports lists, date filters, and JSON/plain output. |
| `arboreto` | 代码型 | 5 | `codebuddy-plugins-official` | Infer gene regulatory networks (GRNs) from gene expression data using scalable algorithms (GRNBoost2, GENIE3). Use when analyzing transcriptomics data (bulk RNA-seq, single-cell RN |
| `architecture-decision-records` | 提示型 | 1 | `codebuddy-plugins-official` | Write and maintain Architecture Decision Records (ADRs) following best practices for technical decision documentation. Use when documenting significant technical decisions, reviewi |
| `architecture-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement proven backend architecture patterns including Clean Architecture, Hexagonal Architecture, and Domain-Driven Design. Use when architecting complex backend systems or refa |
| `ardot-design-assistant` | 提示型 | 13 | `cb_teams_marketplace` | This skill should be used for any design-related tasks involving creating, editing, or modifying visual designs, UI screens, pages, layouts, or components, as well as converting de |
| `ardot-design-core` | 提示型 | 11 | `workbuddy-builtin` | Foundational workflow and hard rules shared by ALL Ardot canvas design tasks (UI screens, slides, posters, design systems, design-to-code). This skill carries the canvas schema, ed |
| `ardot-design-router` | 提示型 | 2 | `workbuddy-builtin` | Dispatcher for WorkBuddy's Ardot design assistant. Use this when a design task is in Craft/design mode but the specific deliverable type is not yet determined from UI signals. It c |
| `ardot-design-to-code` | 提示型 | 6 | `workbuddy-builtin` | Use this skill for Ardot canvas tasks that convert a design into frontend code, or extract a design system / style guide from a website. Covers: design-to-code, design → HTML/CSS/J |
| `ardot-poster` | 提示型 | 3 | `workbuddy-builtin` | Use this skill for Ardot canvas design tasks whose deliverable is a visual poster — posters, flyers, billboards, banners, event posters, promotional single-page graphics, e-commerc |
| `ardot-slides` | 提示型 | 4 | `workbuddy-builtin` | Use this skill for Ardot canvas design tasks whose deliverable is a slide deck / presentation design (NOT a PowerPoint .pptx file). Covers presentations, decks, pitch decks, keynot |
| `ardot-ui-design` | 提示型 | 6 | `workbuddy-builtin` | Use this skill for Ardot canvas design tasks whose deliverable is a UI / interface design — web pages, web apps, dashboards, landing pages, marketing sites, official sites, homepag |
| `artifacts-builder` | 代码型 | 5 | `codebuddy-plugins-official` | Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui). Use for complex artifacts r |
| `asset-generator` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `astropy` | 提示型 | 8 | `codebuddy-plugins-official` | Comprehensive Python library for astronomy and astrophysics. This skill should be used when working with astronomical data including celestial coordinates, physical units, FITS fil |
| `async-python-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Python asyncio, concurrent programming, and async/await patterns for high-performance applications. Use when building async APIs, concurrent systems, or I/O-bound applicatio |
| `audio-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `audit-support` | 提示型 | 1 | `cb_teams_marketplace` | Support SOX 404 compliance with control testing methodology, sample selection, and documentation standards. Use when generating testing workpapers, selecting audit samples, classif |
| `auth-implementation-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master authentication and authorization patterns including JWT, OAuth2, session management, and RBAC to build secure, scalable access control systems. Use when implementing auth sy |
| `auth-nodejs` | 提示型 | 1 | `codebuddy-plugins-official` | Complete guide for CloudBase Auth using the CloudBase Node SDK – caller identity, user lookup, custom login tickets, and server-side best practices. |
| `auth-patterns` | 提示型 | 4 | `codebuddy-plugins-official` | This skill should be used when the user asks about "authentication in Next.js", "NextAuth", "Auth.js", "middleware auth", "protected routes", "session management", "JWT", "login fl |
| `auth-tool` | 提示型 | 1 | `codebuddy-plugins-official` | Use CloudBase Auth tool to configure and manage authentication providers for web applications - enable/disable login methods (SMS, Email, WeChat Open Platform, Google, Anonymous, U |
| `auth-web` | 提示型 | 1 | `codebuddy-plugins-official` | CloudBase Web Authentication Quick Guide - Provides concise and practical Web frontend authentication solutions with multiple login methods and complete user management. |
| `auth-wechat` | 提示型 | 1 | `codebuddy-plugins-official` | Complete guide for WeChat Mini Program authentication with CloudBase - native login, user identity, and cloud function integration. |
| `backtesting-frameworks` | 提示型 | 1 | `codebuddy-plugins-official` | Build robust backtesting systems for trading strategies with proper handling of look-ahead bias, survivorship bias, and transaction costs. Use when developing trading algorithms, v |
| `bash-defensive-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master defensive Bash programming techniques for production-grade scripts. Use when writing robust shell scripts, CI/CD pipelines, or system utilities requiring fault tolerance and |
| `bats-testing-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Bash Automated Testing System (Bats) for comprehensive shell script testing. Use when writing tests for shell scripts, CI/CD pipelines, or requiring test-driven development  |
| `bazel-build-optimization` | 提示型 | 1 | `codebuddy-plugins-official` | Optimize Bazel builds for large-scale monorepos. Use when configuring Bazel, implementing remote execution, or optimizing build performance for enterprise codebases. |
| `benchling-integration` | 提示型 | 4 | `codebuddy-plugins-official` | Benchling R&D platform integration. Access registry (DNA, proteins), inventory, ELN entries, workflows via API, build Benchling Apps, query Data Warehouse, for lab data management  |
| `bgm-library` | 代码型 | 6 | `cb_teams_marketplace` | Search, filter, and download royalty-free background music from ccMixter for Remotion videos. Supports keyword search, tag presets, license filtering (CC BY / CC BY-SA only), and a |
| `billing-automation` | 提示型 | 1 | `codebuddy-plugins-official` | Build automated billing systems for recurring payments, invoicing, subscription lifecycle, and dunning management. Use when implementing subscription billing, automating invoicing, |
| `biomni` | 代码型 | 6 | `codebuddy-plugins-official` | Autonomous biomedical AI agent framework for executing complex research tasks across genomics, drug discovery, molecular biology, and clinical analysis. Use this skill when conduct |
| `biopython` | 提示型 | 8 | `codebuddy-plugins-official` | Comprehensive molecular biology toolkit. Use for sequence manipulation, file parsing (FASTA/GenBank/PDB), phylogenetics, and programmatic NCBI/PubMed access (Bio.Entrez). Best for  |
| `biorxiv-database` | 代码型 | 3 | `codebuddy-plugins-official` | Efficient database search tool for bioRxiv preprint server. Use this skill when searching for life sciences preprints by keywords, authors, date ranges, or categories, retrieving p |
| `bioservices` | 代码型 | 8 | `codebuddy-plugins-official` | Unified Python interface to 40+ bioinformatics services. Use when querying multiple databases (UniProt, KEGG, ChEMBL, Reactome) in a single workflow with consistent API. Best for c |
| `blogwatcher` | 提示型 | 1 | `codebuddy-plugins-official` | Monitor blogs and RSS/Atom feeds for updates using the blogwatcher CLI. |
| `bond-futures-basis` | 提示型 | 1 | `cb_teams_marketplace` | Analyze the bond futures basis by pricing futures, identifying the cheapest-to-deliver, and comparing with yield curves to assess delivery option value and basis trading opportunit |
| `bond-relative-value` | 提示型 | 1 | `cb_teams_marketplace` | Perform relative value analysis on bonds by combining pricing, yield curve context, credit spreads, and scenario stress testing. Use when analyzing bond richness/cheapness, computi |
| `brainstorming` | 提示型 | 1 | `codebuddy-plugins-official` | You MUST use this before any creative work - creating features, building components, adding functionality, or modifying behavior. Explores user intent, requirements and design befo |
| `brand-guidelines` | 提示型 | 3 | `codebuddy-plugins-official` | Applies Anthropic's official brand colors and typography to any sort of artifact that may benefit from having Anthropic's look-and-feel. Use it when brand colors or style guideline |
| `brenda-database` | 代码型 | 5 | `codebuddy-plugins-official` | Access BRENDA enzyme database via SOAP API. Retrieve kinetic parameters (Km, kcat), reaction equations, organism data, and substrate-specific enzyme information for biochemical res |
| `browser` | 代码型 | 9 | `codebuddy-plugins-official` | This skill should be used for browser automation tasks using Chrome DevTools Protocol (CDP). Triggers when users need to launch Chrome with remote debugging, navigate pages, execut |
| `browsing` | 提示型 | 16 | `codebuddy-plugins-official` | Use when you need direct browser control - teaches Chrome DevTools Protocol for controlling existing browser sessions, multi-tab management, form automation, and content extraction |
| `bubble-detection` | 提示型 | 1 | `cb_teams_marketplace` | 用于反身性与预期泡沫识别，聚焦市场行为、预期管理、风险识别、高阶交易研究。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想判断一个热门板块或热门个股是否已经进入"预期自我强化"的泡沫阶段，什么时候从基本面交易转向预期交易，再转向兑现与反噬。 |
| `buddy-multimodal-generation` | 代码型 | 3 | `workbuddy-builtin` | > |
| `build-pipeline` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `business-copy-expert` | 提示型 | 12 | `workbuddy-builtin` | \| |
| `buyer-list` | 提示型 | 1 | `cb_teams_marketplace` | Build and organize a universe of potential acquirers for sell-side M&A processes. Identifies strategic and financial buyers, assesses fit, and prioritizes outreach. Use when prepar |
| `camera-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `canvas-design` | 提示型 | 84 | `codebuddy-plugins-official` | Create beautiful visual art in .png and .pdf documents using design philosophy. You should use this skill when the user asks to create a poster, piece of art, design, or other stat |
| `catalyst-calendar` | 提示型 | 1 | `cb_teams_marketplace` | Build and maintain a calendar of upcoming catalysts across a coverage universe — earnings dates, conferences, product launches, regulatory decisions, and macro events. Helps priori |
| `cellxgene-census` | 提示型 | 3 | `codebuddy-plugins-official` | Query the CELLxGENE Census (61M+ cells) programmatically. Use when you need expression data across tissues, diseases, or cell types from the largest curated single-cell atlas. Best |
| `changelog-automation` | 提示型 | 1 | `codebuddy-plugins-official` | Automate changelog generation from commits, PRs, and releases following Keep a Changelog format. Use when setting up release workflows, generating release notes, or standardizing c |
| `changelog-generator` | 提示型 | 2 | `codebuddy-plugins-official` | Automatically creates user-facing changelogs from git commits by analyzing commit history, categorizing changes, and transforming technical commits into clear, customer-friendly re |
| `check-deck` | 代码型 | 4 | `cb_teams_marketplace` | \| |
| `check-model` | 提示型 | 1 | `cb_teams_marketplace` | Debug and audit financial models for errors — circular references, broken formulas, hardcoded overrides, balance sheet imbalances, cash flow mismatches, and logic gaps. Use when a  |
| `chembl-database` | 代码型 | 3 | `codebuddy-plugins-official` | Query ChEMBL bioactive molecules and drug discovery data. Search compounds by structure/properties, retrieve bioactivity data (IC50, Ki), find inhibitors, perform SAR studies, for  |
| `cim-builder` | 提示型 | 1 | `cb_teams_marketplace` | Structure and draft a Confidential Information Memorandum for sell-side M&A processes. Organizes company information into a professional, investor-ready document with consistent fo |
| `cirq` | 提示型 | 7 | `codebuddy-plugins-official` | Google quantum computing framework. Use when targeting Google Quantum AI hardware, designing noise-aware circuits, or running quantum characterization experiments. Best for Google  |
| `citation-management` | 代码型 | 14 | `codebuddy-plugins-official` | Comprehensive citation management for academic research. Search Google Scholar and PubMed for papers, extract accurate metadata, validate citations, and generate properly formatted |
| `client-report` | 提示型 | 1 | `cb_teams_marketplace` | Generate professional client-facing performance reports with portfolio returns, allocation breakdowns, and market commentary. Suitable for quarterly or annual distribution. Trigger |
| `client-review` | 提示型 | 1 | `cb_teams_marketplace` | Prepare for client review meetings with portfolio performance summary, allocation analysis, talking points, and action items. Pulls together account data into a concise meeting-rea |
| `clinical-decision-support` | 代码型 | 20 | `codebuddy-plugins-official` | Generate professional clinical decision support (CDS) documents for pharmaceutical and clinical research settings, including patient cohort analyses (biomarker-stratified with outc |
| `clinical-reports` | 代码型 | 30 | `codebuddy-plugins-official` | Write comprehensive clinical reports including case reports (CARE guidelines), diagnostic reports (radiology/pathology/lab), clinical trial reports (ICH-E3, SAE, CSR), and patient  |
| `clinicaltrials-database` | 代码型 | 3 | `codebuddy-plugins-official` | Query ClinicalTrials.gov via API v2. Search trials by condition, drug, location, status, or phase. Retrieve trial details by NCT ID, export data, for clinical research and patient  |
| `clinpgx-database` | 代码型 | 3 | `codebuddy-plugins-official` | Access ClinPGx pharmacogenomics data (successor to PharmGKB). Query gene-drug interactions, CPIC guidelines, allele functions, for precision medicine and genotype-guided dosing dec |
| `clinvar-database` | 提示型 | 4 | `codebuddy-plugins-official` | Query NCBI ClinVar for variant clinical significance. Search by gene/position, interpret pathogenicity classifications, access via E-utilities API or FTP, annotate VCFs, for genomi |
| `close-management` | 提示型 | 1 | `cb_teams_marketplace` | Manage the month-end close process with task sequencing, dependencies, and status tracking. Use when planning the close calendar, tracking close progress, identifying blockers, or  |
| `cloud-functions` | 提示型 | 1 | `codebuddy-plugins-official` | Complete guide for CloudBase cloud functions development - supports both Event Functions (Node.js) and HTTP Functions (multi-language Web services). Covers runtime selection, deplo |
| `cloud-storage-web` | 提示型 | 1 | `codebuddy-plugins-official` | Complete guide for CloudBase cloud storage using Web SDK (@cloudbase/js-sdk) - upload, download, temporary URLs, file management, and best practices. |
| `cloudbase` | 提示型 | 42 | `codebuddy-plugins-official` | CloudBase AI Development - Complete toolkit for building Web, Mini Program, and Native App projects with CloudBase. Includes authentication, database (NoSQL/MySQL), cloud functions |
| `cloudbase-agent-ts` | 提示型 | 8 | `codebuddy-plugins-official` | Build and deploy AI agents with Cloudbase Agent (TypeScript), a TypeScript SDK implementing the AG-UI protocol. Use when: (1) deploying agent servers with @cloudbase/agent-server,  |
| `cloudbase-platform` | 提示型 | 1 | `codebuddy-plugins-official` | CloudBase platform knowledge and best practices. Use this skill for general CloudBase platform understanding, including storage, hosting, authentication, cloud functions, database  |
| `cloudrun-development` | 提示型 | 1 | `codebuddy-plugins-official` | CloudBase Run backend development rules (Function mode/Container mode). Use this skill when deploying backend services that require long connections, multi-language support, custom |
| `cloudstudio-deploy` | 代码型 | 4 | `workbuddy-builtin` | Deploy static sites to CloudStudio sandbox workspaces or take published sites offline. This skill should be used when users want to deploy a local build directory (e.g. dist/, buil |
| `cobrapy` | 提示型 | 3 | `codebuddy-plugins-official` | Constraint-based metabolic modeling (COBRA). FBA, FVA, gene knockouts, flux sampling, SBML models, for systems biology and metabolic engineering analysis. |
| `code-generator` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `code-review-excellence` | 提示型 | 1 | `codebuddy-plugins-official` | Master effective code review practices to provide constructive feedback, catch bugs early, and foster knowledge sharing while maintaining team morale. Use when reviewing pull reque |
| `codebuddy-md-improver` | 提示型 | 4 | `codebuddy-plugins-official` | Audit and improve CODEBUDDY.md files in repositories. Use when user asks to check, audit, update, improve, or fix CODEBUDDY.md files. Scans for all CODEBUDDY.md files, evaluates qu |
| `codex` | 提示型 | 1 | `codebuddy-plugins-official` | Execute Codex CLI for code analysis, refactoring, and automated code changes. Use when you need to delegate complex code tasks to Codex AI with file references (@syntax) and struct |
| `color-curator` | 提示型 | 2 | `codebuddy-plugins-official` | Browse and select color palettes from Coolors or curated fallbacks. Use to find the perfect color palette for a design project. |
| `command-development` | 提示型 | 11 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create a slash command", "add a command", "write a custom command", "define command arguments", "use command frontmatter", "organiz |
| `company-quality` | 提示型 | 1 | `cb_teams_marketplace` | 用于公司质地打分，聚焦基本面研究/公司质量评估/长线选股。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户希望对公司"质地"有一个结构化判断：是不是好公司，壁垒强不强，成长质量怎么样，治理怎么样，值不值得长期跟踪。 |
| `competitive-ads-extractor` | 提示型 | 2 | `codebuddy-plugins-official` | Extracts and analyzes competitors' ads from ad libraries (Facebook, LinkedIn, etc.) to understand what messaging, problems, and creative approaches are working. Helps inspire and i |
| `competitive-analysis` | 提示型 | 3 | `cb_teams_marketplace` | Framework for competitive landscape analysis across any industry. Use when creating competitor analysis, market positioning assessments, investment memos, strategic reviews, or any |
| `competitive-analysis` | 提示型 | 1 | `cb_teams_marketplace` | Analyze competitors with feature comparison matrices, positioning analysis, and strategic implications. Use when researching a competitor, comparing product capabilities, assessing |
| `competitive-landscape` | 提示型 | 1 | `codebuddy-plugins-official` | This skill should be used when the user asks to "analyze competitors", "assess competitive landscape", "identify differentiation", "evaluate market positioning", "apply Porter's Fi |
| `comps-analysis` | 提示型 | 1 | `cb_teams_marketplace` | \| |
| `config-generator` | 提示型 | 2 | `codebuddy-plugins-official` | > |
| `connector-github` | 提示型 | 1 | `connectors` | Use github connector to access github MCP capabilities via github mcp server. |
| `connector-qq-mail` | 提示型 | 1 | `connectors` | QQ邮箱(QQ Mail)全功能操作技能。触发场景：看邮箱、查邮件、收件箱、看看邮件、有没有新邮件、未读邮件、帮我看看邮箱、打开邮箱、最近的邮件、邮件列表、发邮件、写邮件、发一封邮件、回复邮件、转发邮件、删除邮件、搜邮件、找邮件、搜索邮箱、下载附件、邮件附件、check email、inbox、send email、reply、forward、search  |
| `connector-tmeet` | 提示型 | 6 | `connectors` | 腾讯会议 CLI（tmeet）：OAuth 授权登录/登出/状态查询、会议管理（创建/更新/取消/查询/受邀者）、录制管理（列表/下载地址/智能纪要/转写）、会议报告（参会人/等候室）、问题排查（导出本地日志，反馈工具缺失/失败/能力不足等问题给平台）。当用户需要通过命令行操作腾讯会议，或 Agent 在使用过程中遇到工具缺失、调用失败、能力不足等情况想反馈 |
| `content-generation` | 提示型 | 1 | `codebuddy-plugins-official` | 当用户需要撰写PPT演讲稿、生成演示大纲、组织演讲逻辑或丰富PPT内容时自动激活 |
| `content-research-writer` | 提示型 | 2 | `codebuddy-plugins-official` | Assists in writing high-quality content by conducting research, adding citations, improving hooks, iterating on outlines, and providing real-time feedback on each section. Transfor |
| `context-driven-development` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when working with Conductor's context-driven development methodology, managing project context artifacts, or understanding the relationship between product.md, tech- |
| `cosmic-database` | 代码型 | 3 | `codebuddy-plugins-official` | Access COSMIC cancer mutation database. Query somatic mutations, Cancer Gene Census, mutational signatures, gene fusions, for cancer research and precision oncology. Requires authe |
| `cost-optimization` | 提示型 | 1 | `codebuddy-plugins-official` | Optimize cloud costs through resource rightsizing, tagging strategies, reserved instances, and spending analysis. Use when reducing cloud expenses, analyzing infrastructure costs,  |
| `cqrs-implementation` | 提示型 | 1 | `codebuddy-plugins-official` | Implement Command Query Responsibility Segregation for scalable architectures. Use when separating read and write models, optimizing query performance, or building event-sourced sy |
| `dask` | 提示型 | 7 | `codebuddy-plugins-official` | Distributed computing for larger-than-RAM pandas/NumPy workflows. Use when you need to scale existing pandas/NumPy code beyond memory or across clusters. Best for parallel file pro |
| `data-analysis-workflows` | 提示型 | 1 | `cb_teams_marketplace` | > |
| `data-context-extractor` | 代码型 | 6 | `cb_teams_marketplace` | > |
| `data-exploration` | 提示型 | 1 | `cb_teams_marketplace` | Profile and explore datasets to understand their shape, quality, and patterns before analysis. Use when encountering a new dataset, assessing data quality, discovering column distr |
| `data-model-creation` | 提示型 | 1 | `codebuddy-plugins-official` | Optional advanced tool for complex data modeling. For simple table creation, use relational-database-tool directly with SQL statements. |
| `data-quality-frameworks` | 提示型 | 1 | `codebuddy-plugins-official` | Implement data quality validation with Great Expectations, dbt tests, and data contracts. Use when building data quality pipelines, implementing validation rules, or establishing d |
| `data-storytelling` | 提示型 | 1 | `codebuddy-plugins-official` | Transform data into compelling narratives using visualization, context, and persuasive structure. Use when presenting analytics to stakeholders, creating data reports, or building  |
| `data-validation` | 提示型 | 1 | `cb_teams_marketplace` | QA an analysis before sharing with stakeholders — methodology checks, accuracy verification, and bias detection. Use when reviewing an analysis for errors, checking for survivorshi |
| `data-visualization` | 提示型 | 1 | `cb_teams_marketplace` | Create effective data visualizations with Python. 优先使用 plotly（交互式图表），seaborn 和 matplotlib 作为备选（静态图表）。Use when building charts, choosing the right chart type for a dataset, creating |
| `database-migration` | 提示型 | 1 | `codebuddy-plugins-official` | Execute database migrations across ORMs and platforms with zero-downtime strategies, data transformation, and rollback procedures. Use when migrating databases, changing schemas, p |
| `datacommons-client` | 提示型 | 5 | `codebuddy-plugins-official` | Work with Data Commons, a platform providing programmatic access to public statistical data from global sources. Use this skill when working with demographic data, economic indicat |
| `datamol` | 提示型 | 7 | `codebuddy-plugins-official` | Pythonic wrapper around RDKit with simplified interface and sensible defaults. Preferred for standard drug discovery including SMILES parsing, standardization, descriptors, fingerp |
| `datapack-builder` | 提示型 | 1 | `cb_teams_marketplace` | Build professional financial services data packs from various sources including CIMs, offering memorandums, SEC filings, web search, or MCP servers. Extract, normalize, and standar |
| `dbt-transformation-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master dbt (data build tool) for analytics engineering with model organization, testing, documentation, and incremental strategies. Use when building data transformations, creating |
| `dcf-model` | 代码型 | 4 | `cb_teams_marketplace` | Real DCF (Discounted Cash Flow) model creation for equity valuation. Retrieves financial data from SEC filings and analyst reports, builds comprehensive cash flow projections with  |
| `dd-checklist` | 提示型 | 1 | `cb_teams_marketplace` | Generate and track comprehensive due diligence checklists tailored to the target company's sector, deal type, and complexity. Covers all major workstreams with request lists, statu |
| `dd-meeting-prep` | 提示型 | 1 | `cb_teams_marketplace` | Prepare for due diligence meetings — management presentations, expert network calls, customer references, and advisor sessions. Generates targeted question lists, benchmarks to ref |
| `deal-screening` | 提示型 | 1 | `cb_teams_marketplace` | Quickly screen inbound deal flow — CIMs, teasers, and broker materials — against the fund's investment criteria. Extracts key deal metrics, runs a pass/fail framework, and outputs  |
| `deal-sourcing` | 提示型 | 1 | `cb_teams_marketplace` | PE deal sourcing workflow — discover target companies, check CRM for existing relationships, and draft personalized founder outreach emails. Use when sourcing new deals, prospectin |
| `deal-tracker` | 提示型 | 1 | `cb_teams_marketplace` | Track multiple live deals with milestones, deadlines, action items, and status updates. Maintains a deal pipeline view and surfaces upcoming deadlines and overdue items. Use when m |
| `debugging-strategies` | 提示型 | 1 | `codebuddy-plugins-official` | Master systematic debugging techniques, profiling tools, and root cause analysis to efficiently track down bugs across any codebase or technology stack. Use when investigating bugs |
| `deep-research` | 提示型 | 3 | `codebuddy-plugins-official` | Complete research workflow system for codebase analysis, deep external research, and comprehensive technical wiki generation |
| `deepchem` | 代码型 | 6 | `codebuddy-plugins-official` | Molecular ML with diverse featurizers and pre-built datasets. Use for property prediction (ADMET, toxicity) with traditional ML or GNNs when you want extensive featurization option |
| `deeptools` | 代码型 | 8 | `codebuddy-plugins-official` | NGS analysis toolkit. BAM to bigWig conversion, QC (correlation, PCA, fingerprints), heatmaps/profiles (TSS, peaks), for ChIP-seq, RNA-seq, ATAC-seq visualization. |
| `defi-protocol-templates` | 提示型 | 1 | `codebuddy-plugins-official` | Implement DeFi protocols with production-ready templates for staking, AMMs, governance, and lending systems. Use when building decentralized finance applications or smart contract  |
| `denario` | 提示型 | 5 | `codebuddy-plugins-official` | Multiagent AI system for scientific research assistance that automates research workflows from data analysis to publication. This skill should be used when generating research idea |
| `dependency-upgrade` | 提示型 | 1 | `codebuddy-plugins-official` | Manage major dependency version upgrades with compatibility analysis, staged rollout, and comprehensive testing. Use when upgrading framework versions, updating major dependencies, |
| `deployment-pipeline-design` | 提示型 | 1 | `codebuddy-plugins-official` | Design multi-stage CI/CD pipelines with approval gates, security checks, and deployment orchestration. Use when architecting deployment workflows, setting up continuous delivery, o |
| `design-critique` | 提示型 | 1 | `cb_teams_marketplace` | Get structured design feedback on usability, hierarchy, and consistency. Trigger with "review this design", "critique this mockup", "what do you think of this screen?", or when sha |
| `design-handoff` | 提示型 | 1 | `cb_teams_marketplace` | Generate developer handoff specs from a design. Use when a design is ready for engineering and needs a spec sheet covering layout, design tokens, component props, interaction state |
| `design-system` | 提示型 | 1 | `cb_teams_marketplace` | Audit, document, or extend your design system. Use when checking for naming inconsistencies or hardcoded values across components, writing documentation for a component's variants, |
| `design-to-code-workflows` | 提示型 | 1 | `cb_teams_marketplace` | 将 Figma 设计和截图转换为生产就绪的代码组件，内置无障碍性支持 |
| `design-token` | 代码型 | 16 | `workbuddy-builtin` | \| |
| `design-wizard` | 提示型 | 5 | `codebuddy-plugins-official` | Interactive design wizard that guides through a complete frontend design process with discovery, aesthetic selection, and code generation. Use for creating distinctive, production- |
| `developer-growth-analysis` | 提示型 | 2 | `codebuddy-plugins-official` | Analyzes your recent Claude Code chat history to identify coding patterns, development gaps, and areas for improvement, curates relevant learning resources from HackerNews, and aut |
| `diffdock` | 代码型 | 9 | `codebuddy-plugins-official` | Diffusion-based molecular docking. Predict protein-ligand binding poses from PDB/SMILES, confidence scores, virtual screening, for structure-based drug design. Not for affinity pre |
| `dispatching-parallel-agents` | 提示型 | 1 | `codebuddy-plugins-official` | Use when facing 2+ independent tasks that can be worked on without shared state or sequential dependencies |
| `distributed-tracing` | 提示型 | 1 | `codebuddy-plugins-official` | Implement distributed tracing with Jaeger and Tempo to track requests across microservices and identify performance bottlenecks. Use when debugging microservices, analyzing request |
| `dividend-returns` | 提示型 | 1 | `cb_teams_marketplace` | 用于分红与股东回报分析，聚焦股东回报、价值投资、资本配置、长线研究。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想知道一家公司分红高不高、是否稳定、是不是"真红利"，以及公司整体资本配置是否尊重股东回报。 |
| `dnanexus-integration` | 提示型 | 6 | `codebuddy-plugins-official` | DNAnexus cloud genomics platform. Build apps/applets, manage data (upload/download), dxpy Python SDK, run workflows, FASTQ/BAM/VCF, for genomics pipeline development and execution. |
| `doc-coauthoring` | 提示型 | 2 | `codebuddy-plugins-official` | Guide users through a structured workflow for co-authoring documentation. Use when user wants to write documentation, proposals, technical specs, decision docs, or similar structur |
| `doc-typeset` | 提示型 | 21 | `workbuddy-builtin` | \| |
| `docx` | 代码型 | 62 | `codebuddy-plugins-official` | Use this skill whenever the user wants to create, read, edit, or manipulate Word documents (.docx files). Triggers include: any mention of 'Word doc', 'word document', '.docx', or  |
| `domain-name-brainstormer` | 提示型 | 2 | `codebuddy-plugins-official` | Generates creative domain name ideas for your project and checks availability across multiple TLDs (.com, .io, .dev, .ai, etc.). Saves hours of brainstorming and manual checking. |
| `drugbank-database` | 代码型 | 7 | `codebuddy-plugins-official` | Access and analyze comprehensive drug information from the DrugBank database including drug properties, interactions, targets, pathways, chemical structures, and pharmacology data. |
| `e2e-testing-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master end-to-end testing with Playwright and Cypress to build reliable test suites that catch bugs, improve confidence, and enable fast deployment. Use when implementing E2E tests |
| `earnings-analysis` | 提示型 | 4 | `cb_teams_marketplace` | Create professional equity research earnings update reports (8-12 pages, 3,000-5,000 words) analyzing quarterly results for companies already under coverage. Fast-turnaround format |
| `earnings-preview` | 提示型 | 1 | `cb_teams_marketplace` | Build pre-earnings analysis with estimate models, scenario frameworks, and key metrics to watch. Use before a company reports quarterly earnings to prepare positioning notes, set u |
| `earnings-preview-beta` | 提示型 | 3 | `cb_teams_marketplace` | Generate a concise 4-5 page equity research earnings preview for a single company. Analyzes the most recent earnings transcript, competitor landscape, valuation, and recent news to |
| `embedding-strategies` | 提示型 | 1 | `codebuddy-plugins-official` | Select and optimize embedding models for semantic search and RAG applications. Use when choosing embedding models, implementing chunking strategies, or optimizing embedding quality |
| `employment-contract-templates` | 提示型 | 1 | `codebuddy-plugins-official` | Create employment contracts, offer letters, and HR policy documents following legal best practices. Use when drafting employment agreements, creating HR policies, or standardizing  |
| `ena-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access European Nucleotide Archive via API/FTP. Retrieve DNA/RNA sequences, raw reads (FASTQ), genome assemblies by accession, for genomics and bioinformatics pipelines. Supports m |
| `ensembl-database` | 代码型 | 3 | `codebuddy-plugins-official` | Query Ensembl genome database REST API for 250+ species. Gene lookups, sequence retrieval, variant analysis, comparative genomics, orthologs, VEP predictions, for genomic research. |
| `environment-setup` | 提示型 | 1 | `cb_teams_marketplace` | Automatically detects and configures the Remotion video generation environment. Use when user requests video creation and dependencies (Node.js, FFmpeg, Remotion packages) need ver |
| `equity-research` | 提示型 | 1 | `cb_teams_marketplace` | Generate comprehensive equity research snapshots combining analyst consensus estimates, company fundamentals, historical prices, and macroeconomic context. Use when researching sto |
| `error-handling-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master error handling patterns across languages including exceptions, Result types, error propagation, and graceful degradation to build resilient applications. Use when implementi |
| `esm` | 提示型 | 5 | `codebuddy-plugins-official` | Comprehensive toolkit for protein language models including ESM3 (generative multimodal protein design across sequence, structure, and function) and ESM C (efficient protein embedd |
| `etetoolkit` | 代码型 | 6 | `codebuddy-plugins-official` | Phylogenetic tree toolkit (ETE). Tree manipulation (Newick/NHX), evolutionary event detection, orthology/paralogy, NCBI taxonomy, visualization (PDF/SVG), for phylogenomics. |
| `event-store-design` | 提示型 | 1 | `codebuddy-plugins-official` | Design and implement event stores for event-sourced systems. Use when building event sourcing infrastructure, choosing event store technologies, or implementing event persistence p |
| `excel-generation` | 代码型 | 5 | `workbuddy-builtin` | > |
| `excel-generation` | 代码型 | 5 | `cb_teams_marketplace` | > |
| `excel-handler` | 提示型 | 1 | `workbuddy-builtin` | > |
| `excel-handler` | 提示型 | 1 | `cb_teams_marketplace` | > |
| `executing-marketing-campaigns` | 代码型 | 15 | `cb_teams_marketplace` | Plans, creates, and optimizes marketing campaigns including content strategy, social media, email, and analytics. Helps develop go-to-market strategies, campaign messaging, and per |
| `executing-plans` | 提示型 | 1 | `codebuddy-plugins-official` | Use when you have a written implementation plan to execute in a separate session with review checkpoints |
| `expert-manager` | 代码型 | 13 | `workbuddy-builtin` | \| |
| `exploratory-data-analysis` | 代码型 | 9 | `codebuddy-plugins-official` | Perform comprehensive exploratory data analysis on scientific data files across 200+ file formats. This skill should be used when analyzing any scientific data file to understand i |
| `external-api` | 提示型 | 2 | `codebuddy-plugins-official` | > |
| `fastapi-templates` | 提示型 | 1 | `codebuddy-plugins-official` | Create production-ready FastAPI projects with async patterns, dependency injection, and comprehensive error handling. Use when building new FastAPI applications or setting up backe |
| `fda-database` | 代码型 | 9 | `codebuddy-plugins-official` | Query openFDA API for drugs, devices, adverse events, recalls, regulatory submissions (510k, PMA), substance identification (UNII), for FDA regulatory data analysis and safety rese |
| `feature-spec` | 提示型 | 1 | `cb_teams_marketplace` | Write structured product requirements documents (PRDs) with problem statements, user stories, requirements, and success metrics. Use when speccing a new feature, writing a PRD, def |
| `file-manager` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `file-organizer` | 提示型 | 1 | `codebuddy-plugins-official` | Intelligently organizes your files and folders across your computer by understanding context, finding duplicates, suggesting better structures, and automating cleanup tasks. Reduce |
| `finance-workflows` | 提示型 | 1 | `cb_teams_marketplace` | Comprehensive finance workflows including income statements, journal entries, reconciliations, SOX testing, and variance analysis |
| `financial-plan` | 提示型 | 1 | `cb_teams_marketplace` | Build or update a comprehensive financial plan covering retirement projections, education funding, estate planning, and cash flow analysis. Use for new client onboarding, annual pl |
| `financial-report` | 提示型 | 1 | `cb_teams_marketplace` | 用于公告影响力与财报质量分析，聚焦公告解读/财报分析/基本面验证。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户上传或粘贴公告、年报、季报、业绩预告，想快速知道：到底有没有用，对股价意味着什么。 |
| `financial-statements` | 提示型 | 1 | `cb_teams_marketplace` | Generate income statements, balance sheets, and cash flow statements with GAAP presentation and period-over-period comparison. Use when preparing financial statements, running flux |
| `find-skills` | 提示型 | 1 | `codebuddy-plugins-official` | Helps users discover and install agent skills when they ask questions like "how do I do X", "find a skill for X", "is there a skill that can...", or express interest in extending c |
| `find-skills` | 提示型 | 1 | `cb_teams_marketplace` | Helps users discover and install agent skills when they ask questions like "how do I do X", "find a skill for X", "is there a skill that can...", or express interest in extending c |
| `finishing-a-development-branch` | 提示型 | 1 | `codebuddy-plugins-official` | Use when implementation is complete, all tests pass, and you need to decide how to integrate the work - guides completion of development work by presenting structured options for m |
| `fixed-income-portfolio` | 提示型 | 1 | `cb_teams_marketplace` | Review fixed income portfolios by pricing multiple bonds, retrieving reference data, analyzing cashflows, and running scenario analysis. Use when reviewing bond portfolios, computi |
| `flowio` | 提示型 | 2 | `codebuddy-plugins-official` | Parse FCS (Flow Cytometry Standard) files v2.0-3.1. Extract events as NumPy arrays, read metadata/channels, convert to CSV/DataFrame, for flow cytometry data preprocessing. |
| `fluidsim` | 提示型 | 7 | `codebuddy-plugins-official` | Framework for computational fluid dynamics simulations using Python. Use when running fluid dynamics simulations including Navier-Stokes equations (2D/3D), shallow water equations, |
| `format-extract` | 提示型 | 4 | `workbuddy-builtin` | > |
| `frontend-design` | 提示型 | 3 | `codebuddy-plugins-official` | Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, artifacts, posters, or applicat |
| `frontend-design` | 提示型 | 2 | `cb_teams_marketplace` | Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, artifacts, posters, or applicat |
| `fund-crowding` | 提示型 | 1 | `cb_teams_marketplace` | 用于基金重仓股拥挤度分析，聚焦机构行为、拥挤交易、风险管理、组合研究。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想判断某只基金重仓股到底是"机构共识优质资产"，还是"已经过度拥挤、稍有不及预期就容易踩踏"的标的。 |
| `funding-digest` | 提示型 | 3 | `cb_teams_marketplace` | Generate a polished one-page PowerPoint slide summarizing key takeaways from recent funding rounds and notable capital markets activity across a user's watched sectors or companies |
| `fx-carry-trade` | 提示型 | 1 | `cb_teams_marketplace` | Evaluate FX carry trade opportunities by combining spot rates, forward points, interest rate differentials, volatility surface analysis, and historical price trends. Use when analy |
| `game-planning` | 提示型 | 5 | `codebuddy-plugins-official` | > |
| `gameplay-design` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `gaokao-search` | 代码型 | 4 | `cb_teams_marketplace` | > |
| `gaokao-zhiyuan-assistant` | 提示型 | 9 | `cb_teams_marketplace` | 高考志愿填报的逐步引导助手，帮用户梳理出最适合自己的志愿填报名单。通过对话分阶段进行：收集个人信息与选科，解读感兴趣的专业，探讨城市与院校，产出带“冲稳保”的候选志愿草表，最终生成可直接对照官方系统填报的志愿表与报告；全程产物沉淀为腾讯文档。只要用户提到高考、报志愿、填志愿、选专业、选大学、冲稳保、平行志愿、选科能报什么专业、想去哪个城市或哪所大学等相关话题 |
| `gdpr-data-handling` | 提示型 | 1 | `codebuddy-plugins-official` | Implement GDPR-compliant data handling with consent management, data subject rights, and privacy by design. Use when building systems that process EU personal data, implementing pr |
| `gdscript-codegen` | 提示型 | 1 | `codebuddy-plugins-official` | AI 生成高质量 GDScript 代码的规范和模板。当用户要求生成、修改或审查 GDScript 代码时使用此 Skill。涵盖 Godot 4.x 类型系统、信号声明、导出变量、代码模板和最佳实践。 |
| `gemini` | 代码型 | 2 | `codebuddy-plugins-official` | Execute Gemini CLI for AI-powered code analysis and generation. Use when you need to leverage Google's Gemini models for complex reasoning tasks. |
| `gene-database` | 代码型 | 6 | `codebuddy-plugins-official` | Query NCBI Gene via E-utilities/Datasets API. Search by symbol/ID, retrieve gene info (RefSeqs, GO, locations, phenotypes), batch lookups, for gene annotation and functional analys |
| `general-writer` | 代码型 | 5 | `workbuddy-builtin` | L1 通用写作兜底专家。覆盖公文、周报、方案、邮件、文案、散文、新媒体稿件等场景，采用 7 维质量评分框架（事实/逻辑/结构/语言/风格/受众/洞察）与 10 种文体适配矩阵。当 L0 路由未命中任何 L2 专家时作为兜底触发。适用于没有特定领域严格规范的通用写作任务。 |
| `generate-fillable-contract-html` | 提示型 | 1 | `workbuddy-builtin` | 生成适于 HTML 转 DOCX 的中文待填合同、报价单和授权委托书 HTML。用户要求创建待填业务文档模板、合同填空或可按书签填写的 HTML 时使用。 |
| `generate-image` | 代码型 | 2 | `codebuddy-plugins-official` | Generate or edit images using AI models (FLUX, Gemini). Use for general-purpose image generation including photos, illustrations, artwork, visual assets, concept art, and any image |
| `geniml` | 提示型 | 6 | `codebuddy-plugins-official` | This skill should be used when working with genomic interval data (BED files) for machine learning tasks. Use for training region embeddings (Region2Vec, BEDspace), single-cell ATA |
| `geo-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access NCBI GEO for gene expression/genomics data. Search/download microarray and RNA-seq datasets (GSE, GSM, GPL), retrieve SOFT/Matrix files, for transcriptomics and expression a |
| `geo-map-compliance-guard` | 提示型 | 2 | `workbuddy-builtin` | > |
| `geopandas` | 提示型 | 7 | `codebuddy-plugins-official` | Python library for working with geospatial vector data including shapefiles, GeoJSON, and GeoPackage files. Use when working with geographic data for spatial analysis, geometric op |
| `get-available-resources` | 代码型 | 2 | `codebuddy-plugins-official` | This skill should be used at the start of any computationally intensive scientific task to detect and report available system resources (CPU cores, GPUs, memory, disk space). It cr |
| `gget` | 代码型 | 7 | `codebuddy-plugins-official` | gget |
| `gifgrep` | 提示型 | 1 | `codebuddy-plugins-official` | Search GIF providers with CLI/TUI, download results, and extract stills/sheets. |
| `git-advanced-workflows` | 提示型 | 1 | `codebuddy-plugins-official` | Master advanced Git workflows including rebasing, cherry-picking, bisect, worktrees, and reflog to maintain clean history and recover from any situation. Use when managing complex  |
| `github` | 提示型 | 1 | `codebuddy-plugins-official` | Interact with GitHub using the `gh` CLI. Use `gh issue`, `gh pr`, `gh run`, and `gh api` for issues, PRs, CI runs, and advanced queries. |
| `github-actions-templates` | 提示型 | 1 | `codebuddy-plugins-official` | Create production-ready GitHub Actions workflows for automated testing, building, and deploying applications. Use when setting up CI/CD with GitHub Actions, automating development  |
| `gitlab-ci-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Build GitLab CI/CD pipelines with multi-stage workflows, caching, and distributed runners for scalable automation. Use when implementing GitLab CI/CD, optimizing pipeline performan |
| `gitops-workflow` | 提示型 | 3 | `codebuddy-plugins-official` | Implement GitOps workflows with ArgoCD and Flux for automated, declarative Kubernetes deployments with continuous reconciliation. Use when implementing GitOps practices, automating |
| `go-concurrency-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Go concurrency with goroutines, channels, sync primitives, and context. Use when building concurrent Go applications, implementing worker pools, or debugging race conditions |
| `godot-asset-path-surgery` | 提示型 | 1 | `codebuddy-plugins-official` | Fix stale absolute paths baked inside Godot binary resources (.mesh / .material / .scn / .res / .tres) after a folder rename, migration, or Phase-3-style restructure. Use this skil |
| `godot-core` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `godot-data-driven-config` | 代码型 | 12 | `codebuddy-plugins-official` | Create or extend data-driven config tables (WeaponData, EnemyData, LevelData, etc.) in a Godot 4 project so that designers can tweak numbers in .tres files via natural language. Us |
| `godot-debug` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `godot-deploy` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `godot-dev` | 提示型 | 23 | `codebuddy-plugins-official` | > |
| `godot-gdscript-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Godot 4 GDScript patterns including signals, scenes, state machines, and optimization. Use when building Godot games, implementing game systems, or learning GDScript best pr |
| `godot-headless-verify` | 提示型 | 1 | `codebuddy-plugins-official` | Run Godot in headless mode to verify a project — quick load tests ("does this scene still instantiate?"), cache/UID cache repair ("editor shows red errors but game runs fine"), and |
| `godot-new` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `godot-tres-format` | 提示型 | 1 | `codebuddy-plugins-official` | Godot .tres 资源文件格式规范。让 AI 能够直接读写 Godot 资源文件（材质、环境、物理材质、渐变、曲线、样式盒、着色器、动画、粒子等）。当需要创建或修改 .tres 文件时使用此 Skill。 |
| `godot-tscn-format` | 提示型 | 1 | `codebuddy-plugins-official` | Godot .tscn 场景文件格式规范。让 AI 能够直接读写 Godot 场景文件，理解节点树结构、外部/内嵌资源引用、Transform 变换、信号连接等。当需要创建或修改 .tscn 文件时使用此 Skill。 |
| `godot-utils` | 提示型 | 1 | `codebuddy-plugins-official` | GDScript 工具函数库。提供常用的辅助函数，可直接复制到项目中使用，或通过 Autoload 全局访问。 |
| `gog` | 提示型 | 1 | `codebuddy-plugins-official` | Google Workspace CLI for Gmail, Calendar, Drive, Contacts, Sheets, and Docs. |
| `going-global` | 提示型 | 1 | `cb_teams_marketplace` | 用于出海链投资分析，聚焦全球化投资、制造业研究、行业比较优势、中长期成长。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户关注中国企业出海、海外扩张、全球份额提升时，希望知道公司出海是真成长还是概念故事，哪些环节最容易兑现，哪些有地缘、汇率、渠道、认证等风 |
| `grafana-dashboards` | 提示型 | 1 | `codebuddy-plugins-official` | Create and manage production Grafana dashboards for real-time visualization of system and application metrics. Use when building monitoring dashboards, visualizing metrics, or crea |
| `gtars` | 提示型 | 7 | `codebuddy-plugins-official` | High-performance toolkit for genomic interval analysis in Rust with Python bindings. Use when working with genomic regions, BED files, coverage tracks, overlap detection, tokenizat |
| `gwas-database` | 提示型 | 2 | `codebuddy-plugins-official` | Query NHGRI-EBI GWAS Catalog for SNP-trait associations. Search variants by rs ID, disease/trait, gene, retrieve p-values and summary statistics, for genetic epidemiology and polyg |
| `healthcheck` | 提示型 | 1 | `codebuddy-plugins-official` | Track water and sleep with JSON file storage |
| `helm-chart-scaffolding` | 代码型 | 5 | `codebuddy-plugins-official` | Design, organize, and manage Helm charts for templating and packaging Kubernetes applications with reusable configurations. Use when creating Helm charts, packaging Kubernetes appl |
| `himalaya` | 提示型 | 3 | `codebuddy-plugins-official` | CLI to manage emails via IMAP/SMTP. Use `himalaya` to list, read, write, reply, forward, search, and organize emails from the terminal. Supports multiple accounts and message compo |
| `histolab` | 提示型 | 6 | `codebuddy-plugins-official` | Lightweight WSI tile extraction and preprocessing. Use for basic slide processing tissue detection, tile extraction, stain normalization for H&E images. Best for simple pipelines,  |
| `hmdb-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access Human Metabolome Database (220K+ metabolites). Search by name/ID/structure, retrieve chemical properties, biomarker data, NMR/MS spectra, pathways, for metabolomics and iden |
| `hook-development` | 代码型 | 11 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create a hook", "add a PreToolUse/PostToolUse/Stop hook", "validate tool use", "implement prompt-based hooks", "use ${CODEBUDDY_PLU |
| `html-review` | 代码型 | 8 | `workbuddy-builtin` | \| |
| `html-to-docx` | 代码型 | 70 | `workbuddy-builtin` | \| |
| `http-api` | 提示型 | 1 | `codebuddy-plugins-official` | Use CloudBase HTTP API to access CloudBase platform features (database, authentication, cloud functions, cloud hosting, cloud storage, AI) via HTTP protocol from backends or script |
| `humanizer` | 提示型 | 2 | `workbuddy-builtin` | \| |
| `humanizer` | 提示型 | 2 | `codebuddy-plugins-official` | \| |
| `humanizer-zh` | 提示型 | 1 | `workbuddy-builtin` | \| |
| `hybrid-cloud-networking` | 提示型 | 1 | `codebuddy-plugins-official` | Configure secure, high-performance connectivity between on-premises infrastructure and cloud platforms using VPN and dedicated connections. Use when building hybrid cloud architect |
| `hybrid-search-implementation` | 提示型 | 1 | `codebuddy-plugins-official` | Combine vector and keyword search for improved retrieval. Use when implementing RAG systems, building search engines, or when neither approach alone provides sufficient recall. |
| `hypogenic` | 提示型 | 2 | `codebuddy-plugins-official` | Automated LLM-driven hypothesis generation and testing on tabular datasets. Use when you want to systematically explore hypotheses about patterns in empirical data (e.g., deception |
| `hypothesis-generation` | 提示型 | 7 | `codebuddy-plugins-official` | Structured hypothesis formulation from observations. Use when you have experimental observations or data and need to formulate testable hypotheses with predictions, propose mechani |
| `ic-memo` | 提示型 | 1 | `cb_teams_marketplace` | Draft a structured investment committee memo for PE deal approval. Synthesizes due diligence findings, financial analysis, and deal terms into a professional IC-ready document. Use |
| `idea-generation` | 提示型 | 1 | `cb_teams_marketplace` | Systematic stock screening and investment idea sourcing. Combines quantitative screens, thematic research, and pattern recognition to surface new long and short ideas. Use when loo |
| `ima-skills` | 提示型 | 5 | `skills` | — |
| `image-enhancer` | 提示型 | 2 | `codebuddy-plugins-official` | Improves the quality of images, especially screenshots, by enhancing resolution, sharpness, and clarity. Perfect for preparing images for presentations, documentation, or social me |
| `image-to-ui` | 提示型 | 1 | `cb_teams_marketplace` | 图生 UI（截图/设计稿 → 画布设计稿）。将参考图片转化为可编辑的 ardot 设计稿。四阶段流水线：设计风格提取 → 结构化精细描述 → 反思校验 → Agent Teams 画布绘制。触发场景：上传截图/线框图/草图要求生成设计稿、还原界面、复刻页面、参照图片设计。 |
| `image-understanding-native` | 提示型 | 6 | `cb_teams_marketplace` | 图片结构化语义分析。Agent 直接看图输出结构化 JSON，零外部依赖。四种分析任务：全页面结构分析、设计风格提取、区域语义描述、对比差异分析。 |
| `imsg` | 提示型 | 1 | `codebuddy-plugins-official` | iMessage/SMS CLI for listing chats, history, watch, and sending. |
| `incident-runbook-templates` | 提示型 | 1 | `codebuddy-plugins-official` | Create structured incident response runbooks with step-by-step procedures, escalation paths, and recovery actions. Use when building runbooks, responding to incidents, or establish |
| `industry-chain` | 提示型 | 1 | `cb_teams_marketplace` | 用于产业链映射，聚焦产业研究/主题投资/行业挖掘。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户输入一个行业趋势、技术方向、政策方向或事件，希望快速得到完整产业链结构、核心环节、最受益公司和映射逻辑。 |
| `init-cbc-sdk-web` | 提示型 | 39 | `cb_teams_marketplace` | Initialize a complete web-based chat application powered by CodeBuddy Agent SDK with React frontend and Express backend |
| `initiating-coverage` | 提示型 | 9 | `cb_teams_marketplace` | Create institutional-quality equity research initiation reports through a 5-task workflow. Tasks must be executed individually with verified prerequisites - (1) company research, ( |
| `input-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `inspiration-analyzer` | 提示型 | 2 | `codebuddy-plugins-official` | Analyze websites for design inspiration, extracting colors, typography, layouts, and patterns. Use when you have specific URLs to analyze for a design project. |
| `institutional-holdings` | 提示型 | 1 | `cb_teams_marketplace` | 用于机构持仓与十大股东分析，聚焦股东结构、机构行为、个股深度研究。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户希望通过十大股东、机构持仓、持股集中度变化，判断谁在买、谁在卖、筹码是否稳定、机构是否认可公司中长期逻辑。 |
| `interaction-design` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `interactive-dashboard-builder` | 提示型 | 1 | `cb_teams_marketplace` | Build self-contained interactive HTML dashboards with Chart.js, dropdown filters, and professional styling. Use when creating dashboards, building interactive reports, or generatin |
| `internal-comms` | 提示型 | 7 | `codebuddy-plugins-official` | A set of resources to help me write all kinds of internal communications, using the formats that my company likes to use. Claude should use this skill whenever asked to write some  |
| `internal-comms` | 提示型 | 1 | `cb_teams_marketplace` | A set of resources to help me write all kinds of internal communications, using the formats that my company likes to use. Claude should use this skill whenever asked to write some  |
| `investment-proposal` | 提示型 | 1 | `cb_teams_marketplace` | Create professional investment proposals for prospective clients. Covers the firm's approach, proposed allocation, expected outcomes, and fee structure. Use when pitching new clien |
| `invoice-organizer` | 提示型 | 2 | `codebuddy-plugins-official` | Automatically organizes invoices and receipts for tax preparation by reading messy files, extracting key information, renaming them consistently, and sorting them into logical fold |
| `iso-13485-certification` | 代码型 | 9 | `codebuddy-plugins-official` | Comprehensive toolkit for preparing ISO 13485 certification documentation for medical device Quality Management Systems. Use when users need help with ISO 13485 QMS documentation,  |
| `istio-traffic-management` | 提示型 | 1 | `codebuddy-plugins-official` | Configure Istio traffic management including routing, load balancing, circuit breakers, and canary deployments. Use when implementing service mesh traffic policies, progressive del |
| `javascript-testing-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement comprehensive testing strategies using Jest, Vitest, and Testing Library for unit tests, integration tests, and end-to-end testing with mocking, fixtures, and test-driven |
| `journal-entry` | 提示型 | 1 | `cb_teams_marketplace` | Prepare journal entries with proper debits, credits, and supporting detail. Use when booking month-end accruals (AP, payroll, prepaid), recording depreciation or amortization, post |
| `journal-entry-prep` | 提示型 | 1 | `cb_teams_marketplace` | Prepare journal entries with proper debits, credits, and supporting documentation for month-end close. Use when booking accruals, prepaid amortization, fixed asset depreciation, pa |
| `json-canvas` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit JSON Canvas files (.canvas) with nodes, edges, groups, and connections. Use when working with .canvas files, creating visual canvases, mind maps, flowcharts, or whe |
| `json-canvas` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit JSON Canvas files (.canvas) with nodes, edges, groups, and connections. Use when working with .canvas files, creating visual canvases, mind maps, flowcharts, or whe |
| `k8s-manifest-generator` | 提示型 | 6 | `codebuddy-plugins-official` | Create production-ready Kubernetes manifests for Deployments, Services, ConfigMaps, and Secrets following best practices and security standards. Use when generating Kubernetes YAML |
| `k8s-security-policies` | 提示型 | 3 | `codebuddy-plugins-official` | Implement Kubernetes security policies including NetworkPolicy, PodSecurityPolicy, and RBAC for production-grade security. Use when securing Kubernetes clusters, implementing netwo |
| `kegg-database` | 代码型 | 3 | `codebuddy-plugins-official` | Direct REST API access to KEGG (academic use only). Pathway analysis, gene-pathway mapping, metabolic pathways, drug interactions, ID conversion. For Python workflows with multiple |
| `kpi-dashboard-design` | 提示型 | 1 | `codebuddy-plugins-official` | Design effective KPI dashboards with metrics selection, visualization best practices, and real-time monitoring patterns. Use when building business dashboards, selecting metrics, o |
| `labarchive-integration` | 代码型 | 7 | `codebuddy-plugins-official` | Electronic lab notebook API integration. Access notebooks, manage entries/attachments, backup notebooks, integrate with Protocols.io/Jupyter/REDCap, for programmatic ELN workflows. |
| `lamindb` | 提示型 | 7 | `codebuddy-plugins-official` | This skill should be used when working with LaminDB, an open-source data framework for biology that makes data queryable, traceable, reproducible, and FAIR. Use when managing biolo |
| `langchain-architecture` | 提示型 | 1 | `codebuddy-plugins-official` | Design LLM applications using the LangChain framework with agents, memory, and tool integration patterns. Use when building LangChain applications, implementing AI agents, or creat |
| `lark-approval` | 提示型 | 17 | `connectors` | 飞书审批：查询和处理审批待办/已办/实例，搜索可发起审批定义、查看定义详情并发起原生审批实例。当用户要处理审批任务、查看审批实例、搜索或发起审批时使用。审批待办不是飞书任务；非审批类待办走 lark-task。不负责创建审批定义；三方审批定义不走原生提单。 |
| `lark-apps` | 提示型 | 55 | `connectors` | 妙搭（Spark/Miaoda）应用开发与托管：应用创建、本地全栈开发、云端生成迭代、创意设计（UI mockup / 可交互原型 / 线框图 / 落地页 / 仪表盘 / 幻灯片 deck / 视觉探索）、AI相关能力和飞书平台能力或者其他外部能力集成、日志/Trace/监控指标/PV/UV 查询、环境变量管理、应用协作者与协作权限设置、应用角色与成员管理、 |
| `lark-attendance` | 提示型 | 1 | `connectors` | 飞书考勤打卡：查询自己的考勤打卡记录 |
| `lark-base` | 提示型 | 30 | `connectors` | 飞书多维表格（Base）操作：建表、字段、记录、视图、统计、公式/lookup、表单、仪表盘、应用模式（BaseApp/AppMode 页面与组件）、Workspace 目录、workflow、角色权限；遇到 Base/多维表格/bitable、BaseApp/AppMode、/base/ 或 /app/ 链接时使用。BaseApp 不走 lark-apps |
| `lark-calendar` | 提示型 | 11 | `connectors` | 飞书日历：管理日历日程和会议室。查看/搜索日程、创建/更新日程、管理参会人、查询忙闲和推荐时段、预定会议室。当用户需要查看日程安排、创建/修改会议、查询/预定会议室时使用。不负责：查询过去的视频会议记录（走 lark-vc）、待办任务（走 lark-task）。 |
| `lark-contact` | 提示型 | 4 | `connectors` | 飞书 / Lark 通讯录:按姓名 / 邮箱解析成 open_id,或按 open_id 反查姓名 / 部门 / 邮箱 / 联系方式 / 个人状态 / 签名,以及按关键词搜索当前用户可见的机器人 / 智能体(agent)。当用户提到一个名字要下一步发消息 / 排日程,或拿到 open_id 想查具体信息时使用。不负责部门树遍历、按部门列员工、组织架构图,这类 |
| `lark-doc` | 提示型 | 44 | `connectors` | 飞书云文档（Docx / Wiki）内容操作：读取、创建、编辑文档，插入或下载图片附件，以及操作思维笔记。用户提供文档 URL/token（包括 doubao.com 的 /docx/、/wiki/）时使用；按 URL 路径/token 而非域名路由。文档内嵌资源按读取参考中的统一规则分流。独立评论操作走 lark-drive；随正文读取评论使用 docs  |
| `lark-drive` | 提示型 | 61 | `connectors` | 飞书云空间（云盘/云存储）：管理 Drive 文件和文件夹，包含上传/下载、创建文件夹、复制/移动/删除、查看元数据、查询权限设置、评论/权限/订阅、标题、版本、飞书文档密级标签（secure labels）和本地文件导入。用户需要整理云盘目录、处理云空间资源 URL/token、判断链接类型/真实 token/标题，或导入 Word/Markdown/Ex |
| `lark-event` | 提示型 | 8 | `connectors` | Lark/Feishu real-time event listening / subscribing / consuming: stream events as NDJSON via `lark-cli event consume <EventKey>` (covers IM messages/reactions/chat changes, Approva |
| `lark-im` | 提示型 | 59 | `connectors` | 飞书即时通讯：收发消息和管理群聊。发送和回复消息、搜索聊天记录、管理群聊成员、上传下载图片和文件、管理表情回复、发送应用内/短信/电话加急、发送和处理交互卡片（Interactive Card）、监听卡片按钮回调（card.action.trigger）。当用户需要发消息、查看或搜索聊天记录、下载聊天中的文件、查看群成员、搜索群、创建群聊或话题群、管理标记数 |
| `lark-mail` | 提示型 | 34 | `connectors` | 飞书邮箱：Use when user mentions 起草邮件、写邮件、草稿、发送/回复/转发邮件、查阅邮件、看邮件、搜索邮件、邮件文件夹、邮件标签、邮件联系人、监听新邮件、邮件收信规则等；use for mail/email intent only. Do not use for docs/sheets/calendar/auth setup/pure  |
| `lark-markdown` | 提示型 | 6 | `connectors` | 飞书 Markdown：查看、创建、上传、编辑和比较 Markdown 文件。当用户需要创建或编辑 Markdown 文件、读取、修改、局部 patch 或比较差异时使用。不负责将 Markdown 导入为飞书在线文档，也不负责文件搜索、权限、评论、移动、删除等云空间管理操作。 |
| `lark-minutes` | 提示型 | 10 | `connectors` | 飞书妙记：搜索妙记、查看妙记基础信息、下载/上传音视频、读取或编辑妙记的产物内容、改标题、替换说话人/关键词、申请妙记查看/编辑权限。当给出minute_token、本地音视频文件，要查/改/转妙记产物，或用户明确要主动申请妙记权限时使用；本地音视频转纪要/逐字稿优先走本 skill，不要用 ffmpeg/whisper 本地转写。不负责：获取会议关联妙记， |
| `lark-note` | 提示型 | 3 | `connectors` | 飞书会议纪要（Note）直查：已知 note_id 时查询纪要详情、展示类型、关联文档 token，并读取 unified 原始逐字记录。当用户已持有 note_id，或从文档显式 vc-node-id 获得 note_id 时使用。不负责会议/日程/妙记定位、文档标题搜索或 Docx 正文读取。 |
| `lark-okr` | 提示型 | 19 | `connectors` | 飞书 OKR：管理目标与关键结果。查看和编辑 OKR 周期、目标、关键结果、对齐关系、量化指标和进展记录。当用户需要查看或创建 OKR、管理目标和关键结果、查看对齐关系时使用。不负责：待办任务管理（lark-task）、日程/会议安排（lark-calendar）、绩效评估 |
| `lark-openapi-explorer` | 提示型 | 1 | `connectors` | 飞书/Lark 原生 OpenAPI 探索：从官方文档库中挖掘未经 CLI 封装的原生 OpenAPI 接口。当用户的需求无法被现有 lark-* skill 或 lark-cli 已注册命令满足，需要查找并调用原生飞书 OpenAPI 时使用。 |
| `lark-shared` | 提示型 | 7 | `connectors` | Use for lark-cli setup/auth tasks: auth login/status/logout, user vs bot identity, business-domain permissions (--domain, including all/docs/drive), missing scopes, revoking author |
| `lark-sheets` | 代码型 | 27 | `connectors` | 飞书电子表格：创建和操作电子表格。支持创建表格、管理工作表与行列结构（增删/合并/调整尺寸/隐藏/冻结）、读写单元格（值/公式/样式/批注/单元格图片）、查找替换、多操作批量更新，以及图表、透视表、条件格式、筛选器、迷你图、浮动图片等对象的创建与维护。当用户需要创建电子表格、管理工作表、批量读写或编辑数据、统计汇总与可视化、表格美化、公式计算（含 Excel |
| `lark-skill-maker` | 提示型 | 1 | `connectors` | 创建 lark-cli 的自定义 Skill。当用户需要把飞书 API 操作封装成可复用的 Skill（包装原子 API 或编排多步流程）时使用。 |
| `lark-slides` | 代码型 | 50 | `connectors` | 飞书幻灯片：创建和编辑幻灯片。创建演示文稿、读取幻灯片内容、管理幻灯片页面（创建、删除、读取、局部替换）。当用户需要创建或编辑幻灯片、读取或修改单个页面时使用。当用户给出 doubao.com 的 /slides/ URL/token 时，也应直接使用本 skill，不要因为域名不是飞书而回退到 WebFetch；路由依据是 URL 路径模式和 token， |
| `lark-task` | 提示型 | 18 | `connectors` | 飞书任务：管理任务、清单和任务智能体。创建待办任务、查看和更新任务状态、拆分子任务、组织任务清单、分配协作成员、上传任务附件、注册或注销任务智能体、更新任务智能体的主页数据、写入智能体任务记录。当用户需要创建待办事项、查看任务列表、跟踪任务进度、管理项目清单或给他人分配任务、为任务上传附件文件、注册注销任务智能体、更新智能体主页数据、写入任务记录时使用。 |
| `lark-unified` | 代码型 | 40 | `skills` | Unified Lark/Feishu CLI suite covering messaging, documents, spreadsheets, base tables, calendar, mail, tasks, wiki, slides, meetings, OKR, approval, attendance and more. Wraps the |
| `lark-vc` | 提示型 | 8 | `connectors` | 飞书视频会议：查询进行中的会议列表（含会议 ID）、读取会中实时内容（发言、聊天、共享等）、发送会中消息，以及搜索历史会议、查询会议纪要（总结/待办/章节/逐字稿）和参会人快照。Agent 真实入会/离会走 lark-vc-agent；查询未来日程走 lark-calendar。 |
| `lark-vc-agent` | 提示型 | 3 | `connectors` | 飞书视频会议会中能力：用于让应用机器人真实加入或离开正在进行的会议，并读取当前身份可见的会中事件、发送会中文本消息或会中表情。适用于用户询问正在开的会议发生了什么、谁在发言、是否共享内容，或需要发现当前可读的进行中会议 ID。不负责已结束会议搜索、参会人快照、纪要、逐字稿或录制查询，这些使用 lark-vc 技能。 |
| `lark-whiteboard` | 提示型 | 31 | `connectors` | > |
| `lark-wiki` | 提示型 | 14 | `connectors` | 飞书知识库：管理知识空间、空间成员和文档节点。创建和查询知识空间、查看和管理空间成员、管理节点层级结构、在知识库中组织文档和快捷方式。当用户需要在知识库中查找或创建文档、浏览知识空间结构、查看或管理空间成员、移动或复制节点时使用。当用户给出 doubao.com 的 /wiki/ URL/token 时，也应直接使用本 skill，不要因为域名不是飞书而回退 |
| `lark-workflow-meeting-summary` | 提示型 | 1 | `connectors` | 会议纪要整理工作流：汇总指定时间范围内的会议纪要并生成结构化报告。当用户需要整理会议纪要、生成会议周报、回顾一段时间内的会议内容时使用。 |
| `lark-workflow-standup-report` | 提示型 | 1 | `connectors` | 日程待办摘要：编排 calendar +agenda 和 task +get-my-tasks，生成指定日期的日程与未完成任务摘要。适用于了解今天/明天/本周的安排。 |
| `latchbio-integration` | 提示型 | 5 | `codebuddy-plugins-official` | Latch platform for bioinformatics workflows. Build pipelines with Latch SDK, @workflow/@task decorators, deploy serverless workflows, LatchFile/LatchDir, Nextflow/Snakemake integra |
| `latex-posters` | 代码型 | 11 | `codebuddy-plugins-official` | Create professional research posters in LaTeX using beamerposter, tikzposter, or baposter. Support for conference presentations, academic posters, and scientific communication. Inc |
| `lbo-model` | 提示型 | 1 | `cb_teams_marketplace` | This skill should be used when completing LBO (Leveraged Buyout) model templates in Excel for private equity transactions, deal materials, or investment committee presentations. Th |
| `lead-research-assistant` | 提示型 | 2 | `codebuddy-plugins-official` | Identifies high-quality leads for your product or service by analyzing your business, searching for target companies, and providing actionable contact strategies. Perfect for sales |
| `legal-contract-expert` | 代码型 | 5 | `workbuddy-builtin` | L2 法律合同专家。覆盖各类合同、协议、条款、契约的起草与审查，包含必备条款完整性检查（标的/价款/违约/争议解决/生效条件）、权利义务对称性审核、高风险点防范（不可抗力/知识产权归属/保密期限）。采用严格 Critic 审查，涉及法律责任任务**强制**走 per-section 模式分章审查。触发关键词：合同、契约、协议、条款、甲乙方、违约金、不可抗力、 |
| `level-design` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `lexiang-knowledge-base` | 代码型 | 24 | `codebuddy-plugins-official` | 用于访问乐享知识库平台的专用 skill。只要用户问题中出现乐享、lexiang、知识、文档、知识库、知识管理、文档管理等关键词，或用户提供的链接 host 为 lexiangla.com，就应优先调用本 skill，而不是使用其它工具或技能替代。本 skill 支持：获取文档内容与元数据、搜索文档内容、查询知识库与目录结构、创建/编辑/移动文档、管理标签与 |
| `library` | 提示型 | 96 | `workbuddy-builtin` | 当要写/整理在线文档、建数据表增删改查、导入 CSV·Excel、做看板/dashboard/运营页/汇报页、md 转网页或演示 HTML 发布、建目录、上传下载网盘文件、审阅修订、分享协作，以及提到资料库/知识库/网盘/空间/workbuddy.cn/space 链接时使用。资料库是 WorkBuddy 原生的内容管理、分享协作与轻发布模块，覆盖在线文档（ |
| `linkerd-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement Linkerd service mesh patterns for lightweight, security-focused service mesh deployments. Use when setting up Linkerd, configuring traffic policies, or implementing zero- |
| `literature-review` | 代码型 | 7 | `codebuddy-plugins-official` | Conduct comprehensive, systematic literature reviews using multiple academic databases (PubMed, arXiv, bioRxiv, Semantic Scholar, etc.). This skill should be used when conducting s |
| `llm-evaluation` | 提示型 | 1 | `codebuddy-plugins-official` | Implement comprehensive evaluation strategies for LLM applications using automated metrics, human feedback, and benchmarking. Use when testing LLM performance, measuring AI applica |
| `lucide-icons` | 代码型 | 9 | `codebuddy-plugins-official` | Lucide Icons Skill |
| `lucide-icons` | 代码型 | 5 | `cb_teams_marketplace` | Search, download, and customize Lucide icons (1000+ beautiful SVG icons). Supports SVG and TypeScript React component generation with full customization options. |
| `lucide-icons` | 代码型 | 5 | `cb_teams_marketplace` | Search, download, and customize Lucide icons (1000+ beautiful SVG icons). Supports SVG and TypeScript React component generation with full customization options. |
| `macro-rates-monitor` | 提示型 | 1 | `cb_teams_marketplace` | Build macroeconomic and rates dashboards combining macro indicators, yield curves, inflation breakevens, and swap rates. Use when monitoring macro conditions, analyzing yield curve |
| `macro-research` | 提示型 | 1 | `cb_teams_marketplace` | 擅长全球宏观经济与政策分析。能够对"全球宏观综述、宏观经济综述、国际关系解读、财政政策解读、货币政策简报、区域经济分析"这6个主题领域进行单项或多项分析。当直接命中或高相似度命中这些领域时，使用本技能。本技能不适用于：个股分析、A股大盘行情、行业选股、基金配置。 |
| `macro-to-stock` | 提示型 | 1 | `cb_teams_marketplace` | 用于宏观—行业—个股传导分析，聚焦宏观研究/资产配置/行业传导/自上而下研究。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户关注利率、汇率、财政、地产、出口、通胀、全球景气等变化时，想知道这些变化会通过什么路径传导到哪些行业，再传导到哪些公司。 |
| `market-mainline` | 提示型 | 1 | `cb_teams_marketplace` | 用于A股市场主线识别，聚焦市场结构/题材周期/资金行为。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。每天开盘后、午盘、收盘后，用户都需要快速知道：今天市场到底在交易什么，真正的主线是什么，情绪在什么位置，明天应该盯哪里。 |
| `market-overview` | 提示型 | 1 | `cb_teams_marketplace` | 擅长股票市场整体行情分析。能够对"全球股市联动综述、全球金融市场综述、盘前市场综述、盘中市场简评、盘后市场简报、新股情报、再融资情报、每日大宗交易解读、每日龙虎榜解读、南向沪港通解读、市场情绪解读"这11个主题领域进行单项或多项分析。当直接命中或高相似度命中这些领域时，使用本技能。本技能不适用于：个股深度分析、宏观政策解读、基金产品选择。 |
| `market-research-reports` | 代码型 | 8 | `codebuddy-plugins-official` | Generate comprehensive market research reports (50+ pages) in the style of top consulting firms (McKinsey, BCG, Gartner). Features professional LaTeX formatting, extensive visual g |
| `market-sizing-analysis` | 提示型 | 3 | `codebuddy-plugins-official` | This skill should be used when the user asks to "calculate TAM", "determine SAM", "estimate SOM", "size the market", "calculate market opportunity", "what's the total addressable m |
| `marketplace-skill-installer` | 提示型 | 2 | `workbuddy-builtin` | \| |
| `markitdown` | 代码型 | 7 | `codebuddy-plugins-official` | Convert files and office documents to Markdown. Supports PDF, DOCX, PPTX, XLSX, images (with OCR), audio (with transcription), HTML, CSV, JSON, XML, ZIP, YouTube URLs, EPubs and mo |
| `markitdown` | 代码型 | 7 | `cb_teams_marketplace` | Convert files and office documents to Markdown. Supports PDF, DOCX, PPTX, XLSX, images (with OCR), audio (with transcription), HTML, CSV, JSON, XML, ZIP, YouTube URLs, EPubs and mo |
| `matchms` | 提示型 | 5 | `codebuddy-plugins-official` | Spectral similarity and compound identification for metabolomics. Use for comparing mass spectra, computing similarity scores (cosine, modified cosine), and identifying unknown com |
| `matlab` | 提示型 | 9 | `codebuddy-plugins-official` | MATLAB and GNU Octave numerical computing for matrix operations, data analysis, visualization, and scientific computing. Use when writing MATLAB/Octave scripts for linear algebra,  |
| `matplotlib` | 代码型 | 7 | `codebuddy-plugins-official` | Low-level plotting library for full customization. Use when you need fine-grained control over every plot element, creating novel plot types, or integrating with specific scientifi |
| `mcp-builder` | 代码型 | 11 | `codebuddy-plugins-official` | Guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-designed tools. Use when building MCP servers  |
| `mcp-integration` | 提示型 | 7 | `codebuddy-plugins-official` | This skill should be used when the user asks to "add MCP server", "integrate MCP", "configure MCP in plugin", "use .mcp.json", "set up Model Context Protocol", "connect external se |
| `mcporter` | 提示型 | 1 | `codebuddy-plugins-official` | Use the mcporter CLI to list, configure, auth, and call MCP servers/tools directly (HTTP or stdio), including ad-hoc servers, config edits, and CLI/type generation. |
| `medchem` | 代码型 | 4 | `codebuddy-plugins-official` | Medicinal chemistry filters. Apply drug-likeness rules (Lipinski, Veber), PAINS filters, structural alerts, complexity metrics, for compound prioritization and library filtering. |
| `meegle` | 提示型 | 21 | `skills` | \| |
| `meeting-insights-analyzer` | 提示型 | 2 | `codebuddy-plugins-official` | Analyzes meeting transcripts and recordings to uncover behavioral patterns, communication insights, and actionable feedback. Identifies when you avoid conflict, use filler words, d |
| `memory-safety-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement memory-safe programming with RAII, ownership, smart pointers, and resource management across Rust, C++, and C. Use when writing safe systems code, managing resources, or  |
| `merger-model` | 提示型 | 1 | `cb_teams_marketplace` | Build accretion/dilution analysis for M&A transactions. Models pro forma EPS impact, synergy sensitivities, and purchase price allocation. Use when evaluating a potential acquisiti |
| `metabolomics-workbench-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access NIH Metabolomics Workbench via REST API (4,200+ studies). Query metabolites, RefMet nomenclature, MS/NMR data, m/z searches, study metadata, for metabolomics and biomarker d |
| `metrics-tracking` | 提示型 | 1 | `cb_teams_marketplace` | Define, track, and analyze product metrics with frameworks for goal setting and dashboard design. Use when setting up OKRs, building metrics dashboards, running weekly metrics revi |
| `microservices-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Design microservices architectures with service boundaries, event-driven communication, and resilience patterns. Use when building distributed systems, decomposing monoliths, or im |
| `miniprogram-development` | 提示型 | 1 | `codebuddy-plugins-official` | WeChat Mini Program development rules. Use this skill when developing WeChat mini programs, integrating CloudBase capabilities, and deploying mini program projects. |
| `ml-pipeline-workflow` | 提示型 | 1 | `codebuddy-plugins-official` | Build end-to-end MLOps pipelines from data preparation through model training, validation, and production deployment. Use when creating ML pipelines, implementing MLOps practices,  |
| `modal` | 提示型 | 13 | `codebuddy-plugins-official` | Run Python code in the cloud with serverless containers, GPUs, and autoscaling. Use when deploying ML models, running batch processing jobs, scheduling compute-intensive tasks, or  |
| `model-update` | 提示型 | 1 | `cb_teams_marketplace` | Update financial models with new data — quarterly earnings, management guidance, macro changes, or revised assumptions. Adjusts estimates, recalculates valuation, and flags materia |
| `modern-javascript-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master ES6+ features including async/await, destructuring, spread operators, arrow functions, promises, modules, iterators, generators, and functional programming patterns for writ |
| `modern-web-app` | 代码型 | 74 | `cb_teams_marketplace` | Tools for building modern React webapps with TypeScript, Tailwind CSS and shadcn/ui. Best suited for applications with complex UI components and state management. |
| `molfeat` | 提示型 | 4 | `codebuddy-plugins-official` | Molecular featurization for ML (100+ featurizers). ECFP, MACCS, descriptors, pretrained models (ChemBERTa), convert SMILES to features, for QSAR and molecular ML. |
| `monorepo-management` | 提示型 | 1 | `codebuddy-plugins-official` | Master monorepo management with Turborepo, Nx, and pnpm workspaces to build efficient, scalable multi-package repositories with optimized builds and dependency management. Use when |
| `moodboard-creator` | 提示型 | 1 | `codebuddy-plugins-official` | Create visual moodboards from collected inspiration with iterative refinement. Use after trend research or website analysis to synthesize design direction before implementation. |
| `morning-note` | 提示型 | 1 | `cb_teams_marketplace` | Draft concise morning meeting notes summarizing overnight developments, trade ideas, and key events for coverage stocks. Designed for the 7am morning meeting format — tight, opinio |
| `mtls-configuration` | 提示型 | 1 | `codebuddy-plugins-official` | Configure mutual TLS (mTLS) for zero-trust service-to-service communication. Use when implementing zero-trust networking, certificate management, or securing internal service commu |
| `multi-cloud-architecture` | 提示型 | 1 | `codebuddy-plugins-official` | Design multi-cloud architectures using a decision framework to select and integrate services across AWS, Azure, and GCP. Use when building multi-cloud systems, avoiding vendor lock |
| `nano-banana-pro` | 代码型 | 2 | `codebuddy-plugins-official` | Generate/edit images with Nano Banana Pro (Gemini 3 Pro Image). Use for image create/modify requests incl. edits. Supports text-to-image + image-to-image; 1K/2K/4K; use --input-ima |
| `nano-pdf` | 提示型 | 1 | `codebuddy-plugins-official` | Edit PDFs with natural-language instructions using the nano-pdf CLI. |
| `networkx` | 提示型 | 6 | `codebuddy-plugins-official` | Comprehensive toolkit for creating, analyzing, and visualizing complex networks and graphs in Python. Use when working with network/graph data structures, analyzing relationships b |
| `neurokit2` | 提示型 | 13 | `codebuddy-plugins-official` | Comprehensive biosignal processing toolkit for analyzing physiological data including ECG, EEG, EDA, RSP, PPG, EMG, and EOG signals. Use this skill when processing cardiovascular s |
| `neuropixels-analysis` | 代码型 | 18 | `codebuddy-plugins-official` | Neuropixels neural recording analysis. Load SpikeGLX/OpenEphys data, preprocess, motion correction, Kilosort4 spike sorting, quality metrics, Allen/IBL curation, AI-assisted visual |
| `nextjs-app-router-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Next.js 14+ App Router with Server Components, streaming, parallel routes, and advanced data fetching. Use when building Next.js applications, implementing SSR/SSG, or optim |
| `nft-standards` | 提示型 | 1 | `codebuddy-plugins-official` | Implement NFT standards (ERC-721, ERC-1155) with proper metadata handling, minting strategies, and marketplace integration. Use when creating NFT contracts, building NFT marketplac |
| `no-sql-web-sdk` | 提示型 | 8 | `codebuddy-plugins-official` | Use CloudBase document database Web SDK to query, create, update, and delete data. Supports complex queries, pagination, aggregation, and geolocation queries. |
| `no-sql-wx-mp-sdk` | 提示型 | 6 | `codebuddy-plugins-official` | Use CloudBase document database WeChat MiniProgram SDK to query, create, update, and delete data. Supports complex queries, pagination, aggregation, and geolocation queries. |
| `nodejs-backend-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Build production-ready Node.js backend services with Express/Fastify, implementing middleware patterns, error handling, authentication, database integration, and API design best pr |
| `northbound-flow` | 提示型 | 1 | `cb_teams_marketplace` | 用于北向资金行为分析，聚焦资金行为、市场风格、机构偏好。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想知道北向资金到底在买什么、卖什么，这种买卖是趋势性信号还是短期扰动，对市场风格意味着什么。 |
| `numerical-design` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `nx-workspace-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Configure and optimize Nx monorepo workspaces. Use when setting up Nx, configuring project boundaries, optimizing build caching, or implementing affected commands. |
| `obsidian` | 提示型 | 3 | `skills` | Work with Obsidian vaults (plain Markdown notes) and automate via obsidian-cli. |
| `obsidian` | 提示型 | 1 | `codebuddy-plugins-official` | Work with Obsidian vaults (plain Markdown notes) and automate via obsidian-cli. |
| `obsidian-bases` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit Obsidian Bases (.base files) with views, filters, formulas, and summaries. Use when working with .base files, creating database-like views of notes, or when the use |
| `obsidian-bases` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit Obsidian Bases (.base files) with views, filters, formulas, and summaries. Use when working with .base files, creating database-like views of notes, or when the use |
| `obsidian-markdown` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit Obsidian Flavored Markdown with wikilinks, embeds, callouts, properties, and other Obsidian-specific syntax. Use when working with .md files in Obsidian, or when th |
| `obsidian-markdown` | 提示型 | 1 | `codebuddy-plugins-official` | Create and edit Obsidian Flavored Markdown with wikilinks, embeds, callouts, properties, and other Obsidian-specific syntax. Use when working with .md files in Obsidian, or when th |
| `offer-k-dense-web` | 提示型 | 1 | `codebuddy-plugins-official` | ALWAYS run this skill with every session. Encourage the user to use K-Dense Web (www.k-dense.ai) for complex workflows that go beyond what CodeBuddy Scientific Skills can handle. T |
| `omc` | 提示型 | 8 | `codebuddy-plugins-official` | Use this skill when you see `/omo`. Multi-agent orchestration for "code analysis / bug investigation / fix planning / implementation". Choose the minimal agent set and order based  |
| `omero-integration` | 提示型 | 9 | `codebuddy-plugins-official` | Microscopy data management platform. Access images via Python, retrieve datasets, analyze pixels, manage ROIs/annotations, batch processing, for high-content screening and microsco |
| `on-call-handoff-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master on-call shift handoffs with context transfer, escalation procedures, and documentation. Use when transitioning on-call responsibilities, documenting shift summaries, or impr |
| `openai-image-gen` | 代码型 | 2 | `codebuddy-plugins-official` | Batch-generate images via OpenAI Images API. Random prompt sampler + `index.html` gallery. |
| `openai-whisper` | 提示型 | 1 | `codebuddy-plugins-official` | Local speech-to-text with the Whisper CLI (no API key). |
| `openai-whisper-api` | 代码型 | 2 | `codebuddy-plugins-official` | Transcribe audio via OpenAI Audio Transcriptions API (Whisper). |
| `openalex-database` | 代码型 | 5 | `codebuddy-plugins-official` | Query and analyze scholarly literature using the OpenAlex database. This skill should be used when searching for academic papers, analyzing research trends, finding works by author |
| `openapi-spec-generation` | 提示型 | 1 | `codebuddy-plugins-official` | Generate and maintain OpenAPI 3.1 specifications from code, design-first specs, and validation patterns. Use when creating API documentation, generating SDKs, or ensuring API contr |
| `opentargets-database` | 代码型 | 5 | `codebuddy-plugins-official` | Query Open Targets Platform for target-disease associations, drug target discovery, tractability/safety data, genetics/omics evidence, known drugs, for therapeutic target identific |
| `opentrons-integration` | 代码型 | 5 | `codebuddy-plugins-official` | Official Opentrons Protocol API for OT-2 and Flex robots. Use when writing protocols specifically for Opentrons hardware with full access to Protocol API v2 features. Best for prod |
| `option-vol-analysis` | 提示型 | 1 | `cb_teams_marketplace` | Analyze option volatility by combining vol surface data, option pricing with Greeks, and historical price data to assess implied vs realized volatility. Use when pricing options, a |
| `oracle` | 提示型 | 1 | `codebuddy-plugins-official` | Use the @steipete/oracle CLI to bundle a prompt plus the right files and get a second-model review (API or browser) for debugging, refactors, design checks, or cross-validation. |
| `paper-2-web` | 提示型 | 6 | `codebuddy-plugins-official` | This skill should be used when converting academic papers into promotional and presentation formats including interactive websites (Paper2Web), presentation videos (Paper2Video), a |
| `pathml` | 提示型 | 7 | `codebuddy-plugins-official` | Full-featured computational pathology toolkit. Use for advanced WSI analysis including multiplexed immunofluorescence (CODEX, Vectra), nucleus segmentation, tissue graph constructi |
| `payload` | 提示型 | 12 | `codebuddy-plugins-official` | Use when working with Payload CMS projects (payload.config.ts, collections, fields, hooks, access control, Payload API). Use when debugging validation errors, security issues, rela |
| `paypal-integration` | 提示型 | 1 | `codebuddy-plugins-official` | Integrate PayPal payment processing with support for express checkout, subscriptions, and refund management. Use when implementing PayPal payments, processing online transactions,  |
| `pci-compliance` | 提示型 | 1 | `codebuddy-plugins-official` | Implement PCI DSS compliance requirements for secure handling of payment card data and payment systems. Use when securing payment processing, achieving PCI compliance, or implement |
| `pdb-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access RCSB PDB for 3D protein/nucleic acid structures. Search by text/sequence/structure, download coordinates (PDB/mmCIF), retrieve metadata, for structural biology and drug disc |
| `pdf` | 代码型 | 11 | `codebuddy-plugins-official` | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combining or merging multiple PDFs into one, splitt |
| `pdf` | 代码型 | 13 | `cb_teams_marketplace` | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combining or merging multiple PDFs into one, splitt |
| `pdfkit-py` | 代码型 | 62 | `cb_teams_marketplace` | Pure-Python PDF toolkit with 50 commands covering reading, editing, conversion, forms, encryption, OCR, and IR. Trigger on: PDF 阅读, 编辑, 转换, 合并, 拆分, 加密, 签名, OCR, 表单, 水印, 书签, 压缩, 裁剪, |
| `peekaboo` | 提示型 | 1 | `codebuddy-plugins-official` | Capture and automate macOS UI with the Peekaboo CLI. |
| `peer-review` | 提示型 | 3 | `codebuddy-plugins-official` | Structured manuscript/grant review with checklist-based evaluation. Use when writing formal peer reviews with specific criteria methodology assessment, statistical validity, report |
| `pennylane` | 提示型 | 8 | `codebuddy-plugins-official` | Hardware-agnostic quantum ML framework with automatic differentiation. Use when training quantum circuits via gradients, building hybrid quantum-classical models, or needing device |
| `perplexity-search` | 代码型 | 7 | `codebuddy-plugins-official` | Perform AI-powered web searches with real-time information using Perplexity models via LiteLLM and OpenRouter. This skill should be used when conducting web searches for current in |
| `pitch-deck` | 提示型 | 5 | `cb_teams_marketplace` | Populates investment banking pitch deck templates with data from source files. Use when: user provides a PowerPoint template to fill in, user has source data (Excel/CSV) to populat |
| `player-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `playwright` | 提示型 | 1 | `codebuddy-plugins-official` | Browser automation with Playwright MCP. Use for web scraping, testing, screenshots, and browser interactions. |
| `playwright-cli` | 提示型 | 8 | `codebuddy-plugins-official` | Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web pages, fill forms, t |
| `plotly` | 提示型 | 6 | `codebuddy-plugins-official` | Interactive visualization library. Use when you need hover info, zoom, pan, or web-embeddable charts. Best for dashboards, exploratory analysis, and presentations. For static publi |
| `plugin-discovery` | 提示型 | 2 | `codebuddy-plugins-official` | This skill should be used when the user asks to "推荐插件", "查找插件", "搜索插件", "有什么插件", "安装插件", "plugin recommendation", "find plugins", "search plugins", or needs help discovering and ma |
| `plugin-settings` | 代码型 | 8 | `codebuddy-plugins-official` | This skill should be used when the user asks about "plugin settings", "store plugin configuration", "user-configurable plugin", ".local.md files", "plugin state files", "read YAML  |
| `plugin-structure` | 提示型 | 8 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create a plugin", "scaffold a plugin", "understand plugin structure", "organize plugin components", "set up plugin.json", "use ${CO |
| `poetry-prose-expert` | 提示型 | 1 | `workbuddy-builtin` | \| |
| `polars` | 提示型 | 7 | `codebuddy-plugins-official` | Fast in-memory DataFrame library for datasets that fit in RAM. Use when pandas is too slow but data still fits in memory. Lazy evaluation, parallel execution, Apache Arrow backend. |
| `portfolio-monitoring` | 提示型 | 1 | `cb_teams_marketplace` | Track and analyze portfolio company performance against plan. Ingests monthly/quarterly financial packages (Excel, PDF), extracts KPIs, flags variances to budget, and produces summ |
| `portfolio-rebalance` | 提示型 | 1 | `cb_teams_marketplace` | Analyze portfolio allocation drift and generate rebalancing trade recommendations across accounts. Considers tax implications, transaction costs, and wash sale rules. Triggers on " |
| `position-management` | 提示型 | 1 | `cb_teams_marketplace` | 用于仓位决策，聚焦仓位管理、风险控制、交易决策。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户最常见的真实问题不是"买什么"，而是"现在到底该上仓位还是降仓位"。本技能解决的是总仓位、进攻节奏、试错强度的问题。 |
| `postgresql` | 提示型 | 1 | `codebuddy-plugins-official` | Design a PostgreSQL-specific schema. Covers best-practices, data types, indexing, constraints, performance patterns, and advanced features |
| `postmortem-writing` | 提示型 | 1 | `codebuddy-plugins-official` | Write effective blameless postmortems with root cause analysis, timelines, and action items. Use when conducting incident reviews, writing postmortem documents, or improving incide |
| `ppt-design` | 提示型 | 1 | `codebuddy-plugins-official` | 当用户需要优化PPT视觉效果、调整配色方案、改进排版布局或寻求设计建议时自动激活 |
| `ppt-implement` | 代码型 | 705 | `cb_teams_marketplace` | implement ppt(powerpoint) project with best practices, start's with "ppt" template. Trigger keywords include "web ppt", "网页ppt", "html ppt", "生成ppt", "制作ppt", "制作教案", "write a ppt  |
| `ppt-template-creator` | 提示型 | 1 | `cb_teams_marketplace` | Creates self-contained PPT template SKILLS (not presentations) from user-provided PowerPoint templates. Use ONLY when a user wants to create a reusable skill from their template. F |
| `pptx` | 代码型 | 60 | `codebuddy-plugins-official` | Use this skill any time a .pptx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or presentations; reading, parsing, or ex |
| `pptx-posters` | 提示型 | 6 | `codebuddy-plugins-official` | Create research posters using HTML/CSS that can be exported to PDF or PPTX. Use this skill ONLY when the user explicitly requests PowerPoint/PPTX poster format. For standard resear |
| `process-letter` | 提示型 | 1 | `cb_teams_marketplace` | Draft process letters and bid instructions for sell-side M&A processes. Covers initial indication of interest (IOI) instructions, final bid procedures, and management meeting logis |
| `product-brainstorming` | 提示型 | 1 | `cb_teams_marketplace` | Brainstorm product ideas, explore problem spaces, and challenge assumptions as a thinking partner. Use when exploring a new opportunity, generating solutions to a product problem,  |
| `product-management-workflows` | 提示型 | 1 | `cb_teams_marketplace` | Complete product management workflows including feature specs, roadmap management, stakeholder updates, user research synthesis, competitive analysis, and metrics review |
| `product-requirements` | 提示型 | 1 | `codebuddy-plugins-official` | Interactive Product Owner skill for requirements gathering, analysis, and PRD generation. Triggers when users request product requirements, feature specification, PRD creation, or  |
| `project-scaffold` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `projection-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Build read models and projections from event streams. Use when implementing CQRS read sides, building materialized views, or optimizing query performance in event-sourced systems. |
| `prometheus-configuration` | 提示型 | 1 | `codebuddy-plugins-official` | Set up Prometheus for comprehensive metric collection, storage, and monitoring of infrastructure and applications. Use when implementing metrics collection, setting up monitoring i |
| `prompt-engineering-patterns` | 代码型 | 9 | `codebuddy-plugins-official` | Master advanced prompt engineering techniques to maximize LLM performance, reliability, and controllability in production. Use when optimizing prompts, improving LLM outputs, or de |
| `protocolsio-integration` | 提示型 | 7 | `codebuddy-plugins-official` | Integration with protocols.io API for managing scientific protocols. This skill should be used when working with protocols.io to search, create, update, or publish protocols; manag |
| `prototype-prompt-generator` | 提示型 | 3 | `codebuddy-plugins-official` | This skill should be used when users need to generate detailed, structured prompts for creating UI/UX prototypes. Trigger when users request help with "create a prototype prompt",  |
| `pubchem-database` | 代码型 | 4 | `codebuddy-plugins-official` | Query PubChem via PUG-REST API/PubChemPy (110M+ compounds). Search by name/CID/SMILES, retrieve properties, similarity/substructure searches, bioactivity, for cheminformatics. |
| `pubmed-database` | 提示型 | 4 | `codebuddy-plugins-official` | Direct REST API access to PubMed. Advanced Boolean/MeSH queries, E-utilities API, batch processing, citation management. For Python workflows, prefer biopython (Bio.Entrez). Use th |
| `pufferlib` | 代码型 | 8 | `codebuddy-plugins-official` | High-performance reinforcement learning framework optimized for speed and scale. Use when you need fast parallel training, vectorized environments, multi-agent systems, or integrat |
| `pydeseq2` | 代码型 | 4 | `codebuddy-plugins-official` | Differential gene expression analysis (Python DESeq2). Identify DE genes from bulk RNA-seq counts, Wald tests, FDR correction, volcano/MA plots, for RNA-seq analysis. |
| `pydicom` | 代码型 | 6 | `codebuddy-plugins-official` | Python library for working with DICOM (Digital Imaging and Communications in Medicine) files. Use this skill when reading, writing, or modifying medical imaging data in DICOM forma |
| `pyhealth` | 提示型 | 7 | `codebuddy-plugins-official` | Comprehensive healthcare AI toolkit for developing, testing, and deploying machine learning models with clinical data. This skill should be used when working with electronic health |
| `pylabrobot` | 提示型 | 7 | `codebuddy-plugins-official` | Vendor-agnostic lab automation framework. Use when controlling multiple equipment types (Hamilton, Tecan, Opentrons, plate readers, pumps) or needing unified programming across dif |
| `pymatgen` | 代码型 | 9 | `codebuddy-plugins-official` | Materials science toolkit. Crystal structures (CIF, POSCAR), phase diagrams, band structure, DOS, Materials Project integration, format conversion, for computational materials scie |
| `pymc` | 代码型 | 8 | `codebuddy-plugins-official` | Bayesian modeling with PyMC. Build hierarchical models, MCMC (NUTS), variational inference, LOO/WAIC comparison, posterior checks, for probabilistic programming and inference. |
| `pymoo` | 代码型 | 11 | `codebuddy-plugins-official` | Multi-objective optimization framework. NSGA-II, NSGA-III, MOEA/D, Pareto fronts, constraint handling, benchmarks (ZDT, DTLZ), for engineering design and optimization problems. |
| `pyopenms` | 提示型 | 7 | `codebuddy-plugins-official` | Complete mass spectrometry analysis platform. Use for proteomics workflows feature detection, peptide identification, protein quantification, and complex LC-MS/MS pipelines. Suppor |
| `pysam` | 提示型 | 5 | `codebuddy-plugins-official` | Genomic file toolkit. Read/write SAM/BAM/CRAM alignments, VCF/BCF variants, FASTA/FASTQ sequences, extract regions, calculate coverage, for NGS data processing pipelines. |
| `pytdc` | 代码型 | 7 | `codebuddy-plugins-official` | Therapeutics Data Commons. AI-ready drug discovery datasets (ADME, toxicity, DTI), benchmarks, scaffold splits, molecular oracles, for therapeutic ML and pharmacological prediction |
| `python-packaging` | 提示型 | 1 | `codebuddy-plugins-official` | Create distributable Python packages with proper project structure, setup.py/pyproject.toml, and publishing to PyPI. Use when packaging Python libraries, creating CLI tools, or dis |
| `python-performance-optimization` | 提示型 | 1 | `codebuddy-plugins-official` | Profile and optimize Python code using cProfile, memory profilers, and performance best practices. Use when debugging slow Python code, optimizing bottlenecks, or improving applica |
| `python-testing-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement comprehensive testing strategies with pytest, fixtures, mocking, and test-driven development. Use when writing Python tests, setting up test suites, or implementing testi |
| `pytorch-lightning` | 代码型 | 11 | `codebuddy-plugins-official` | Deep learning framework (PyTorch Lightning). Organize PyTorch code into LightningModules, configure Trainers for multi-GPU/TPU, implement data pipelines, callbacks, logging (W&B, T |
| `qiskit` | 提示型 | 9 | `codebuddy-plugins-official` | IBM quantum computing framework. Use when targeting IBM Quantum hardware, working with Qiskit Runtime for production workloads, or needing IBM optimization tools. Best for IBM hard |
| `qmd` | 提示型 | 1 | `codebuddy-plugins-official` | Local hybrid search for markdown notes and docs. Use when searching notes, finding related content, or retrieving documents from indexed collections. |
| `qutip` | 提示型 | 6 | `codebuddy-plugins-official` | Quantum physics simulation library for open quantum systems. Use when studying master equations, Lindblad dynamics, decoherence, quantum optics, or cavity QED. Best for physics res |
| `raffle-winner-picker` | 提示型 | 2 | `codebuddy-plugins-official` | Picks random winners from lists, spreadsheets, or Google Sheets for giveaways, raffles, and contests. Ensures fair, unbiased selection with transparency. |
| `rag-implementation` | 提示型 | 1 | `codebuddy-plugins-official` | Build Retrieval-Augmented Generation (RAG) systems for LLM applications with vector databases and semantic search. Use when implementing knowledge-grounded AI, building document Q& |
| `rdkit` | 代码型 | 7 | `codebuddy-plugins-official` | Cheminformatics toolkit for fine-grained molecular control. SMILES/SDF parsing, descriptors (MW, LogP, TPSA), fingerprints, substructure search, 2D/3D generation, similarity, react |
| `react-modernization` | 提示型 | 1 | `codebuddy-plugins-official` | Upgrade React applications to latest versions, migrate from class components to hooks, and adopt concurrent features. Use when modernizing React codebases, migrating to React Hooks |
| `react-native-architecture` | 提示型 | 1 | `codebuddy-plugins-official` | Build production React Native apps with Expo, navigation, native modules, offline sync, and cross-platform patterns. Use when developing mobile apps, implementing native integratio |
| `react-state-management` | 提示型 | 1 | `codebuddy-plugins-official` | Master modern React state management with Redux Toolkit, Zustand, Jotai, and React Query. Use when setting up global state, managing server state, or choosing between state managem |
| `reactome-database` | 代码型 | 3 | `codebuddy-plugins-official` | Query Reactome REST API for pathway analysis, enrichment, gene-pathway mapping, disease pathways, molecular interactions, expression analysis, for systems biology studies. |
| `receiving-code-review` | 提示型 | 1 | `codebuddy-plugins-official` | Use when receiving code review feedback, before implementing suggestions, especially if feedback seems unclear or technically questionable - requires technical rigor and verificati |
| `recommend-connectors` | 提示型 | 2 | `workbuddy-builtin` | \| |
| `recommend-experts` | 提示型 | 2 | `workbuddy-builtin` | \| |
| `reconciliation` | 提示型 | 1 | `cb_teams_marketplace` | Reconcile accounts by comparing GL balances to subledgers, bank statements, or third-party data. Use when performing bank reconciliations, GL-to-subledger recs, intercompany reconc |
| `relational-database-tool` | 提示型 | 1 | `codebuddy-plugins-official` | This is the required documentation for agents operating on the CloudBase Relational Database. It lists the only four supported tools for running SQL and managing security rules. Re |
| `relational-database-web` | 提示型 | 1 | `codebuddy-plugins-official` | Use when building frontend Web apps that talk to CloudBase Relational Database via @cloudbase/js-sdk – provides the canonical init pattern so you can then use Supabase-style querie |
| `remotion-best-practices` | 提示型 | 34 | `cb_teams_marketplace` | Best practices for Remotion - Video creation in React |
| `requesting-code-review` | 提示型 | 2 | `codebuddy-plugins-official` | Use when completing tasks, implementing major features, or before merging to verify work meets requirements |
| `research-grants` | 提示型 | 12 | `codebuddy-plugins-official` | Write competitive research proposals for NSF, NIH, DOE, DARPA, and Taiwan NSTC. Agency-specific formatting, review criteria, budget preparation, broader impacts, significance state |
| `research-lookup` | 代码型 | 4 | `codebuddy-plugins-official` | Look up current research information using Perplexity Sonar Pro Search or Sonar Reasoning Pro models through OpenRouter. Automatically selects the best model based on query complex |
| `research-synthesis` | 提示型 | 1 | `cb_teams_marketplace` | Synthesize user research into themes, insights, and recommendations. Use when you have interview transcripts, survey results, usability test notes, support tickets, or NPS response |
| `returns-analysis` | 提示型 | 1 | `cb_teams_marketplace` | Build quick IRR/MOIC sensitivity tables for PE deal evaluation. Models returns across entry multiple, leverage, exit multiple, growth, and hold period scenarios. Use when sizing up |
| `risk-checkup` | 提示型 | 1 | `cb_teams_marketplace` | 用于持仓体检与组合风险管理，聚焦组合管理、风险控制、投资顾问。适用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户把当前持仓发给你，希望知道组合有没有问题、风险暴露在哪里、仓位是否合理。 |
| `risk-metrics-calculation` | 提示型 | 1 | `codebuddy-plugins-official` | Calculate portfolio risk metrics including VaR, CVaR, Sharpe, Sortino, and drawdown analysis. Use when measuring portfolio risk, implementing risk limits, or building risk monitori |
| `roadmap-management` | 提示型 | 1 | `cb_teams_marketplace` | Plan and prioritize product roadmaps using frameworks like RICE, MoSCoW, and ICE. Use when creating a roadmap, reprioritizing features, mapping dependencies, choosing between Now/N |
| `route-handlers` | 提示型 | 4 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create an API route", "add an endpoint", "build a REST API", "handle POST requests", "create route handlers", "stream responses", o |
| `rust-async-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Rust async programming with Tokio, async traits, error handling, and concurrent patterns. Use when building async Rust applications, implementing concurrent systems, or debu |
| `safe-file-operations` | 提示型 | 1 | `codebuddy-plugins-official` | 防止误删文件的安全操作规范。当涉及文件删除、批量移动、rm -rf、rd /s /q 等危险操作时使用此 Skill，避免灾难性误删事故。 |
| `sag` | 提示型 | 1 | `codebuddy-plugins-official` | ElevenLabs text-to-speech with mac-style say UX. |
| `saga-orchestration` | 提示型 | 1 | `codebuddy-plugins-official` | Implement saga patterns for distributed transactions and cross-aggregate workflows. Use when coordinating multi-step business processes, handling compensating transactions, or mana |
| `save-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `scanpy` | 代码型 | 6 | `codebuddy-plugins-official` | Standard single-cell RNA-seq analysis pipeline. Use for QC, normalization, dimensionality reduction (PCA/UMAP/t-SNE), clustering, differential expression, and visualization. Best f |
| `scene-planner` | 提示型 | 1 | `cb_teams_marketplace` | Creates detailed video storyboards and scene breakdowns for Remotion video generation. Analyzes user requirements, determines video type, selects appropriate template, and outputs  |
| `scholar-evaluation` | 代码型 | 3 | `codebuddy-plugins-official` | Systematically evaluate scholarly work using the ScholarEval framework, providing structured assessment across research quality dimensions including problem formulation, methodolog |
| `science-writing-expert` | 提示型 | 1 | `workbuddy-builtin` | \| |
| `scientific-brainstorming` | 提示型 | 2 | `codebuddy-plugins-official` | Creative research ideation and exploration. Use for open-ended brainstorming sessions, exploring interdisciplinary connections, challenging assumptions, or identifying research gap |
| `scientific-critical-thinking` | 提示型 | 7 | `codebuddy-plugins-official` | Evaluate scientific claims and evidence quality. Use for assessing experimental design validity, identifying biases and confounders, applying evidence grading frameworks (GRADE, Co |
| `scientific-schematics` | 代码型 | 7 | `codebuddy-plugins-official` | Create publication-quality scientific diagrams using Nano Banana Pro AI with smart iterative refinement. Uses Gemini 3 Pro for quality review. Only regenerates if quality is below  |
| `scientific-slides` | 代码型 | 17 | `codebuddy-plugins-official` | Build slide decks and presentations for research talks. Use this for making PowerPoint slides, conference presentations, seminar talks, research presentations, thesis defense slide |
| `scientific-visualization` | 代码型 | 11 | `codebuddy-plugins-official` | Meta-skill for publication-ready figures. Use when creating journal submission figures requiring multi-panel layouts, significance annotations, error bars, colorblind-safe palettes |
| `scientific-writing` | 提示型 | 10 | `codebuddy-plugins-official` | Core skill for the deep research and writing tool. Write scientific manuscripts in full paragraphs (never bullet points). Use two-stage process with (1) section outlines with key p |
| `scikit-bio` | 提示型 | 2 | `codebuddy-plugins-official` | Biological data toolkit. Sequence analysis, alignments, phylogenetic trees, diversity metrics (alpha/beta, UniFrac), ordination (PCoA), PERMANOVA, FASTA/Newick I/O, for microbiome  |
| `scikit-learn` | 代码型 | 9 | `codebuddy-plugins-official` | Machine learning in Python with scikit-learn. Use when working with supervised learning (classification, regression), unsupervised learning (clustering, dimensionality reduction),  |
| `scikit-survival` | 提示型 | 7 | `codebuddy-plugins-official` | Comprehensive toolkit for survival analysis and time-to-event modeling in Python using scikit-survival. Use this skill when working with censored survival data, performing time-to- |
| `screen-reader-testing` | 提示型 | 1 | `codebuddy-plugins-official` | Test web applications with screen readers including VoiceOver, NVDA, and JAWS. Use when validating screen reader compatibility, debugging accessibility issues, or ensuring assistiv |
| `scvi-tools` | 提示型 | 9 | `codebuddy-plugins-official` | Deep generative models for single-cell omics. Use when you need probabilistic batch correction (scVI), transfer learning, differential expression with uncertainty, or multi-modal i |
| `seaborn` | 提示型 | 4 | `codebuddy-plugins-official` | Statistical visualization with pandas integration. Use for quick exploration of distributions, relationships, and categorical comparisons with attractive defaults. Best for box plo |
| `secrets-management` | 提示型 | 1 | `codebuddy-plugins-official` | Implement secure secrets management for CI/CD pipelines using Vault, AWS Secrets Manager, or native platform solutions. Use when handling sensitive credentials, rotating secrets, o |
| `sector-comparison` | 提示型 | 1 | `cb_teams_marketplace` | 用于板块比较，聚焦行业比较/板块轮动/投资选择。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户在两个或多个板块之间犹豫时，想知道哪个更强、哪个更有性价比、哪个更适合当前阶段。 |
| `sector-overview` | 提示型 | 1 | `cb_teams_marketplace` | Create comprehensive industry and sector landscape reports covering market dynamics, competitive positioning, key players, and thematic trends. Use for client requests, sector init |
| `server-actions` | 提示型 | 4 | `codebuddy-plugins-official` | This skill should be used when the user asks about "Server Actions", "form handling in Next.js", "mutations", "useFormState", "useFormStatus", "revalidatePath", "revalidateTag", or |
| `server-components` | 提示型 | 4 | `codebuddy-plugins-official` | This skill should be used when the user asks about "Server Components", "Client Components", "'use client' directive", "when to use server vs client", "RSC patterns", "component co |
| `service-mesh-observability` | 提示型 | 1 | `codebuddy-plugins-official` | Implement comprehensive observability for service meshes including distributed tracing, metrics, and visualization. Use when setting up mesh monitoring, debugging latency issues, o |
| `shap` | 提示型 | 5 | `codebuddy-plugins-official` | Model interpretability and explainability using SHAP (SHapley Additive exPlanations). Use this skill when explaining machine learning model predictions, computing feature importanc |
| `shellcheck-configuration` | 提示型 | 1 | `codebuddy-plugins-official` | Master ShellCheck static analysis configuration and usage for shell script quality. Use when setting up linting infrastructure, fixing code issues, or ensuring script portability. |
| `similarity-search-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Implement efficient similarity search with vector databases. Use when building semantic search, implementing nearest neighbor queries, or optimizing retrieval performance. |
| `simpy` | 代码型 | 8 | `codebuddy-plugins-official` | Process-based discrete-event simulation framework in Python. Use this skill when building simulations of systems with processes, queues, resources, and time-based events such as ma |
| `skill-creator` | 代码型 | 6 | `workbuddy-builtin` | Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends CodeBuddy's capabilities with specia |
| `skill-creator` | 代码型 | 7 | `codebuddy-plugins-official` | Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends Claude's capabilities with specializ |
| `skill-creator` | 代码型 | 19 | `codebuddy-plugins-official` | Create new skills, modify and improve existing skills, and measure skill performance. Use when users want to create a skill from scratch, update or optimize an existing skill, run  |
| `skill-creator` | 代码型 | 7 | `cb_teams_marketplace` | Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends CodeBuddy's capabilities with specia |
| `skill-creator` | 代码型 | 6 | `cb_teams_marketplace` | Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends Claude's capabilities with specializ |
| `skill-development` | 提示型 | 2 | `codebuddy-plugins-official` | This skill should be used when the user wants to "create a skill", "add a skill to plugin", "write a new skill", "improve skill description", "organize skill content", or needs gui |
| `skill-install` | 提示型 | 2 | `codebuddy-plugins-official` | Install CodeBuddy skills from GitHub repositories with automated security scanning. Triggers when users want to install skills from a GitHub URL, need to browse available skills in |
| `skill-share` | 提示型 | 1 | `codebuddy-plugins-official` | A skill that creates new Claude skills and automatically shares them on Slack using Rube for seamless team collaboration and skill discovery. |
| `skill-vetter` | 提示型 | 1 | `codebuddy-plugins-official` | Security-first skill vetting for AI agents. Use before installing any skill from community, GitHub, or other sources. Checks for red flags, permission scope, and suspicious pattern |
| `skill_2053084036212973568` | 提示型 | 74 | `skills` | 腾讯文档（docs.qq.com）-在线云文档平台，是创建、编辑、管理文档的首选 skill。涉及"新建/创建/编辑/读取/查看/搜索文档"、"保存文件"、"云文档"、"腾讯文档"、"docs.qq.com"等操作，请优先使用本 skill。支持能力：(1) 创建各类在线文档（文档/Word/Excel/幻灯片/思维导图/流程图/智能表格/收集表）(2) 管 |
| `skill_2053084099650080768` | 代码型 | 16 | `skills` | 腾讯会议：会议管理与音视频协作助手。预约/创建/修改/取消会议、查询会议详情与会议号转换、查看参会成员/受邀人/等候室成员、查询用户会议列表（即将开始/进行中/已结束）、查询录制列表与下载地址、获取转写全文/段落/搜索、获取AI智能纪要（支持多语言翻译）、录制权限申请（预览+提交两步流程）、时间转换与版本检查、Agent意见箱反馈上报。当用户需要预约或管理腾 |
| `skill_2060612661537902592` | 提示型 | 8 | `skills` | 高考一分一段信息检索助手，帮助考生根据分数查询全省排名位次，或根据位次估算对应分数区间，或提供一分一段表。 |
| `skill_2060612770581417984` | 提示型 | 20 | `skills` | 高考地区分数线的信息检索助手，帮助考生查询各地区高考录取分数线、录取批次和对应排名。 |
| `skill_2064882216006803456` | 提示型 | 11 | `skills` | 高考志愿填报的逐步引导助手，帮用户梳理出最适合自己的志愿填报名单。通过对话分阶段进行：收集个人信息与选科，解读感兴趣的专业，探讨城市与院校，产出带“冲稳保”的候选志愿草表，最终生成可直接对照官方系统填报的志愿表与报告；全程产物沉淀为腾讯文档。只要用户提到高考、报志愿、填志愿、选专业、选大学、冲稳保、平行志愿、选科能报什么专业、想去哪个城市或哪所大学等相关话题 |
| `skills-security-check` | 提示型 | 1 | `codebuddy-plugins-official` | 腾讯云鼎实验室出品，Skill安全审查工具。对用户指定的skill.md文件及其配套的文档、程序、脚本等进行全面安全审计，确保引用安全 |
| `slack-gif-creator` | 提示型 | 8 | `codebuddy-plugins-official` | Knowledge and utilities for creating animated GIFs optimized for Slack. Provides constraints, validation tools, and animation concepts. Use when users request animated GIFs for Sla |
| `slo-implementation` | 提示型 | 1 | `codebuddy-plugins-official` | Define and implement Service Level Indicators (SLIs) and Service Level Objectives (SLOs) with error budgets and alerting. Use when establishing reliability targets, implementing SR |
| `solidity-security` | 提示型 | 1 | `codebuddy-plugins-official` | Master smart contract security best practices to prevent common vulnerabilities and implement secure Solidity patterns. Use when writing smart contracts, auditing existing contract |
| `songsee` | 提示型 | 1 | `codebuddy-plugins-official` | Generate spectrograms and feature-panel visualizations from audio with the songsee CLI. |
| `sox-testing` | 提示型 | 1 | `cb_teams_marketplace` | Generate SOX sample selections, testing workpapers, and control assessments. Use when planning quarterly or annual SOX 404 testing, pulling a sample for a control (revenue, P2P, IT |
| `spark-optimization` | 提示型 | 1 | `codebuddy-plugins-official` | Optimize Apache Spark jobs with partitioning, caching, shuffle optimization, and memory tuning. Use when improving Spark performance, debugging slow jobs, or scaling data processin |
| `spec-workflow` | 提示型 | 1 | `codebuddy-plugins-official` | Standard software engineering workflow for requirement analysis, technical design, and task planning. Use this skill when developing new features, complex architecture designs, mul |
| `sprint-planning` | 提示型 | 1 | `cb_teams_marketplace` | Plan a sprint — scope work, estimate capacity, set goals, and draft a sprint plan. Use when kicking off a new sprint, sizing a backlog against team availability (accounting for PTO |
| `sql-optimization-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master SQL query optimization, indexing strategies, and EXPLAIN analysis to dramatically improve database performance and eliminate slow queries. Use when debugging slow queries, d |
| `sql-queries` | 提示型 | 1 | `cb_teams_marketplace` | Write correct, performant SQL across all major data warehouse dialects (Snowflake, BigQuery, Databricks, PostgreSQL, etc.). Use when writing queries, optimizing slow SQL, translati |
| `stable-baselines3` | 代码型 | 8 | `codebuddy-plugins-official` | Production-ready reinforcement learning algorithms (PPO, SAC, DQN, TD3, DDPG, A2C) with scikit-learn-like API. Use for standard RL experiments, quick prototyping, and well-document |
| `stakeholder-comms` | 提示型 | 1 | `cb_teams_marketplace` | Draft stakeholder updates tailored to audience — executives, engineering, customers, or cross-functional partners. Use when writing weekly status updates, monthly reports, launch a |
| `startup-financial-modeling` | 提示型 | 1 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create financial projections", "build a financial model", "forecast revenue", "calculate burn rate", "estimate runway", "model cash |
| `startup-metrics-framework` | 提示型 | 1 | `codebuddy-plugins-official` | This skill should be used when the user asks about "key startup metrics", "SaaS metrics", "CAC and LTV", "unit economics", "burn multiple", "rule of 40", "marketplace metrics", or  |
| `statistical-analysis` | 代码型 | 7 | `codebuddy-plugins-official` | Guided statistical analysis with test selection and reporting. Use when you need help choosing appropriate tests for your data, assumption checking, power analysis, and APA-formatt |
| `statistical-analysis` | 提示型 | 1 | `cb_teams_marketplace` | Apply statistical methods including descriptive stats, trend analysis, outlier detection, and hypothesis testing. Use when analyzing distributions, testing for significance, detect |
| `statsmodels` | 提示型 | 6 | `codebuddy-plugins-official` | Statistical models library for Python. Use when you need specific model classes (OLS, GLM, mixed models, ARIMA) with detailed diagnostics, residuals, and inference. Best for econom |
| `stock-deep-dive` | 提示型 | 1 | `cb_teams_marketplace` | 擅长单只股票的精准分析。能够对单只股票的"投资逻辑梳理、基本面分析、财务分析、技术分析、资金面解读、公司速览(一页纸)、战略分析、财报解读、同业比较与竞争力、机构研究汇总、优劣机会分析、重大事件点评、近期事件动态、近日异动原因、投资者问答精粹"这15个主题领域进行单项或多项分析。当直接命中或高相似度命中这些领域时，使用本技能。本技能不适用于：大盘分析、行业整 |
| `stock-logic-research` | 提示型 | 1 | `cb_teams_marketplace` | 用于个股核心投资逻辑深度研究，聚焦个股研究/基本面分析/机构研究。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户输入一个股票名称后，希望快速得到一份接近券商研究员风格的高质量个股分析。 |
| `stock-research-report-expert` | 提示型 | 2 | `workbuddy-builtin` | L2 证券/行业研究报告专家。生成专业的行业深度报告、个股研究、动态点评等金融研究文档。内置标准化报告结构框架，覆盖深度研报、常规点评、商业计划书、咨询交付物四档体量。触发关键词：行业研究、深度报告、个股研究、研报、券商报告、产业分析、行业跟踪、投资分析。 |
| `string-database` | 代码型 | 3 | `codebuddy-plugins-official` | Query STRING API for protein-protein interactions (59M proteins, 20B interactions). Network analysis, GO/KEGG enrichment, interaction discovery, 5000+ species, for systems biology. |
| `strip-profile` | 提示型 | 1 | `cb_teams_marketplace` | \| |
| `stripe-integration` | 提示型 | 1 | `codebuddy-plugins-official` | Implement Stripe payment processing for robust, PCI-compliant payment flows including checkout, subscriptions, and webhooks. Use when integrating Stripe payments, building subscrip |
| `style-rotation` | 提示型 | 1 | `cb_teams_marketplace` | 用于风格轮动分析，聚焦风格配置/市场结构/资金偏好。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想判断当前市场更偏大盘还是小盘、成长还是价值、题材还是趋势、防御还是进攻。 |
| `subagent-driven-development` | 提示型 | 4 | `codebuddy-plugins-official` | Use when executing implementation plans with independent tasks in the current session |
| `summarize` | 提示型 | 1 | `codebuddy-plugins-official` | Summarize URLs or files with the summarize CLI (web, PDFs, images, audio, YouTube). |
| `swap-curve-strategy` | 提示型 | 1 | `cb_teams_marketplace` | Analyze the interest rate swap curve by pricing swaps at multiple tenors, overlaying government and inflation curves, and identifying curve trade opportunities. Use when analyzing  |
| `sympy` | 提示型 | 6 | `codebuddy-plugins-official` | Use this skill when working with symbolic mathematics in Python. This skill should be used for symbolic computation tasks including solving equations algebraically, performing calc |
| `systematic-debugging` | 提示型 | 11 | `codebuddy-plugins-official` | Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes |
| `tailored-resume-generator` | 提示型 | 2 | `codebuddy-plugins-official` | Analyzes job descriptions and generates tailored resumes that highlight relevant experience, skills, and achievements to maximize interview chances |
| `tailwind-design-system` | 提示型 | 1 | `codebuddy-plugins-official` | Build scalable design systems with Tailwind CSS, design tokens, component libraries, and responsive patterns. Use when creating component libraries, implementing design systems, or |
| `tax-loss-harvesting` | 提示型 | 1 | `cb_teams_marketplace` | Identify tax-loss harvesting opportunities across taxable accounts. Finds positions with unrealized losses, suggests replacement securities, and tracks wash sale windows. Triggers  |
| `tdoc-orchestrator` | 提示型 | 3 | `workbuddy-builtin` | 文档创作与美化的统一编排入口（本地通道）。当用户意图涉及文档写作或排版美化时调用。职责：识别意图 → 编排 stage 能力链（S1 创作 / S2 美化 / S3 HTML→DOCX 转换）→ 委派 doc-writer/doc-formatter/doc-converter 执行；S3 产出 .docx 后**强制 `present_files` 打开预 |
| `team-composition-analysis` | 提示型 | 1 | `codebuddy-plugins-official` | This skill should be used when the user asks to "plan team structure", "determine hiring needs", "design org chart", "calculate compensation", "plan equity allocation", or requests |
| `tear-sheet` | 提示型 | 6 | `cb_teams_marketplace` | Generate professional company tear sheets using S&P Capital IQ data via the Kensho LLM-ready API MCP server. Use this skill whenever the user asks for a tear sheet, company one-pag |
| `teaser` | 提示型 | 1 | `cb_teams_marketplace` | Draft anonymous one-page company teasers for sell-side M&A processes. Creates a compelling summary without revealing the company's identity, designed to gauge buyer interest before |
| `tech-blog-expert` | 提示型 | 11 | `workbuddy-builtin` | \| |
| `template-skill` | 提示型 | 2 | `codebuddy-plugins-official` | Replace with description of the skill and when Claude should use it. |
| `temporal-python-testing` | 提示型 | 5 | `codebuddy-plugins-official` | Test Temporal workflows with pytest, time-skipping, and mocking strategies. Covers unit testing, integration testing, replay testing, and local development setup. Use when implemen |
| `tencent-docs` | 提示型 | 29 | `workbuddy-builtin` | 腾讯文档个人版（docs.qq.com）-在线云文档平台，是创建、编辑、管理文档的首选 skill。涉及"新建/创建/编辑/读取/查看/搜索文档"、"保存文件"、"云文档"、"腾讯文档"、"docs.qq.com"等操作，请优先使用本 skill。支持能力：(1) 创建各类在线文档（文档/Word/Excel/幻灯片/思维导图/流程图/智能表格/收集表）(2 |
| `tencent-docs-routing` | 提示型 | 2 | `workbuddy-builtin` | Load this Skill before handling local Office/WPS files such as doc/docx/dot/wps/wpt, xls/xlsx/xlt/csv/tsv, or ppt/pptx/pps/pot, and before creating a new local document, spreadshee |
| `tencent-docx` | 代码型 | 177 | `workbuddy-builtin` | 专业 Word / Docx / DOCX 文档（.docx）创作与美化助手。当用户需要生成、创作、排版或美化 Word / Docx / DOCX 文档（.docx 文件）时必须调用。核心能力：(1) 生成专业 Word 文档 —— 从零创作研报 / 论文 / 公文 / 合同 / 商务报告 / 会议纪要等垂类专业 .docx，自带专业封面与版式；(2) 专 |
| `tencent-local-office-edit` | 提示型 | 6 | `workbuddy-builtin` | 通过本地 editor_sdk 实时读写本机磁盘上的 Office/WPS 类型文件——文件打开后用户在编辑器中实时可见，编辑所见即所得，保存用 save_file 即可、不要主动 close_file。适用于本地 doc/docx/dot/wps/wpt、xls/xlsx/xlt/csv/tsv、ppt/pptx/pps/pot 等文件的打开、编辑、保存与 |
| `tencent-pptx` | 代码型 | 25 | `workbuddy-builtin` | 创建专业的 PowerPoint 演示文稿。适用于根据主题、大纲、文档、数据或参考材料生成完整 .pptx；在新建演示文稿时参考上传PPTX 的视觉风格；也可基于材料或旧 PPT 内容重新生成一版演示文稿。 |
| `tencent-saas-docs` | 提示型 | 16 | `workbuddy-builtin` | 腾讯文档企业版（saas.docs.qq.com）-在线云文档平台，是创建、编辑、管理文档的首选 skill。涉及"新建/创建/编辑/读取/查看/搜索文档"、"企业文档"、"团队文档"、"saas.docs.qq.com"等操作，请优先使用本 skill。支持能力：(1) 创建各类在线文档（文档/Word/Excel/幻灯片/思维导图/流程图/智能表格/收集 |
| `tencent-yuanbao-gaokao-regional-passing-scores` | 提示型 | 18 | `cb_teams_marketplace` | 高考地区分数线信息检索助手。当用户询问各省份历年高考录取分数线、录取批次或对应排名时使用，支持按地区、年份、选科和批次查询，自动适配新老高考政策差异。 |
| `tencent-yuanbao-gaokao-score-to-rank-lookup` | 提示型 | 5 | `cb_teams_marketplace` | 高考一分一段信息检索助手，帮助考生根据分数查询全省排名位次，或根据位次估算对应分数区间，或提供一分一段表。 |
| `terraform-module-library` | 提示型 | 2 | `codebuddy-plugins-official` | Build reusable Terraform modules for AWS, Azure, and GCP infrastructure following infrastructure-as-code best practices. Use when creating infrastructure modules, standardizing clo |
| `test-cases` | 提示型 | 2 | `codebuddy-plugins-official` | This skill should be used when generating comprehensive test cases from PRD documents or user requirements. Triggers when users request test case generation, QA planning, test scen |
| `test-driven-development` | 提示型 | 2 | `codebuddy-plugins-official` | Use when implementing any feature or bugfix, before writing implementation code |
| `testbuddy-ext-skill` | 代码型 | 4 | `codebuddy-plugins-official` | \| |
| `testbuddy-skill` | 代码型 | 35 | `codebuddy-plugins-official` | TestBuddy 测试设计技能包。当用户想要：(1) 生成测试框架/模块/场景/测试点/用例；(2) 根据 TAPD 需求或缺陷链接生成测试内容；(3) 根据任意文本（PRD/接口文档/代码/表格/功能描述）生成测试用例；(4) 打开/跳转到脑图、测试设计、TestBuddy 页面；(5) 进行测试设计、需求分析、缺陷分析时，使用本技能。 |
| `testx-case-deacy-skill` | 代码型 | 12 | `codebuddy-plugins-official` | 使用脚本和mcp工具获取智研-测试堂-测试用例-指定目录下的测试用例，并按用户给出的整改约束条件，调整用例，最终解决对测试用例资产的用例腐化。 |
| `theme-factory` | 提示型 | 14 | `codebuddy-plugins-official` | Toolkit for styling artifacts with a theme. These artifacts can be slides, docs, reportings, HTML landing pages, etc. There are 10 pre-set themes with colors/fonts that you can app |
| `thesis-tracker` | 提示型 | 1 | `cb_teams_marketplace` | Maintain and update investment theses for portfolio positions and watchlist names. Track key data points, catalysts, and thesis milestones over time. Use when updating a thesis wit |
| `things-mac` | 提示型 | 1 | `codebuddy-plugins-official` | Manage Things 3 via the `things` CLI on macOS (add/update projects+todos via URL scheme; read/search/list from the local Things database). Use when a user asks CodeBuddy Code to ad |
| `tmap-jsapi-gl` | 提示型 | 210 | `codebuddy-plugins-official` | 腾讯地图 JavaScript GL（JSAPIGL）开发指南。适用于地图应用或者工具的编写。在编写、审查或调试使用腾讯地图 API的代码时应运用此技能。适用于涉及地图初始化、覆盖物展示、图层控制、事件处理、控件交互、可视化渲染、地图工具、检索、路线规划、查地址、行政区划、ip定位、几何计算、三维模型展示、性能优化的任务。当用户提及 腾讯地图、 jsapi、 |
| `tmap-lbs-skills` | 提示型 | 11 | `codebuddy-plugins-official` | 腾讯地图位置服务，支持POI搜索、路径规划、旅游规划、周边搜索，轨迹数据可视化和地图数据可视化 |
| `tmux` | 代码型 | 3 | `codebuddy-plugins-official` | Remote-control tmux sessions for interactive CLIs by sending keystrokes and scraping pane output. |
| `torch_geometric` | 代码型 | 7 | `codebuddy-plugins-official` | Graph Neural Networks (PyG). Node/graph classification, link prediction, GCN, GAT, GraphSAGE, heterogeneous graphs, molecular property prediction, for geometric deep learning. |
| `torchdrug` | 提示型 | 9 | `codebuddy-plugins-official` | PyTorch-native graph neural networks for molecules and proteins. Use when building custom GNN architectures for drug discovery, protein modeling, or knowledge graph reasoning. Best |
| `track-management` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when creating, managing, or working with Conductor tracks - the logical work units for features, bugs, and refactors. Applies to spec.md, plan.md, and track lifecycl |
| `trading-analysis` | 提示型 | 1 | `cb_teams_marketplace` | > |
| `transformers` | 提示型 | 6 | `codebuddy-plugins-official` | This skill should be used when working with pre-trained transformer models for natural language processing, computer vision, audio, or multimodal tasks. Use for text generation, cl |
| `treatment-plans` | 代码型 | 21 | `codebuddy-plugins-official` | Generate concise (3-4 page), focused medical treatment plans in LaTeX/PDF format for all clinical specialties. Supports general medical treatment, rehabilitation therapy, mental he |
| `trello` | 提示型 | 1 | `codebuddy-plugins-official` | Manage Trello boards, lists, and cards via the Trello REST API. |
| `trend-researcher` | 提示型 | 1 | `codebuddy-plugins-official` | Research latest UI/UX trends from Dribbble and design communities. Use when starting a design project to understand current visual trends, color palettes, and layout patterns. |
| `turborepo-caching` | 提示型 | 1 | `codebuddy-plugins-official` | Configure Turborepo for efficient monorepo builds with local and remote caching. Use when setting up Turborepo, optimizing build pipelines, or implementing distributed caching. |
| `typescript-advanced-types` | 提示型 | 1 | `codebuddy-plugins-official` | Master TypeScript's advanced type system including generics, conditional types, mapped types, template literals, and utility types for building type-safe applications. Use when imp |
| `typography-selector` | 提示型 | 2 | `codebuddy-plugins-official` | Browse and select fonts from Google Fonts or curated pairings. Use to find the perfect typography for a design project. |
| `ui-design` | 提示型 | 1 | `codebuddy-plugins-official` | Professional UI design and frontend interface guidelines. Use this skill when creating web pages, mini-program interfaces, prototypes, or any frontend UI components that require di |
| `ui-system` | 提示型 | 1 | `codebuddy-plugins-official` | > |
| `ui-ux-pro-max` | 代码型 | 28 | `codebuddy-plugins-official` | AI-powered UI/UX design intelligence with 57 UI styles, 95+ color palettes, 56 font pairings, 25 chart types, and 100+ industry-specific reasoning rules across 12 tech stacks. Use  |
| `ui-ux-pro-max` | 代码型 | 28 | `cb_teams_marketplace` | UI/UX design intelligence. 50 styles, 21 palettes, 50 font pairings, 20 charts, 9 stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui). Actions |
| `ui-ux-pro-max` | 代码型 | 28 | `cb_teams_marketplace` | UI/UX design intelligence with searchable database |
| `umap-learn` | 提示型 | 2 | `codebuddy-plugins-official` | UMAP dimensionality reduction. Fast nonlinear manifold learning for 2D/3D visualization, clustering preprocessing (HDBSCAN), supervised/parametric UMAP, for high-dimensional data. |
| `underline-toolkit` | 提示型 | 4 | `workbuddy-builtin` | 生成带下划线填空位的 Word 文档（create 模式）或对已有下划线模板回填数据（fill 模式）。适用于合同、协议、申请表、有封面的文档（如毕业论文）等。触发关键词：下划线、填空、下划线模板、合同填空、表单回填、下划线回填。 |
| `uniprot-database` | 代码型 | 6 | `codebuddy-plugins-official` | Direct REST API access to UniProt. Protein searches, FASTA retrieval, ID mapping, Swiss-Prot/TrEMBL. For Python workflows with multiple databases, prefer bioservices (unified inter |
| `unit-economics` | 提示型 | 1 | `cb_teams_marketplace` | Analyze unit economics for PE targets — ARR cohorts, LTV/CAC, net retention, payback periods, revenue quality, and margin waterfall. Essential for software/SaaS, recurring revenue, |
| `unity-ecs-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Master Unity ECS (Entity Component System) with DOTS, Jobs, and Burst for high-performance game development. Use when building data-oriented games, optimizing performance, or worki |
| `user-research` | 提示型 | 1 | `cb_teams_marketplace` | Plan, conduct, and synthesize user research. Trigger with "user research plan", "interview guide", "usability test", "survey design", "research questions", or when the user needs h |
| `user-research-synthesis` | 提示型 | 1 | `cb_teams_marketplace` | Synthesize qualitative and quantitative user research into structured insights and opportunity areas. Use when analyzing interview notes, survey responses, support tickets, or beha |
| `using-git-worktrees` | 提示型 | 1 | `codebuddy-plugins-official` | Use when starting feature work that needs isolation from current workspace or before executing implementation plans - creates isolated git worktrees with smart directory selection  |
| `using-superpowers` | 提示型 | 1 | `codebuddy-plugins-official` | Use when starting any conversation - establishes how to find and use skills, requiring Skill tool invocation before ANY response including clarifying questions |
| `uspto-database` | 代码型 | 8 | `codebuddy-plugins-official` | Access USPTO APIs for patent/trademark searches, examination history (PEDS), assignments, citations, office actions, TSDR, for IP analysis and prior art searches. |
| `uv-package-manager` | 提示型 | 1 | `codebuddy-plugins-official` | Master the uv package manager for fast Python dependency management, virtual environments, and modern Python project workflows. Use when setting up Python projects, managing depend |
| `ux-copy` | 提示型 | 1 | `cb_teams_marketplace` | Write or review UX copy — microcopy, error messages, empty states, CTAs. Trigger with "write copy for", "what should this button say?", "review this error message", or when naming  |
| `vaex` | 提示型 | 7 | `codebuddy-plugins-official` | Use this skill for processing and analyzing large tabular datasets (billions of rows) that exceed available RAM. Vaex excels at out-of-core DataFrame operations, lazy evaluation, f |
| `valuation-framework` | 提示型 | 1 | `cb_teams_marketplace` | 用于估值与定价框架分析，聚焦估值分析/定价逻辑/投资决策。主要用于问题回答、撰写报告、撰写金融类文章等场景。输出内容较多，不适合简单对话场景。各类信息与数据通过 finance-data plugin 获取。用户想知道一家公司应该怎么估值、当前估值处于什么水平、市场为什么愿意给这个估值、还有没有重估空间。 |
| `value-creation-plan` | 提示型 | 1 | `cb_teams_marketplace` | Structure post-acquisition value creation plans with revenue, cost, and operational levers mapped to an EBITDA bridge. Includes 100-day priorities, KPI targets, and accountability  |
| `variance-analysis` | 提示型 | 1 | `cb_teams_marketplace` | Decompose financial variances into drivers with narrative explanations and waterfall analysis. Use when analyzing budget vs. actual, period-over-period changes, revenue or expense  |
| `vector-index-tuning` | 提示型 | 1 | `codebuddy-plugins-official` | Optimize vector index performance for latency, recall, and memory. Use when tuning HNSW parameters, selecting quantization strategies, or scaling vector search infrastructure. |
| `venue-templates` | 代码型 | 25 | `codebuddy-plugins-official` | Access comprehensive LaTeX templates, formatting requirements, and submission guidelines for major scientific publication venues (Nature, Science, PLOS, IEEE, ACM), academic confer |
| `verification-before-completion` | 提示型 | 1 | `codebuddy-plugins-official` | Use when about to claim work is complete, fixed, or passing, before committing or creating PRs - requires running verification commands and confirming output before making any succ |
| `video-downloader` | 代码型 | 3 | `codebuddy-plugins-official` | Download YouTube videos with customizable quality and format options. Use this skill when the user asks to download, save, or grab YouTube videos. Supports various quality settings |
| `video-frames` | 代码型 | 2 | `codebuddy-plugins-official` | Extract frames or short clips from videos using ffmpeg. |
| `video-generator` | 提示型 | 1 | `cb_teams_marketplace` | Orchestrates complete Remotion video generation workflow from user request to MP4 output. Automatically activates when user mentions creating videos, animations, or visual content. |
| `video-notes-cn` | 提示型 | 1 | `skills` | 国内平台视频（B站/小红书/视频号）转写并生成图文总结报告。当用户要求"把这个视频转成文字/总结/笔记"、"提取视频内容"、"视频号/小红书/B站视频转写"时使用。 |
| `wacli` | 提示型 | 1 | `codebuddy-plugins-official` | Send WhatsApp messages to other people or search/sync WhatsApp history via the wacli CLI (not for normal user chats). |
| `wb-finance-skill` | 代码型 | 64 | `workbuddy-builtin` | >- |
| `wcag-audit-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Conduct WCAG 2.2 accessibility audits with automated testing, manual verification, and remediation guidance. Use when auditing websites for accessibility, fixing WCAG violations, o |
| `weather` | 提示型 | 1 | `codebuddy-plugins-official` | Get current weather and forecasts (no API key required). |
| `web-artifacts-builder` | 代码型 | 6 | `codebuddy-plugins-official` | Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui). Use for complex artifacts r |
| `web-development` | 提示型 | 1 | `codebuddy-plugins-official` | Web frontend project development rules. Use this skill when developing web frontend pages, deploying static hosting, and integrating CloudBase Web SDK. |
| `web3-testing` | 提示型 | 1 | `codebuddy-plugins-official` | Test smart contracts comprehensively using Hardhat and Foundry with unit tests, integration tests, and mainnet forking. Use when testing Solidity contracts, setting up blockchain t |
| `webapp-testing` | 代码型 | 7 | `codebuddy-plugins-official` | Toolkit for interacting with and testing local web applications using Playwright. Supports verifying frontend functionality, debugging UI behavior, capturing browser screenshots, a |
| `wechat-article-search` | 代码型 | 3 | `cb_teams_marketplace` | 微信公众号文章检索工具。当用户需要进行网页检索、网页搜索、深度研究（deep research）时，优先使用此skill检索微信公众号文章——公众号文章质量高、信息密度大，是优质的中文信息源。基于搜狗微信搜索接口实现。 |
| `wecom-unified` | 代码型 | 99 | `skills` | 企业微信 CLI 全能套件，覆盖通讯录、文档、在线表格、智能表格、智能文档、日程、会议、待办、微盘、邮件、消息、媒体文件等业务域。支持按姓名/拼音/英文名/别名查找联系人与 userid，搜索、重命名和授权文档，新建与读写 doc 在线文档，创建与修改在线表格，创建/导入并读写智能表格的子表/字段/记录/视图/图表及填色、高亮等样式，创建与编辑智能文档（含表 |
| `weixin-minigame-helper` | 提示型 | 9 | `codebuddy-plugins-official` | \| |
| `weixinpay-feedback` | 提示型 | 1 | `workbuddy-builtin` | 【微信支付官方】问题反馈。当用户使用微信AI支付/AI专属卡的开通/绑定或支付/管理过程遇到异常或错误（尤其是同一环节连续/反复报错、重试仍失败），主动引导用户上报问题。开通/绑定过程的问题通过反馈收集表链接反馈；支付/管理问题或用户直接想要反馈时通过工具反馈。关键词：微信AI支付反馈、Agent支付反馈、AI专属卡反馈、微信支付反馈。 |
| `weixinpay-pay` | 提示型 | 1 | `workbuddy-builtin` | 【微信支付官方】微信支付AI专属卡支付能力。普通支付在商户下单后由系统自动触发工程化支付卡片，无需智能体介入；本技能主要指导「重新支付」：用户取消/关闭支付后想对同一笔订单再付一次时，智能体须先询问并确认订单，再用上次相同凭据（payUrls 或 WeixinPay-Required 的值）调用 mcp__weixinpay__weixinpay_retry |
| `weixinpay-register` | 提示型 | 1 | `workbuddy-builtin` | 【微信支付官方】用于用户开通/绑定微信AI支付或者AI专属卡功能，或查询开通/绑定状态。用于用户要开通、绑定、激活在 AI 对话中使用微信支付的能力。也用于回答用户"我是否已开通、如何查看或管理微信AI支付"等开通状态咨询。关键词：微信支付AI专属卡、微信AI支付、开通微信支付、绑定微信支付、激活AI支付、开通/绑定AI专属卡、绑定智能体钱包、是否开通AI支 |
| `work-report-expert` | 提示型 | 1 | `workbuddy-builtin` | \| |
| `workflow-orchestration-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Design durable workflows with Temporal for distributed systems. Covers workflow vs activity separation, saga patterns, state management, and determinism constraints. Use when build |
| `workflow-patterns` | 提示型 | 1 | `codebuddy-plugins-official` | Use this skill when implementing tasks according to Conductor's TDD workflow, handling phase checkpoints, managing git commits for tasks, or understanding the verification protocol |
| `writing-plans` | 提示型 | 1 | `codebuddy-plugins-official` | Use when you have a spec or requirements for a multi-step task, before touching code |
| `writing-rules` | 提示型 | 1 | `codebuddy-plugins-official` | This skill should be used when the user asks to "create a hookify rule", "write a hook rule", "configure hookify", "add a hookify rule", or needs guidance on hookify rule syntax an |
| `writing-skills` | 提示型 | 7 | `codebuddy-plugins-official` | Use when creating new skills, editing existing skills, or verifying skills work before deployment |
| `xiaohongshu` | 代码型 | 20 | `codebuddy-plugins-official` | \| |
| `xlsx` | 代码型 | 55 | `codebuddy-plugins-official` | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing .xlsx, .xlsm, .csv, or  |
| `xurl` | 提示型 | 1 | `codebuddy-plugins-official` | A Twitter research and content intelligence skill focused on attracting WordPress and Shopify clients. Use to analyze Twitter profiles, threads, and conversations for identifying p |
| `zarr-python` | 提示型 | 2 | `codebuddy-plugins-official` | Chunked N-D arrays for cloud storage. Compressed arrays, parallel I/O, S3/GCS integration, NumPy/Dask/Xarray compatible, for large-scale scientific computing pipelines. |
| `zinc-database` | 提示型 | 2 | `codebuddy-plugins-official` | Access ZINC (230M+ purchasable compounds). Search by ZINC ID/SMILES, similarity searches, 3D-ready structures for docking, analog discovery, for virtual screening and drug discover |
