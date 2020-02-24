# Android
あれこれ試してる最中なので使うべきでは無い！

## Start
```bash
$ docker-compose up --build -d
```

## Run go file
```bash
$ docker-compose exec android /workdir/TestAppp/gradlew assembleDebug
```


## エラー集

### Build時

- 原因
Android SDKのインストールにはライセンスの承諾が必要だが、Gradleによるインストールでは勝手に承諾してくれないために発生する
```
Failed to install the following Android SDK packages as some licences have not been accepted.
     platforms;android-28 Android SDK Platform 28
     build-tools;28.0.2 Android SDK Build-Tools 28.0.2
  To build this project, accept the SDK license agreements and install the missing components using the Android Studio SDK Manager.
  Alternatively, to transfer the license agreements from one workstation to another, see http://d.android.com/r/studio-ui/export-licenses.html
```

- 解決策
コマンドでインストールする
```bash
$ android update sdk --no-ui --all --filter "android-28,build-tools-28.0.2"
```

- gradlew作成
`gradle wrap`


```
https://services.gradle.org/distributions/gradle-5.5.1-bin.zip
https://download.jetbrains.com/kotlin/native/builds/releases/1.3.61/linux/kotlin-native-linux-1.3.61.tar.gz
```
