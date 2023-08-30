# KeiCOT
- KeiCOコーパス[[Liu and Kobayashi 22]](https://github.com/Liumx2020/KeiCO-corpus)を元に構築された敬語理解タスク評価データセット
- Chain-of-Thoughtプロンプティング[[Wei+ 22]](https://arxiv.org/abs/2201.11903)の有用性を検証するために、CoTあり/なしのテストセットをそれぞれ含む

## Problems
- KeiCOから[explore_keico.ipynb](./explore_keico.ipynb)と、手動でのフィルタリングおよびアノテーションでデータセット[keicot_base.tsv](./data/keicot_base.tsv)を作成
- データセット70件から、5種類の各設定で問題を生成し、350件のテストセットを作成

```txt
1. 背景情報：常体文が正 発言文：常体文 ラベル：正解
2. 背景情報：常体文が正 発言文：敬体文 ラベル：不正解
3. 背景情報：敬体文が正 発言文：常体文 ラベル：不正解
4. 背景情報：敬体文が正 発言文：敬体文 ラベル：正解 
5. 背景情報：敬体文が正 発言文：誤った敬体文 ラベル：不正解
```

### Prompt settings
- zero-shot w/o CoT
- zero-shot w/ CoT
- few-shot w/o CoT
- few-shot w/ CoT
(few-shot example num = 4)

## Predictions
### Models
- gpt-3.5-turbo
- gpt-4
### Hyperparameters
temperature = 0.0
```python
if do_cot:
    max_tokens = 512
else:
    max_tokens = 16
```

## Update
- 2023/08/31 正誤判定タスクでのテストセットと結果をアップ

## LICENSE
The KeiCOT dataset is under [CC-BY-4.0](
https://creativecommons.org/licenses/by/4.0/deed.ja).
