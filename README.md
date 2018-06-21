# keras-yolo3-kitti

base on [keras-yolo3](https://github.com/qqwweee/keras-yolo3)

## Introduction

A Keras implementation of YOLOv3 worked on kitti dataset.

---

---

## Training
1. Generate your own annotation file and class names file.  
    One row for one image;  
    Row format: `image_file_path box1 box2 ... boxN`;  
    Box format: `x_min,y_min,x_max,y_max,class_id` (no space).  
    For VOC dataset, try `python voc_annotation.py`  
    Here is an example:
    ```
    path/to/img1.jpg 50,100,150,200,0 30,50,200,120,3
    path/to/img2.jpg 120,300,250,600,2
    ...
    ```
    There is a notebook jupyter  called kitti_train.ipynb
    The kitti dataset is [Kitti Object](http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=2d),I only use 3 classes.
    
2. Make sure you have run `python convert.py -w yolov3.cfg yolov3.weights model_data/yolo_weights.h5`  
    The file model_data/yolo_weights.h5 is used to load pretrained weights.

3. Modify train.py and start training.  
    `python train.py`  
    Use your trained weights or checkpoint weights in yolo.py.  
    Remember to modify class path or anchor path.

4 test the images
  ```python yolo.py -s test_images -d output_images```
  Label images in folder test_images into folder output_images

---

## Some issues to know
In convert.py I have some hard code for the pretrained model. You can also use the original code.
I write a blog in Chinese. Here is the address.
https://blog.csdn.net/yangchengtest/article/details/80732237