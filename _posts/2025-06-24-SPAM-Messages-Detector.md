---
layout: post
title: "SPAM Messages Detector Using Logistic Regression and Naive Bayes Model"
date: 2025-06-24
---
![Spam Messages](/assets/img/posts/WAYS-TO-STOP-SMS-SPAM-ON-iPhone-Android-HERES-HOW-1.jpg)

Hello 👋🏾, Angelina here!

This past week I've been working on a project that is detecting spam messages through big data. This project was developed using ***Python 3.13.2*** and ***Jupyter Notebook*** and ***VScode*** as an IDE (Integrated Development Environment). I've used the ***Logistic Regression Algorithm*** to detect the differences and patterns in the messages. The messages are named as *SPAM* for the spam messages and *HAM* for the unidentified, not spam or missing data messages. 
In the next few (or maybe a little more lines), I will explain the project in more details, just so I can report and present the project better.

### Project Description

In the beginning, I downloaded and imported the dataset as a CSV file, into the Jupyter Notebook. 
This particular data set I got from [Kaggle](https://kaggle.com). I did find Kaggle very helpful as it has a lot of projects that can be used by beginners and intermediate, and also allows to not only have datasets, but a lot of information that are very helpful.

The second step is to import all the libraries that are going to be used during the project: 
- [Pandas](https://pypi.org/project/pandas/)
- [Numpy](https://pypi.org/project/numpy/) 
- [Seaborn](https://pypi.org/project/seaborn/)
- [Matplotlib](https://pypi.org/project/matplotlib/)
- [Spacy](https://pypi.org/project/spacy/)


When it comes to Spacy I did have some difficulties importing the library into my project, as it was always giving me an error. However, after quiet a research I installed spacy and then imported it, which fixed my bug. 

### Data Cleanup & Processing
After fixing the problem with Spacy, I had to read and present my data set table. 
Since the data that I downloaded had many columns, categories and data that I actually did not need for this project, I just had to use the V1 and V2 columns which respectfully I defined as *label* and *messages*, removing the rest of the unnecessary information. 

After decluttering the data and saving what I needed, I wanted to check what is the differencial number between the *HAM* and *SPAM* messages. 

Which one would be more in the data set? 

Using a bar chart, I was able to visualize the difference between the count between both variables. The Bar Chart has the name **"Distribution of Spam vs. Ham Messages"** and on the Y-axis has the count, while on the X-axis has the two message types *SPAM* and *HAM*. 
From the visualized data through Bar Chart, we can see that the *HAM* messages were dominating with 4825 vs the *SPAM* messages that are 747. 


After, defining which messages were more, I continued to clean the data to make it easily readable and destinguishable. 
I used `TfidVectorizer` to transform the data form a raw text document into a numerical representation that the machine learning algorithm that I will use later will understand and read. 

The next step was to import the **Logistic Regression Algorithm** and started training it accordingly. 

I created a `Confusion Matrix` to predict the accuracy of the algorithm, and from the matrix we can see that the algorithm is giving a very high average score of accuracy 97%, as well as high average F1 - score (the performance) 96%. 

Considering the fact that there is a class imbalance in the CSV file, I used `GridSearchCV` to make sure I'm on the right track and the `Logistc Regression` is the right algorithm to use. `GridSearchCV` showed that the best Logistic Regression model will be `C=100` and with balanced class weight, considering the fact the data is not as balanced as it should be. 

After configuring the right algorithm and model, I created a `ROC curve`, which is a diagram that is representing the performance between the `True Positive Rate` (TPR) and the `False Positive Rate` (FPT). 
I did the ROC curve to represent how well the model can distinguish between the different classes. I also included treshold to minimize the difference between the two.

In order to have an accurate curve, I had to calculate the Area Under the Curve also known as `AUC`. The specification of AUC is that the higher it is, the more accurate the model is in distinguishing between the classes. After doing the AUC, I started plotting the ROC curve in order to get to the visualization. The diagram gave me an AUC of 0.99 which can be considered a great score. 

Another thing that I put on the ROC curve is a `Random classifier` just so I can have a base for comparison and provide a better visualization of the ROC curve and the results. 
The next thing that I did is to create another type of visualization that is going to give me predictions about the *SPAM* and *HAM* words that are used in our data set. 

### Vizualization
The visualization is a horizontal bar chart, and the colors that are indicating the *SPAM* and *HAM* words are respecfully red for *SPAM* and green for *HAM*. This is the best way to visualize it, because psychologically *SPAM* is something bad which is represented by red and *HAM* is represented as words that are indicating a non-spam messages and it is giving the "green light" in the project. 
Not only the colors are indicating the difference between *good* and *bad*, I also made the colors gradient, indicating which specific word is more likely to be used in a "SPAM" or "HAM" text. 

From the horizontal bar chart we can see that the most likely the word *txt* is a number one word used in *SPAM* message. Contrary, the word *my* is considered a word that would likely be used in *HAM* message. 

This helped me categorize the words that are used in the messages, and helped in finding the "parasite" words to categorize which message is *SPAM* or *HAM*. 

The next step that I took was to use the `Naive Bayes Model`. 

### Naive Bayes Model

After finding out which words are a red flag, the last thing I was supposed to do is to find where exatly those words are in the text. This is why I decided to use Naive Bayes Model, which is helping to find a data point's place in the data set. 

After coding the model, I had to check how accurate it is and if, it is performing well. It turned out the model is almost 88% accurate which is considered a well score overall, but can be causing some bugs depending on the data. The problem is probably coming from some of the data not being processed.
After finding out how well is our model performing, I extracted a sample with few of the text messages that are detecting the *SPAM* words from the horizontal bar graph before.

### Conclusion 
The project is involving a raw data that is about messages that I classified as *SPAM* or regular messages. I went through cleaning the data, categorizing the data that I need for my project and creating the Logistic Algorithm. 
In addition I created a Bar Graph that is serving the purpose of visualizing the difference between the amount of *SPAM* and *HAM* messages. 

Also, I created a `Receiver Operating Characteristic` curve, also known as ROC. The linear graph is visualizing our Area Under the Curve (AUC), which gave us a great coeficient of 0.99, which means that the model is distinguishing between the classes in a good manner. In addition, I created a horizontal bar chart graph that is visualizing the *TOP 15 words* that are used in *SPAM* or *HAM*. Thanks to this graph I was able to use the Naive Bayes Model, which takes one point of data (in this scenarion, words) and detects where it was used in the data. 

The project involves a Machine Learning algorithm which is the Logistic Regression and the Naive Bayes Model. I did my Jupyter Notebook on VScode and it was coded with Python 2.13.2

Link to the coding of this project: https://github.com/imangelinak/messages_spam_detector 

#### ***Till Next Time!*** #
*Angelina Katrandzhiyska*

<script
  src="https://utteranc.es/client.js"
  repo="imangelinak/imangelinak.github.io"
  issue-term="pathname"
  theme="github-light | github-black"
  crossorigin="anonymous"
  async
></script>





