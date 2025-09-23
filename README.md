## Author:
Anastasiia Britan

## Description of the project

We tried to re-create an automatic bird feeder from the article (https://habr.com/ru/articles/322520/) by Maltsev Anton, using Raspberry Pi.

## Construction of the instrument

As a base for this project we used a plastic box for laundry (60x50x40 cm) as a base for bird feeder. At the top wall we decided to put a Raspberry Pi camera, covered in plastic coating for making it waterproof. We decided that Raspberry shouldn't be put outside, because the weather might be too harsh for the computer, so there is no waterproof coating for this component.


## Process of making the feeder


#Python enviroment
A bird-env environment was created and the following were installed:
pip install opencv-python python-telegram-bot numpy
In Makefile.config for Caffe, the paths to bird-env were specified.

#Caffe installation

> sudo apt install build - essential cmake git libatlas - base - dev libboost
- all - dev \
libgflags - dev libgoogle - glog - dev libhdf5 - dev libprotobuf - dev \
libleveldb - dev liblmdb - dev libopencv - dev libsnappy - dev protobuf -
compiler \
python3 - dev python3 - numpy python3 - pip python3 - protobuf libopenblas -
dev

Caffe was downloaded and configured

> git clone https :// github . com / BVLC / caffe . git
> cd caffe
cp Makefile . config . example Makefile . config
# Edycja cieek do bird - env
make all - j2
make pycaffe









![design overview](IMG_2967.jpeg) 
![design overview](IMG_2968.jpeg) 
![design overview](IMG_2969.jpeg) 



## How it works?



## Results

The instrument works properly, but the sounds are horrible. I do not think that we can consider that as a music...


## Sourses:
- [Wiki.amperka.ru] (https://wiki.amperka.ru/%D0%BA%D0%BE%D0%BD%D1%81%D0%BF%
