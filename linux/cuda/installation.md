# INSTALLING CUDA ON UBUNTU 16.06

* Make sure you execute the steps in the manual
* Use the third method installation (Deb remote) - no need to leave the GUI
* one example in Cuda samples will not compile - filter it out in the Makefile
* remember to add PATH in .profilerc

```
FILTER_OUT := 3_Imaging/cudaDecodeGL/Makefile
```

# COMPILING TENSORFLOW

* Remember to use Bazel 0.5.2
* Variables must be exported manually

```
export TF_NEED_CUDA=1
export TF_CUDA_VERSION=8.0
export TF_CUDNN_VERSION=5.1.10
export CUDA_TOOLKIT_PATH=/usr/local/cuda-8.0
export TF_CUDA_COMPUTE_CAPABILITIES=6.1
export GCC_HOST_COMPILER_PATH=/usr/bin/gcc
export TF_CUDA_LANG=0
export CUDNN_INSTALL_PATH=/home/diegoami/library/dnn/cuda
export TF_CUDA_COMPUTE_CAPABILITIES=6.1

```
