<h1 align="center">IOPaint</h1>
<p align="center">A free and open-source inpainting & outpainting tool powered by SOTA AI model.</p>

<p align="center">
  <a href="https://github.com/Sanster/IOPaint">
    <img alt="total download" src="https://pepy.tech/badge/iopaint" />
  </a>
  <a href="https://pypi.org/project/iopaint">
    <img alt="version" src="https://img.shields.io/pypi/v/iopaint" />
  </a>
  <a href="">
    <img alt="python version" src="https://img.shields.io/pypi/pyversions/iopaint" />
  </a>
  <a href="https://huggingface.co/spaces/Sanster/iopaint-lama">
    <img alt="HuggingFace Spaces" src="https://img.shields.io/badge/%F0%9F%A4%97%20HuggingFace-Spaces-blue" />
  </a>
  <a href="https://colab.research.google.com/drive/1TKVlDZiE3MIZnAUMpv2t_S4hLr6TUY1d?usp=sharing">
    <img alt="Open in Colab" src="https://colab.research.google.com/assets/colab-badge.svg" />
  </a>
</p>

| 擦除 ([LaMa](https://www.iopaint.com/models/erase/lama))                                             | 替换对象 ([PowerPaint](https://www.iopaint.com/models/diffusion/powerpaint))                         |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| <video src="https://github.com/Sanster/IOPaint/assets/3998421/264bc27c-0abd-4d8b-bb1e-0078ab264c4a"> | <video src="https://github.com/Sanster/IOPaint/assets/3998421/1de5c288-e0e1-4f32-926d-796df0655846"> |

| 绘制文本 ([AnyText](https://www.iopaint.com/models/diffusion/anytext))                               | 图像扩充 ([PowerPaint](https://www.iopaint.com/models/diffusion/powerpaint))                         |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| <video src="https://github.com/Sanster/IOPaint/assets/3998421/ffd4eda4-f7d4-4693-93d8-d2cd5aa7c6d6"> | <video src="https://github.com/Sanster/IOPaint/assets/3998421/c4af8aef-8c29-49e0-96eb-0aae2f768da2"> |

## 功能特性

- **完全免费开源**，支持完全自托管，支持 CPU、GPU 和 Apple Silicon。
- [Windows 一键安装包](https://www.iopaint.com/install/windows_1click_installer)
- [OptiClean](https://apps.apple.com/ca/app/opticlean/id6452387177)：适用于 macOS 和 iOS 的对象擦除 App。
- 支持多种 AI [模型](https://www.iopaint.com/models) 以执行擦除、局部重绘或图像扩充任务。

  - [擦除模型 (Erase models)](https://www.iopaint.com/models#erase-models)：此类模型主要用于从图像中移除不需要的物体、瑕疵、水印或人物。
  - 扩散模型 (Diffusion models)：此类模型可用于替换对象或执行图像扩充。一些常用的流行模型包括：
    - [runwayml/stable-diffusion-inpainting](https://huggingface.co/runwayml/stable-diffusion-inpainting)
    - [diffusers/stable-diffusion-xl-1.0-inpainting-0.1](https://huggingface.co/diffusers/stable-diffusion-xl-1.0-inpainting-0.1)
    - [andregn/Realistic_Vision_V3.0-inpainting](https://huggingface.co/andregn/Realistic_Vision_V3.0-inpainting)
    - [Lykon/dreamshaper-8-inpainting](https://huggingface.co/Lykon/dreamshaper-8-inpainting)
    - [Sanster/anything-4.0-inpainting](https://huggingface.co/Sanster/anything-4.0-inpainting)
    - [BrushNet](https://www.iopaint.com/models/diffusion/brushnet)
    - [PowerPaintV2](https://www.iopaint.com/models/diffusion/powerpaint_v2)
    - [Sanster/AnyText](https://huggingface.co/Sanster/AnyText)
    - [Fantasy-Studio/Paint-by-Example](https://huggingface.co/Fantasy-Studio/Paint-by-Example)

- [插件系统](https://www.iopaint.com/plugins)：

  - [Segment Anything](https://iopaint.com/plugins/interactive_seg)：精准快速的交互式对象分割。
  - [RemoveBG](https://iopaint.com/plugins/rembg)：移除图像背景或为前景对象生成遮罩 (Mask)。
  - [Anime Segmentation](https://iopaint.com/plugins/anime_seg)：类似于 RemoveBG，但模型专为动漫图像训练。
  - [RealESRGAN](https://iopaint.com/plugins/RealESRGAN)：超分辨率重建。
  - [GFPGAN](https://iopaint.com/plugins/GFPGAN)：人脸修复。
  - [RestoreFormer](https://iopaint.com/plugins/RestoreFormer)：人脸修复。

- [文件管理器](https://iopaint.com/file_manager)：便捷地浏览图片并将其直接保存到输出目录。

## Quick Start

### 启动 WebUI

IOPaint 提供了一个便捷的 Web 界面，让你可以利用最新的 AI 模型编辑图像。
你可以通过运行以下命令轻松安装并启动 IOPaint：

```bash
# 若要使用 GPU，请先安装 CUDA 版本的 pytorch。
# pip3 install torch==2.1.2 torchvision==0.16.2 --index-url https://download.pytorch.org/whl/cu118
# AMD GPU 用户请使用以下命令（仅适用于 Linux，因为 Windows 下的 ROCm 尚未支持 PyTorch）。
# pip3 install torch==2.1.2 torchvision==0.16.2 --index-url https://download.pytorch.org/whl/rocm5.6

pip3 install iopaint
iopaint start --model=lama --device=cpu --port=8080

```

搞定！现在你可以通过浏览器访问 http://localhost:8080 开始使用 IOPaint。

所有模型将在启动时自动下载。如果你想更改下载目录，可以添加 `--model-dir` 参数。更多文档请参阅[此处](https://www.iopaint.com/install/download_model)。

你可以点击[此处](https://www.iopaint.com/models)查看其他支持的模型，或点击[此处](https://www.iopaint.com/models#load-ckptsafetensors)了解如何使用本地的 sd ckpt/safetensors 文件。

### 插件

你可以在启动服务时指定要使用的插件，使用 `iopaint start --help` 命令可以查看启用插件的具体指令。

更多插件演示请见[此处](https://www.iopaint.com/plugins)。

```bash
iopaint start --enable-interactive-seg --interactive-seg-device=cuda

```

### 批量处理

你也可以在命令行中使用 IOPaint 对图像进行批量处理：

```bash
iopaint run --model=lama --device=cpu \
--image=/path/to/image_folder \
--mask=/path/to/mask_folder \
--output=output_dir

```

`--image` 是包含输入图像的文件夹，`--mask` 是包含对应遮罩图像的文件夹。
当 `--mask` 指定为单个遮罩文件的路径时，所有图像都将使用该遮罩进行处理。

你可以在下方查看更多关于 IOPaint 支持的可用模型和插件的信息。

## 开发指南

首先安装 [nodejs](https://nodejs.org/en)，然后安装前端依赖。

```bash
git clone https://github.com/Sanster/IOPaint.git
cd IOPaint/web_app
npm install
npm run build
cp -r dist/ ../iopaint/web_app

```

在 `web_app` 目录下创建一个 `.env.local` 文件，并填写后端 IP 和端口。

```
VITE_BACKEND=http://127.0.0.1:8080

```

启动前端开发环境：

```bash
npm run dev

```

安装后端依赖并启动后端服务：

```bash
pip install -r requirements.txt
python3 main.py start --model lama --port 8080

```

然后你可以访问 `http://localhost:5173/` 进行开发。
前端代码修改后会自动更新，但修改 Python 代码后需要重启后端服务。
