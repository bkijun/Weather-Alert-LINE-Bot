# Weather-Alert-LINE-Bot

神戸市の天気情報と気象庁の警報・注意報を取得し、LINE に自動送信する Bot の開発用リポジトリです。

もともとは Discord へ通知する Python 実装でしたが、今回は学習も兼ねて Go 言語で LINE Bot として作り直す前提で整理しています。

## できること

- 神戸市の現在の天気を取得する
- 気象庁の警報・注意報を取得する
- 毎日1回、LINE に自動送信する

## 予定している構成

- Go で実装する
- 天気取得には OpenWeather API を使う
- 警報・注意報は気象庁の XML フィードを参照する
- LINE 送信には LINE Messaging API を使う
- 定期実行は GitHub Actions で毎日実行する

## 取得する情報

### 天気情報

- 対象地域: 神戸市
- 取得項目: 天気、現在気温、最高気温、最低気温

### 警報・注意報

- 兵庫県の気象警報・注意報を対象にする
- 発表時刻もあわせて送信する

## 使う予定の API

- OpenWeather API
- 気象庁 XML フィード
- LINE Messaging API

## 環境変数

実装時は、以下のような環境変数を利用する想定です。

```env
LINE_CHANNEL_ACCESS_TOKEN=xxxxxxxx
LINE_CHANNEL_SECRET=xxxxxxxx
LINE_USER_ID=xxxxxxxx
OPENWEATHER_API_KEY=xxxxxxxx
```

## 実装方針

1. 天気情報取得処理を関数化する
2. 気象庁 XML を解析して警報・注意報を整形する
3. LINE へメッセージを送信する処理をまとめる
4. GitHub Actions で毎日実行するワークフローを作る

## メッセージ例

📍 神戸市の天気（06/03）
☀️ 天気：晴れ
🌡 現在：25.4℃
⬆ 最高：27.0℃
⬇ 最低：20.1℃

⚠️ 兵庫県 気象警報・注意報
【神戸市】大雨注意報

## 今後の追加予定

- Go のプロジェクト初期化
- LINE Bot の送信処理実装
- API 取得失敗時のエラーハンドリング強化
- GitHub Actions による毎日実行の自動化
- Docker 化
