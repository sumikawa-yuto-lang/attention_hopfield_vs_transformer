# Hopfield–Transformer Benchmark Suite

## 概要
Modern Hopfield (学習なし) と Transformer (K≠V のデノイズ学習) を **同一条件で比較**するベンチマーク環境です。  
α（パターン数/次元）、β（温度/鋭さ）、ノイズ強度を掃引し、復元オーバーラップを測定します。  
実測カーブと理論臨界線を同一図に重ねて可視化できます。

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
- CSV: `out/results.csv`
- 図版: `out/figure.png`

---

## デモ
- 実行例と結果を紹介した動画: **[YouTube限定公開リンク]** (差し替え予定)

---

## 再現性への配慮
- 乱数 seed を固定
- 実行ごとに CSV/PNG を自動保存
- `requirements.txt` で依存関係を明示
