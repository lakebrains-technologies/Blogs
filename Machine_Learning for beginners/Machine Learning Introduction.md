# **Machine Learning Introduction**

## **What is Machine Learning?**

#### *Machine Learning is the Science of Programming computers so they can learn from data.*

---
### **What is Data Mining?**        </br>

*Apply ML techniques to dig into large amount of data can help discover patterns that were not immediately apparent. This is called Data Mining*

---
## **To summarize, Machine Learning is great for:**

*1. Problems for which existing solutions require a lot of hand-tuning or long lists of rules: one Machine Learning algorithm can often simplify code and perform better.* </br>
*2.	Complex problems for which there is no good solution at all using a traditional approach: the best Machine Learning techniques can find a solution.*</br> 
*3.	Fluctuating environments: a Machine Learning system can adapt to new data.* </br> 
*4.	Getting insights about complex problems and large amounts of data.* 

---

## **Type Of Machine Learning System:**

*Whether or not they are trained with human supervision (supervised learning, unsupervised learning, semi-supervised learning and Reinforcement learning) Whether or not they can learn incrementally on the fly (online versus batch learning) Whether they work by simply comparing new data points to known data points, or instead detect patterns in the training data and build a predictive model, much like scientists do (instance-based versus model-based learning)* </br>

*Machine Learning systems can be classified according to the amount and type of supervision they get during training. There are four major categories: supervised learning, unsupervised learning, semi-supervised learning, and Reinforcement Learning.*

1.	*Supervised Learning :-* </br> 
*In Supervised learning the training data you feed to the algorithm includes the desired solutions , called Lable. A typical supervised learning task is Classification. Basically supervised learning is a learning in which we teach or train the machine using data which is well labeled that means some data is already tagged with the correct answer.
For instance :- Suppose you are given a basket filled with different kinds of fruits. Now the first step is to train the machine with all different fruits one by one like this:* </br>

•	*If shape of object is rounded and depression at top having color Red then it will be labeled as –Apple.* </br>

•	*If shape of object is long curving cylinder having color Green-Yellow then it will be labeled as –Banana.* </br>

•	*Now suppose after training the data, you have given a new separate fruit say Banana from basket and asked to identify it.* </br> 

•	*Since the machine has already learned the things from previous data and this time have to use it wisely. It will first classify the fruit with its shape and color and would confirm the fruit name as BANANA and put it in Banana category. Thus the machine learns the things from training data(basket containing fruits) and then apply the knowledge to test data(new fruit).* </br>

### Supervised learning classified into two categories of algorithms :- </br>

### •  Classification: </br>
    *A classification problem is when the output variable is a category, such as “Red” or “blue” or “disease” and “no disease”. Classification algorithms in machine learning use input training data to predict the likelihood that subsequent data will fall into one of the predetermined categories. One of the most common uses of classification is filtering emails into “spam” or “non-spam.”* </br>

### •	Regression: </br>
  *A regression problem is when the output variable is a real value, such as “dollars” or “weight”. Another typical task is to predict a target numeric value, such as the price of a car,given a set of features (mileage, age, brand, etc.) called predictors.* </br>
 
  *A regression problem is when the output variable is a real or continuous value, such as “salary” or “weight”. Many different models can be used, the simplest is the linear regression. It tries to fit data with the best hyper-plane which goes through the points.* </br>

### There are two type of regression model. </br>

## A.	Linear Regression:- </br>
 *It is a statistical method that is used for predictive analysis. Linear regression makes predictions for continuous/real or numeric variables such as sales, salary, age, product price, etc.*

### There are two types of linear regression algorithm:-
#### a.	Simple Linear :- </br>
 *If a single independent variable is used to predict the value of a numerical dependent variable, then such a Linear Regression algorithm is called Simple Linear Regression.* </br>

### b.	Multiple Linear :- </br>
 *If more than one independent variable is used to predict the value of a numerical dependent variable, then such a Linear Regression algorithm is called Multiple Linear Regression.*


### B.	Non-linear Regression:- </br>
 *Non-Linear regression is a type of polynomial regression. It is a method to model a non-linear relationship between the dependent and independent variables. It is used in place when the data shows a curvy trend, and linear regression would not produce very accurate results when compared to non-linear regression. This is because in linear regression it is pre-assumed that the data is linear.* </br>

### Types:-
•	*Logistic Regression* </br>
•	*Naive Bayes Classifiers* </br>
•	*K-NN (k nearest neighbors)* </br>
•	*Decision Trees* </br>
•	*Support Vector Machine* </br>
•	*Neural networks* </br>

## 2. Unsupervised Learning :- </br>
*In unsupervised learning, as you might guess, the training data is unlabeled. The system tries to learn without a teacher. It is basically a type of unsupervised learning method . An unsupervised learning method is a method in which we draw references from datasets consisting of input data without labelled responses. Generally, it is used as a process to find meaningful structure, explanatory underlying processes, generative features, and groupings inherent in a set.* </br>

