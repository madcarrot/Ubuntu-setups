# Ubuntu-setups (Dual with Windows on 2 SSDs)

1. Install Ubuntu on one SSD by UEFI on flash drive
2. Install Windows 10 on the other SSD (with DVD or another flash drive)

## Windows will break the GRUB menu from Ubuntu
3. Use the ubuntu bootable flash drive, boot into "Try ubuntu", open terminal and use the following commands: ([Source](https://help.ubuntu.com/community/Boot-Repair))
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```
4. then select "Recommand repair"
5. after fix is done, reboot

## Then install NVIDIA driver
6. press "e" when the GRUB menu appears, and add `nouveau.modeset=0` to the end of the linux line ([Source](http://askubuntu.com/questions/742483/can-not-login-after-nvidia-driver-installation)
7. then go to terminal and execute
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361
sudo reboot
```

## install tensorflow
8. install Anaconda
9. execute
```
conda create -n tensorflow python=3.5
source activate tensorflow
# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5
# Requires CUDA toolkit 7.5 and CuDNN v5. For other versions, see "Install from sources" below.
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0-cp35-cp35m-linux_x86_64.whl
pip install --ignore-installed --upgrade $TF_BINARY_URL
```

## install cuda and cudnn
10. First download the cuda run file from NVIDIA
```
bash cuda_7.5.18_linux.run
# Select "yes" for create symbolic link
```
11. download the cudnn library
12. execute
```
tar xvzf cudnn-7.5-linux-x64-v5.1.tgz
sudo cp cuda/include/cudnn.h /usr/local/cuda/include
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```

## Test TensorFlow
13. Use the following command to find where tensorflow is installed:
`python -c 'import os; import inspect; import tensorflow; print(os.path.dirname(inspect.getfile(tensorflow)))'`
14. go to the directory where tensorflow is located, then `cd` into `models/image/mnist`, then use python to run `convolutional.py`

15. 
