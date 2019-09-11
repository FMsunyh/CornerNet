# CornerNet: Training and Evaluation Code

## Training and Evaluation
To train and evaluate a network, you will need to create a configuration file, which defines the hyperparameters, and a model file, which defines the network architecture. The configuration file should be in JSON format and placed in `config/`. Each configuration file should have a corresponding model file in `models/`. i.e. If there is a `<model>.json` in `config/`, there should be a `<model>.py` in `models/`. There is only one exception which we will mention later.

To train a model:
```
python train.py <model>
```

We provide the configuration file (`CornerNet.json`) and the model file (`CornerNet.py`) for CornerNet in this repo. 

To train CornerNet:
```
python train.py CornerNet
```
We also provide a trained model for `CornerNet`, which is trained for 500k iterations using 10 Titan X (PASCAL) GPUs. You can download it from [here](https://drive.google.com/open?id=16bbMAyykdZr2_7afiMZrvvn4xkYa-LYk) and put it under `<CornerNet dir>/cache/nnet/CornerNet` (You may need to create this directory by yourself if it does not exist). If you want to train you own CornerNet, please adjust the batch size in `CornerNet.json` to accommodate the number of GPUs that are available to you.

To use the trained model:
```
python test.py CornerNet --testiter 500000 --split <split>
```

If you want to test different hyperparameters in testing and do not want to overwrite the original configuration file, you can do so by creating a configuration file with a suffix (`<model>-<suffix>.json`). You **DO NOT** need to create `<model>-<suffix>.py` in `models/`.

To use the new configuration file:
```
python test.py <model> --testiter <iter> --split <split> --suffix <suffix>
```

We also include a configuration file for multi-scale evaluation, which is `CornerNet-multi_scale.json`, in this repo. 

To use the multi-scale configuration file:
```
python test.py CornerNet --testiter <iter> --split <split> --suffix multi_scale
```
