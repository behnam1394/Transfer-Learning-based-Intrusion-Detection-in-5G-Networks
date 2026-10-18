# DTL-5G Focused Code Sample

This repository contains three notebooks implementing a compact source-to-target
deep transfer learning workflow for DDoS detection in 5G network traffic.

## Dataset

The source-domain dataset used in this work is publicly available through IEEE DataPort:

**DoS/DDoS Attack Dataset of 5G Network Slicing**  
Md Sajid Khan, Behnam Farzaneh, Nashid Shahriar, Md Mahibul Hasan  
IEEE DataPort, 2023  
DOI: [10.21227/32k1-dr12](https://doi.org/10.21227/32k1-dr12)  
Dataset page: [IEEE DataPort](https://ieee-dataport.org/documents/dosddos-attack-dataset-5g-network-slicing)

The dataset files are not duplicated in this repository. Download them from the official
IEEE DataPort record and configure `DTL5G_SOURCE_DATA_ROOT` before running Notebook 1.

Additional dataset details and the recommended citation are provided in
[`DATASET.md`](DATASET.md).

## Related publications

This repository accompanies the 5G network-slicing and deep-transfer-learning research
developed through the following publications:

1. **B. Farzaneh, N. Shahriar, A. H. Al Muktadir, M. S. Towhid, and M. S. Khosravani**,  
   “DTL-5G: Deep transfer learning-based DDoS attack detection in 5G and beyond networks,”  
   *Computer Communications*, vol. 228, article 107927, 2024.  
   DOI: [10.1016/j.comcom.2024.107927](https://doi.org/10.1016/j.comcom.2024.107927)

2. **B. Farzaneh, N. Shahriar, A. H. Al Muktadir, and M. S. Towhid**,  
   “DTL-IDS: Deep Transfer Learning-based Intrusion Detection System in 5G Networks,”  
   *2023 19th International Conference on Network and Service Management (CNSM)*, pp. 1–5, 2023.  
   DOI: [10.23919/CNSM59352.2023.10327918](https://doi.org/10.23919/CNSM59352.2023.10327918)

3. **M. S. Khan, B. Farzaneh, N. Shahriar, N. Saha, and R. Boutaba**,  
   “SliceSecure: Impact and Detection of DoS/DDoS Attacks on 5G Network Slices,”  
   *2022 IEEE Future Networks World Forum (FNWF)*, pp. 639–642, 2022.  
   DOI: [10.1109/FNWF55208.2022.00117](https://doi.org/10.1109/FNWF55208.2022.00117)

## Notebooks

### 1. `01_BiLSTM_Source_Pretraining.ipynb`
- loads source-domain traffic from two network slices
- balances benign and attack traffic
- trains the source BiLSTM
- saves `models/BiLSTM_VM_Obj1_1.keras`

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

The datasets are not included in this repository.

Set:

- `DTL5G_SOURCE_DATA_ROOT` to the source VM dataset directory
- `NIDD_DATA_ROOT` to the 5G-NIDD dataset directory
- optionally `DTL5G_SOURCE_MODEL` to another source checkpoint

## Installation

```bash
pip install -r requirements.txt
```

Run the notebooks in numerical order.

## Citation

BibTeX entries for the dataset and related publications are available in
[`CITATION.bib`](CITATION.bib).
