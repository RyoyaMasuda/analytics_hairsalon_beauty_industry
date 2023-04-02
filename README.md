# analytics_hairsalon_beauty_industry
ヘアサロン業界の口コミ分析(スクレイピング&自然言語)を実施した。

## レポート
[HPB口コミ分析結果(広島市中区)](https://drive.google.com/file/d/1r2SSmXJ2qvom_KvRWFxEx-wkHeEO9NR-/view?usp=sharing)  
  
予備リンク： https://drive.google.com/file/d/1r2SSmXJ2qvom_KvRWFxEx-wkHeEO9NR-/view?usp=sharing

## データセット
[データセットサンプル(スクレイピング結果)](https://drive.google.com/file/d/1TcF6u2DwF3wiVebZEHVhH-aFhTujtYMk/view?usp=sharing)  
  
予備リンク： https://drive.google.com/file/d/1TcF6u2DwF3wiVebZEHVhH-aFhTujtYMk/view?usp=sharing

## 実施内容
1. ホットペッパービューティーの口コミをスクレイピングし、データを収集する。(広島市中区口コミ総件数６万件)
1. 口コミを元にデータ分析を行う。（統計量、可視化、自然言語処理） *公開しているnotebookは分析に使用した全ての地域ではなく、一部の地域をサンプルとしている。

## 開発環境
- ローカル： macOS Monterery
- コンテナ： docker-compose, Dockerfile
  - 言語: python3.9（dockerの公式imageを使用）
  - スクレイピング環境(scraping)
  - 分析環境(analysis)
- 使用ライブラリ
  - pandas
  - numpy
  - matplotlib
  - sklearn
  - MeCab
  - selenium

## ディレクトリ構成と各種処理
ディレクトリ構成は以下となる。
```
.
├── docker-compose.yml
├── analysis
│   ├── Dockerfile
│   ├── requirements.txt
│   └── root
│       ├── data
│       │   └── hirosima_central.csv （GitHubリポジトリからは削除しておく。）
│       └── hpb_analysis.ipynb
└── scraping
    ├── Dockerfile
    ├── requirements.txt
    └── root
        ├── config.yml
        ├── data
        │   └── hirosima_central.csv （GitHubリポジトリからは削除しておく。）
        ├── hpb_scraping.py
        └── log
            └── scraping.log
```   
- 環境構築はdocker-composeを使用 (分析用【`scraping`】とスクレイピング用【`analysis`】のコンテナ立ち上げ)
- 作業用ディレクトリ: `root` (コンテナ内の`root`にマウント)
- 分析notebook:　`analysis/root/hpb_analysis.ipynb`
- スクレイピングソース: `scraping/root/hpb_scraping.py`
- サンプルファイル取得時のログ情報: `scraping/root/log/scraping.log`
- ログ出力設定ファイル: `scraping/root/config.yml`
