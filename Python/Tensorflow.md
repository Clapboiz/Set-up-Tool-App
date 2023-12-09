# Install tensorflow-gpu
### Request:
```
	python 3.8.10
	pips 21.3.1
	Cuda & CuDNN 11.8
	The rest of setuptools & wheel, install the latest version
	Must add the above to the path env system
```
Check Cuda version

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/424c88ed-2378-4543-ba74-3eb78b41acbe)

### Install command: pip install tensorflow-gpu or pip install tensorflow-gpu --pre

### Check: tensorflow-gpu work?
* Turn on cmd: write python
```
	from tensorflow.python.client import device_lib
	print(device_lib.list_local_devices())
```

* Or follow page: https://www.codingforentrepreneurs.com/blog/install-tensorflow-gpu-windows-cuda-cudnn/

### To download tensorflow-gpu without error please follow 1 of the following steps:

* Error of missing dll of CuDNN: then watch this clip

* https://www.youtube.com/watch?v=oDxMPb2xfbs

* See this site for download: https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#installwindows

### path env: 
```
	C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin
	C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\libnvvp
	C:\cuda\bin
	C:\cuda\include
	C:\cuda\lib\x64
	D:\Set up app\Python
	C:\Program Files\NVIDIA Corporation\Nsight Compute 2022.3.0\
```

### conflict libs

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/490793f9-a9e1-41d4-8f9d-4fe7f5005e9f)
```
	example: keras tensorflow-estimator tensorboard tensorflow-gpu tensorflow-intel conflicted


	## Solved:

 	pip uninstall keras tensorflow-estimator tensorboard tensorflow-gpu tensorflow-intel
	pip install --upgrade pip
	## clear cache
	pip cache purge
	pip install tensorflow keras tensorflow-gpu==2.10.1		
```
**Installed successfully**

```
	import tensorflow as tf
	print("Num GPUs Available: ", len(tf.config.list_physical_devices('GPU')))
```

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/4fa34b05-fb9f-4fc0-a5ad-dcbdce76d694)
