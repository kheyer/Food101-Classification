# Food101-Classification
This repo contains notebooks training a classification model on the Food-101 dataset. Food-101 is a dataset consisting of 101 classes with 1000 images 
per class. For each class, 250 images are reserved as for the test set. The dataset is difficult for a number of reasons. There's a small amount of 
training data for each class. Many classes look similar to each other (ex steak vs filet mignon). Many images in the dataset have poor lighting 
or framing. Several images contain multiple correct classes (ex burgers + fries), despite the dataset being structured as a single class 
classification problem. On top of all that there are a number of mislabeled images.

To deal with this, a number of augmentation strategies are required. I found the best combination was to use traditional image augmentation 
with mixup augmentation. The best model scored 89.79% accuracy on the test set when predicting with 8 fold test time augmentation.

## Notebooks

__Part 1 Setup and Exploration__ investigates the dataset.

__Part 2 Model Training__ shows the training and prediction process for the top scoring model, including explanation of the augmentation and 
regularization strategies used.

## Experiments

In the process of developing the final classification model shown in the __Part 2__ notebook, I experimented with different combinations of 
augmentation and regularization. The notebooks for these experiments can be found in the [Experiments](https://github.com/kheyer/Food101-Classification/tree/master/Experiments) directory. 

This is a summary of the four experiments:

| Notebook 	| Image Augmentation 	| Mixup Augmentation 	| Label Smoothing 	| Top-1 Accuracy 	| TTA Top-1 Accuracy 	|
|:--------:	|:------------------:	|:------------------:	|:---------------:	|:--------------:	|:------------------:	|
|    EX1   	|          1         	|          0         	|        0        	|      88.53     	|        89.26       	|
|    EX2   	|          0         	|          1         	|        1        	|      88.32     	|        88.75       	|
|    EX3   	|          1         	|          1         	|        1        	|      __89.28__     	|        89.70       	|
|    EX4   	|          1         	|          1         	|        0        	|      89.09     	|        __89.79__       	|

(EX4, the model with the highest TTA accuracy, is the model shown in the __Part 2__ notebook)
