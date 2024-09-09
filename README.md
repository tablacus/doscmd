# Tablacus DOS cmd

Tablacus DOS cmdはMSXのBASICからDOSコマンドを実行させるソフトです。  
64KBのディスクカーネルを持つMSXで実行できます。

ディスクカーネルは[Tablacus Disk ROM Lite](https://github.com/tablacus/TablacusDiskRomLite)でも大丈夫です。

64KBのRAMの前半48KBをDOS用として、後半16KBをBASIC用として使用します。

## インストール

```bas
BLOAD"DOSCMD.BIN",R
```

インストールを実行するとBASICは`NEW`状態になります。

`AUTOEXEC.BAT`で実行する場合は以下のようにすぐ下に`RUN`コマンドで次に実行するBASICファイルを実行します。

```autoexec.bas
10 BLOAD"DOSCMD.BIN",R
20 RUN"DOSCMD.BAS"
```

## DOSコマンドの実行

引数「BAR」でFOO.COMを実行する場合は以下のようにします。実行ファイルの指定には必ず拡張子の「.com」も必要です。

```bas
CMD "FOO.COM BAR"
```

DOS2カーネルを使っている場合とTablacus Disk ROM Liteを使っている場合はCOMファイルの指定に階層ディレクトリを指定することができます。

```bas
CMD "A:\DIR\FOO.COM BAR"
```
