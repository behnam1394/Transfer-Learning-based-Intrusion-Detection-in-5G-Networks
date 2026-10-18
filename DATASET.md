# Dataset

## DoS/DDoS Attack Dataset of 5G Network Slicing

**Authors:** Md Sajid Khan, Behnam Farzaneh, Nashid Shahriar, Md Mahibul Hasan  
**Repository:** IEEE DataPort  
**Release:** September 25, 2023  
**DOI:** [10.21227/32k1-dr12](https://doi.org/10.21227/32k1-dr12)  
**Official record:** [IEEE DataPort](https://ieee-dataport.org/documents/dosddos-attack-dataset-5g-network-slicing)

The dataset contains flow-level benign and DoS/DDoS traffic generated in a 5G
network-slicing testbed. The code in this repository expects the downloaded source
dataset to be available locally and does not redistribute the dataset files.

## Use with this repository

Set the source-data directory before running `01_BiLSTM_Source_Pretraining.ipynb`:

```bash
export DTL5G_SOURCE_DATA_ROOT=/path/to/source/VM
```

The notebook expects the source directory to contain the benign and attack CSV files
referenced in its data manifest.

The target-domain notebooks additionally use 5G-NIDD. Set:

```bash
export NIDD_DATA_ROOT=/path/to/5G-NIDD
```

## Citation

```text
M. S. Khan, B. Farzaneh, N. Shahriar, and M. M. Hasan,
"DoS/DDoS Attack Dataset of 5G Network Slicing,"
IEEE DataPort, 2023, doi: 10.21227/32k1-dr12.
```

Please use the official IEEE DataPort record for dataset access, licensing information,
and the latest metadata.
