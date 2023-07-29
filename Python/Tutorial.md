Request:
	python 3.8.10
	pips 21.3.1
	Cuda & CuDNN 11.8
	the rest of setuptools & wheel, install the latest version
	Must add the above to the path env system

Install command: pip install tensorflow-gpu or pip install tensorflow-gpu --pre

Check: tensorflow-gpu work?
* turn on cmd: write python
	from tensorflow.python.client import device_lib
	print(device_lib.list_local_devices())

Or follow page: https://www.codingforentrepreneurs.com/blog/install-tensorflow-gpu-windows-cuda-cudnn/


To download tensorflow-gpu without error please follow 1 of the following steps:

* Error of missing dll of CuDNN: then watch this clip

* https://www.youtube.com/watch?v=oDxMPb2xfbs

* See this site for download: https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#installwindows

path env: 
	C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin
	C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\libnvvp
	C:\cuda\bin
	C:\cuda\include
	C:\cuda\lib\x64
	D:\Set up app\Python
	C:\Program Files\NVIDIA Corporation\Nsight Compute 2022.3.0\
	
	
	
	
