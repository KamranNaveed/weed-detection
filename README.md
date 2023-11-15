# Project Name README

## Step 1:

- If custom training model, follow instructions in 'training' folder.
- If deploying pretrained model, obtain weight file from `train/weed_detection/training`.

## Step 2:

### Inference on Darknet on Jetson Nano:

1. Navigate to the darknet folder in the terminal.
2. Type the following commands:
    ```bash
    make
    ./darknet detector demo cfg/obj.data cfg/yolov4-tiny-custom.cfg yolov4-tiny-custom_best.weights -c 0
    ```
   - Notes:
      - Remember to check that locations of files are accurate.
      - Can also take image and video inputs as the last argument.

### Inference on Darknet on TensorRT on Jetson Nano:

1. Copy weights and configurations file to `tensorrt/yolo`.
2. (Important) Change the name of both files to 'yolov4-tiny-416'.
3. Type the following commands in the terminal:
    ```bash
    cd ${HOME}/project/tensorrt_demos/ssd
    ./install_pycuda.sh
    cd ${HOME}/project/tensorrt_demos/plugins
    make
    cd ${HOME}/project/tensorrt_demos/yolo
    python3 yolo_to_onnx.py -m yolov4-416
    python3 onnx_to_tensorrt.py -m yolov4-416
    cd ${HOME}/project/tensorrt_demos
    python3 trt_yolo.py --usb 0 -m yolov4-416
    ```
   - Notes:
      - To run inference on videos or images, will need to change `trt_yolo_cv.py`.
      - Change `cv2.VideoCapture` argument.
