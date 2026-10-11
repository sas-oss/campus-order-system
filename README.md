# 智慧校园食堂智能订餐系统（Campus Order System）

> 面向高校食堂的智能化在线订餐系统 · 软件工程综合实训项目（前后端分离全栈）

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-brightgreen)](https://spring.io/projects/spring-boot)
[![Vue](https://img.shields.io/badge/Vue-3.5-42b883)](https://vuejs.org/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)](https://www.mysql.com/)

## 项目简介

针对高校食堂用餐高峰期排队时间长、信息不对称等问题，设计并实现的在线订餐系统。系统采用前后端分离架构，后端 Spring Boot 3 + MyBatis-Plus，前端 Vue 3 + Element Plus，数据库 MySQL 8.0，并集成 DeepSeek 大模型实现 AI 智能点餐推荐。

系统支持三种角色：
- **学生**：浏览菜单、AI 智能推荐、购物车、在线下单、模拟支付、取餐码取餐
- **食堂管理员**：菜品管理、订单处理、扫码确认取餐、数据统计
- **系统管理员**：食堂窗口管理、用户管理、全局数据看板

## 技术栈

| 端 | 技术 |
|---|---|
| 后端 | Spring Boot 3.2.5 · MyBatis-Plus 3.5.5 · Spring Security · JWT · Knife4j(Swagger/OpenAPI) · WebSocket |
| 前端 | Vue 3.5 · Element Plus · Pinia · Vue Router · Axios · ECharts · Vite |
| 数据库 | MySQL 8.0 |
| AI | DeepSeek 大模型 API（兼容 OpenAI 风格，本地规则兜底降级） |
| 工具 | Git · Maven · JUnit 5 · JMeter · Linux |

## 我的分工（个人负责模块）

> 本项目为 6 人团队协作完成，以下为本人独立负责的模块：

- **需求规格说明书（SRS）主要编制**：参与 v1.0 → v3.0 三轮迭代，独立完成 FR-01 用户认证、FR-09 AI 智能功能两大模块的需求定义、用例规约（UC-01~04）与接口清单。
- **用户认证模块（FR-01）**：设计 5 个认证接口（注册/登录/获取用户信息/修改密码/更新资料），实现三角色统一登录、JWT 签发、路由守卫鉴权、个人中心。
- **AI 智能功能模块（FR-09）**：独立完成 AI 点餐助手、AI 今日推荐、偏好设置、AI 容错降级、AI 配置管理共 9 个子需求的前后端开发与 Prompt 指令链调优。
- **系统管理端用户管理**：用户列表分页/筛选、新增/编辑/禁用/密码重置、管理员与窗口绑定。
- **消息通知模块**：消息中心、未读红点提醒。
- **前端接口封装**：独立封装 4 个接口模块（auth.ts / ai.ts / message.ts / user-admin.ts）共 **16 个接口，占系统 50 个接口的 32%**。
- **独立开发前端页面 7 个**：登录注册、学生首页、AI 点餐助手、AI 配置、个人中心、消息中心、用户管理；封装可复用组件 6+ 个。

## 工程指标

- 单元测试 35 个用例 100% 通过，行覆盖率 90.8%（JUnit 5 + Mockito）
- JMeter 九场景压测：登录接口 580 TPS、300 并发综合峰值 215 TPS；定位 AI 推荐接口 P95 1150ms 延迟瓶颈并以缓存 + 超时降级优化
- 五阶段 202 个测试用例、12 个缺陷全部闭环；作为项目负责人现场演示通过验收（用户满意度 5/5）

## 目录结构

```
├── order-system-backend/     # Spring Boot 后端
├── order-system-frontend/    # Vue 3 前端
└── docs/                     # 项目文档（SRS / 设计 / 测试 / 验收）
```

## 快速开始

### 后端
```bash
cd order-system-backend
# 修改 src/main/resources/application.yml 中的数据库账号密码、JWT secret、AI api-key
mvn spring-boot:run
```
接口文档（Knife4j）：启动后访问 `http://localhost:8080/doc.html`

### 前端
```bash
cd order-system-frontend
npm install
npm run dev
```

## 配置说明

后端 `application.yml` 中以下配置项为占位符，运行时需填入真实值：
- `spring.datasource.password`：MySQL 密码
- `jwt.secret`：JWT 签名密钥（随机长字符串）
- `ai.api-key`：DeepSeek API Key（留空时 AI 功能自动降级为本地规则推荐，功能仍可用）

## 许可

本项目为桂林信息科技学院软件工程综合实训课程项目，仅用于学习交流。
