# StackOverflow-Tag-Predict
This project basically gives tags to the various questions of StackOverflow by taking into account the Title and Body of the question.
![SO](https://user-images.githubusercontent.com/51243187/88142213-bc5e5d80-cc12-11ea-93e8-4df454c11145.png)
## What is Stack Overflow?
Stack Overflow is the largest, most trusted online community for developers to learn, share their programming knowledge, and build their careers.
It is something which every programmer use one way or another. Each month, over 50 million developers come to Stack Overflow to learn, share their knowledge, and build their careers. It features questions and answers on a wide range of topics in computer programming. The website serves as a platform for users to ask and answer questions, and, through membership and active participation, to vote questions and answers up or down and edit questions and answers in a fashion similar to a wiki or Digg.
## 1. Overview
The problem says that we will be provided a bunch of questions. A question in Stack Overflow contains three segments Title, Description and Tags. By using the text in the title and description we should suggest the tags related to the subject of the question automatically. These tags are extremely important for the proper working of Stack Overflow.
## 2. Business Objectives and Constraints
So for this problem we should get high precision and high recall rates. For example, let’s assume that we have a title, description with 4 tags. If we want to predict any of the tags we should have a high precision value i.e, we have to be really sure that the predicted tag belongs to the given question. Also, we want to have a high Recal rate, which means If the tag actually supposed to be present, we want it to be present most number of times.
## 3. Mapping to an Machine Learning Problem
Since we understand the Business problem well, let’s try to pose it as a proper Machine Learning problem. The first thing to do is to aquire the data and understand it.<br />
Source: https://www.kaggle.com/c/facebook-recruiting-iii-keyword-extraction/data<br />
Data Overview:<br />
i. Train.csv contains 4 columns: Id,Title,Body,Tags.<br />
ii. Test.csv contains the same columns but without the Tags, which we have to predict.<br />
iii. Size of Train.csv: 6.75GB<br />
iv. Size of Test.csv: 2GB<br />
v. Number of rows in Train.csv = 6034195<br /><br />
The questions are randomized and contains a mix of verbose text sites as well as sites related to math and programming. The number of questions from each site may vary, and no filtering has been performed on the questions (such as closed questions).
Data set contains 6,034,195 rows. The columns in the table are:
Id : Unique identifier for each question<br />
Title: The question’s title<br />
Body: The body of the question<br />
Tags: The tags associated with the question in a space separated format (all lowercase, should not contain tabs ‘\t’ or ampersands ‘&’)<br /><br />
Since there are almost 6M rows which is too huge to consider, so depending on my system I have used 100k rows. I have also consider only top 2500 tags as from these tags also I am covering almost 97% of the total tags.
## 4. Performance Metrics
For a standard Binary of Multi-class classification problems, we can use performance metrics like Precision,Recall,F1-Score,Log-loss,AUC Curve etc..But for the present Multi-Label problem the mentioned metrics may not work well. As part of the business requirement we want high precision and recall rates for each and every predicted tag. We can use F1 Score here as it only gives good value if both the Precision and Recall are high. The F1 Score performs really well for Binary classifications. So for Multi Label Setting we can modify it into two types
i. Micro Averaged F1 Score
Imagine we have t1,t2,t3,…,tn labels and ‘A’ is basically set of all labels. We know the general formula of precision and recall.<br />
<align="center">![image](https://user-images.githubusercontent.com/51243187/88142023-64bff200-cc12-11ea-821c-b1fb6e06dd8e.png)
<br /><br />And we also know the formula of f1 score as<br />
<align="center">![1_cdmfghgZw3d7-rm0YYZPAQ](https://user-images.githubusercontent.com/51243187/88142156-a2bd1600-cc12-11ea-9c16-0e51f399c257.png)

The formulas for Micro F1 and Macro F1 are<br/>
![image](https://user-images.githubusercontent.com/51243187/88143960-be75eb80-cc15-11ea-8028-5c033687edfe.png)

![image](https://user-images.githubusercontent.com/51243187/88144064-f3823e00-cc15-11ea-8526-1d8b812ac2cb.png)



