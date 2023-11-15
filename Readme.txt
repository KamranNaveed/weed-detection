Step 1:
    - If custom training model, folllow instructions in 'training' folder.
    - If deploying pretrained model, obtain weight file from train/weed_detection/training
Step 2:
    - To run inference on darknet on jetson nano:
	- Navigate to darknet folder in terminal
	- Type the following commands:
		- make
		- ./darknet detector demo cfg/obj.data cfg/yolov4-tiny-custom.cfg yolov4-tiny-custom_best.weights -c 0
		Notes: - Remember to check that locations of files are accurate.
		       - Can also take image and video inputs as last argument.

    - To run inference on darknet on TensorRT on jetson nano:
	- Copy weights and configurations file to tensorrt/yolo
	- (Important) Change name of both files to 'yolov4-tiny-416'
	- Type the following commands in terminal:
		- $ cd ${HOME}/project/tensorrt_demos/ssd
		- $ ./install_pycuda.sh
		- $ cd ${HOME}/project/tensorrt_demos/plugins
		- $ make
		- $ cd ${HOME}/project/tensorrt_demos/yolo
		- $ python3 yolo_to_onnx.py -m yolov4-416
		- $ python3 onnx_to_tensorrt.py -m yolov4-416
		- $ cd ${HOME}/project/tensorrt_demos
		- $ python3 trt_yolo.py --usb 0 -m yolov4-416
		Notes:  - To run inference on videos or images, will need to change trt_yolo_cv.py
			- Change cv2.VideoCapture argument
      