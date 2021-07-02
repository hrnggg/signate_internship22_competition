## SIGNATE 22卒インターンコンペ Silver Medal Solution

### Model
- Stacking 
	- 1st-stage: LightGBM, MLP, Logistic Regeressionなどを含む10モデル
	- 2nd-stage: LightGBM
- LightGBM x2
- Blending(Stacking + LightGBM)

### Feature Engineering
- 組み合わせ特徴量
- 集約特徴量（min, max, mean, std, count）
- binning
- SVDによる次元削減
- 正規化
- 決定木ベースのモデルについてはfeature importance上位10%程度を選択
- Target Encoding/One-Hot Encoding

### Validation
- StratifiedKFold 5-Fold(3 seed average)

### Post Processing
- 正例に対する予測確率から資金調達の成否を決定する際の閾値の最適化
- scipy.optimize.minimizeを使用して局所最適化
