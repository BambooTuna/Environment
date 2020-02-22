# Environment
各種言語の環境構築


## Windows10 HomeにDockerを導入する際の注意点
1. bios設定で`virtual technology`が有効になっているか確認
`virtual technology`とは「Virtual Box」や「Hyper-V」を利用する際の仮想化支援機能

2. コマンドプロンプトではなく`PowerShell`を使う

3. `docker version`でエラーが出るときは`PowerShell`で以下コマンドを実行してみよう
```sh
$ docker-machine env default | Invoke-Expression
```
