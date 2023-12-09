# fcbformer
For original repo, see [fcbfomer](https://github.com/ESandML/FCBFormer)

#### Dataset

#### Environment

Python = 3.7, Pytorch = 1.8.0, Torchvision = 1.9.0, CUDA = 11.1 

#### GPU

1 NVIDIA GeForce RTX 2080

#### Docker


#### Install dependencies


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
                
#### Preprocess

#### Train

Specify `dataset` and  `data-root` to the file path 

```
python train.py --dataset siim --data-root $root_path

```

Your ckpt will be saved in ` `. You can change it in the ` `.

For training, lr = 0.001, batch size = 1, epoch = 100
#### Inference


```
python predict.py --train-dataset --test-dataset --data-root 
```

