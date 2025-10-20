# ai-assistant
# AI助手管理系统

<div align="center">

一个功能完整的AI助手管理平台，支持智能任务分配、多助手协作和实时监控

 [![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) [![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)



------

## 中文

### 项目简介

AI助手管理系统是一个现代化的Web应用程序，用于统一管理和调度多个AI助手。系统提供了直观的可视化界面，支持任务的智能分配、多助手协作处理，以及详细的运行数据统计和日志追踪功能。

### 效果图

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/7df1f891-ccc8-4e3f-aad6-4311bdabb86f" />
数据中心
![dashboard](https://github.com/user-attachments/assets/b60665a4-06ca-4cd7-9e41-1e6da1f67ae3)

### 核心功能

#### 智能助手管理

- **助手CRUD操作**：创建、编辑、删除AI助手
- **多类型支持**：文本生成、图像处理、数据分析、语音识别
- **状态控制**：一键启动/停止助手服务
- **能力评分**：基于助手性能的评分系统

#### 任务队列管理

- **任务生命周期**：等待中 → 运行中 → 已完成/失败
- **智能分配**：自动匹配最优助手处理任务
- **多助手协作**：支持多个助手协同完成复杂任务
- **实时更新**：任务状态实时同步显示

#### 数据可视化

- **统计仪表盘**：助手数量、任务完成率、运行状态总览
- **饼图分析**：任务分布可视化（使用Chart.js）
- **详细统计**：成功率、平均评分等关键指标

#### 操作日志中心

- **完整记录**：所有操作的详细日志追踪
- **状态标记**：成功/失败状态清晰展示
- **时间轴**：按时间顺序查看操作历史

### 技术栈

#### 前端技术

- **HTML5 + CSS3**：现代化响应式布局
- **原生JavaScript (ES6+)**：无框架依赖，轻量高效
- **Chart.js 3.9.1**：数据可视化图表
- **Fetch API**：RESTful API交互

#### 后端接口

- **RESTful API**：标准化接口设计
- **端口配置**：`http://localhost:8080/api`
- **JSON数据交换**：统一数据格式

### 项目结构

```
ai-assistant-dashboard/
├── ai-assistant-dashboard.html  # 主页面
├── bg-img.png                   # 背景图片
├── README.md                    # 项目文档
└── api/                         # 后端API（需单独部署）
    ├── /stats                   # 统计数据
    ├── /assistant               # 助手管理
    ├── /task                    # 任务队列
    ├── /assign                  # 任务分配
    └── /log                     # 操作日志
```

### 快速开始

#### 前置要求

- 现代浏览器（Chrome 90+, Firefox 88+, Edge 90+）
- 后端API服务（需自行实现或使用Mock数据）

#### 安装步骤

1. **克隆项目**

```bash
git clone https://github.com/yourusername/ai-assistant-dashboard.git
cd ai-assistant-dashboard
```

1. **配置后端**

```javascript
// 在 ai-assistant-dashboard.html 中修改API地址
const BASE_URL = 'http://your-backend-url:8080/api';
```

1. **启动前端**

```bash
# 使用任意HTTP服务器
python -m http.server 8000
# 或
npx serve
```

1. **访问应用**

```
http://localhost:8000/ai-assistant-dashboard.html
```

### API接口说明

#### 统计接口

```http
GET /api/stats
```

返回系统统计数据：助手数量、任务状态、成功率等

#### 助手管理

```http
GET    /api/assistant           # 获取所有助手
GET    /api/assistant/{id}      # 获取单个助手
POST   /api/assistant           # 创建新助手
PUT    /api/assistant/{id}      # 更新助手
DELETE /api/assistant/{id}      # 删除助手
PUT    /api/assistant/{id}/start # 启动服务
PUT    /api/assistant/{id}/stop  # 停止服务
```

#### 任务管理

```http
GET  /api/task/queue            # 获取任务队列
POST /api/task                  # 创建新任务
PUT  /api/task/{id}/status      # 更新任务状态
```

#### 任务分配

```http
POST /api/assign/auto/{taskId}  # 自动分配
POST /api/assign/multi/{taskId} # 多助手协作
```

#### 日志接口

```http
GET /api/log                    # 获取所有日志
```

### 功能演示

#### 数据中心仪表盘

- 实时统计卡片展示
- 任务分布饼图（自定义配色）
- 待处理任务队列

#### 助手管理页面

- 表格化展示助手列表
- 在线/离线状态标识
- 快捷操作按钮

#### 任务管理视图

- 分状态展示（运行中/已完成）
- 智能分配与多助手协作
- 状态实时更新

#### 统计中心

- 多维度数据展示
- 助手性能指标
- 任务成功率分析

### 自定义配置

#### 修改主题色

```css
/* 在 <style> 标签中修改 */
.blue { color: #4285f4; }    /* 主色调 */
.green { color: #388e3c; }   /* 成功色 */
.orange { color: #f57c00; }  /* 警告色 */
.purple { color: #7b1fa2; }  /* 强调色 */
```

#### 调整图表配色

```javascript
// 在 updateTaskChart 函数中修改
const BACKGROUND_COLORS = [
    '#6c757d',  // 灰色 - 等待中
    '#6dca37',  // 绿色 - 运行中
    '#007bff',  // 蓝色 - 已完成
    '#ff4040'   // 红色 - 失败
];
```

------

<div align="center">

