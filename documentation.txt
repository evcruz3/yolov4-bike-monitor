	

1. CUDA Toolkit Installation

   Try:
	sudo apt install nvidia-cuda-toolkit
   Or:
	wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
	sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600

	wget https://developer.download.nvidia.com/compute/cuda/11.3.0/local_installers/cuda-repo-ubuntu2004-11-3-local_11.3.0-465.19.01-1_amd64.deb
	sudo dpkg -i cuda-repo-ubuntu2004-11-3-local_11.3.0-465.19.01-1_amd64.deb

	sudo apt-key add /var/cuda-repo-ubuntu2004-11-3-local/7fa2af80.pub
	sudo apt-get update

	sudo apt-get -y install cuda
	export PATH=/usr/local/cuda-11.3/bin${PATH:+:${PATH}}
	export LD_LIBRARY_PATH=/usr/local/cuda-11.3/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

2. Download the ff files:
	https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.2.0.53/11.3_04222021/Ubuntu20_04-x64/libcudnn8_8.2.0.53-1+cuda11.3_amd64.deb
	https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.2.0.53/11.3_04222021/Ubuntu20_04-x64/libcudnn8-dev_8.2.0.53-1+cuda11.3_amd64.deb
	https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.2.0.53/11.3_04222021/Ubuntu20_04-x64/libcudnn8-samples_8.2.0.53-1+cuda11.3_amd64.deb

3. Install the packages:
	sudo dpkg -i libcudnn8_8.2.0.53-1+cuda11.3_amd64.deb
	sudo dpkg -i libcudnn8-dev_8.2.0.53-1+cuda11.3_amd64.deb
	sudo dpkg -i libcudnn8-samples_8.2.0.53-1+cuda11.3_amd64.deb

4. Install Darknet
	git clone https://github.com/AlexeyAB/darknet.git

5. Change the values of GPU, CUDNN and OPENCV to 1. 
	cd darknet
	gedit Makefile
	
6. Scroll down and comment the default ARCH values and uncomment the ARCH values that match your GPU config
If you don't know you can try running the python code
	python3 architecture_check.py 

7. Copy contents of “backup”, “cfg”, and “data” folders from Drive to the darknet “backup”, “cfg”, and “data” folders respectively
	
8. Run the python code for video inferencing (example):
	python3 darknet_video.py --input "sampleVideo3.mp4" --weights backup/custom-yolov4-detector_best.weights --config_file cfg/custom-yolov4-detector.cfg  --data_file data/obj.data --thresh .9


	


