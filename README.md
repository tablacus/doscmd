# Tablacus DOS cmd

Tablacus DOS cmdはMSXのBASICからDOSコマンドを実行させるソフトです。  
64KBのディスクカーネルを持つMSXで実行できます。

ディスクカーネルは[Tablacus Disk ROM Lite](https://github.com/tablacus/TablacusDiskRomLite)の64KB対応版でも大丈夫です。

64KBのRAMの前半48KBをDOS用として、後半16KBをBASIC用として使用します。

DOS2とマッパーRAMを使用して両方とも64KBのRAMをスイッチして使用する[Tablacus DOS cmd 2](https://github.com/tablacus/doscmd2)ができました。

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

## アンインストール

```
POKE&HF676,1:POKE&HF677,&H80:POKE&H8000,0:POKE&H8001,0:POKE&HFE0D,&HC9:NEW
```
`NEW`の代わりに`RUN"ファイル名.BAS"`でも良いです。

## DOSコマンドの実行

引数「BAR」でFOO.COMを実行する場合は以下のようにします。v0.10から実行ファイルの指定に拡張子の「.com」が不要になりました。

```bas
CMD "FOO BAR"
```

DOS2カーネルを使っている場合とTablacus Disk ROM Liteを使っている場合はCOMファイルの指定に階層ディレクトリを指定することができます。

```bas
CMD "A:\DIR\FOO BAR"
```
## サンプル

WebMSXを使ったサンプルです。BPBINFO.COMを実行しています。

MSX1  
https://webmsx.org/?MACHINE=MSX1J&DISKA=https://github.com/tablacus/doscmd/raw/main/doscmd.dsk

MSX2  
https://webmsx.org/?MACHINE=MSX2J&DISKA=https://github.com/tablacus/doscmd/raw/main/doscmd.dsk

MSX turbo R  
https://webmsx.org/?MACHINE=MSXTR&DISKA=https://github.com/tablacus/doscmd/raw/main/doscmd.dsk

## ライセンス

[Apache-2.0 license](https://github.com/tablacus/doscmd/blob/main/LICENSE)のオープンソースです。

※有料、無料にかかわらず同人ソフトに組み込んで配布してもらっても問題ありません。
