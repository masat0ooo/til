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
本番環境でPodmanをrootlessモードで運用する場合、専用のユーザーアカウントを設定して実行するのが一般的であり、推奨される方法です。

コンテナ起動
```sh
podman run -d \
  --name postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -v pgdata:/var/lib/postgresql/data \
  postgres

```

# podって何？
Podは、複数のコンテナが共有するリソース（ネットワークIP、ポート範囲など）を持つコンテナグループです。これにより、密接に関連するコンテナが協力して一つの単位として機能することができます。KubernetesやPodmanなどのコンテナオーケストレーションツールで用いられ、アプリケーションのデプロイメントと管理を効率化します。

# yamlでpodを起動

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: postgres-pod
spec:
  containers:
  - name: postgres
    image: postgres
    env:
    - name: POSTGRES_PASSWORD
      value: "mysecretpassword"
    volumeMounts:
    - mountPath: /var/lib/postgresql/data
      name: postgres-storage
  volumes:
  - name: postgres-storage
    volume:
      name: pgdata

```


```sh
podman play kube /path/to/yaml-file.yaml

```
