# つかいかた

## DockerでContainerまで立ち上げる
-1 カレントディレクトリをここのフォルダにしてください。

-1 `docker build . -t gcloud:201809` でimageを作成してください。なお、`gcloud:201809`は好きな名前で良いです。（image名を命名しているだけですので）

-1 `docker run -d -it --name gcloud_ctr gcloud:201809`でContainerを立ち上げてください。なお、`gcloud_ctr`は好きな名前で良いです。（Container名を命名しているだけなので)

-1 `docker exec -it gcloud_ctr /bin/bash`でbashに入ってください。

## gcloudの初期化

このあたりは`gcloud init`で検索をかけるとわかりやすいかもしれません。

-1 `gcloud init`コマンドを入力します。

`You must log in to continue. Would you like to log in (Y/n)?`　は　`Y`　を押下してください。

-1 以下のような文言が現れます。
```
Go to the following link in your browser:

https://accounts.google.com/o/oauth2/auth?redirect_uri=*******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************

Enter verification code:
```

上記の様なURLが出てくるのでWebブラウザに貼り付けてください。

Googleアカウントを聞かれるので、`GCPのアカウント`を選択してください。

コードが出るので、それをターミナルの`Enter verification code:`に貼り付けてください。

`You are logged in as: [GMAILのアドレス].`が表示されたら成功です。

-1 以下のような文言が現れます。

```
Pick cloud project to use:
 [1] project1
 [2] project2
Please enter numeric choice or text value (must exactly match list
item):
```

好きなプロジェクトを選んでください。（project2を使う場合は`2`を入力します。)

-1 以下のような文言が出ます。

```
Do you want to configure a default Compute Region and Zone? (Y/n)?
```

`n`を押します。

これで`gcloud`の初期化が完了しました。

## kubectlのインストール

`apt install kubectl`とコマンドを打ってください。

これでkubectlまで使えるようになりました。

kubectlを使うと下記Warningが出ますが、後ほど対応します。

```
WARNING: Starting in 1.12, new clusters will have basic authentication disabled by default. Basic authentication can be enabled (or disabled) manually using the `--[no-]enable-basic-auth` flag.
WARNING: Starting in 1.12, new clusters will not have a client certificate issued. You can manually enable (or disable) the issuance of the client certificate using the `--[no-]issue-client-certificate` flag.
WARNING: Currently VPC-native is not the default mode during cluster creation. In the future, this will become the default mode and can be disabled using `--no-enable-ip-alias` flag. Use `--[no-]enable-ip-alias` flag to suppress this warning.
This will enable the autorepair feature for nodes. Please see
https://cloud.google.com/kubernetes-engine/docs/node-auto-repair for more
information on node autorepairs.

WARNING: Starting in Kubernetes v1.10, new clusters will no longer get compute-rw and storage-ro scopes added to what is specified in --scopes (though the latter will remain included in the default --scopes). To use these scopes, add them explicitly to --scopes. To use the new behavior, set container/new_scopes_behavior property (gcloud config set container/new_scopes_behavior true).
```