# 目的
ディレクトリのアクセス回数, 更新回数, 作成日からの経過日数から各ディレクトリの使用頻度を算出する
# プログラムの説明
- count.csvを読み込み, ファイルに記入されている各ディレクトリのアクセス回数, 更新回数を取得する.
- ディレクトリのタイムスタンプから作成日時を取得する. これを作成日からの経過日数に変換する.
- (アクセス+回数更新)/作成日からの経過日数, で各ディレクトリの使用頻度(1日当たりの使用回数の平均)を算出する. 
- プログラム実行終了時に使用頻度の昇順に, 各ディレクトリのディレクトリ名, 作成日数からの経過日数, アクセス回数, 更新回数, 使用頻度を出力する.
- 出力されたものの中から, ディレクトリ名, 使用頻度のみを抽出し, 実験.csvに書き込む.
# プログラムの実行と実行例, プログラムの注意点
プログラムを実行するコマンドと実行結果を以下に示す. 
```
ken@MyComputer:~/mkprogram$ python3 frequency_use.py
  Directory  Age (days)  Access Count  Update Count  Ratio
0    2021前期         988             5             0    5.0
1    2021後期         911            10             5   15.0
2    2022前期         659            15             0   15.0
3    2022後期         659            20             5   25.0
4    2023前期         281            15            10   25.0
5    2023後期         281            20            15   35.0
--------------------
2021前期        5.0
2021後期        15.0
2022前期        15.0
2022後期        25.0
2023前期        25.0
2023後期        35.0
ken@MyComputer:~/mkprogram$
```
print関数による出力から, 各ディレクトリの, 作成されてからの経過日数, 1日当たりのアクセス回数, 1日当たりの更新回数, 使用頻度[回/日]をそれぞれ確認できる. 
ただし, プログラムの23～25行目でパスを指定している. そのため, このプログラムを利用する際はtarget_directory,cvs_file,csv_fileを各自任意のパスに変更する必要がある.
# csvファイルの詳細
プログラムの24行目でcount.csv, 25行目で実験.csvを指定している.
ここで各csvファイルを説明する.
- count.csv
count.csvは以下のようになっている.

![image](https://github.com/c0a21155/frequency_use/assets/85731547/d8f77750-26a4-459a-b11e-823bd61136f3)

count.csvにはディレクトリ名, ディレクトリの1日当たりのアクセス回数, ディレクトリの1日当たりの更新回数が記入されている.
frequency_use.pyはこれらの要素を読み込む. 

- 実験.csv
実験.csvは以下のようになっている.

![image](https://github.com/c0a21155/frequency_use/assets/85731547/f49ae6b1-78c1-4457-a067-e4b769b55556)

実験.csvにはfrequency_use.pyで出力されたディレクトリ名, 使用頻度が新たに記入される. 
これにより, ディレクトリ名と計算結果のみを抽出し, 一目でプログラム実行結果を確認できる.
