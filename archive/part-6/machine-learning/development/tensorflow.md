### Tensorflow

**Installation**

1. Setup GPU for Mac

   ```
   Follow the link https://www.tensorflow.org/get_started/os_setup#optional_setup_gpu_for_mac

   brew install coreutils
   brew tap caskroom/cask
   brew cask install cuda

   export CUDA_HOME=/usr/local/cuda
   export DYLD_LIBRARY_PATH="$DYLD_LIBRARY_PATH:$CUDA_HOME/lib"
   export PATH="$CUDA_HOME/bin:$PATH"

   sudo mv include/cudnn.h /Developer/NVIDIA/CUDA-8.0/include/
   sudo mv lib/libcudnn* /Developer/NVIDIA/CUDA-8.0/lib
   sudo ln -s /Developer/NVIDIA/CUDA-8.0/lib/libcudnn* /usr/local/cuda/lib/

   Also,
   Create an account for Accelerated Computing Developer Program
   ```

2. Check



