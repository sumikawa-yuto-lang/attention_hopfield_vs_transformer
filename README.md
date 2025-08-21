# Hopfield vs. Transformer Benchmark Suite

## 概要
Modern Hopfield（記憶埋め込み、学習なし) と Transformer (K≠V のデノイズ学習) を **同一条件で比較**するベンチマーク環境です。  
α（パターン数/次元）、β（温度、鋭さ）、ノイズ強度を掃引し、復元オーバーラップを測定します。  
実測カーブを同一図に重ねて可視化します。

Modern Hopfield とは　
Modern Hopfield Network (MHN) は「検索型メモリ」として動作します。
入力ベクトル（クエリ）に対して、保存されたパターン（キー・バリュー）の中から最も関連するものを検索し、対応する記憶を呼び出す仕組みです。数理的にはTransformerのAttention機構と同型であり、両者は「検索による情報取得」という共通の枠組みで理解できます。

![MHN vs TF](docs/attention_cmp.png)

---

## 実行方法

### 1. 依存関係インストール
```bash
pip install -r requirements.txt
```

### 2. 実行方法
- Jupyter Notebook を使う場合:
```bash
jupyter notebook beta_comparison_simple.ipynb
```

- Python スクリプトを使う場合（例）:
```bash
python run_benchmark.py --variant A --alpha 0.5 --beta 2.0 --noise 0.1
```

### 3. variant の指定
- `variant=A` : Modern Hopfield (学習なし)
- `variant=B` : Transformer (デノイズ学習)

---

## 出力
- CSV: `out/records.csv`
- 図版: `out/summary_perf.png`,`out/summary_2d.png`

---

## 再現性への配慮
- 乱数 seed を固定
- 実行ごとに CSV/PNG を自動保存
- `requirements.txt` で依存関係を明示
