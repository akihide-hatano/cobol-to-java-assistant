# COBOL to Java Knowledge Assistant

## ■ 概要

COBOLコードをAI APIに送信し、Javaでの変換案を取得・保存するアプリです。
過去に調べたCOBOL構文やJava変換例をナレッジとして蓄積し、後から見返せるようにします。

---

## ■ 誰の何を解決するのか

### 対象ユーザー

COBOL案件に関わりながら、Java / Spring Boot 開発へ移行したいエンジニア。

### 課題

- COBOLの処理をJavaでどう表現すればよいか分かりにくい
- 一度調べた変換パターンや理解が散らばりやすい
- 過去に調べた内容を再利用しにくい
- AIに聞いた結果をその場限りで終わらせてしまう

### 解決したい状態

- COBOLコードを入力すると、Java変換案を確認できる
- AI APIの結果をMySQLに保存できる
- COBOLコード・Java変換結果・自分のメモを後から見返せる
- 調べた内容を個人のナレッジとして蓄積できる

---

## ■ MVP（最小構成）

以下の機能に絞って実装します。

- COBOLコード入力
- AI APIによるJava変換案の取得
- Java変換結果の表示
- 変換結果の保存
- 変換履歴一覧
- 変換履歴詳細
- 自分用メモの登録

---

## ■ データモデル（MVP）

```text
users
  1
  │
  │
  N
conversions
```

■ 保存方針

AI APIから返却されたJava変換結果は、Spring Boot側で受け取り、
MySQLの conversions テーブルに保存する。

COBOLコード入力
↓
Spring Boot が AI API を叩く
↓
AIからJava変換結果が返る
↓
Spring Boot が MySQL に保存
↓
一覧・詳細画面で見返す

■ 技術構成

* Spring Boot
* MySQL
* Thymeleaf
* Git / GitHub
* Maven
* JUnit
* AI API

⸻

■ 技術選定理由

Spring Boot

Java / Spring Boot 案件への参画を見据え、
MVC構成・DI・DB連携・例外処理・外部API連携を学ぶため。

MySQL

COBOLコード、Java変換結果、メモを保存し、
過去の変換履歴を再利用可能にするため。

Thymeleaf

フロントを複雑にせず、Spring Boot内で画面表示まで完結させるため。

Maven

依存関係管理・ビルド・テスト実行を統一的に行うため。

JUnit

変換履歴保存や入力チェックなど、業務ロジックをテスト可能にするため。

AI API

COBOLコードに対するJava変換案を取得するため。
MVPでは、まずダミー応答で保存処理まで実装し、その後API連携に差し替える。

⸻

■ MVPでやらないこと

* タグ管理
* 複数ユーザー認証
* 権限管理
* COBOL構文解析の自前実装
* 完全自動変換
* 複雑な検索機能

⸻

■ 今後の拡張

* タグ分類
* キーワード検索
* AI APIのプロンプト改善
* 変換前後の差分表示
* よく使う変換パターンの辞書化
* ログイン機能
* Dockerによる環境構築

⸻

■ 目的

COBOL現場で得た知識を活かしながら、
Java / Spring Boot / SQL / 外部API連携の基礎力を身につけること。
# COBOL to Java Knowledge Assistant

## 概要

COBOLコードをAI APIに送信し、Javaでの変換案を取得・保存するアプリです。  
過去に調べたCOBOL構文やJava変換例をナレッジとして蓄積し、後から見返せるようにします。

---

## 誰の何を解決するのか

### 対象ユーザー
COBOL案件に関わりながら、Java / Spring Boot 開発へ移行したいエンジニア

### 課題
- COBOLの処理をJavaでどう表現すればよいか分かりにくい
- 一度調べた変換パターンや理解が散らばりやすい
- 過去に調べた内容を再利用しにくい
- AIに聞いた結果をその場限りで終わらせてしまう

### 解決したい状態
- COBOLコードを入力すると、Java変換案を確認できる
- AI APIの結果をMySQLに保存できる
- COBOLコード・Java変換結果・自分のメモを後から見返せる
- 調べた内容を個人のナレッジとして蓄積できる

---

## MVP（最小構成）

以下の機能に絞って実装します。

- COBOLコード入力
- AI APIによるJava変換案の取得
- Java変換結果の表示
- 変換結果の保存
- 変換履歴一覧
- 変換履歴詳細
- 自分用メモの登録

---

## データモデル（MVP）

```text
users
  1
  │
  │
  N
conversions
```

---

## 保存フロー

```text
COBOLコード入力
↓
Spring Boot が AI API を呼び出す
↓
AIからJava変換結果が返る
↓
MySQL に保存
↓
一覧・詳細画面で表示
```

---

## 技術構成

- Spring Boot
- MySQL
- Thymeleaf
- Git / GitHub
- Maven
- JUnit
- AI API

---

## 技術選定理由

### Spring Boot
Java / Spring Boot 案件への参画を見据え、  
MVC構成・DI・DB連携・例外処理・外部API連携を学ぶため。

### MySQL
COBOLコード、Java変換結果、メモを保存し、  
過去の変換履歴を再利用可能にするため。

### Thymeleaf
フロントを複雑にせず、Spring Boot内で画面表示まで完結させるため。

### Maven
依存関係管理・ビルド・テスト実行を統一的に行うため。

### JUnit
変換履歴保存や入力チェックなど、業務ロジックをテスト可能にするため。

### AI API
COBOLコードに対するJava変換案を取得するため。  
MVPではダミー応答で保存処理まで実装し、その後API連携に差し替える。

---

## MVPでやらないこと

- タグ管理
- 複数ユーザー認証
- 権限管理
- COBOL構文解析の自前実装
- 完全自動変換
- 複雑な検索機能

---

## 今後の拡張

- タグ分類
- キーワード検索
- AI APIのプロンプト改善
- 変換前後の差分表示
- よく使う変換パターンの辞書化
- ログイン機能
- Dockerによる環境構築

---

## 目的

COBOL現場で得た知識を活かしながら、
Java / Spring Boot / SQL / 外部API連携の基礎力を身につけること。