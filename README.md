# car-detector-tensorflow
Detect the primary car in images with TensorFlow using RCNN + Inception-ResNet-V2

Primary car is the subject of the image. Detecting and cropping out the primary car act as a preprocessing step for further computer vision tasks on the car such as [detecting damage](https://github.com/politecat314/car-damage-detection-peltarion).
<br><br><img src="https://github.com/politecat314/car-detector-tensorflow/blob/master/demo.png" width="600"><br>

List of objects considered as cars here are: 'Car','Bus','Van' and 'Truck'. To edit/customize this, edit the `selectCars` function in `RCNN Inception_Resnet_V2.ipynb`. Add or remove items fromm the list `cars`.

## How it works?
Object detection is done by RCNN + Inception-ResNet-V2. To change this to a different model such as SSD + MobileNet V2, follow the instructions [here](https://www.tensorflow.org/hub/tutorials/object_detection).
Object detection is first done for all objects. A maximum of the 100 highest confident objects are chosen. From this, cars are filtered out (>0.1 confidence is accpeted for cars). Car with the largest area is chosen as the primary car and the bounding box is drawn around it.

### Warnings 
* If the confidence level for car is <0.9, a warning is shown.
* If no car is found, all returned values for `run_detector` function are -1 and a warning is shown.


## How to use?
Create a folder `test_images` in the root dir. Place your image(s) there. Open `RCNN Inception_Resnet_V2.ipynb` and run.

## Requirements
* TensorFlow >= 2.6.0
* TensorFlow Hub >= 0.12.0
* Pillow >= 8.3.2
* LiberationSansNarrow-Regular.ttf (optional)
