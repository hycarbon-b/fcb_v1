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

1. Use `scale.py` to scale up the orginal images (some original shape (D, W, H) is (D, 512, 512)) to (D, 1024, 1024)
2. Use `utils/preprocess.py` to preprocess the converted data.

#### Train
Change training configuration and data configuration in `config.py`, especially the path to your preprocessed data.

You can change network configuration in `net/config.py`, then run training script:

```
python train.py
```

Your ckpt will be saved in `results/experiment_5/model`. You can change it in the `config.py`.

For training, using Adam optimizer, lr = 0.001, batch size = 1, epoch = 100
#### Inference

For checkpoint, see [UaNet_HaN-Seg_bs1_epoch100](https://github.com/Richardqiyi/UaNet_OAR/releases/tag/UaNet_HaN-Seg_bs1_epoch100)

```
python mytest.py test --weight $PATH_TO_WEIGHT --nrrd-path $DICOM_PATH --out-dir $OUTPUT_DIR
```

Can only inference one image at a time.
