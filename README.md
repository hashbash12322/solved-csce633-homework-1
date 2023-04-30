Download Link: https://assignmentchef.com/product/solved-csce633-homework-1
<br>
<h1>Question 1</h1>

<strong>1-dimensional linear regression</strong>: Assume a 1-dimensional linear regression model <em>y </em>= <em>w</em><sub>0 </sub>+ <em>w</em><sub>1</sub><em>x</em>. The residual sum of squares (RSS) of the training data D<em><sup>train </sup></em>= {(<em>x</em><sub>1</sub><em>,y</em><sub>1</sub>)<em>,…,</em>(<em>x<sub>N</sub>,y<sub>N</sub></em>)} can be written as:

<em>N</em>

<em>RSS</em>(<em>w</em><sub>0</sub><em>,w</em><sub>1</sub>) = <sup>X</sup>(<em>y<sub>n </sub></em>− <em>w</em><sub>0 </sub>− <em>w</em><sub>1</sub><em>x<sub>n</sub></em>)<sup>2</sup>

<em>n</em>=1

We estimate the weights <em>w</em><sub>0</sub>, <em>w</em><sub>1 </sub>by minimizing the above error.

<ul>

 <li>Show that minimizing RSS results in the following closed-form expression:</li>

</ul>

<em>Tip: </em>Set the partial derivatives  and  equal to 0. Then solve a 2 × 2 system of linear equations with respect to <em>w</em><sub>0 </sub>and <em>w</em><sub>1</sub>.

<ul>

 <li>Show that the above expressions for and are equivalent to the following:</li>

</ul>

where ¯ and ¯ are the sample means of input features and outcome values, respectively.

<ul>

 <li>How would you interpret the above expression in terms of the descriptive statistics (e.g.sample mean, variance, co-variance) of populations and?</li>

</ul>

<h1>Question 2</h1>

<strong>Principled method for learning the step size in gradient descent</strong>: In class we discussed that when we use gradient descent to minimize target function <em>J</em>(<strong>w</strong>) with respect to <strong>w</strong>, the step size <em>α</em>(<em>k</em>) at iteration <em>k </em>is a crucial hyperparameter. We further said that we can experimentally determine <em>α</em>(<em>k</em>) through cross-validation. There is actually a principled way for computing the optimal <em>α</em>(<em>k</em>) in each iteration and we are going to derive the expression for that.

<ul>

 <li>According to Taylor series expansion, a differentiable function <em>f</em>(<strong>x</strong>) can be written around <strong>x<sub>0 </sub></strong>as follows:</li>

</ul>

where ∇<em>f </em>are the gradient vector and <strong>H</strong><em><sub>f </sub></em>Hessian matrix of <em>f </em>evaluated at <strong>x<sub>0</sub></strong>.

Let <strong>w</strong>(<em>k</em>) be the value of <strong>w </strong>at the <em>k<sup>th </sup></em>iteration of gradient descent. Show that the second order Taylor expansion of the target function <em>J</em>(<strong>w</strong>) around <strong>w</strong>(<em>k</em>) is the following:

where ∇<em>J </em>are the gradient vector and <strong>H</strong><em><sub>J </sub></em>Hessian matrix of <em>J </em>evaluated at <strong>w</strong>(<em>k</em>).

<ul>

 <li>Show that the above expression of <em>J</em>(<strong>w</strong>) evaluated at <strong>w</strong>(<em>k</em>+1) (i.e. at the (<em>k</em>+1)<em><sup>th </sup></em>gradient descent iteration) can be written as:</li>

</ul>

<em>Tip: </em>Take into account the gradient descent update rule <strong>w</strong>(<em>k </em>+ 1) = <strong>w</strong>(<em>k</em>) − <em>α</em>(<em>k</em>) · ∇<em>J</em>|<strong><sub>w</sub></strong><sub>=<strong>w</strong>(<em>k</em>) </sub>(c) Show that minimizing the above expression with respect to the step size <em>α</em>(<em>k</em>) results in:

The above expression gives a closed-form solution of the step size at iteration k (i.e. <em>a</em>(<em>k</em>)) that minimizes the target function at the next iteration.

(d) What is the cost of computing <em>a</em>(<em>k</em>) at each iteration <em>k </em>using the above expression?

<h1>Question 3</h1>

