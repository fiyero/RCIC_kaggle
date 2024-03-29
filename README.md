# Kaggle Recursion Cellular Image Classification
## This repo serves as the developing log of my submission to Kaggle Recursion Cellular Image Classification
https://www.kaggle.com/c/recursion-cellular-image-classification

### My goal:
- Finalize the final submission ~~within 10 days~~ (failed)
- aim to get into top ~~17% or above~~ (not enough time and effort, better aim top 30%)

## Result:
- ![p1](https://github.com/fiyero/RCIC_kaggle/blob/master/RCIC_rank.JPG)<br/>
- solo 128th out of 866 teams, within top 15%

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

## Day 10 17th Sep 2019
- model v5 resnetxt
- rewrite dataloader, make use of the official rxrx repo to merge 6-channel image into RGB
- use albumentations for faster augmentation
- img size 512, lr =0.001, batch_size=12
- more than 90mins for one epoch

## Day 11 18th Sep 2019
- model v6 efficientNet B5
- still keep experimenting single best model, now trying efficientNet in Pytorch
- freeze the extraction layers and train classifier only for 2 warm up epochs then continue the training to see if have improvement
- batch_size=4, accumulate batch update into batch_size=16, lr=0.001

## Day 12 19th Sep 2019
- it takes around 2hr 20mins to train for one epoch for model v6
- time is running short so use progressive training for model v7 and add weight decay to optimizer
- Still trying to understand arcface, cosface, focal loss..etc guess will just apply vanila loss function for simplicity
- wont hv decent result but main purpose is for learning

## Day 16 23th Sep 2019
- just occassionally experiment different techniques for the past few days
- v9.4 has reached around the top 20% of the public LB
- the greatest limitation for my model is img size as can be seen from the discussion forum all outstanding models are using at least img size=512, while I am only using img size=224
- The time it takes for me to train one epoch with 512 pixel img is more than 2 hrs, i cant afford the time.
- the current v9.4 model has been trained for around 5x epochs, each costs around 28mins only.
- To score better result, I have to train with img size=512, re-write loss function such as arcface, cosface or even 
combine them all and with heavier augmentation which will take me a lot of time to train and to learn.
- Have to compromise with the resources and reality

## Day 18 25th Sep 2019
- v10.7 figured out how to utlize some part of the control_csv
- but is a bit too late as the completition will end soon, looking forward to see the solution by top performers
- seem my model is not overfit yet, hope can rush into top 15% at the private LB

## Day 20 27th Sep 2019
- The completition is over, I rank 128th, out of 866 teams, within the top 15%.
- ![p1](https://github.com/fiyero/RCIC_kaggle/blob/master/RCIC_rank.JPG)<br/>
- I am satisfied with the result as my original goal was just getting into top 17%(later change to top 30%)
- I failed to wake up at the morning to submit my last training model before the deadline, otherwise my ranking maybe 3-5th higher, but it doesnt't matter as won't change the big picture.
- Still have a lot to learn and a long way to go, now is time to learn from the top performers and aim at better ranking for the next competition

## TBC
- how to use train_control csv?
- CosFace loss function?
- ~~227 plates leak info?~~
