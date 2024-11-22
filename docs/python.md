# python镜像源

## 设置镜像源

#### 全局

```shell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/
```

#### 临时

```shell
pip install ?  -i https://mirrors.aliyun.com/pypi/simple/
```

## 镜像-官方

```shell
https://pypi.python.org/simple/  
```

## 镜像-阿里

```shell
https://mirrors.aliyun.com/pypi/simple/
```

#### pytorch

```shell
https://mirrors.aliyun.com/pytorch-wheels
```

```shell
# -f 指定下载源
# torch2.1.2版本对应
pip install torch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 -f https://mirrors.aliyun.com/pytorch-wheels/cu121
# 
pip install torch==2.3.1 torchvision==0.18.1 torchaudio==2.3.1 -f https://mirrors.aliyun.com/pytorch-wheels/cu121
```

## 镜像-中科大

```shell
https://pypi.mirrors.ustc.edu.cn/simple/ 
```

## 镜像-清华

```shell
https://pypi.tuna.tsinghua.edu.cn/simple/
```

## 镜像-中国科学院 

```shell
https://pypi.mirrors.opencas.cn/simple/        
```