<strong>Predicting forest fires: </strong>Forest fires are a major environmental issue endangering human lives. This renders their fast detection a key element for controlling them and potentially preventing them. Since it is hard for humans to monitor all forests, we can use automatic tools based on local sensors to do that. Through these sensors we can get information regarding the meteorological conditions, such as temperature, wind, relative humidity (RH), and amount of rain. We can also compute several fire hazard indexes, such as the forest fire weather index (FWI), fine fuel moisture code (FFMC), duff moisture code (DMC), drought code (DC), and initial spread index (ISI). Using these measures, we can predict whether fire is going to occur in the forest, as well as to estimate the amount of burned area. Such data are part of the “Forest Fires Data Set” of the UCI Machine Learning Repository and their description can be found here: http://archive.ics.uci.edu/ml/datasets/Forest+Fires.

Inside “Homework 1” folder on Piazza you can find two files including the train and test data (named “train.csv” and “test.csv”) for our experiments. The rows of these files refer to the data samples, while the columns denote the features (columns 1-12) and the outcome variable (column 13), as describe bellow:

<ol>

 <li><strong>X</strong>: x-axis spatial coordinate of the forest: 1 to 9</li>

 <li><strong>Y</strong>: y-axis spatial coordinate of the forest: 2 to 9</li>

 <li><strong>month</strong>: month of the year: 1 to 12 to denote ”jan” to ”dec”</li>

 <li><strong>day</strong>: day of the week: 1 to 7 to denote ”mon” to ”sun”</li>

 <li><strong>FFMC</strong>: FFMC index from the FWI system</li>

 <li><strong>DMC</strong>: DMC index from the FWI system</li>

 <li><strong>DC</strong>: DC index from the FWI system</li>

 <li><strong>ISI</strong>: ISI index from the FWI system</li>

 <li><strong>temp</strong>: temperature in Celsius degrees</li>

 <li><strong>RH</strong>: relative humidity</li>

 <li><strong>wind</strong>: wind speed in km/h</li>

 <li><strong>rain</strong>: outside rain in mm/m2</li>

 <li><strong>area</strong>: the burned area of the forest (this is the <strong>outcome </strong>variable)</li>

</ol>

<ul>

 <li><strong>Data exploration: </strong>Inspect the input features (e.g. you can plot histograms, scatter plots, etc.). Which of the features are continuous and which categorical?</li>

 <li><strong>Classification: </strong>From data exploration, we can notice that the the outcome value (i.e. the burned area) is zero for many samples, meaning that the corresponding forests are not affected by fire. Therefore we can dichotomize the outcome variable, based on whether its corresponding value is zero or greater than zero. This creates the following two classes:</li>

</ul>

<strong>Class 0: </strong>Forests not affected by the fire, i.e. area = 0

<strong>Class 1: </strong>Forests affected by the fire, i.e. area <em>&gt; </em>0

After dichotomizing the outcome variable, we can run a classification task to <em>predict whether or not fire will occur in a certain forest </em>based on the input features.

<ul>

 <li>Implement a K-Nearest Neighbor classifier (K-NN) using the euclidean distance as a distance measure to perform the above binary classification task. <em>Reminder: </em>Don’t forget to normalize the features.</li>

 <li>Explore different values of <em>K </em>through cross-validation on the training set. Plot the classification accuracy, i.e. (#samples correctly classified) / (total #samples), against the different values of <em>K</em>.</li>

 <li>Report the classification accuracy on the test set using the best <em>K </em>from cross-validation. (b.iv) <strong>Bonus: </strong>Instead of using the euclidean distance for all features, experiment with different types of distances or distance combinations, i.e. Hamming distance for categorical features. Report your findings.</li>

</ul>

<ul>

 <li><strong>Linear Regression: </strong>Among the forests that were affected by the fire, we can use linear regression to predict the actual amount of area that was burned. For this task, <strong>we will only use the samples of the train and test set with burned area (column 13) greater than zero, i.e. area </strong><em>&gt; </em><strong>0</strong>.

  <ul>

   <li>Plot the histogram of the outcome variable. What do you observe? Plot the histogram ofthe logarithm of the outcome value, i.e. log(area). What do you observe now?</li>

   <li>Implement a linear regression model to fit the outcome data using the ordinary leastsquares (OLS) solution.</li>

   <li>Test your model on the test data and compute the residual sum of squares error (RSS) and the correlation between the actual and predicted outcome variable.</li>

  </ul></li>

</ul>

(c.iii) <strong>Bonus: </strong>Experiment with different non-linear functions of the input features. Report your findings on the train and test sets.