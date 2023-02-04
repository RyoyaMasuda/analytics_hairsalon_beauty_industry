# analytics_hairsalon_beauty_industry
ヘアサロン業界の口コミ分析(スクレイピング&自然言語)を実施した。

# レポート
[HPB口コミ分析結果(広島市中区)](https://drive.google.com/file/d/12ynpp37xWIYNA31MNEyLZ1irOtfADT-x/view?usp=sharing)  
  
予備リンク： https://drive.google.com/file/d/12ynpp37xWIYNA31MNEyLZ1irOtfADT-x/view?usp=sharing

# データセット
[データセットサンプル(スクレイピング結果)]https://drive.google.com/file/d/1TcF6u2DwF3wiVebZEHVhH-aFhTujtYMk/view?usp=sharing  
  
予備リンク： https://drive.google.com/file/d/1TcF6u2DwF3wiVebZEHVhH-aFhTujtYMk/view?usp=sharing

# 実施内容
1. ホットペッパービューティーの口コミをスクレイピングし、データを収集する。(広島市中区口コミ総件数６万件)
1. 口コミを元にデータ分析を行う。（統計量、可視化、自然言語処理） *公開しているnotebookは分析に使用した全ての地域ではなく、一部の地域をサンプルとしている。

# 開発環境
- ローカル： macOS Monterery
- コンテナ： docker　compose, Dockerfile
  - スクレイピング環境(scraping)
  - 分析環境(analysis)
- 使用ライブラリ
  - pandas
  - numpy
  - matplotlib
  - sklearn
  - MeCab
  - selenium
