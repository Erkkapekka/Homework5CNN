# Homework 5 - Machine Learning

This repository contains Group59 solution to the Homework5. The solution is based on retraining the MobilenetV1.

References: 

Retrain MobileNet for the web: (https://github.com/woudsma/retrain-mobilenet-for-the-web)


Operating system and software:

MacOS Mojave version 10.14

Python version 3.7


## 0. Initialization

In this exersice we used the Kaggle Fruits-360 dataset. The dataset was alreaydy split to Test and Training set. The training set is in the folder dataset and the test set in folder Test. We erased the specific fruits from the sets that we were not suppose to used.

The folders contains alreaydy the model, bottleneck files, the label file and the graph file. Delete those files before retraining.

## 1. Retrain a model using a pre-trained MobileNet V1

We retrained the pre-trained MobileNet V1 with new data and different input and output layers. To retrain the model we used the retrain.py program.

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

We used the evaluate.py program to evaluate the results. We used the test set of kaggle Fruits-360 dataset to obtain the test results.

```sh
python evaluate.py retrained_graph.pb
```
For this net, the test results looks like this:

```sh
Accuracy: 0.968023
Cross Entropy: 0.17778
```

Using label_image.py is the option to recognize only one picture at the time.

```sh
IMAGE_SIZE=224

python label_image.py \
  --graph=retrained_graph.pb \
  --input_width=$IMAGE_SIZE \
  --input_height=$IMAGE_SIZE \
  --image=tf_files/dataset/Lemon/0_100.jpg

# Top result should be Lemon

```

## 4. Optimizing the web

When optimizing the net we used the different parameters and collected the results.

We changed the size of the input layer, the architecture of the web, number of epochs and learning rate.






