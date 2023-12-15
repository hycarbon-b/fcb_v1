# fcbformer
For original repo, see [fcbfomer](https://github.com/ESandML/FCBFormer)

#### Dataset

#### Environment

Python = 3.7, Pytorch = 1.8.0, Torchvision = 1.9.0, CUDA = 11.1 

#### GPU

1 NVIDIA GeForce RTX 2080

#### Docker
```
docker pull stevezeyuzhang/colab:1.7.1
```

#### Install dependencies

```
pip install -r requirements.txt
```


#### File Directory
```

|-- root
	|-- imagesTr
		|-- 1.png
		|-- ...
	|-- labelssTr
		|-- 1.png
		|-- ...
	|-- imagesTs
		|-- 1.png
		|-- ...
	|-- labelssTs
		|-- 1.png
		|-- ...

```

#### Train

Specify `dataset` and  `data-root` to the file path 

```
python train.py --dataset siim --data-root $root_path

```

Your ckpt will be saved in `/code/fcbformer/zhou/Trained_models`. You can change it in the `train.py`.

For training, lr = `1e-4`, batch size = `16`, epoch = `200`, optimizer = `AdamW`, lr_scheduler = `CosineAnnealingLR`
#### Inference


```
python predict.py --train-dataset --test-dataset --data-root 
```

