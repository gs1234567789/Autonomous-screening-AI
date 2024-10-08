<h1>Autonomous screening AI</h1>
  
The model aims to create atool that can be used to autonmously sort apples and tomatoes on a factory line
<h1>The Algorithm</h1>

The model is trained on the "jatson nano" application of tomato and potato photo collections
<h1>Running this project</h1>
The following are the required file packages
[app_tom.zip](https://github.com/user-attachments/files/16552439/app_tom.zip)
You need to download it to :"jetson-inference/python/training/classification/data"

back in the jetson-inference
run
```
./docker/run.sh
```
cd to jetson-inference/python/training/classification
run
```
python3 train.py --model-dir=models/app_tom data/app_tom
```
While it's running, you can stop it at any time using Ctl+C.

Make sure you are in the docker container and in jetson-inference/python/training/classification

Run the onnx export script.
```
python3 onnx_export.py --model-dir=models/app_tom
```
Exit the docker container by pressing Ctl + D.



On your nano, navigate to the jetson-inference/python/training/classification directory.
Set the NET and DATASET variables
```
NET=models/app_tom
DATASET=data/app_tom
```


Run this command to see how it operates on an image from the cat folder.
```
imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/apples/img_p1_14.jpeg output1.jpeg
imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/tomatoes/img_p1_24.jpeg output2.jpeg
imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/apples/img_p1_7.jpeg output3.jpeg
```
Below is a demonstration image
![text1](https://github.com/user-attachments/assets/715f6ee9-3e91-4588-a1c6-cb3c5cbf10fd)
![text2](https://github.com/user-attachments/assets/8a2a8bd8-88b6-411e-8af8-2a0100f8ff7d)
![text3](https://github.com/user-attachments/assets/7b0e01d0-ffc8-4bc7-a062-cd3d92f48280)

Show video link:https://youtu.be/ebs3eiam0T0
