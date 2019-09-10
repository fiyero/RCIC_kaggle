# Kaggle Recursion Cellular Image Classification
## This repo serves as the developing log of my submission to Kaggle Recursion Cellular Image Classification
https://www.kaggle.com/c/recursion-cellular-image-classification

### My goal:
- Finalize the final submission within 10 days
- aim to get into top 17% or above

# Developing log
## Day 1 8th Sep 2019
- take a quick scan of the dataset, EDA

## Day 2 9th Sep 2019
- Build customize dataset class and dataloader to load the dataset
- Build prototype model with densenet-121 structure with Pytorch, just first 100 data with 10 epochs and ran successfully

## Day 3 10th Sep 2019
- Customized the classifier part of densne-121 with dropout and batchnorm
- Starting full run with whole complete training set with batch_size=6, lr=0.001, epoch=20, print and validate every 1200
- Ran 5 hours for 4 epochs, obtained the following result and decided to early stop it
- ![v1](https://github.com/fiyero/RCIC_kaggle/blob/master/1st_run.JPG)
- Adjust lr into 0.001 and accumulate gradient update into batch_size=30

## TBC
- Find the proper way for augmentation in 6 channel image
- Se resnet structure
