# DTL-5G Code Sample

This folder contains a focused subset of code that I implemented for my research on deep transfer learning for DDoS detection in 5G and beyond networks.

The notebooks illustrate the main experimental pipeline:

1. Source-domain BiLSTM model training
2. Target-domain baseline evaluation using the 5G-NIDD dataset
3. DTL1 transfer learning through selective layer freezing and fine-tuning

## My Contribution

I implemented the experimental workflow, including data preprocessing, model construction and training, transfer-learning configurations, evaluation, and performance analysis used in these notebooks.

## Associated Publication

Farzaneh, Behnam, Nashid Shahriar, Abu Hena Al Muktadir, Md Shamim Towhid, and Mohammad Sadegh Khosravani. "DTL-5G: Deep transfer learning-based DDoS attack detection in 5G and beyond networks." Computer Communications 228 (2024): 107927.

## Files

- `01_BiLSTM_Source_Pretraining.ipynb`  
  Trains the BiLSTM model on the source-domain 5G network-slicing dataset.

- `02_BiLSTM_Target_Baseline.ipynb`  
  Trains and evaluates the same architecture directly on the 5G-NIDD target dataset without transfer learning.

- `03_BiLSTM_DTL1_TransferLearning.ipynb`  
  Applies the DTL1 fine-tuning strategy by freezing part of the pretrained model and retraining the remaining layers on 5G-NIDD.

## Notes

The datasets are not included in this code sample. Dataset paths in the original experimental notebooks may need to be adjusted before execution.
