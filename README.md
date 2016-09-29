## 事前準備

プロジェクトの任意の場所に下記コマンドを作成します。

``` sh:run
#!/usr/bin/env bash

set -ex

docker run --rm -it \
  -v ~/.ssh:/root/.ssh:ro \
  -v $(pwd)/../capistrano:/root/source \
  dorapro/capistrano ./cap $@
```

コマンド実行時に下記ディレクトリがコンテナにマウントされます。

|ホストマシン|ゲストマシン|備考|
|:--|:--|:--|
|~/.ssh|/root/.ssh:ro|SSHの設定|
|$(pwd)/../capistrano|/root/source|capistranoの設定|


----


## Basic usage

コマンド実行時に`.ssh`ディレクトリ内の秘密鍵をssh-agentに自動登録されます。

```
./run -T
```
