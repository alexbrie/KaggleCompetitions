# KaggleCompetitions
Repository of my work on various Kaggle competitions. Kinda private/messy/not useful.

## Competitions:

### protein
https://www.kaggle.com/c/human-protein-atlas-image-classification
Code here is mostly useless, but it helped me practice on bulk data preparation, which compacts 3 images into the separate rgb channels of a new one, plus resizes.
The approach didn't perform better than simply using a custom file data provider for fastai that builds the numpy array for the image's channels on the fly.
Particular challenges: disk space on the AWS machine used (default 64GB) was insufficient to hold both the dataset and the resulting compacted images, so I had to juggle things around.

### Humpback whale id
https://www.kaggle.com/c/humpback-whale-identification
Code here uses and/or merges various public kernels on Kaggle for this competition.  

New techniques learned:
1. use stratified sampling to make sure we don't miss entire classes in training
2. skip the 'unnamed' category (which was multiple orders of magnitude larger than the others, thus skewing the training) and add it at the end in predictions phase based on the probability threshold
3. smart image resizing
4. run a separate predictor in data preparation, to find the actual bounding boxes of the data we're interested in, and only pass the section of the image within the boundingbox to our predictor. This improved prediction by 1/5 (from < 50% to > 60%)
5. use proportional ensembling from the results - that is, a average from our previous predictions weighted by the kaggle public score; this improved public prediction with cca 5%
6. use larger/more complex nets; initial resnet30 was limited in prediction to 0.4, whereas resnet50 went to 0.6.


.. to be continued
