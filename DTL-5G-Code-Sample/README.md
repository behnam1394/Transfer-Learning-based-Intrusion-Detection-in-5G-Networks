# DTL-5G Focused Code Sample

This repository contains three notebooks implementing a compact source-to-target
deep transfer learning workflow for DDoS detection in 5G network traffic.

## Notebooks

### 1. `01_BiLSTM_Source_Pretraining.ipynb`
- loads source-domain traffic from two network slices
- balances benign and attack traffic
- trains the source BiLSTM
- saves `artifacts/BiLSTM_VM_Obj1_1.keras`

### 2. `02_BiLSTM_Target_Baseline.ipynb`
- loads and balances 5G-NIDD
- trains the same BiLSTM architecture from scratch
- provides the no-transfer target baseline

### 3. `03_DTL1_BiLSTM_TransferLearning.ipynb`
- loads the source checkpoint
- freezes the first 6 of 9 layers
- fine-tunes the final 3 layers on 5G-NIDD

## Experimental configuration

- 8 selected traffic features
- 80/20 stratified train/test split
- StandardScaler fitted only on the training partition
- Objective-1 seeds: `42, 142, 12, 4, 80`
- 9-layer BiLSTM
- 99,970 total parameters
- L2 regularization = 0.001
- dropout = 0.5
- Adam learning rate = 1e-5
- maximum 200 epochs with early stopping
- attack is the positive class for recall, precision, F1, and ROC-AUC
- deterministic TensorFlow operations requested where supported
- explicit checks for duplicate filenames and non-finite selected-feature values

## Focused sample

The notebooks are configured for Objective-1 iteration 1 (`random_state=42`).
The complete experiment can be repeated with all five fixed seeds and the metrics
aggregated across runs.

Notebook 3 uses the checkpoint produced by Notebook 1 by default. Set
`DTL5G_SOURCE_MODEL` to use another source checkpoint.

## Data paths

The datasets are not included.

Set:

- `DTL5G_SOURCE_DATA_ROOT` to the source VM dataset directory
- `NIDD_DATA_ROOT` to the 5G-NIDD dataset directory
- optionally `DTL5G_SOURCE_MODEL` to another source checkpoint

## Installation

```bash
pip install -r requirements.txt
```

Run the notebooks in numerical order.
