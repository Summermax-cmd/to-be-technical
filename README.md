# Node.js/Express + SQLite Movies API

一个使用 Node.js/Express 搭配 SQLite 的简单后端示例。启动时若未存在 `movies` 表会自动创建（包含 `id`, `title`, `year`）。

## 运行

```bash
# 安装依赖
npm install

# 开发运行（ts-node）
npm run dev

# 或先构建再运行
npm run build
npm start
```

服务默认在 `http://localhost:3000` 启动。

## API

- GET `/api/movies`
  - 返回所有电影：
  ```json
  [
    { "id": 1, "title": "Inception", "year": 2010 }
  ]
  ```

- POST `/api/movies`
  - 请求体：
  ```json
  { "title": "Interstellar", "year": 2014 }
  ```
  - 响应体（201）：
  ```json
  { "id": 2, "title": "Interstellar", "year": 2014 }
  ```

## 数据库

- 数据文件位于项目根目录：`data.sqlite`
- 启动时自动建表：
  ```sql
  CREATE TABLE IF NOT EXISTS movies (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    year INTEGER NOT NULL
  );
  ```

