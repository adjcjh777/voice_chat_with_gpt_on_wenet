# 基于WENET的语音聊天GPT

## 项目介绍

本项目是在[WeNet](https://github.com/wenet-e2e/wenet)的基础上，在Windows11上结合其给出的示例并调用OPENAI的API做出的尝试性实验。

## 准备

- 参考WeNet源项目下的[pretrained_models](https://github.com/wenet-e2e/wenet/blob/main/docs/pretrained_models.md),下载自己需要的数据集，本次项目中在进行过程中对给出的**4个中文语料模型**进行了测试，**wenetspeech**数据集的测试识别效果是最好的，当然也可以根据需求自己训练自己需要的数据集。
- 项目使用WeNet中给出的[Prebuilt Docker](https://github.com/wenet-e2e/wenet/blob/main/runtime/libtorch/README.md)，所以需要熟悉Docker的使用，晚上拉不下来镜像的可以等到早上再试试。
- 项目调用了GPT的API，所以学习OPENAI的API调用方法也是必要的。

## 动手实现

### 关于Docker

由于Docker默认的容器和镜像的储存位置在C盘，不想要C盘变红的朋友还是把数据的默认储存位置改到D盘比较好，教程网上有很多，这里不再赘述。

### 克隆项目

已经安装Git的情况下直接克隆项目到你的项目文件夹即可。

```shell
git clone https://github.com/adjcjh777/voice_chat_with_gpt_on_wenet
```

没有安装Git的小伙伴也可以手动下载代码压缩包并解压到你的项目文件夹。

### 预训练数据集

可以先使用WeNet源项目的index.html对数据集进行测试，选择效果满意的数据集。

### 启动Docker

安装完成Docker之后在项目文件夹下打开Windows Terminal（或Power Shell），输入以下代码。

```shell
docker run --name voice_chat_gpt -it -p 10086:10086 -v $PWD/YOUR_MODEL_DIR:/home/wenet/model wenetorg/wenet-mini:latest bash /home/run.sh
```

将容器命名为***voice_chat_gpt***，启动WeNet官方的Prebuilt Docker并将输出映射到本地10086端口。

### chat.html

将apiKey替换为自己的OpenAI api key,并根据需求修改页面布局和CSS样式，目前还有很多不足的地方，只能实现一问一答。



