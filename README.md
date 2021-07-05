# Tensorflow-2.4.1-python3.8 CUDA with no avx support for Ubuntu 20

The following wheel has been compiled on xeon x5660 , a cpu with no AVX support.

** If you want to get the wheel by cloning the repo, make sure you have git lfs installed since this repo is using it !**, if not, please download it directly from github.

before installing it , follow these steps:

## CUDA

* get the correct version for cuda to make it work :
 
* wget https://developer.download.nvidia.com/compute/cuda/11.0.3/local_installers/cuda_11.0.3_450.51.06_linux.run

* sudo sh cuda_11.0.3_450.51.06_linux.run

* Make sure the PATH is correctly edited after the install , if not , edit it correctly with regard to the output installation instructions.

PS: Just in case reboot the computer here , I am not sure it is mandatory, but who knows;)

## CUDNN

* get the correct version of cudnn :cudnn-11.3-linux-x64-v8.2.0.53 on nvida cudnn archive (**Download cuDNN v8.2.0 (April 23rd, 2021), for CUDA 11.x** then **cuDNN Library for Linux (x86_64)**) : https://developer.nvidia.com/rdp/cudnn-archive

* copy the include folder's files of the downloaded cudnn files in  /usr/local/cuda-11.0/include

* do the same with the lib64 files. copy them in /usr/local/cuda-11.0/lib64

* finally, execute : sudo chmod a+r /usr/local/cuda-11.0/include/cudnn*.h /usr/local/cuda-11.0/lib64/libcudnn

again make a reboot here, just in case.

## INSTALLATION OF THE WHEEL

python3.8 -m pip install path/to/the/wheel/tensorflow-2.4.1-cp38-cp38-linux_x86_64.whl

## Test the installation

* import tensorflow as tf

* physical_devices = tf.config.list_physical_devices() 

* print(physical_devices)

If everything works , you should have no core dump when importing tensorflow and the physical_devices variable should contain a GPU if your computer has a NVIDIA card.



