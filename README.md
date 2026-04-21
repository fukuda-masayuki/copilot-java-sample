# Java + Spring Boot + PostgreSQL + Docker Compose 最小サンプル

Java 17 / Spring Boot / Maven / PostgreSQL で構成した最小 Web システムです。

## 機能

- `GET /hello`
  - `Hello, Spring Boot!` を返します
- `GET /`
  - ToDo 画面を表示します（タスクの一覧表示・登録）
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
    # ToDo画面
    # ブラウザで http://localhost:8080/ を開く

    curl http://localhost:8080/hello
    curl http://localhost:8080/tasks
    curl -X POST http://localhost:8080/tasks -H "Content-Type: application/json" -d '{"title":"最初のタスク"}'
    ```

4. 画面での確認

    - ブラウザで `http://localhost:8080/` にアクセスすると ToDo 画面が開きます
    - 入力欄にタイトルを入力して `登録` を押すと、一覧が更新されます
    - 入力欄が空または空白のみの場合は、画面上にエラーメッセージが表示されます
