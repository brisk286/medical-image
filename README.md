## 指令说明

#### 聚类模型

```shell
python calculate.py --option [默认为red，检测红色模型] --source_path [原生图片文件夹地址] --out_image_path [图片输出结果地址] --out_txt_path [文字输出结果地址]
```

```shell
例：
python calculate.py --option red --source_path raw_images/raw_box/red --out_image_path results/red --out_txt_path results/red
```

> 注意文件分隔符用  /
>

> 路径中不要含有中文(文件夹、文件不用中文命名)

### 彩色识别

#### 区域检测模型

```shell
python detect.py  --device [使用的设备，默认为CPU] --source [原生图片文件夹地址] --save-txt [是否保存文本] --save-conf [是否保存详细信息] --save-crop [是否保存目标图片]
```

```shell
例：
python detect.py  --device cpu --source input\ --save-txt --save-conf --save-crop
```

#### 裁剪脚本

```shell
python crop_img.py  --source_path [区域检测模型结果地址] --out_image_path [裁剪图片保存地址]
```

```shell
例：
python crop_img.py  --source_path runs/detect/exp2/crops/colors --out_image_path ../../raw_images/raw_box/colors
```

#### 聚类模型

```shell
python calculate.py --option [默认为red，检测红色模型] --source_path [原生图片文件夹地址] --out_image_path [图片输出结果地址] --out_txt_path [文字输出结果地址]
```

```shell
例：
python calculate.py --option colors --source_path raw_images/raw_box/colors --out_image_path results/colors --out_txt_path results/colors
```





## 使用步骤说明

### 红色识别

1. 将人工裁剪好的绿框区域放入`medical-images/raw_images/raw_box` 中
2. 打开`Anaconda Prompt`
3. 切换到目标`medical-images`文件下(切换硬盘：如切换到D盘  d:   进入某个文件夹： cd 文件夹名  返回上一层: cd ..)
4. 输入 `python calculate.py --option red --source_path raw_images/raw_box/red --out_image_path results/red --out_txt_path results/red `
5. 等待输出结束
6. 结果文件默认存放地址 `medical-images/results/red`



### 彩色识别

1. 将原生图片放入`medical-images/box_detector/yolo5/input`
2. 打开`Anaconda Prompt`，进入文件夹`medical-images/box_detector/yolo5`
4. 输入`python detect.py  --device cpu --source input/ --save-txt --save-conf --save-crop `
5. 等待输出结束， 查看输出结果保存路径
6. 输入`python crop_img.py  --source_path [输出结果保存路径]` 例:`runs/detect/exp2/crops/colors`
7. 进入文件夹`medical-images/`
8. 地址栏输入`cmd` 进入命令行
9. 输入`python calculate.py --option colors --source_path raw_images/raw_box/colors  --out_image_path results/colors --out_txt_path results/colors `
10. 等待输出结束
11. 结果文件默认存放地址 `medical-images/results/colors`





## 环境配置

1. 新建虚拟环境


```shell
conda create -n yolo5 python=3.7
```

2. 安装pytorch

```shell
pip3 install torch torchvision torchaudio
```

> 默认使用CPU计算，如果要使用更快计算速度需要安装对应的CUDA和pytorch-gpu版本

3. 切换到yolo5项目文件夹下，安装环境

```shell
pip install -r requirements.txt
```

```shell
pip install scikit-learn
```

