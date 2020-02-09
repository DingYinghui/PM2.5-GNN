# PM2.5-GNN

PM2.5-GNN: A Domain Knowledge Enhanced Graph Neural Network For PM2.5 Forecasting

## Dataset

- Download dataset **KnowAir** from [Google Drive](https://drive.google.com/open?id=1R6hS5VAgjJQ_wu8i5qoLjIxY0BG7RD1L) or [Baiduyun](https://pan.baidu.com/s/1sdPFSR8Oq3XPrXMnXFqd1w) with code `2mr6`.

## Requirements

```bash
pip install -r requirements.txt
```

## Experiment Setup

open `config.yaml`, do the following setups.

- set data path after your server name. Like,

```python
filepath:
  GPU-Server:
    knowair_fp: /data/wangshuo/haze/pm25gnn/KnowAir.npy
    results_dir: /data/wangshuo/haze/pm25gnn/results

```

- Uncomment the model you want to run.

```python
#  model: MLP
#  model: LSTM
#  model: GRU
#  model: GC_LSTM
#  model: nodesFC_GRU
   model: PM25_GNN
#  model: PM25_GNN_nosub
```

- Choose the sub-datast number in [1,2,3].

```python
 dataset_num: 3
```

- Set weather variables you wish to use. Following is the default setting in the paper. You can uncomment specific variables. Variables in dataset **KnowAir** is defined in `metero_var`.

```python
  metero_use: ['2m_temperature',
               'boundary_layer_height',
               'k_index',
               'relative_humidity+950',
               'surface_pressure',
               'total_precipitation',
               'u_component_of_wind+950',
               'v_component_of_wind+950',]

```

## Run

```bash
python train.py
```