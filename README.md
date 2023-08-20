# docker-cron-sample

[![PHP](https://img.shields.io/badge/PHP-8.2.8-red.svg)](https://www.php.net/downloads.php)
[![Docker](https://img.shields.io/badge/Docker-24.0.2-red.svg)](https://docs.docker.com/engine/release-notes/24.0/)
[![License](https://img.shields.io/badge/License-MIIT-blue.svg)](https://licenses.opensource.jp/MIT/MIT.html)

# 概要

Docker で cron を実行しPHPファイルを実行するサンプルリポジトリです。

# 目的

コンテナ内で複数のプロセスを起動したり、cronを実行するための方法の学習を目的としています。

# 使用方法

Docker と VS Code の拡張機能 Devcontainer を使用することを前提としています。

1. 適当な作業ディレクトリで、以下のコマンドを実行します。
```bash
$ git clone git@github.com:shimanamisan/docker-cron-sample.git
```

2. `docker-cron-sample`を VS Code で開き、`F1`キーでコマンドパレット開き、開発コンテナを起動します。
![スクリーンショット 2023-07-30 093122](https://github.com/shimanamisan/php-test-object/assets/49751604/8f2b59ca-8205-494d-9b47-dc385b03ccb0)

3. VS Code のターミナルを開き、起動したコンテナにアタッチされていることを確認します。
![スクリーンショット 2023-07-30 095036](https://github.com/shimanamisan/php-test-object/assets/49751604/401d5ef6-5fa0-4e2a-baf2-698f300c5124)

4. 1分間隔で`public/index.php`ファイルの内容が`/var/log/cron.log`に出力されていることを確認します。