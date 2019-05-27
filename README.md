# Homework 5 - Machine Learning

This repository contains Group59 model to the Homework5. The solution is based on retraining the MobilenetV1.

#### System
MacOS Mojave version 10.14

Python version 3.7

## 0. Initialization

In this exersice we used the Kaggle Fruits-360 dataset. The dataset is alreaydy splitted to test set and training set. The training set is in the folder named dataset and the test set is in the folder named Test. The specific fruits that was not included in this exercise were erased.

Kaggle Fruits-360 dataset: (https://www.kaggle.com/moltean/fruits)

The programs used to retrain and evaluate the MobilenetV1 can be upload from:

TensorFlow for poets 2: (https://github.com/googlecodelabs/tensorflow-for-poets-2)

The tf-files folder contains alreaydy the model, bottleneck files, the label file and the graph file. Delete those files before retraining.

## 1. Retrain a model using a pre-trained MobileNet V1

We retrained the pre-trained MobileNet V1 with new data and different input and output layers. To retrain the model we used the retrain.py program.

### The parameters:

Input layers = image size

Architecture = the version + input layers

How many learning steps = Epochs

Learning rate

Code below uses mobilenetv1 version 1.0 architecture (224 input layers), epochs = 3000 and learning rate = 0.001

```sh
input_layers=224
at=mobilenet_1.0_$input_layers

python -m scripts.retrain \
  --image_dir=tf_files/dataset \
  --model_dir=tf_files/models \
  --architecture=$at \
  --output_graph=retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --bottleneck_dir=tf_files/bottlenecks \
  --summaries_dir=tf_files/training_summaries/$at \
  --how_many_training_steps=3000 \
  --learning_rate=0.001
```

## 2. Evaluating the results

We used the evaluate.py program to evaluate the results (Input and output layers must be modified to the program). The test set was used to obtain the test results.

```sh
python evaluate.py retrained_graph.pb
```
For this net, the test results looks like this:

```sh
Accuracy: 0.968023
Cross Entropy: 0.17778
```

## 3. Optimizing the web

When optimizing the net we used the different parameters and collected the results.

We changed the size of the input layer, the architecture of the web, number of epochs and learning rate.

## References

Retrain MobileNet for the web: (https://github.com/woudsma/retrain-mobilenet-for-the-web)

TensorFlow for poets 2: (https://github.com/googlecodelabs/tensorflow-for-poets-2)