### The most important unsupervised learning algorithms are:-</br>

### Clustering :-</br>
*Clustering is the task of dividing the population or data points into a number of groups such that data points in the same groups are more similar to other data points in the same group and dissimilar to the data points in other groups. It is basically a collection of objects on the basis of similarity and dissimilarity between them.* </br>

### Clustering Methods :-</br>

### • Density-Based Methods :- </br>
*These methods consider the clusters as the dense region having some similarity and different from the lower dense region of the space. These methods have good accuracy and ability to merge two clusters.Example DBSCAN (Density-Based Spatial Clustering of Applications with Noise) , OPTICS (Ordering Points to Identify Clustering Structure) etc.*</br>

### • Hierarchical Based Methods :-</br>
*The clusters formed in this method forms a tree-type structure based on the hierarchy. New clusters are formed using the previously formed one. It is divided into two category.*</br>
*o Agglomerative (bottom up approach)* </br>
*o Divisive (top down approach)*</br>
*o examples CURE (Clustering Using Representatives), BIRCH (Balanced Iterative Reducing Clustering and using Hierarchies) etc.* </br>

### • Partitioning Methods :-</br>
*These methods partition the objects into k clusters and each partition forms one cluster. This method is used to optimize an objective criterion similarity function such as when the distance is a major parameter example K-means, CLARANS (Clustering Large Applications based upon Randomized Search) etc.*</br>

### • Grid-based Methods :- </br> 
*In this method the data space is formulated into a finite number of cells that form a grid-like structure. All the clustering operation done on these grids are fast and independent of the number of data objects example STING (Statistical Information Grid), wave cluster, CLIQUE (CLustering In Quest) etc.* </br>

### — K-Means Clustering :-</br>
*It is the simplest unsupervised learning algorithm that solves clustering problem K-means algorithm partition n observations into k clusters where each observation belongs to the cluster with the nearest mean serving as a prototype of the cluster.*</br>

### — DBSCAN (Density-based Spatial Clustering of Applications with Noise):-</br>
*These data points are clustered by using the basic concept that the data point lies within the given constraint from the cluster centre. Various distance methods and techniques are used for calculation of the outliers.* </br>

#### — Hierarchical Cluster Analysis (HCA)</br>

### • Anomaly detection and novelty detection
#### — One-class SVM
#### — Isolation Forest </br>

### • Visualization and dimensionality reduction
#### — Principal Component Analysis (PCA)
#### — Kernel PCA
#### — Locally-Linear Embedding (LLE)
#### — t-distributed Stochastic Neighbor Embedding (t-SNE)
### • Association rule learning
#### — Apriori
#### — Eclat

### Applications of Clustering in different fields

### • Marketing :- </br> 
*It can be used to characterize & discover customer segments for marketing purposes.* </br>

### • Biology :- </br>
*It can be used for classification among different species of plants and animals.*
### • Libraries :- </br>
*It is used in clustering different books on the basis of topics and information.*</br>
### • Insurance :- </br>
*It is used to acknowledge the customers, their policies and identifying the frauds.*

## Semi-supervised learning </br>

*Some algorithms can deal with partially labelled training data, usually a lot of un-labelled data and a little bit of labelled data. This is called semi-supervised learning.* </br>

*In this type of learning, the algorithm is trained upon a combination of labeled and unlabeled data. Typically, this combination will contain a very small amount of labeled data and a very large amount of unlabeled data. The basic procedure involved is that first, the programmer will cluster similar data using an unsupervised learning algorithm and then use the existing labeled data to label the rest of the unlabeled data. The typical use cases of such type of algorithm have a common property among them – The acquisition of unlabeled data is relatively cheap while labeling the said data is very expensive.*</br>

### Example:- </br> 
*Google Photos is a very good example of this as we upload our family photos and in some photos person 1 is in photo number 2,5,9 and person 2 is in photo number 1,3,6 this is a unsupervised part of algorithm(clustering). Now you have to put marks that who is person 1 and who is person 2 so we just have to one label per person ,and it is able to name everyone in every photo.* </br>

*When the system works perfectly. In practice it often creates a few clusters per person, and sometimes mixes up two people who look alike, so you need to provide a few labels per person and manually clean up some clusters.*</br>

### A Semi-Supervised algorithm assumes the following about the data – </br>

### Continuity Assumption:- </br>
*The algorithm assumes that the points which are closer to each other are more likely to have the same output label.* </br>

### Cluster Assumption:- </br> 
*The data can be divided into discrete clusters and points in the same cluster are more likely to share an output label.*</br>

### Manifold Assumption:- </br> 
*The data lie approximately on a manifold of much lower dimension than the input space. This assumption allows the use of distances and densities which are defined on a manifold.* </br>

