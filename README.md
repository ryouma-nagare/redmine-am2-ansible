# redmine-am2-ansible


## 概要

Amazon Linux 2 にRedmineをインストールするためのplaybookです。

## MW等の構成

* OS：Amazon Linux 2
* DB：PostgreSQL 11(for CentOS)
* APサーバ：unicorn
* Webサーバ：apache2
* Ruby：2.4
* Redmine：trunk

yum/gemだけでインストールできるように選んでいます。

## 環境依存の設定

#### MW設定
- `group_vars/redmine-aws`
    - データベース設定
        - `postgres.db_name` にデータベース名
        - `postgres.db_user` にデータベース接続のユーザ名
        - `postgres.db_pass` にデータベース接続のパスワード
    - Redmine設定
        - `redmine.mail_server.domain` にメールのドメイン

#### ssh設定
- `keys/` 配下に鍵ファイルを配置

- `inventory/hosts`
    - `ansible_host` にEC2のIP
    - `ansible_ssh_private_key_file` に配置した鍵ファイル名


## 実行方法

```
ansible-playbook -i ./inventory/hosts redmine.yml
```
