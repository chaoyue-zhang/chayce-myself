# 🧠 个人知识图谱 — 定制指南

## 这是什么？

一个**交互式个人能力知识图谱**，帮助你：
- 📊 可视化展示你的技能、项目、经历之间的关联
- 🎯 快速匹配目标岗位的能力要求
- 💼 在投递简历时，给 HR 一个直观的能力全景图

## 🚀 快速开始

1. 用浏览器打开 `index.html` 即可看到示例图谱
2. 按下面的说明修改 `data.json`，替换为你自己的数据
3. 刷新页面即可看到你的个人知识图谱

> 💡 **推荐部署方式**：将 `index.html` 和 `data.json` 上传到 **GitHub Pages** / **Vercel** / **Netlify**，生成一个可分享的链接，直接附在简历上。

---

## 📝 数据模型说明

知识图谱由 **节点（Nodes）** 和 **边（Edges）** 组成：

### 6 种节点类型

| 类型 | category | 用途 | 示例 |
|------|----------|------|------|
| 🔧 技能 | `skill` | 编程语言、框架、工具、软技能 | React、Python、团队管理 |
| 📦 项目 | `project` | 工作项目、个人项目、开源贡献 | SaaS 管理平台、开源组件库 |
| 💼 经历 | `experience` | 工作经历、实习经历 | ABC科技 · 高级前端工程师 |
| 🎓 教育 | `education` | 学历、培训 | 计算机科学 · 本科 |
| 🌐 领域 | `domain` | 行业领域知识 | SaaS、低代码、金融科技 |
| 📜 证书 | `certificate` | 认证和资质 | AWS 认证、PMP |

### 5 种关系类型

| 类型 | type | 含义 | 示例 |
|------|------|------|------|
| 使用 | `uses` | 技能 → 项目 | React → SaaS平台（技能用于项目） |
| 属于 | `part_of` | 项目 → 经历 | SaaS平台 → ABC科技（项目属于某段经历） |
| 领域 | `domain_of` | 领域 → 项目 | SaaS → SaaS平台（项目属于某领域） |
| 认证 | `certifies` | 证书 → 技能 | AWS认证 → Docker（证书认证技能） |
| 关联 | `related_to` | 技能 → 技能 | React → TypeScript（技能之间的关联） |
| 发展 | `leads_to` | 经历 → 经历 | 初级 → 高级（职业发展路径） |

---

## ✏️ 如何定制

### 第 1 步：填写个人信息

打开 `data.json`，修改 `profile` 部分：

```json
{
  "profile": {
    "name": "你的名字",
    "title": "你的职位头衔",
    "summary": "一句话总结你的核心竞争力（建议50字以内）",
    "email": "你的邮箱",
    "github": "你的 GitHub 主页（可选）",
    "linkedin": "你的 LinkedIn 主页（可选）",
    "targetPositions": ["目标岗位1", "目标岗位2", "目标岗位3"]
  }
}
```

### 第 2 步：添加技能节点

```json
{
  "id": "s1",                    // 唯一ID，建议 s+序号
  "category": "skill",           // 固定为 skill
  "label": "React",              // 技能名称
  "level": 5,                    // 熟练度 1-5（会影响节点大小）
  "description": "精通 React Hooks、组件设计...",  // 能力描述
  "tags": ["前端", "框架"],       // 标签，用于搜索
  "icon": "⚛️"                   // Emoji 图标
}
```

#### 熟练度参考

| Level | 含义 | 节点效果 |
|-------|------|----------|
| 1 | 了解基础概念 | 最小圆点 |
| 2 | 能在指导下使用 | 较小圆点 |
| 3 | 独立使用 | 中等圆点 |
| 4 | 熟练，能指导他人 | 较大圆点 |
| 5 | 精通，能设计架构 | 最大圆点 |

### 第 3 步：添加项目节点

```json
{
  "id": "p1",
  "category": "project",
  "label": "企业级 SaaS 管理平台",
  "description": "从0到1搭建的B端SaaS平台...",
  "url": "https://github.com/your/project",
  "highlights": ["从0到1交付", "多租户架构", "日活10万+"],
  "tags": ["SaaS", "React"],
  "icon": "🏢"
}
```

### 第 4 步：添加经历节点

```json
{
  "id": "e1",
  "category": "experience",
  "label": "ABC科技 · 高级前端工程师",
  "period": "2023.03 - 至今",
  "description": "负责核心产品前端架构设计...",
  "tags": ["在职", "团队管理"],
  "icon": "💼"
}
```

### 第 5 步：添加教育节点

