# Java + Spring Boot + PostgreSQL + Docker Compose 最小サンプル

Java 17 / Spring Boot / Maven / PostgreSQL で構成した最小 Web システムです。

## 機能

- `GET /hello`
  - `Hello, Spring Boot!` を返します
- `GET /tasks`
  - タスク一覧を JSON で返します
- `POST /tasks`
  - `{"title":"..."}` を受け取り DB に保存し、保存後の Task を JSON で返します

## 動作確認手順

1. Maven でビルド

   ```bash
   ./mvnw clean package
   ```

2. Docker Compose で起動

   ```bash
   docker compose up --build
   ```

3. エンドポイント確認

   ```bash
   curl http://localhost:8080/hello
   curl http://localhost:8080/tasks
   curl -X POST http://localhost:8080/tasks -H "Content-Type: application/json" -d '{"title":"最初のタスク"}'
   ```
