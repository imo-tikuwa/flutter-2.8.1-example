# flutter_2_8_1_example

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## fvmインストール&fvmでflutter2.5.3,2.8.1インストール
 - https://github.com/leoafarias/fvm/releases から`fvm-2.2.6-windows-x64.zip`をダウンロード
 - C直下に展開
   - fvm.batの場所`C:\fvm-2.2.6-windows-x64\fvm\fvm.bat`
 - Path環境変数に追加
   - C:\fvm-2.2.6-windows-x64\fvm
 - flutter2.5.3,2.8.1インストール
```
>fvm --version
2.2.6

>fvm install 2.5.3
>fvm install 2.8.1
>fvm list
Cache Directory:  C:\Users\[username]\fvm\versions

2.8.1
2.5.3
```

## 初回のプロジェクト構築手順
### メモ
 - `.fvm`と同じディレクトリ内にプロジェクトを作成したい
   - カレントのディレクトリ名について以下のリンクの命名規則に沿う必要がある
     - https://dart.dev/tools/pub/pubspec#name
   - `fvm flutter create .`でカレントのディレクトリ名をもとにしたプロジェクトを作成できる
     - 〇 flutter_2_8_1_example 
     - × flutter-2.8.1-example
     - 命名規則に沿わない場合以下のようなアラートが出る
```
"flutter-2.8.1-example" is not a valid Dart package name.

See https://dart.dev/tools/pub/pubspec#name for more information.
```

 - `fvm use`はPCの開発者用モードを有効化するか、管理者として実行したコマンドプロンプトで実行する必要がある
   - 通常のcmdで実行するとシンボリックリンクが作成できなくて以下のエラーが出る。
```
>fvm use --force 2.8.1
Seems you don't have the required permissions on C:\Users\[username]\fvm On Windows FVM requires to run as an administrator or turn on developer mode: https://bit.ly/3vxRr2M 
```

### 手順
管理者として実行した`cmd`で以下実行
```
>cd /D C:\workspace_flutter\
>mkdir flutter_2_8_1_example
>cd flutter_2_8_1_example\

>fvm use --force 2.8.1
Project now uses Flutter [2.8.1]

>fvm flutter --version
Flutter 2.8.1 • channel stable • https://github.com/flutter/flutter.git
Framework • revision 77d935af4d (2 weeks ago) • 2021-12-16 08:37:33 -0800
Engine • revision 890a5fca2e
Tools • Dart 2.15.1

>fvm flutter create .
```

---
`.vscode/settings.json`に以下の記載を追加
```diff
{
+  "dart.flutterSdkPath": ".fvm/flutter_sdk"
}
```

---
`.gitignore`に以下の設定を追加
```diff
+.fvm/flutter_sdk
```
`.fvm/flutter_sdk`のシンボリックリンクはPCごとに異なるパスとなるためGit管理しない

---
gitにコミット&プッシュ
```
>git init
>git add -A
>git remote add origin https://github.com/imo-tikuwa/flutter-2.8.1-example.git
>git commit -m "init commit"
>git push -u origin master
```

## 他のPCのプロジェクト構築手順
「fvmインストール&fvmでflutter2.5.3,2.8.1インストール」を行ったうえで、管理者として実行した`cmd`で以下実行
```
>git clone https://github.com/imo-tikuwa/flutter-2.8.1-example.git
>cd flutter-2.8.1-example\

>fvm use 2.8.1
Project now uses Flutter [2.8.1]

>fvm flutter --version
Flutter 2.8.1 • channel stable • https://github.com/flutter/flutter.git
Framework • revision 77d935af4d (2 weeks ago) • 2021-12-16 08:37:33 -0800
Engine • revision 890a5fca2e
Tools • Dart 2.15.1
```
