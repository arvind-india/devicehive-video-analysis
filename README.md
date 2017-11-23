[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square)](LICENSE)

# Video analysis demo

## Requirements

### Python
* python 3
* openCV with video support ([Instruction](https://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html))
* tensorflow ([Instruction](https://www.tensorflow.org/install/install_linux))
* [devicehive-python-webconfig](https://github.com/devicehive/devicehive-python-webconfig) (for daemon.py)

### Models data
* download and extract [data.tar.gz](https://s3.amazonaws.com/video-analysis-demo/data.tar.gz) to source folder

## Running

### Local demo
To evaluate video file run
```bash
python eval.py --video=/path_to_video_file/
```
If _--video_ is not provided video device "0" (usually it's web cam) will be used by default.

Press _q_ to close program.\
Press _s_ to save currents frame to file.

Run 
```bash
python eval.py --help
``` 
for more info about available arguments.

Currently there are two supported models:
* Yolo9kModel - YOLO model trained to recognize more than 9000 classes.
* Yolo2Model - YOLO-coco model with 80 classes and pretty good accuracy.

Yolo2Model is used by default but this behavior can be changed by passing _--model_name_ argument.


### Web based demo
There is demo with web interface and devicehive integration.
It will capture video stream from your web cam, evaluate it and send predictions to devicehive.
To use it run
```bash
python daemon.py
```
and go to http://127.0.0.1:8000 to configure devicehive connection.
Video stream is available on http://127.0.0.1:8000/events/
