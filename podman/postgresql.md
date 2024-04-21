# posrgresqlをpodmanで起動

### podmanのインストールは割愛

永続化のためのボリューム作成

```sh
podman volume create pgdata
```

Podmanで名前付きボリュームを作成した場合、ボリュームはrootlessモードで実行しているユーザーのホームディレクトリの下に特定のパスで保存されます。

```sh
/home/ユーザー名/.local/share/containers/storage/volumes/ボリューム名/_data
```
