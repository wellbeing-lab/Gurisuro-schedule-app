# Gurisuro Schedule App

Green Slow Mobility の運転手・添乗員スケジュール管理アプリ

---

## システム構成

GitHub  
wellbeing-lab/Gurisuro-schedule-app  
↓  
Vercel（アプリ公開）  
↓  
Neon（PostgreSQL Database）

---

## ローカル環境構築

リポジトリ取得

git clone https://github.com/wellbeing-lab/Gurisuro-schedule-app.git  
cd Gurisuro-schedule-app  

依存関係インストール

npm install

ローカル起動

npm start

ブラウザ

http://localhost:3000

---

## Vercel デプロイ方法

Vercel にアクセス

https://vercel.com/new

手順

1. GitHub連携  
2. Repository選択  

wellbeing-lab/Gurisuro-schedule-app  

3. Import Project  
4. Deploy  

デプロイ後、公開URLが発行される

例  
https://gurisuro-schedule-app.vercel.app

---

## Neon データベース設定

Neon Console

https://console.neon.tech

新しいプロジェクト作成

Create Project

例

Project Name  
gurisuro-db

Database 作成

Database name  
gurisuro

---

## 接続URL

Neonは以下の形式の接続URLを発行する

postgresql://user:password@xxxx.neon.tech/dbname

---

## Vercel 環境変数

Vercel Project

Settings  
Environment Variables  

追加

Name  
DATABASE_URL  

Value  
postgresql://xxxxx

---

## Neon データ移行

旧データベースからエクスポート

pg_dump "旧DATABASE_URL" > backup.sql

新データベースへインポート

psql "新DATABASE_URL" < backup.sql

---

## 再デプロイ

Vercel

Redeploy

または

git push

---

## 最終構成

GitHub  
↓  
Vercel  
↓  
Neon

---

## 注意

DATABASE_URL は GitHub に含めない  
環境変数は Vercel に設定する

## Neonバックアップ手順

1. Neon Console の Connect から Connection pooling を OFF にする
2. unpooled connection string をコピーする
3. 以下を実行する

```bash
pg_dump -Fc -v -d "OLD_DATABASE_URL_UNPOOLED" -f backup.dump
