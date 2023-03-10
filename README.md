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
        ├── hpb_scraping,py
        └── log
            └── scraping.log
```   
- 今回は分析とスクレイピングの２つのコンテナ（`scraping`と`analysis`）をdocker-composeを使用して立ち上げた。
- docker-compose.ymlファイルが最上位にあり、Dockerfile、requirements.txtはそれぞれのディレクトリ内（`scraping`と`analysis`）にある。
- 作業用ディレクトリは`root`とし、コンテナ内の`root`ディレクトリにマウントしている。
- `scraping/root/data`を`analysisコンテナ内のroot/data`にマウントする設計にしている。(以下目的)
  - スクレイピングで取得したデータは`scrapingコンテナの/root/data`に出力され、`analysisコンテナ内の/root/data`にも現れる。（サンプルファイル： hirosima_central.csv）
  - `analysysコンテナ内の/root/hpb_analysis.ipynb`から`data/hirosima_central.csv`を読み込んで分析を実施している。
- `scraping/root/log/scraping.log`にサンプルファイル取得時のログ情報を出力した。（`scraping/root/config.yml`はログ出力設定ファイル）
