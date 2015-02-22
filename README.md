# Machine-Learning-Assignment

title: "PML_assignment"
author: "Jyothsna Kasu"
date: "February 22, 2015"
output: html_document

library("caret")
Loading required package: lattice
Loading required package: ggplot2
Warning message:
package 'caret' was built under R version 3.1.2
library(randomForest)
randomForest 4.6-10
Type rfNews() to see new features/changes/bug fixes.
Warning message:
package 'randomForest' was built under R version 3.1.1 
> getwd()
[1] "/Users/pkasu"
> setwd("/Users/pkasu/PML")]
> traindataread <- read.csv(file = "pml-training.csv", na.strings=c("", "NA", "NULL"))
> testdataread <- read.csv(file = "pml-testing.csv", na.strings=c("", "NA", "NULL"))
> traindataread_subset <- data.frame(traindataread[,8:11], traindataread[,37:49], traindataread[,60:68], traindataread[,84:86], total_accel_dumbbell=traindataread[,102], traindataread[,113:124], traindataread[,151:160])
> inTrain <- createDataPartition(y=traindataread_subset$classe, p=0.7, list=FALSE)
> traindata <- traindataread_subset[inTrain,]
> traindata <- na.omit(traindata)
> testdata <- data.frame(testdataread[,8:11], testdataread[,37:49], testdataread[,60:68], testdataread[,84:86], total_accel_dumbb
> testdata <- data.frame(testdataread[,8:11], testdataread[,37:49], testdataread[,60:68], testdataread[,84:86], total_accel_dumbbell=testdataread[,102], testdataread[,113:124], testdataread[,151:160])
> modelFit <- randomForest(classe ~., data=traindata, do.trace=10)
ntree      OOB      1      2      3      4      5
   10:   4.88%  2.63%  6.85%  6.14%  6.03%  4.05%
   20:   1.92%  0.72%  2.97%  2.34%  2.71%  1.58%
   30:   1.14%  0.31%  1.77%  1.46%  2.09%  0.63%
   40:   0.89%  0.18%  1.20%  1.34%  1.73%  0.48%
   50:   0.71%  0.08%  0.98%  1.09%  1.55%  0.32%
   60:   0.72%  0.10%  1.09%  1.04%  1.55%  0.24%
   70:   0.71%  0.10%  1.02%  0.92%  1.64%  0.28%
   80:   0.63%  0.10%  0.83%  0.88%  1.42%  0.32%
   90:   0.61%  0.10%  0.83%  0.83%  1.47%  0.20%
  100:   0.58%  0.08%  0.71%  0.79%  1.38%  0.28%
  110:   0.55%  0.08%  0.64%  0.88%  1.29%  0.20%
  120:   0.52%  0.08%  0.60%  0.71%  1.29%  0.24%
  130:   0.52%  0.08%  0.53%  0.88%  1.20%  0.24%
  140:   0.48%  0.08%  0.49%  0.79%  1.15%  0.20%
  150:   0.48%  0.08%  0.49%  0.83%  1.11%  0.20%
  160:   0.47%  0.08%  0.49%  0.83%  1.07%  0.20%
  170:   0.47%  0.10%  0.53%  0.71%  1.11%  0.20%
  180:   0.48%  0.08%  0.60%  0.71%  1.11%  0.20%
  190:   0.47%  0.08%  0.56%  0.71%  1.07%  0.24%
  200:   0.47%  0.08%  0.53%  0.75%  1.07%  0.24%
  210:   0.49%  0.08%  0.53%  0.79%  1.11%  0.24%
  220:   0.50%  0.08%  0.49%  0.88%  1.07%  0.28%
  230:   0.49%  0.08%  0.53%  0.83%  1.07%  0.24%
  240:   0.47%  0.08%  0.45%  0.79%  1.07%  0.28%
  250:   0.50%  0.08%  0.56%  0.88%  1.07%  0.24%
  260:   0.51%  0.08%  0.56%  0.88%  1.11%  0.24%
  270:   0.46%  0.05%  0.45%  0.83%  1.02%  0.24%
  280:   0.47%  0.08%  0.41%  0.83%  1.07%  0.28%
  290:   0.47%  0.05%  0.45%  0.83%  1.07%  0.24%
  300:   0.47%  0.05%  0.49%  0.79%  1.07%  0.24%
  310:   0.49%  0.05%  0.53%  0.79%  1.15%  0.24%
  320:   0.49%  0.08%  0.45%  0.83%  1.11%  0.28%
  330:   0.50%  0.08%  0.49%  0.83%  1.11%  0.28%
  340:   0.49%  0.08%  0.49%  0.83%  1.07%  0.28%
  350:   0.46%  0.05%  0.45%  0.79%  1.02%  0.28%
  360:   0.47%  0.05%  0.45%  0.75%  1.11%  0.28%
  370:   0.48%  0.05%  0.49%  0.79%  1.07%  0.32%
  380:   0.47%  0.05%  0.41%  0.83%  1.07%  0.32%
  390:   0.47%  0.05%  0.41%  0.83%  1.07%  0.32%
  400:   0.49%  0.05%  0.45%  0.83%  1.11%  0.32%
  410:   0.47%  0.05%  0.41%  0.79%  1.07%  0.32%
  420:   0.46%  0.05%  0.45%  0.79%  1.07%  0.24%
  430:   0.46%  0.05%  0.45%  0.79%  1.02%  0.28%
  440:   0.44%  0.05%  0.41%  0.79%  1.02%  0.24%
  450:   0.45%  0.05%  0.41%  0.75%  1.07%  0.28%
  460:   0.45%  0.05%  0.41%  0.79%  1.07%  0.24%
  470:   0.44%  0.05%  0.41%  0.79%  1.07%  0.20%
  480:   0.44%  0.05%  0.41%  0.79%  1.07%  0.20%
  490:   0.44%  0.05%  0.41%  0.79%  1.02%  0.24%
  500:   0.47%  0.05%  0.45%  0.83%  1.07%  0.28%
> modelFit

Call:
 randomForest(formula = classe ~ ., data = traindata, do.trace = 10) 
               Type of random forest: classification
                     Number of trees: 500
No. of variables tried at each split: 7

        OOB estimate of  error rate: 0.47%
Confusion matrix:
     A    B    C    D    E  class.error
A 3904    2    0    0    0 0.0005120328
B    9 2646    3    0    0 0.0045146727
C    0   14 2376    6    0 0.0083472454
D    0    0   20 2228    4 0.0106571936
E    0    0    1    6 2518 0.0027722772
> prediction <- predict(modelFit, testdata)
> prediction
 1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 
 B  A  B  A  A  E  D  B  A  A  B  C  B  A  E  E  A  B  B  B 
Levels: A B C D E
> pml_write_files = function(x){
+   n = length(x)
+   for(i in 1:n){
+     filename = paste0("problem_id_",i,".txt")
+     write.table(x[i],file=filename,quote=FALSE,row.names=FALSE,col.names=FALSE)
+   }
+ }
> answers = predictions
Error: object 'predictions' not found
> answers = prediction
> pml_write_files(answers)
> 
