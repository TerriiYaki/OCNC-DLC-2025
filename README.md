# DeepLabCut Tutorial for OCNC 2025
This tutorial is part of the OIST computational neuroscience course 2025. For more information please visit the OIST OCNC website: https://groups.oist.jp/ocnc. This tutorial is in **addition** to the OIST DLC workshop on July 1st: https://www.oist.jp/conference/deeplabcut-workshop
## Contents and Motivation
The DeepLabCut (DLC) tutorial is put into the jupyter notebook:`OCNC-DLC-tutorial.ipynb` for simplicity of the workshop. I aimed to assemble it in a way that uses <span style="background-color:rgb(125, 194, 255)">**DLC without a GUI**</span>. So, I envisioned the user case to be more helpful if you want to set it up in a compute node/cluster. Or just in general, to facilitate for an automated workflow. Obviously in that case, it shouldn't be in a notebook! 

Oh! There is also a notebook for some plotting of results: `OCNC-DLC-tutorial-plotting.ipynb`! 
## Setup and Installation of tutorial materials
Please find the installation guidelines from the DLC repo here: https://deeplabcut.github.io/DeepLabCut/docs/installation.html
- <span style="background-color:rgb(237, 172, 194)">If you <b>do not</b> have a native DLC installation</span>, you can use the `OCNC_DLC_ENV.yml` file to install the requirements. This also includes the libraries I use for the plotting. *Note:* This disregards the GPU engagement.
- <span style="background-color:rgb(237, 172, 194)">If you <b>do</b> have a native DLC installation</span>, make sure you are using the correct kernel in the ipybn notebook.

### 1. Get the tutorial materials
```shell
git clone https://github.com/TerriiYaki/OCNC-DLC-2025.git
```
Move into the directory.
```shell
cd OCNC-DLC-2025
```
#### If no DLC installation:
```shell
conda env create -f OCNC_DLC_ENV.yml
```
Activate the tutorial environment
```shell
conda activate OCNC_DLC
```
### 2. Download the video into the video directory
```shell
mkdir -p video
```
Click the following link to download: https://filesender2.oist.jp/filesender/?s=download&token=ed4fe7e6-2a76-4e6a-90e0-963a4cb3223e
```shell
mv <"PATH of where your videos are downloaded to/M_190124_110324_12_60fps.avi"> video/
```
```shell
mv <"PATH of where your videos are downloaded to/M_190124_110324_12_30fps_30s.mp4"> video/
```
## This is the panic section with maybe some random tips (?)
- If you are a windows user (i'm sorry) please keep in mind the path specification and be consistent. Avoid using both to avoid confusion for *dear* computer. 
    - `r"C:\Users\"`(single slash) OR`"C:\\Users\\"` (double slash)
- If code *scary*, or to test, you can use the following to open the GUI:
    ```shell
        python -m deeplabcut
    ```
- If you have multiple python/conda's (miniforge.. miniconda.. brew.. etc) try some of the following to figure out the current situation (in case of conda). 
    ```shell
    which conda
    ```
    If it is wrong, do a check which environments are installed:
    ```shell
    conda env list
    ```
    Followed by the activation.
    ```shell
    source <"path to your miniforge/miniconda/anaconda/bin/activate">
    ```
- Check GPU engagement (nvidia) PyTorch version:
    ```shell
    python -c "import torch; print(torch.cuda.is_available())"
    ```
- Check GPU engagement (nvidia) TensorFlow version:
    ```shell
    python -c "import tensorflow as tf; print(tf.config.list_physical_devices())"
    ```