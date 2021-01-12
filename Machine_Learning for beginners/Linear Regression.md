# Example of Linear Regression

<code>import pandas as pd</br></code>

<code>import numpy as np</br></code>

<code>import sklearn</br></code>

<code>from sklearn import linear_model</br></code>

<code>from sklearn.utils import shuffle</br></code>

<code>import matplotlib.pyplot as plt</br></code>

<code>import pickle</br></code>

<code>from matplotlib import style</br> </code>


### #Reading the CSV and sep the data by using sep = ; because data is seperated by ; in CSV file** </br>

<code>data = pd.read_csv("student-mat.csv", sep= ";")</br> </code>

### #Getting Relevant data by selecting the columns we want</br>

<code>
data =data[["G1","G2","G3","studytime","failures","absences"]] </br> </code>

### #The attribute we are trying to predict</br>

<code>
predict ="G3"
</code>

#### #Creating two arrays one is for containing lable and other one is containing features </br>

<code>
X =  np.array(data.drop([predict], 1))# Features
Y = np.array(data[predict]) #label
</code>

### Train the data and test the data we define our test data as 10% of all data

<code>
x_train , x_test , y_train, y_test = sklearn.model_selection.train_test_split(X,Y, test_size=0.1)
</code>

### #best = 0 is for finding best score

<code>
best = 0
for _ in range(20): #train our model multiple times for best score

</code>

    x_train , x_test , y_train, y_test = sklearn.model_selection.train_test_split(X,Y, test_size=0.1)
    linear = linear_model.LinearRegression()
    linear.fit(x_train,y_train) # Train the model  
    accuracy = linear.score(x_test,y_test) # Score the model using array
    print(accuracy) # Checked how algorithm performed
    if accuracy>best: #if current model have better score or best score than save
        best = accuracy
        with open ("studentmodel.pickle","wb")as f:
            pickle.dump(linear,f)
              
### #Saving the model and linear is ourmodel name

<code>
pickle_in =open("studentmodel.pickle" , "rb")
</code>

### #loading the model to predict grades

<code>
linear =pickle.load(pickle_in)
print ('Coefficient: \n', linear.coef_)
print ('Intercept: \n',linear.intercept_)
predictions = linear.predict(x_test)
for x in range(len(predictions)):
    print (predictions[x], x_test[x],y_test[x])
</code>

### #Drawing a ploting model

<code>
p = 'G1'
style.use("ggplot")
plt.scatter(data[p], data["G3"]) # scatter is a diagram where each value in data is shown as dot
# plt.xlable("G1") #name of xlable
# plt.ylable("final grade") # name of ylable
plt.show() # to show the grapical representation </br>

</code>


<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Machine_Learning%20for%20beginners/Images/Linear.png?raw=true"/>