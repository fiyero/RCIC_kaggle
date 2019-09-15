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
- Ran 5 hours for 4 epochs, obtained the following result and decided to early stop it <br/>
- ![v1](https://github.com/fiyero/RCIC_kaggle/blob/master/1st_run.JPG)<br/>
- Adjust lr into 0.0001 and accumulate gradient update into batch_size=30
- rewrite and fix the mean_val_loss

## Day 4 11th Sep 2019
- Pioneer submission of the public score is so bad, thinking whether the poor result is due to imbalance data/sub-optimal training(only 4 epochs) / inappropriate loss function nor poor model archiecture
- Try with resnetxt 50 model with lr= 0.001, accumulate gradient batch_size=60, Customized classifier
- edit callbacks schedule, save checkpt after every epoch and the best checkpt every 500 steps
- spot typo and fix the train, valid dataset split
- if similar situation occur should go back to deal with the data set

## Day 5 12th Sep 2019
- model v2 resnetxt 50 took almost 2 hours to train for one epoch with 1080ti, which is impractical for me to continue. From the Kaggle discussion generally people have to train 2x-4x epochs to reach optimal. 
- I switch back to densenet121 for model v3, reduce half of input size, only do validation per epoch to cut down the training time for testing
- if still take 1 hr + for one epoch I will largely simplify the classifer 
- anyways I look at the inference result I think I should edit the dataset preprocessing way 

## Day 8 15th Sep 2019
- didnt update for a few days because busy at researching data sciecne master related info
- found that simplifying the classifier actually give better result and now one epoch run for around 35mins
- pretty sure cannot finalize the training model within 10 days

## TBC
- Find the proper way for augmentation in 6 channel image
- how to use train_control csv?
- rewrite the pipeline for creating dataset
- 
