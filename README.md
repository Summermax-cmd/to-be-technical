# 个人作品集网站

这是一个完整的全栈项目，包含现代化的前端界面和 Node.js/Express 后端 API，提供留言系统功能。

## 功能特性

### 后端功能
- ✅ 创建 SQLite 数据库和 messages 表
- ✅ POST /api/contact 端点：接收并保存访客留言
- ✅ GET /api/messages 端点：查看所有留言（仅限本地访问）
- ✅ 数据验证和错误处理
- ✅ CORS 支持
- ✅ 健康检查端点

### 前端功能
- ✅ 现代化暗色主题设计
- ✅ 响应式布局，支持移动端
- ✅ 三个主要部分：Header/Hero、Projects、Contact
- ✅ 平滑滚动和动画效果
- ✅ 联系表单与后端 API 集成
- ✅ 移动端导航菜单
- ✅ Tailwind CSS 框架

## 数据库结构

### messages 表
| 字段 | 类型 | 说明 |
|------|------|------|
| id | INTEGER | 主键，自增 |
| name | TEXT | 访客姓名 |
| email | TEXT | 访客邮箱 |
| message | TEXT | 留言内容 |
| timestamp | DATETIME | 创建时间（默认当前时间） |

## API 端点

### 1. 提交留言
- **URL**: `POST /api/contact`
- **请求体**:
```json
{
  "name": "Summer",
  "email": "zhangsan@example.com",
  "message": "这是一条测试留言"
}
```
- **响应**:
```json
{
  "success": true,
  "message": "留言已成功提交",
  "data": {
    "id": 1,
    "name": "Summer",
    "email": "zhangsan@example.com",
    "message": "这是一条测试留言",
    "timestamp": "2024-01-01T12:00:00.000Z"
  }
}
```

### 2. 查看所有留言（仅本地访问）
- **URL**: `GET /api/messages`
- **限制**: 仅允许 localhost 访问
- **响应**:
```json
{
  "success": true,
  "message": "查询成功",
  "data": [
    {
      "id": 1,
      "name": "Summer",
      "email": "zhangsan@example.com",
      "message": "这是一条测试留言",
      "timestamp": "2024-01-01T12:00:00.000Z"
    }
  ],
  "count": 1
}
```

### 3. 健康检查
- **URL**: `GET /health`
- **响应**:
```json
{
  "success": true,
  "message": "服务器运行正常",
  "timestamp": "2024-01-01T12:00:00.000Z"
}
```

## 安装和运行

### 1. 安装依赖
```bash
npm install
```

### 2. 启动服务器
```bash
npm start
# 或者
npm run dev
```

服务器将在 `http://localhost:3000` 启动。

## 测试 API

### 使用 curl 测试提交留言
```bash
curl -X POST http://localhost:3000/api/contact \
  -H "Content-Type: application/json" \
  -d '{
    "name": "测试用户",
    "email": "test@example.com",
    "message": "这是一条测试留言"
  }'
```

### 使用 curl 测试查看留言（仅本地）
```bash
curl http://localhost:3000/api/messages
```

## 安全特性

- **本地访问限制**: GET /api/messages 端点仅允许 localhost 访问
- **数据验证**: 验证必需字段和邮箱格式
- **错误处理**: 完善的错误处理和响应
- **CORS 支持**: 支持跨域请求

## 项目结构

```
├── app.js          # Express 服务器主文件
├── database.js     # 数据库连接和初始化
├── index.html      # 主页面（个人作品集）
├── script.js       # 前端 JavaScript 交互功能
├── test.html       # API 测试页面
├── package.json    # 项目配置和依赖
├── messages.db     # SQLite 数据库文件（运行后生成）
└── README.md       # 项目说明文档
```

## 技术栈

### 后端技术
- **Node.js**: JavaScript 运行时
- **Express**: Web 应用框架
- **SQLite3**: 轻量级数据库
- **CORS**: 跨域资源共享中间件

### 前端技术
- **HTML5**: 语义化标记
- **Tailwind CSS**: 实用优先的 CSS 框架
- **JavaScript (ES6+)**: 现代 JavaScript 功能
- **响应式设计**: 移动端优先的设计方法

## 页面预览

### 主页面 (index.html)
- **Header/Hero Section**: 个人介绍、头像、技能标签
- **Projects Section**: 三个项目卡片展示
- **Contact Section**: 联系表单和联系信息

### 测试页面 (test.html)
- API 端点测试工具
- 健康检查测试
- 留言提交测试
- 留言查看测试

## 注意事项

1. 数据库文件 `messages.db` 会在首次运行时自动创建
2. GET /api/messages 端点仅允许本地访问，确保数据安全
3. 服务器支持优雅关闭，按 Ctrl+C 可安全停止服务
4. 前端使用 Tailwind CSS CDN，需要网络连接
5. 建议在生产环境中添加更多安全措施，如身份验证、速率限制等