```json
{
  "id": "ed1",
  "category": "education",
  "label": "计算机科学与技术 · 本科",
  "school": "某985大学",
  "period": "2016.09 - 2020.06",
  "description": "GPA 3.7/4.0，校级优秀毕业生",
  "tags": ["985"],
  "icon": "🎓"
}
```

### 第 6 步：添加领域节点

```json
{
  "id": "d1",
  "category": "domain",
  "label": "SaaS 平台",
  "description": "对B端SaaS产品的商业模式、多租户架构有深入理解",
  "tags": ["B端", "企业服务"],
  "icon": "☁️"
}
```

### 第 7 步：添加证书节点

```json
{
  "id": "c1",
  "category": "certificate",
  "label": "AWS Certified Developer",
  "description": "AWS 认证开发者 - Associate 级别",
  "period": "2024",
  "tags": ["云计算", "认证"],
  "icon": "📜"
}
```

### 第 8 步：定义关系（边）

这是最关键的一步——关系让图"活"起来！

```json
// 技能用于项目
{ "from": "s1", "to": "p1", "type": "uses", "label": "核心使用" },

// 项目属于经历
{ "from": "p1", "to": "e1", "type": "part_of", "label": "在职主导" },

// 经历之间的发展
{ "from": "e1", "to": "e2", "type": "leads_to", "label": "晋升" },

// 证书认证技能
{ "from": "c1", "to": "s10", "type": "certifies", "label": "认证" },

// 技能之间的关联
{ "from": "s1", "to": "s3", "type": "related_to", "label": "强关联" },

// 领域与项目的关系
{ "from": "d1", "to": "p1", "type": "domain_of", "label": "领域" }
```

> ⚠️ **重要**：`from` 和 `to` 的值必须是已存在的节点 ID！

---

## 🎯 操作指南

| 操作 | 方式 |
|------|------|
| 🔍 搜索 | 顶部搜索框输入关键词，或按 `Ctrl+F` |
| 🏷️ 筛选 | 点击顶部分类按钮，只看某类节点 |
| 👆 查看详情 | 点击任意节点，右侧面板显示完整信息 |
| 🔗 跳转关联 | 在详情面板点击关联节点，自动聚焦 |
| 🔍 聚焦节点 | 双击节点放大查看 |
| 🖱️ 拖拽 | 拖拽节点调整位置 |
| 🔄 缩放 | 鼠标滚轮缩放 |
| 📸 导出图片 | 点击"导出图片"按钮 |
| ⎋ 重置 | 按 `Esc` 键恢复默认视图 |

---

## 💡 使用场景建议

### 场景 1：附在简历上
将部署后的链接放在简历的"个人主页"或"作品集"位置：
> 📎 个人能力知识图谱：https://your-name.github.io/knowledge-graph

### 场景 2：面试前发给 HR
在邮件或微信中分享链接，让 HR 快速了解你的能力体系：
> 您好，这是我的个人能力知识图谱，可以快速了解我的技术栈和项目经验：[链接]

### 场景 3：LinkedIn / 脉脉 个人主页
将链接放在社交媒体个人简介中。

### 场景 4：述职 / 晋升答辩
用图谱展示你的能力成长和项目关联，比 PPT 列表更有说服力。

---

## 🔧 进阶定制

### 修改颜色主题

在 `index.html` 中找到 `CATEGORY_COLORS`，修改各类型的颜色：

```javascript
const CATEGORY_COLORS = {
  skill:        { bg: '#6c5ce7', ... },  // 改成你喜欢的颜色
  project:      { bg: '#00b894', ... },
  // ...
};
```

### 调整布局

在 `index.html` 中找到 `physics` 配置：

```javascript
forceAtlas2Based: {
  springLength: 140,    // 节点间距（越大越分散）
  centralGravity: 0.005, // 中心引力
  // ...
}
```

---

## 📂 文件结构

```
knowledge-graph/
├── index.html      ← 主页面（直接用浏览器打开）
├── data.json       ← 你的数据（修改这个文件即可）
└── README.md       ← 本说明文档
```

---

## ❓ 常见问题

**Q: 能否不部署，直接用本地文件？**
A: 可以！直接用浏览器打开 `index.html` 即可。但因为浏览器安全策略，`fetch` 加载本地 JSON 可能失败。建议用 VS Code 的 Live Server 插件，或运行 `npx serve .` 启动本地服务器。

**Q: 如何分享给 HR？**
A: 推荐使用 GitHub Pages（免费）：把这两个文件上传到 GitHub 仓库，在 Settings → Pages 中启用，即可获得 `https://你的用户名.github.io/仓库名` 的链接。

**Q: 节点太多会不会很乱？**
A: 图谱支持物理布局自动排布，你也可以手动拖拽调整。建议核心技能控制在 8-15 个，项目控制在 3-8 个。