## Reinforcement Learning :- </br>

*Reinforcement Learning is a very different beast. The learning system, called an agent in this context, can observe the environment, select and perform actions, and get rewards in return (or penalties in the form of negative rewards). It must then learn by itself what is the best strategy, called a policy, to get the most reward over time. A policy defines what action the agent should choose when it is in a given situation
Reinforcement Learning is nothing but learns everything by his experience like the algorithm performs a task and find the best way to reached to the solution.* </br>

*If the first try is not reached tot the solution than it will learn from it and give another try the algorithm will keep working till it reached to the answer or destination and learn each time whenever it fails* </br>

### Main points in Reinforcement learning :- </br>

### Input:- </br> 
*The input should be an initial state from which the model will start.* </br>

### Output:-</br> 
*There are many possible output as there are variety of solution to a particular problem* </br>

### Training:- </br>
*The training is based upon the input, The model will return a state and the user will decide to reward or punish the model based on its output.* </br>

*The model keeps continues to learn.* </br>

*The best solution is decided based on the maximum reward.* </br>

### Batch learning </br>

*In batch learning, the system is incapable of learning incrementally: it must be trained using all the available data. This will generally take a lot of time and computing resources, so it is typically done offline. First the system is trained, and then it is launched into production and runs without learning anymore; it just applies what it has learned. This is called offline learning.* </br>

### Online learning </br>

*In online learning, you train the system incrementally by feeding it data instances sequentially, either individually or by small groups called mini-batches. Each learning step is fast and cheap, so the system can learn about new data on the fly, as it arrives.* </br>

*Online learning is great for systems that receive data as a continuous flow (e.g., stock prices) and need to adapt to change rapidly or autonomously. It is also a good option if you have limited computing resources: once an online learning system has learned about new data instances, it does not need them anymore, so you can discard them (unless you want to be able to roll back to a previous state and “replay” the data). This can save a huge amount of space
One important parameter of online learning systems is how fast they should adapt to changing data: this is called the learning rate. If you set a high learning rate, then your system will rapidly adapt to new data, but it will also tend to quickly forget the old data.* </br>

### Instance-Based Versus Model-Based Learning </br>

*The Machine Learning systems which are categorized as instance-based learning are the systems that learn the training examples by heart and then generalizes to new instances based on some similarity measure. It is called instance-based because it builds the hypotheses from the training instances. It is also known as memory-based learning or lazy-learning. The time complexity of this algorithm depends upon the size of training data. The worst-case time complexity of this algorithm is O (n), where n is the number of training instances.* </br>

### For example :- </br> 
*If we were to create a spam filter with an instance-based learning algorithm, instead of just flagging emails that are already marked as spam emails, our spam filter would be programmed to also flag emails that are very similar to them. This requires a measure of resemblance between two emails. A similarity measure between two emails could be the same sender or the repetitive use of the same keywords or something else.* </br>

### Advantages:- </br>

*• Instead of estimating for the entire instance set, local approximations can be made to the target function.* </br>
*• This algorithm can adapt to new data easily, one which is collected as we go.* </br>

### Disadvantages:- </br>

*• Classification costs are high* </br>
*• Large amount of memory required to store the data, and each query involves starting the identification of a local model from scratch* </br>

### Some of the instance-based learning algorithms are :- </br>

*• K Nearest Neighbor (KNN)* </br>
*• Self-Organizing Map (SOM)* </br>
*• Learning Vector Quantization (LVQ)* </br>
*• Locally Weighted Learning (LWL)* </br>

### Model-based learning </br>
*Another way to generalize from a set of examples is to build a model of these examples, then use that model to make predictions. This is called model-based learning* </br>

### For example:- </br>
*Suppose you want to know if money makes people happy, so you down load the Better Life Index data from the OECD’s website as well as stats about GDP per capita from the IMF’s website. Then you join the tables and sort by GDP per capita * </br>

*There does seem to be a trend here! Although the data is noisy (i.e., partly random), it looks like life satisfaction goes up more or less linearly as the country’s GDP per capita increases. So you decide to model life satisfaction as a linear function of GDP per capita. This step is called model selection:* </br>

### Main Challenges of Machine Learning </br>

*1. Insufficient Quantity of Training Data* </br> 
*2. Nonrepresentative Training Data*</br>
*3. Poor-Quality Data*</br>
*4. Irrelevant Features*</br>
*5. Overfitting the Training Data*</br>
*6.	Underfitting the Training Data*</br>

### ML | Common Loss Functions </br>

*Loss function estimates how well particular algorithm models the provided data. Loss functions are classified into two classes based on the type of 
learning task –* </br>

### • Regression Models :-</br> 
*predict continuous values.*</br>

### • Classification Models :- </br>
*predict the output from a set of finite categorical values*</br>









