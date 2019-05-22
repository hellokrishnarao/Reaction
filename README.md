# Understanding Pedestrian Behavior to Improve Autonomous Driving Cars 
A major dilemma faced by autonomous cars is understanding the intention of other road users and communicating with them.
To investigate one aspect of this, specifically pedestrian crossing behavior, we shall analyze a large dataset of pedestrian samples at crosswalks under various conditions (e.g., weather, time of the day) and in different types of roads.
Using the data, we shall analyze pedestrian behavior from two different perspectives: the way they communicate with drivers prior to crossing and the factors that influence their behavior.
It is observed that a change in head orientation in the form of looking or glancing at the traffic is a strong indicator of crossing intention.


Our project aims to aid the interaction between the autonomous vehicles and the pedestrians. Overall, our work formulates the problem of pedestrian-driver interaction and sheds light on its complexity in typical traffic scenarios.

### Prerequisites

 8GB of computer RAM alongside a minimum amount (128GB) of secondary storage space
 Operating system- Windows 7 or above, Linux(4.2.x) or above
 Python 2
 OpenCV 
 TensorFlow

##### Python 2 Installation

```
sudo apt-get update
```
```
sudo apt-get install python2.7
```
##### OpenCV Installation (After Successful installation of Python 2.7)

```
sudo apt-get update
```
```
pip install opencv-python
```
##### Tensorflow Installation

```
pip install tensorflow-gpu
```


### Getting Started
To run the file, go to the project directory in the terminal

```
python Pedestrian.py
```
## Variables
 
Variable  | Description
------------- | -------------
maximum_speed | It is the maximum speed the vehicle can attain
minsize  | Mininum size of the face
threshold | Three steps's threshold
factor | Scale Factor
boxes | Open CV frame for Face detection
result | Detected facial features 
acc_factor | Acceleration Factor
dec_factor | Deceleration Factor
video_cature | Source of the video

## Pre-processing

### Face alignment using MTCNN
One problem with the above approach seems to be that the Dlib face detector misses some of the hard examples (partial occlusion, silhouettes, etc). This makes the training set too "easy" which causes the model to perform worse on other benchmarks.
To solve this, other face landmark detectors has been tested. One face landmark detector that has proven to work very well in this setting is the
[Multi-task CNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html). A Matlab/Caffe implementation can be found [here](https://github.com/kpzhang93/MTCNN_face_detection_alignment) and this has been used for face alignment with very good results. A Python/Tensorflow implementation of MTCNN can be found [here](https://github.com/davidsandberg/facenet/tree/master/src/align). This implementation does not give identical results to the Matlab/Caffe implementation but the performance is very similar.

## Running training
Currently, the best results are achieved by training the model using softmax loss. Details on how to train a model using softmax loss on the CASIA-WebFace dataset can be found on the page [Classifier training of Inception-ResNet-v1](https://github.com/davidsandberg/facenet/wiki/Classifier-training-of-inception-resnet-v1) and .

## Pre-trained models
### Inception-ResNet-v1 model
A couple of pretrained models are provided. They are trained using softmax loss with the Inception-Resnet-v1 model. The datasets has been aligned using [MTCNN](https://github.com/davidsandberg/facenet/tree/master/src/align).

## Performance
The accuracy on LFW for the model [20180402-114759](https://drive.google.com/open?id=1EXPBSXwTaqrSC0OhUdXNmKSh9qJUQ55-) is 0.99650+-0.00252. A description of how to run the test can be found on the page [Validate on LFW](https://github.com/davidsandberg/facenet/wiki/Validate-on-lfw). Note that the input images to the model need to be standardized using fixed image standardization (use the option `--use_fixed_image_standardization` when running e.g. `validate_on_lfw.py`).

## Running the tests

### Test 1 
A sample test with a video captured from a camera on the vehicle on a daylight
change the value of the variable in Pedestrain.py: video_capture
```
video_capture = './test1.mp4'

```

###  Test 2
Another sample test with a video captured from a camera on the vehicle on a cloudy/dark day.
change the value of the variable in Pedestrain.py: video_capture
```
video_capture = './test2.mp4'

```



## Built With

* [OpenCV](https://opencv.org/) - Open CV by Big Vision LLC.
* [TensorFlow](https://maven.apache.org/) - Tensorflow by Google Inc.
* [Python2](https://www.python.org/downloads/release/python-27/) - Python2.7 by Python Foundation Inc.

## Authors

* **Pratibha Agarwal**
* **Srikrishna C.N**
* **Malvika Diwan**
## License

This project is licensed under the MIT License - see the [LICENSE.md](https://opensource.org/licenses/MIT) file for details

## Acknowledgments

* [Prof. M.S Anand](https://pesitsouth.pes.edu/faculty/prof-m-s-anand/)
