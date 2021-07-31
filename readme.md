本程序用于将darknet的训练数据转换为coco格式，以便让yolox 使用。


## 使用方法：
```
#for darknet data
python yolo2coco.py --data_path /path/to/darknet/data_config.data 

#for  yolo5 data 

python yolo2coco.py --data_path /path/to/yolo5/dataset/dir
```

上面的data_config.data是以下内容：

```
classes=2
train=gen_train.txt
valid=gen_valid.txt
names=qmobj.names
backup=data

```

文档参见 ： [csdn博客](https://blog.csdn.net/znsoft/article/details/119059967)

[YoloX 原始仓库](https://github.com/Megvii-BaseDetection/YOLOX)

[yolox 官方 自有数据训练方法](https://github.com/Megvii-BaseDetection/YOLOX/blob/main/docs/train_custom_data.md)





资料-  coco voc 格式 : http://www.xyu.ink/3612.html

## coco 数据集格式快速训练 方法 for YOLOX

1. clone yolox
```
  git clone  https://github.com/Megvii-BaseDetection/YOLOX
  cd YOLOX
 ``` 
2. 安装 必要的库 
  pip install -r requirements.txt
  
3. 安装  YOLOX
```
python setup.py  develop
```
  
4. 安装apex

注意，需要保证机器上安装的cuda版本和pytorch编译时的一致
```
git clone https://github.com/NVIDIA/apex

cd apex

pip install -v --disable-pip-version-check --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
```

## 数据准备

将coco 目录link到YOLOX/dataset/COCO 

例如：  ln -s /path/to/COCO  /path/to/YOLOX/dataset/COCO
## 命令行

```
python tools/train.py -n yolox-s -d 1 -b 8 --fp16 -o yolox-m  yolox-l yolox-x  yolox_s
```
d 1表示一块显卡， -b 8 表示批大小，如果多块卡，这儿的8要换成  显卡数＊８
