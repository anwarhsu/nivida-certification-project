# YOLO Object detection For nivida jetson 
I am using the famous YOLO object detection that uses neural networks. The YOLO object detection is famous for training using the COCO dataset which consist of lots of daily objects. 

# basic prerequisites
## Jetson configuration
Please install Conda and make sure you have the right version. Jetson nano  
https://github.com/Archiconda/build-tools/releases/tag/0.2.3

## Extra Downloads
I am using the tiny object model. This allows faster computation for movements like tracking a person running. 
https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v4_pre/yolov4-tiny.weights

# Personal steps 

Clone this repo on your jetson
````
git clone https://github.com/theAIGuysCode/yolov4-deepsort
```` 
Set conda or virtual environment 
```` 
conda env create -f conda-cpu.yml
conda activate yolov4-cpu
```` 

Save Yolo-tiny model

```` 
python save_model.py --weights ./data/yolov4-tiny.weights --output ./checkpoints/yolov4-tiny-416 --model yolov4 --tiny

```` 

Run the Model using webcam \
Note: Model is saved in output path. If you want to test video files change the 0 to the path of the mp4 video. 
```` 
python object_tracker.py --weights ./checkpoints/yolov4-tiny-416 --model yolov4 --video 0 --output ./outputs/tiny.avi --tiny
```` 

# Reflection and Improvment
This was my take on using the jetson device. I attempted to track movement of me playing basketball, with a car background. This issue I faced was the camera quality was 1080p so theres too much data and thus the fps drop. Also the basketball movement seemed to fast for the model to handle and thus didn't detect this. For improvement on making this more robust I need to experiment on changing the resolution of each images. I plan on doing more like ML/AI like facial detection however this was a intro on just getting to know embedded linux.


# Youtube Link 
https://www.youtube.com/watch?v=cyRFi8QzfD4

