# Setup your computer

If you want to use your own computer to work on the course material you should follow the below procedures. 

## System requirements

Note that to successfully run many of the notebooks from Part 2 you'll ned a relatively powerful computer equipped with a CUDA compatible NVIDIA GPU (minimum compute capability of 3.7). Note that you _may_ get by with a ROCm compatible AMD GPU, but that hasn't been tested with the course notebooks. 

You should be running GNU/Linux, f.ex. Ubuntu 18.04 or 20.04. Ubuntu alongside Windows works fine of course (i.e. a dual boot setup). If that's not an option, you can use WSL on Windows 10 and install CUDA there: https://developer.nvidia.com/cuda/wsl. Note that the latter option is way less recommended than a full GNU/Linux installation.

If your system doesn't meet these requirements I recommend that you rather use either the Google Colab or Paperspace Gradient option for the notebooks:

[![Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alu042/PCS956-DL-2021/blob/master/)
&nbsp;&nbsp;&nbsp;[![Gradient](https://assets.paperspace.io/img/gradient-badge.svg)](https://console.paperspace.com/github/alu042/PCS956-DL-2021/blob/master/?runtime=paperspace/fastai)


## NVIDIA driver
You'll need to install a recent NVIDIA driver (f.ex. v470), potentially upgrading the one you're currently using. You'll find plenty of instructions online. This one's pretty good: https://linuxconfig.org/install-the-latest-nvidia-linux-driver. Note that it is not necessary to install CUDA: the driver is sufficient. Anaconda will take care of the CUDA installation.

## Anaconda
You should use the Anaconda Python distribution (https://www.anaconda.com/products/individual) as that'll take care of all the package management, including installing the necessary CUDA components. 

Create a separate conda environment for the course, running Python 3.8: 
```bash
conda create -n pcs956 python=3.8 ipykernel
```
It's convenient to install an accompanying Jupyter kernel: 
```bash
conda activate pcs956
python -m ipykernel install --user --name pcs956
``` 


## PyTorch
For most of the notebooks we'll go through, following these fastai instructions is a good way to go: https://docs.fast.ai/, as you'll end up with PyTorch and several other relevant libraries. In short, run 
```bash
conda activate pcs956
conda install -c fastchan fastai anaconda
``` 

## Instructions specific to the audio example in Part 2
For the notebook `DL-Example-3-1-representing_data_as_images-sound_classification.ipynb` you'll need a separate conda environment as we'll use some packages that are incompatible with those in the `pcs956` environment created above. Do the following before running the notebook:

```
conda create -n pcs956-fastaudio python=3.7 ipykernel pandas
conda activate pcs956-fastaudio
conda install pytorch=1.8.1 torchvision=0.8.1 torchaudio=0.8.1 cudatoolkit -c pytorch -c nvidia
pip install fastaudio
python -m ipykernel install --user --name pcs956-fastaudio
``` 

## Troubleshooting
Once you've gone through the above process you should be able to run the course notebooks using 
```bash
jupyter notebook
```
or `jupyter lab` if you prefer JupyterLab. If you run into problems, check that the notebooks are using the correct kernel (i.e., that it says "pcs956" at the top right in the notebooks). 

If you're having issues with the PyTorch installation you may want to install PyTorch using the official instructions at https://pytorch.org/get-started/locally/ before installing fastai (in the same conda environment).

