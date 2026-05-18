
所有的本地修改（包括调整用于适配 RTX 5070 显存的 `batch_size` 和修复过的文件路径及依赖）我都已经帮你**自动提交 (Commit) 并推送 (Push) 到你名下 Fork 好的 GitHub 仓库中**啰！

现在无论是你要在这里继续训练，还是在别的机器上跑，操作流程都变得非常简单了。

### 之后在任意设备上继续训练的步骤：

1. **拉取你的仓库和数据集**
   ```bash
   git clone https://github.com/zxc20041/Retinexformer.git
   cd Retinexformer
   ```
   *记得像以前一样下载放入 `venv/dataset/LOLv1`*

2. **新建并配置环境**
   ```bash
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   pip install torch==2.4.1+cu121 torchvision==0.19.1+cu121 torchaudio==2.4.1+cu121 --index-url https://download.pytorch.org/whl/cu121
   
   pip install matplotlib scikit-learn scikit-image opencv-python yacs joblib natsort h5py tqdm tensorboard einops gdown addict future lmdb numpy pyyaml requests scipy yapf lpips thop timm
   
   python setup.py develop --no_cuda_ext
   ```
   *(注：这是无 Bug 版本的依赖，后续都可以无脑复用这套安装命令。)*

3. **一键启动训练！**
   ```bash
   # 上面这步环境配好后，直接跑这句就可以开始魔鬼训练了：
   python basicsr/train.py -opt Options/RetinexFormer_LOL_v1.yml
   ```

接下来你可以随时启动本地或远端机器的训练了，顺便你可以先把终端里一直没跑完的 `pip` 终止掉（按 `Ctrl + C`，或者在右上角关闭那个报错残留的 Terminal）。
如果你接下来在执行中抛出如 **OOM（Out of Memory）** 错误，我们可以继续帮你在远端代码中进一步压缩图片输入块的 `Patch Size` 大小。