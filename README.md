# Homework 5 - Machine Learning

This repository contains how Group59 solved the hw5 problem with retraining MobileNet V1.

Operating system and software:
The operating system used in this homework was the MacOS Mojave v.10.14 and the Python v.3.7


## 0. Initialization

## 1. Retrain a model using a pre-trained MobileNet V1

To retrain model we used the retrain.py program.

### The parameters:

Image size = input layers
Architecture = the version + input layers
How many learning steps = Epochs
Learning rate

Code below uses architecture mobilenetv1 version 1.0 with 224 input layers on the web, epochs = 3000 and learning rate = 0.001

```sh
# Set environment variables

IMAGE_SIZE=224
ARCHITECTURE=mobilenet_1.0_$IMAGE_SIZE

# Start training

python -m scripts.retrain \
  --image_dir=tf_files/dataset \
  --model_dir=tf_files/models \
  --architecture=$ARCHITECTURE \
  --output_graph=retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --bottleneck_dir=tf_files/bottlenecks \
  --summaries_dir=tf_files/training_summaries/$ARCHITECTURE \
  --how_many_training_steps=3000 \
  --learning_rate=0.001
```

## 3. Evaluating the results

There are alreaydy program evaluate.py We needed to changes few parts of the program before getting it to work on our problem.
Then just running the program.
```sh
python evaluate.py retrained_graph.pb
```
For example this code the results looks like:

Accuracy: 0.968023
Cross Entropy: 0.17778


## 4. Optimizing the web

When optimizing the net we used the different parameters and collecting the results.

