# podmanやコンテナで覚えたこと

### バージョンアップについて
postgresqlのバージョンが上がった時などは、コンテナごと入れ替える。
データは、名前付きボリュームに格納して消えないようにする。（無名ボリュームはコンテナ削除で消える）

### podmanはrootless
ボリュームに関連して権限に注意する。

### DockerfileのCMDで実行がうまくできない。とりあえず後回しにしているが。
