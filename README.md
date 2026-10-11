# 智慧校园食堂智能订餐系统（Campus Order System）

> 面向高校食堂的智能化在线订餐系统 · 软件工程综合实训（前后端分离全栈 · 个人独立完成）

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-brightgreen)](https://spring.io/projects/spring-boot)
[![Vue](https://img.shields.io/badge/Vue-3.5-42b883)](https://vuejs.org/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)](https://www.mysql.com/)

## 项目简介

针对高校食堂用餐高峰期排队时间长、信息不对称等问题，独立设计并实现了一套完整的在线订餐系统。系统采用前后端分离架构，后端 Spring Boot 3 + MyBatis-Plus，前端 Vue 3 + Element Plus，数据库 MySQL 8.0，并集成 DeepSeek 大模型实现 AI 智能点餐推荐。

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

## 个人独立完成的核心工作

- **后端开发**：基于 Spring Boot 3 + MyBatis-Plus 设计并实现 9 大功能模块、50 个 RESTful API；独立封装 16 个接口（占 32%）；集成 Spring Security + JWT 实现三角色权限隔离；完成 MySQL 数据库表结构设计与数据操作优化。
- **前端开发**：使用 Vue 3 + Element Plus 完成全部用户界面的组件化开发，独立开发 7 个核心页面（登录注册、学生首页、AI 点餐助手、AI 配置、个人中心、消息中心、用户管理），封装 6+ 个可复用业务组件；集成 ECharts 营业数据可视化。
- **AI 智能模块**：独立实现 AI 点餐助手、AI 今日推荐、偏好设置、容错降级、AI 配置管理共 9 个子需求，完成 Prompt 指令链调优与本地规则兜底降级。
- **软件工程全流程**：独立编制需求规格说明书（SRS）三轮迭代、用例规约与 WBS 任务分解，完成需求 → 设计 → 开发 → 测试 → 部署 → 验收的完整生命周期。
- **质量保障**：编写 JUnit 单元测试（35 个用例 100% 通过，行覆盖率 90.8%）；JMeter 九场景压测（登录接口 580 TPS、300 并发峰值 215 TPS），定位 AI 推荐接口 P95 1150ms 延迟瓶颈并以缓存 + 超时降级优化；五阶段 202 个测试用例、12 个缺陷全部闭环。

## 工程指标

- 单元测试 35 个用例 100% 通过，行覆盖率 90.8%（JUnit 5 + Mockito）
- JMeter 压测：登录接口 580 TPS、300 并发综合峰值 215 TPS
- 通过验收（用户满意度 5/5）

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
