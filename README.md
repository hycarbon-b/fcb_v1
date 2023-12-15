# FCBFormer
For original repo, see [FCBFormer](https://github.com/ESandML/FCBFormer)

#### Dataset

[SIIM-ACR Pneumothorax Segmentation](https://www.kaggle.com/datasets/stevezeyuzhang/siim-acr-pneumothorax-segmentation)

#### Environment

Python = 3.7, Pytorch = 1.8.0, Torchvision = 1.9.0, CUDA = 11.1 

#### Docker
```
docker pull stevezeyuzhang/colab:1.7.1
```
#### Install dependencies

```
pip install -r requirements.txt
```

#### GPU

1 NVIDIA GeForce RTX 2080 Ti 11G


#### File Directory
```
|-- root
   |-- FCBFormer
	|-- Data
	|-- Metrics
	|-- Models
	|-- wandb
   |-- originalfile
	|-- imagesTr
		|-- 1.png
		|-- ...
	|-- labelsTr
		|-- 1.png
		|-- ...
	|-- imagesTs
		|-- 1.png
		|-- ...
	|-- labelsTs
		|-- 1.png
		|-- ...
```

#### Train

For training, lr = `1e-4`, batch size = `16`, epoch = `200`, optimizer = `AdamW`, lr_scheduler = `CosineAnnealingLR`

Specify `dataset` and  `data-root` to the file path 

```
python train.py --dataset siim --data-root $root_path
```

<details>
  <summary><b>Detailed command</b></summary>

  ```
python train.py --dataset Kvasir --data-root /path/to/dataset/ --epochs 200 --batch-size 4 --learning-rate 1e-4 --learning-rate-scheduler true --learning-rate-scheduler-minimum 1e-15 --multi-gpu false
Argument Details
--dataset: Specify the dataset to use (choices: Kvasir, CVC, chest, siim).
--data-root: Provide the root directory of the dataset.
--epochs: Number of training epochs (default: 200).
--batch-size: Batch size for training (default: 16).
--learning-rate: Initial learning rate (default: 1e-4).
--learning-rate-scheduler: Use learning rate scheduler (choices: true, false, default: true).
--learning-rate-scheduler-minimum: Minimum learning rate for the scheduler (default: 1e-15).
--multi-gpu: Use multiple GPUs for training (choices: true, false, default: false).
```
  

</details>

Your checkpoints will be saved in `/code/fcbformer/zhou/Trained_models`. You can change it in the `train.py`.

#### Inference

We provide checkpoints:

| checkpoints | logs |
|--------|--------|
| [siim_adamw_cos_lr1e-4_bs4_epoch200](https://github.com/hycarbon-b/fcb_v1/releases/download/siim_adamw_cos_lr1e-4_bs4_epoch200/siim_adamw_cos_lr1e-4_bs4_epoch200.pt) | [log](https://github.com/hycarbon-b/fcb_v1/releases/download/siim_adamw_cos_lr1e-4_bs4_epoch200/siim_adamw_cos_lr1e-4_bs4_epoch200.log) |


If your using the checkpoints we provided, please rename it as `FCBFormer_{}.pt`.

```
python predict.py --train-dataset --test-dataset --data-root 
```

<details>
  <summary><b>Detailed command</b></summary>
	
```
python predict.py --train-dataset siim --test-dataset siim --data-root /path/to/dataset/
Argument Details
--train-dataset: Specify the training dataset to use (choices: Kvasir, CVC, chest, siim).
--test-dataset: Specify the test dataset to use (choices: Kvasir, CVC, chest, siim).
--data-root: Provide the root directory of the dataset.
```

PS. this `predict.py` need the ground truth labels file. If you have none, you need rewrite this file

Please do not use the default path, you need add a forward slash at the end of the file path, for example: 

```
/FCBFormer/predict.py --train-dataset="chest" --test-dataset="chest" --data-root="/code/fcbformer/zhou/originalfile/chest/
```

</details>

