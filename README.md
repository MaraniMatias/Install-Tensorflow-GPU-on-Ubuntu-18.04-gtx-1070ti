# Install Tensorflow on Ubuntu-18.04
Quick install guide for Ubuntu 18.08

## Info

- Ubuntu: 18.04
- NVIDIA: GeForce GTX 1070ti
- Driver Version: 390.48
- CUDA Toolkit: 9.0
- CUDNN: 7.2


## Step by step
### Step 1: Update your GPU driver

Open a terminal and run the following 3 commands
```shell
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-390
```
Reboot your computer. To verify the installation, open a terminal and run the following command
```shell
nvidia-smi
```
The output should show the GPU name and the driver

### Step 2: Install the CUDA Toolkit (9.0)

- go to [developer.nvidia.com/cuda-90-download-archive](https://developer.nvidia.com/cuda-90-download-archive) and download the toolkit for linux, x86_64, ubuntu, 17.04, deb once the download is complete, open a terminal in the directory the base installer is and run the follow commands
```shell
sudo dpkg -i cuda-repo-ubuntu1704-9-0-local_9.0.176-1_amd64.deb
sudo apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
sudo apt-get update
sudo apt-get cuda
```
- Install update
```shell
sudo dpkg -i cuda-repo-ubuntu1704-9-0-local-cublas-performance-update_1.0-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1704-9-0-local-cublas-performance-update-2.0-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1704-9-0-local-cublas-performance-update-3.0-1_amd64.deb
sudo dpkg -1 cuda-repo-ubuntu1704-9-0-176-local-patch-4_1.0-1_amd64.deb
```
- Go to the last line and add the following lines (this will set your PATH variable)
```shell
sudo vim ~/.bashrc
```
```shell
export PATH=/usr/local/cuda-9.0/bin${PATH:+:$PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

### Step 2: Install the CUDA Toolkit (10.0)

- go to [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal) and download the toolkit for linux, x86_64, ubuntu, 17.04, deb once the download is complete, open a terminal in the directory the base installer is and run the follow commands

```shell
sudo dpkg -i cuda-repo-ubuntu1804-10-0-local-10.0.130-410.48_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-0-local-10.0.130-410.48/7fa2af80.pub
sudo apt-get update
sudo apt-get cuda
```
- Go to the last line and add the following lines (this will set your PATH variable)
```shell
sudo vim ~/.bashrc
```
```shell
export PATH=/usr/local/cuda-10.0/bin${PATH:+:$PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

### Step 3: Install CUDNN 7.2.1

- Go to https://developer.nvidia.com/cudnn
- Select cuDNN 7.2.1 for CUDA 9.0
- Download
```
libcudnn7_7.2.1.38-1+cuda9.0_amd64.deb
libcudnn7-dev_7.2.1.38-1+cuda9.0_amd64.deb
libcudnn7-doc_7.2.1.38-1+cuda9.0_amd64.deb
```
- Install
```shell
sudo dpkg -i libcudnn7_7.2.1.38-1+cuda9.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.2.1.38-1+cuda9.0_amd64.deb
sudo dpkg -i libcudnn7-doc_7.2.1.38-1+cuda9.0_amd64.deb
```
### Step 3: Install CUDNN

- Go to https://developer.nvidia.com/cudnn
- Select cuDNN 7.3.1 for CUDA version
- Download

- CUDA 10.0
```
libcudnn7_7.3.1.20-1+cuda10.0_amd64.deb
libcudnn7-dev_7.3.1.20-1+cuda10.0_amd64.deb
libcudnn7-doc_7.3.1.20-1+cuda10.0_amd64.deb
```

- CUDA 9.2
```
libcudnn7_7.3.1.20-1+cuda9.2_amd64.deb
libcudnn7-dev_7.3.1.20-1+cuda9.2_amd64.deb
libcudnn7-doc_7.3.1.20-1+cuda9.2_amd64.deb
```

- CUDA 9.0
```
libcudnn7_7.2.1.38-1+cuda9.0_amd64.deb
libcudnn7-dev_7.2.1.38-1+cuda9.0_amd64.deb
libcudnn7-doc_7.2.1.38-1+cuda9.0_amd64.deb
```

- Install
```shell
sudo dpkg -i libcudnn7_7.3.1.20-1+cuda10.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.3.1.20-1+cuda10.0_amd64.deb
sudo dpkg -i libcudnn7-doc_7.3.1.20-1+cuda10.0_amd64.deb
```

### Step 4: Insstall tensorflow-gpu

#### PIP
- Run the following command to install tensorflow
```shell
sudo apt-get install python3-pip python3-dev
sudo pip3 install -U tensorflow-gpu
```
#### Conda
- Install Anaconda
```shell
conda create -n tensorflow_gpuenv tensorflow-gpu keras
source activate tensorflow_gpuenv
```

## I read

- [www.youtube.com/watch?v=tZYIOrJ07LA](https://www.youtube.com/watch?v=tZYIOrJ07LA)
- [github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu](https://github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu)
