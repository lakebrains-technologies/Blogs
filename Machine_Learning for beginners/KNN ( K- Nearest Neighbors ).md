# KNN (K- Nearest Neighbors) Algorithm


<code>import sklearn</br></code>
<code>from sklearn.utils import shuffle</br></code>
<code>from sklearn.neighbors import KNeighborsClassifier </br></code>
<code>import pandas as pd</br></code>
<code>import numpy as np</br></code>
<code>from sklearn import linear_model, preprocessing  </br></code>

### #Preprocessing use to convert non-numeric value to numeric values

<code>data = pd.read_csv("car.data")</br></code>

<code> print(data.head()) </br> </code> 

<code> le = preprocessing.LabelEncoder() </br> </code>

<code>buying = le.fit_transform(list(data["buying"])) </br> </code> 

### #The method fit_transform() takes a list (each of our columns)

<code>
maint = le.fit_transform(list(data["maint"]))#and will return to us an array containing our new values.</br></code>

<code>door = le.fit_transform(list(data["door"])) </br></code>

<code>persons = le.fit_transform(list(data["persons"]))</br></code>

<code>lug_boot = le.fit_transform(list(data["lug_boot"]))</br></code>

<code>safety = le.fit_transform(list(data["safety"]))</br></code>

<code>cls = le.fit_transform(list(data["class"]))</br></code>

<code>predict = "class" #prediction started </br></code>

### #zip is used to recombine data into featured list and a labled list
<code>X = list(zip(buying,maint,door,persons,lug_boot,safety))</br>
Y = list (cls)</br>
</code>

### #spliting data into train and test </br>
<code>x_train , x_test , y_train, y_test = sklearn.model_selection.train_test_split(X,Y, test_size=0.1) </br></code>

### #how many look neighnors to look = n_neighbors= ?
</br>
<code>model = KNeighborsClassifier(n_neighbors = 9)</br> </code>

### #to train the data
<code>model.fit(x_train, y_train)</br></code>

### #to score the test data
<code>accuracy = model.score(x_test, y_test)</br></code>

### #Print the Accuracy of the data</br>
<code>print(accuracy)</br></code>

#predicting the x_test data </br>
<code>predicted = model.predict(x_test)</br> </code>

### #name list to convert integers into string </br>
<code>names = ["unacc", "acc", "good", "vgood"]</br>
</code>
<code>
### #Giving the predicted data in the for loop
for x in range(len(predicted)):</br> </code>
<code>  
        print("Predicted: ", names[predicted[x]], "Data: ", x_test[x], "Actual: ", names[y_test[x]])</br></code>
#Give the value of [x_test[x], Amount of      
neighbors 9 </br>
<code>
    n = model.kneighbors([x_test[x]], 9, True)</br></code>
    #printing data for each point by printing n
<code>    
    print("N: ", n)</br></code>