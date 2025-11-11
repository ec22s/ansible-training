- forked from https://github.com/Shoma-progr-0210/ansible-training

- fork元の解説 https://qiita.com/Shoma0210/items/7d7d24d7c3f95f19b427

- 0714f49 2025年11月11日時点で動くよう若干修正しました

- 動作確認環境

  - macOS Sequoia 15.6
  
  - GNU bash, version 5.3.3(1)-release (x86_64-apple-darwin23.6.0)
  
  - Docker version 28.5.1, build e180ab8ab8

- 以下, fork元のREADMEです

---

# Ansible on CentOS7

## コンテナ構築

### ビルド

```
$ docker-compose build --no-cache
```

### 削除

```
$ docker-compose down -v
```

## コンテナ起動・停止

### 起動

```
$ docker-compose up -d
```

### 停止

```
$ docker compose stop
```

## centos コンテナの環境構築

コンテナに入る

```
$ docker-compose exec ansible bash
```

ansible の動作確認

```
$ ansible localhost -m ping
```

確認結果

```
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

node0x に対して、SSH で接続確認を行います。  
この作業で、予めターゲットノードを SSH の known_hosts に登録します。  
※node0x の x はターゲットノードの番号に置き換えてください  
※接続を続けるかを聞かれた場合は yes と入力して下さい

```
$ ssh node0x
$ exit
```

ターゲットノードに対して疎通確認を行います。

```
$ ansible node -m ping
```

playbook.yml を実行して、ターゲットノードに httpd をセットアップします。

```
$ ansible-playbook playbook.yml
```

ターゲットノードで httpd が正常に動作しているかをブラウザで確認してください。

node0x: http://localhost:808x
