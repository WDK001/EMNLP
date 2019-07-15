## Response to Review #3:

**Question:** The method seems sensitive to the hyperparameters such as the number of iterations and the percentage of filters kept. Did you find that performance changed significantly between different datasets?

**Answer:** The iterations and percentage of filters kept do not differ much for different datasets used in the experiment. Generally, the best number of iterations is 2 or 3. The selection of filters is based on a sequential search algorithm and validation loss. If the difference between the maximum validation loss and minimum validation loss in 5 consecutive selection steps is smaller than a preset value (0.01 is used in the experiment), we will stop the filter selection procedure. We observed the percentage of filters kept ranges from 0.85 to 0.9. The experiment results show that our proposed model could remove task-irrelevant words efficiently and is effective on all datasets, but the improvements are related to the dataset noise and sample number per class. Our proposed model could achieve more significant improvement on noisier datasets, such as Yelp Full Review dataset. The noise here means words irrelevant to the specific task, usually, long texts contain more irrelevant words to the specific classification task.
 
##In addition, the improvement achieved by our proposed model is more significant for datasets having fewer samples per class, such as Yahoo dataset. This is because the network is easier to capture (fit to) the noise if the sample size per class is smaller. We will discuss this with more details in the final submission.

**Question:** Table 2: Did you train the baseline methods yourself or did you use the accuracies reported by the original papers?

**Answer:** For some models including classical CNN, attention-pooling CNN and RCNN, no results on the datasets used in the paper are reported in the literature, so we run the training by ourselves. The results of Character-based CNN and Deep CNN (29 layer) were directed cited from the respective paper.

**Question:** Section 4: Experimental setup: How did you decide which window sizes to use?

**Answer:** The convolutional filter window size usually corresponds to the phrase length. Most meaningful phrases are usually composed of 1, 2 or 3 words. Window sizes of 1, 2 and 3 are commonly used in convolutional neural network, and are therefore adopted in our paper.

**Question:** Section 4.1: Does your pruning technique help if you use it in conjunction with the other CNN architectures in Table 2?

**Answer:** The main idea of the paper is to improve model generalization capacity by pruning training data. We prove this idea by applying it to the basic CNN with one convolution layer. How to extend the training data pruning idea to other type of neural network and deep CNN is under exploration.

**Question:** How many free parameters are there for each of the network architectures in Table 2?

**Answer:** The parameter size of our model is 153.22k. Since it is the simplest architecture within the models in Table 2, it has the least parameter size. Will give details of parameter size in the final submission.

**Question:** How long does the filtering procedure take? How does it scale with the amount of data?

**Answer:** The filter selection is based on sequential forward search and validation loss. Thus a large number of classifiers for different filter combinations are trained. It takes 5 hours to evaluate the different combinations of 192 convolutional filters on a single graphic card GTX1080 and CPU Intel(R) Xeon(R) CPU E5-1650. The filter number is the major factor to influence the number of classifiers to be trained and hence the procedure time. The influence of amount of data is much less.

**Question:** I don't understand the Figure 6. What is the "convolution value"?

**Answer:** Sorry for the unclear description. It actually refers to the output of max-pooling layer. We will change this in the final version.  
