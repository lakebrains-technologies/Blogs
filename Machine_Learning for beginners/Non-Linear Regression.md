# Example of Non-Linear Regression

<code>import numpy as np</br></code>

<code>import matplotlib.pyplot as plt</br></code>


### #Manually Data assigning targeted data</br>

<code>x = np.arange(-5.0, 5.0, 0.1)</br> </code>

## You can adjust the slope and intercept to verify the changes in the graph 

<code>  
y = np.power(x, 2)  #First array elements raised to powers from second array, element-wise.</br>

y_noise = 2 * np.random.normal(size = x.size) #creates an array of specified shape and fills it with random values</br>

ydata = y + y_noise </br>

plt.plot(x, ydata,  'bo') #ploting the data</br>

plt.plot(x, y, 'r')  #ploting the data</br>

plt.ylabel('Dependent Variable') #assigning name of Y-axis</br>

plt.xlabel('Indepdendent Variable') #assigning name of X-axis</br>

plt.show() #Print the plot
</br
</code>
</br>

<img src="https://github.com/lakebrains-technologies/Blogs/blob/master/Machine_Learning%20for%20beginners/Images/Non-Linear.png?raw=true"/>