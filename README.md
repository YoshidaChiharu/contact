<div id="top"></div>

## 目次

1. [プロジェクト概要](#プロジェクト概要)
2. [使用技術一覧](#使用技術一覧)
3. [環境](#環境)
4. [環境構築手順](#環境構築手順)
5. [ER図](#ER図)
6. [URL](#URL)

## プロジェクト概要

お問い合わせフォームと管理用ページの開発プロジェクト

## 使用技術一覧

- Laravel
- PHP
- NGINX
- MYSQL

## 環境

| 言語・フレームワーク  | バージョン |
| --------------------- | ---------- |
| Laravel               | 8.83.8     |
| PHP                   | 7.4.9      |
| NGINX                 | 1.21.1     |
| MySQL                 | 8.0.26     |

## 環境構築手順

1. **リモートリポジトリをクローンする**
```
$ git clone git@github.com:YoshidaChiharu/todo.git
```
2. **todoディレクトリに移動してDockerコンテナを作成**
```
$ cd todo/
```
```
$ docker-compose up -d --build
```
3. **PHPコンテナ内にログイン**
```
$ docker-compose exec php bash
```
4. **`composer` コマンドでパッケージをインストール**
```
$ composer install
```
5. **`.env` ファイルを作成し、アプリケーションキーを生成**
```
$ cp .env.example .env
$ php artisan key:generate
$ exit
```
6. **（必要に応じて）パーミッションを変更**
```
$ sudo chmod -R 777 src/
```
7. **下記環境変数を基に、`.env` ファイル内のデータベース名／ユーザー名／パスワード等を以下の通り書き換え**
```
// 前略

DB_CONNECTION=mysql
DB_HOST=mysql             # 書き換え箇所
DB_PORT=3306
DB_DATABASE=laravel_db    # 書き換え箇所
DB_USERNAME=laravel_user  # 書き換え箇所
DB_PASSWORD=laravel_pass  # 書き換え箇所

// 後略
```
8. **テーブル作成**
```
$ docker-compose exec php bash
```
```
$ php artisan migrate
```

## ER図

![er-contact](https://github.com/YoshidaChiharu/contact/assets/158742849/d0d4d523-05d6-4aad-b8a2-a5d2058efe35)

## URL

- 開発環境：[http://localhost:8080/](http://localhost:8080/)
- phpMyAdmin：[http://localhost/](http://localhost/)

<p align="right">(<a href="#top">トップへ</a>)</p>
