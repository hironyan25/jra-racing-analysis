# JRA競馬データ分析プロジェクト

本プロジェクトは、JRA（日本中央競馬会）の競馬データを分析し、馬券回収率向上に貢献する特徴量を抽出・評価するものです。特に「人気以上に好走する馬」を見出す特徴を開発し、市場（オッズ）の非効率性を活用した予測モデルの構築を目指します。

## プロジェクト概要

JRA-VAN Data Lab（JVD）のデータベースを活用し、以下の目標を達成します：

- 100種類以上の特徴量の生成と評価
- 回収率向上に特に寄与する重要特徴量の特定
- ディープラーニングによる予測モデルの開発（回収率110%以上を目指す）

## 主要な特化型特徴量

1. **種牡馬×馬場適性ROI**: 特定の種牡馬の産駒が特定の馬場条件で示す回収率傾向を数値化
2. **騎手のコース別平均配当**: 各騎手が特定コースで勝利した際の平均配当と回収率
3. **前走ペース偏差（展開不利指標）**: 前走で展開が不利だった馬を特定し、「展開負けで実力負けではない」馬を見出す
4. **上がりタイム順位**: レース終盤の上がり3ハロンのタイム順位による評価
5. **斤量差適応力**: 馬の斤量変化への適応力を評価

## ディレクトリ構造

```
├── .env                  # 環境変数（データベース接続情報など）
├── requirements.txt      # 必要なPythonライブラリ
├── README.md             # プロジェクト概要
├── data/                 # 中間データ、加工後データの保存先
├── notebooks/            # Jupyter notebooks（分析・実験用）
└── src/                  # ソースコード
    ├── database/         # データベース接続関連
    ├── features/         # 特徴量エンジニアリング関連
    ├── models/           # 予測モデル関連
    └── visualization/    # データ可視化関連
```

## 環境構築

### 必要条件

- Python 3.10以上
- PostgreSQL（JVDデータベース）
- 32GB以上のRAM推奨（大規模データ処理のため）
- NVIDIA GPU（RTX 3080以上推奨、ディープラーニングモデル用）

### インストール方法

```bash
# 仮想環境の作成
conda create -n horse-racing python=3.10
conda activate horse-racing

# 必要なパッケージのインストール
pip install -r requirements.txt

# 環境変数の設定
cp .env.example .env
# .envファイルを編集してデータベース接続情報を入力
```

## 特徴量の評価方法

特徴量の評価は以下の指標に基づいて行います：

1. **回収率（ROI）向上度**: 特徴量を使用した場合としない場合の回収率の差
2. **複合評価指標**: 的中率と回収率の両方を考慮した評価
3. **安定性**: 時系列的な一貫性の評価

## ライセンス

このプロジェクトは [MIT ライセンス](LICENSE) のもとで提供されています。
