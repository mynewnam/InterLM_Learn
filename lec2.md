# Lec 2 轻松玩转书生·浦语大模型趣味 Demo

## 基本技能

+ 安装必要包；
```
conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.7 -c pytorch -c nvidia
pip install huggingface-hub==0.17.3
pip install transformers==4.34 
pip install psutil==5.9.8
pip install accelerate==0.24.1
pip install streamlit==1.32.2 
pip install matplotlib==3.8.3 
pip install modelscope==1.9.5
pip install sentencepiece==0.1.99
```
+ `snapshot_download` 下载模型并保存到指定路径；
```python
import os
from modelscope.hub.snapshot_download import snapshot_download

# 创建保存模型目录
os.system("mkdir /root/models")

# save_dir是模型保存到本地的目录
save_dir="/root/models"

snapshot_download("Shanghai_AI_Laboratory/internlm2-chat-1_8b", 
                  cache_dir=save_dir, 
                  revision='v1.1.0')
```
+ `transformers` 库利用本地模型进行推理的基本使用；
```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM


model_name_or_path = "/root/models/Shanghai_AI_Laboratory/internlm2-chat-1_8b"

tokenizer = AutoTokenizer.from_pretrained(model_name_or_path, trust_remote_code=True, device_map='cuda:0')
model = AutoModelForCausalLM.from_pretrained(model_name_or_path, trust_remote_code=True, torch_dtype=torch.bfloat16, device_map='cuda:0')
```

### 生成 300 字小故事

项目启动方式同`Tutorial`。

见作业

### 部署 “八戒” 模型

项目启动方式同`Tutorial`。

![alt text](pic/2.3.png)

## 基础作业：生成 300 字的小故事

![alt text](pic/2.1.png)

## 基础作业：Lagent 工具调用

![alt text](pic/2.2.png)