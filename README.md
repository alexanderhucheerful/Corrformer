# Corrformer

Corrformer with the Multi-Correlation mechanism, which can unify the temporal auto-correlation and spatial correlation in a learned multiscale tree structure.

## Code Structure

```python
|-- Corrformer
   |-- data_provider # Data loader
   |-- exp # Pipelines for train, validation and test
   |-- layers 
   |   |-- Embed.py # Equ (1) of the paper
   |   |-- Corrformer_EncDec.py # Equ (2) and Equ (3) of the paper
   |   |-- Causal_Conv.py # Causal conv for Cross-Correlation
   |   |-- Multi_Correlation.py # Equ (5)-(10) of the paper
   |-- models
   |   |-- Corrformer.py # Overall framework
   |-- utils
   |-- scripts # Running scripts
   |-- dataset # Place the download datsets here
   |-- checkpoints # Place the output or pretrained models here
```

## Reproduction

1. Find a device with GPU support. Our experiment is conducted on a single RTX 24GB GPU and in the Linux system.
2. Install Python 3.6, PyTorch 1.7.1. The following script can be convenient.

```bash
pip install -r requirements.txt # take about 5 minutes
```

2. Download the dataset from [[Tsinghua Cloud]](https://cloud.tsinghua.edu.cn/d/f5b13a194255457c9460/). And place them under the `./dataset` folder.

3. Train and evaluate the model with the following scripts.

```shell
bash ./scripts/Global_Temp/Corrformer.sh # take about 18 hours
bash ./scripts/Global_Wind/Corrformer.sh # take about 18 hours
```

Note: Since the raw data for Global Temp and Global Wind from the NCEI has been multiplied by ten times, the actual MSE and MAE for these two benchmarks should be divided by 100 and 10 respectively.

## Demo

For a simple demo, we would recommend the experiments with the pre-trained models, which can provide a fast test of our code. Here are the detailed instructions:

1. Configure the environment with the above instructions. Note that the following experiments will take 4GB GPU memory.
2. Download the datasets and pretrained models from [[Tsinghua Cloud]](https://cloud.tsinghua.edu.cn/d/f5b13a194255457c9460/). Place the pretrained models under the `./checkpoints` folder.
3. Execute the demo with the following scripts.

```bash
bash ./scripts/Demo/Global_Temp_demo.sh # take about 35 minutes
bash ./scripts/Demo/Global_Wind_demo.sh # take about 35 minutes
```

Note again: Since the raw data for Global Temp and Global Wind from the NCEI has been multiplied by ten times, **the actual MSE and MAE for these two benchmarks should be divided by 100 and 10 respectively**.
