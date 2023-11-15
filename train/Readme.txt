Already trained model weights can be found in 'weights' folder.


For custom training:
1. Upload 'weed_detection' folder to your google drive.
2. Upload Jupyter notebook to google colab and run all cells
3. After training, weights will be stored in 'training' folder in 'weed_detection'
4. mAP, F1 score and some test predictions are available in cell outputs.

Note: Be careful with naming conventions and configuration when training custom dataset in own folder.
      If training own dataset, change class number and names in obj.data and obj.names respectively. 
      Also, update .cfg file with class number and change input image size and filters (in layers just before yolo layers) according to forumla filters = (5+num_classes)*3.
	