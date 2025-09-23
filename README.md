## Author:
Anastasiia Britan

## Description of the project

We tried to re-create an automatic bird feeder from the article (https://habr.com/ru/articles/322520/) by Maltsev Anton, using Raspberry Pi.

## Construction of the instrument

As a base for this project we used a plastic box for laundry (60x50x40 cm) as a base for bird feeder. At the top wall we decided to put a Raspberry Pi camera, covered in plastic coating for making it waterproof. We decided that Raspberry shouldn't be put outside, because the weather might be too harsh for the computer, so there is no waterproof coating for this component.


## Process of making the feeder


### Python enviroment
A bird-env environment was created and the following were installed:

> pip install opencv-python python-telegram-bot numpy
> In Makefile.config for Caffe, the paths to bird-env were specified.

### Caffe installation

> sudo apt install build - essential cmake git libatlas - base - dev libboost
> - all - dev \
> libgflags - dev libgoogle - glog - dev libhdf5 - dev libprotobuf - dev \
> libleveldb - dev liblmdb - dev libopencv - dev libsnappy - dev protobuf -
> compiler \
> python3 - dev python3 - numpy python3 - pip python3 - protobuf libopenblas -
> dev

Caffe was downloaded and configured

> git clone https :// github . com / BVLC / caffe . git
> cd caffe
> cp Makefile . config . example Makefile . config
> Edycja cieek do bird - env
> make all - j2
> make pycaffe

### Installation and modification of SqueezeNet
> cd ~/ caffe / models
> git clone https :// github . com / DeepScale / SqueezeNet . git
> cd SqueezeNet / S q u e e z e N e t _ v 1 .1
> wget https :// github . com / DeepScale / SqueezeNet / raw / master / S q u e e z e N e t _ v 1
> .1/ s q u e e z e n e t _ v 1 .1. caffemodel

### Modification of the output layer

The final layers in deploy.prototxt were changed to:

layer {
name : " conv10 "
type : " Convolution "
bottom : " fire9 / concat "
top : " conv10 "
c o n v o l u t i o n _ p a r a m {
num_output : 3
kernel_size : 1
stride : 1
w e i g h t _ f i l l e r {
type : " gaussian "
mean : 0.0
std : 0.01
}
bias_filler {
type : " constant "
value : 0
}
}
}
layer {
name : " relu_conv10 "
type : " ReLU "
bottom : " conv10 "
top : " conv10 "
}
layer {
name : " pool10 "
type : " Pooling "

bottom : " conv10 "
top : " pool10 "
p o o l i n g _ p a r a m {
pool : AVE
g l o b a l _ p o o l i n g : true
}
}
layer {
name : " prob "
type : " Softmax "
bottom : " pool10 "
top : " prob "
}

### 3D modeling of the coating





## Results

The instrument works properly, but the sounds are horrible. I do not think that we can consider that as a music...

![design overview](IMG_2967.jpeg) 
![design overview](IMG_2968.jpeg) 
![design overview](IMG_2969.jpeg) 

## Sourses:
- [Wiki.amperka.ru] (https://wiki.amperka.ru/%D0%BA%D0%BE%D0%BD%D1%81%D0%BF%
