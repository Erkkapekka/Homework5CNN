# Homework 5 - Machine Learning

This repository contains how Group59 solved the hw5 problem with retraining MobileNet V1.

Operating system and softwares:
The operating system used in this homework was the MacOS Mojave v.10.14 and the Python v.3.7


## 0. Initialization

## 1. Retrain a model using a pre-trained [MobileNet V1]

### Set environment variables

IMAGE_SIZE=128
ARCHITECTURE=mobilenet_0.25_$IMAGE_SIZE

#### Start training

python -m scripts.retrain \
  --image_dir=tf_files/dataset \
  --model_dir=tf_files/models \
  --architecture=$ARCHITECTURE \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --bottleneck_dir=tf_files/bottlenecks \
  --summaries_dir=tf_files/training_summaries/$ARCHITECTURE \
  --how_many_training_steps=400 \
  --learning_rate=0.001


## 3. Optimize for the web



## 4. Evaluating the results
