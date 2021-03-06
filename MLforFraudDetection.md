# Machine Learning for Fraud Detection 

Analyticts techniques with focus on the fraud practitioner's perspective. 


## Data PREPROCESSING step 



Real data is typically dirty, full of inconsistencies, incompleteness and duplication, from messy data you get messy analytical models
so we have to apply data filtering mechanisms
first step of data anlyting preprocessing par
data preprocessing step -> 80% of your time
lose a lot of time here, data are pain if you have ever worked with a real dataset

Data-filtering mechanisms must be applied to clean up and reduce the data.
Even the slightest mistake can make the data totally unusable and the results invalid.
 
 Different types of data sources: 
-transactional data: structured and detailed information capturing the key characteristics of a customer transaction
Summarized over longer time horizons by aggregating it -> they are meaningful when interpreted individually and furthermore their interaction is useful for fraud detectio  and anti money laundering

-types of data elements
  .continuous data: defined on an interval ( limited and unlimited) 
  .categorial: all the set of data defined on a category  
  -nominal: no meaniningful ordering between a limited set of data
  -ordinal: meaningful ordering
  -binary: two values (yes/no)

### SAMPLING
take a subset of historical data to build an analytical model 
we not analyze directly the full data set because the key requirement for a good sample is to be representative fot the future entities 
-> timing and representativeness are crucial. 
Sampling timing and bias-> choosing the optimal time window, but it is a trade off between lots of data that gives you a mr robust analytical model and recent data that are more representative
An average period to get as accurate as possibile a picture of the target population 
Sampling bias should be avoided even if not straighforward
 
Take a subset of historical data to build an analytical model.
With the availability of high-performance computing
why not analyze directly the full data set?
 
  sampling procedure: problem of bias, biased on your decision/selection
  taking a sample is biased by our decision
  a good sample should not be biased 
  model and select a sample that target the avaerage period and behavior, i want an average picture
  but this is not an easy task 


what can I do ? 
1.build separate models for homogenous time frames or different frames-> complex and demanding solution- multiple models have to be developed, run, maintained and monitored.
2.sampling observations over a period covering a full business cycle and build a single model
  a. cost of reduced fraud detection power since less tailored to a particular data frames
  b. less complex and costly to operate

Sampling has a direct impact on the fraud detection power.

#### adventage of sampling: you have a smaller dataset, faster in creating your model and being ready to update it 

Stratified sampling: a sample is taken according to predefined strata
In a fraud detection context data sets are very skew

a. stratifying according to the target fraud indicator-> sample will contain exactly the same percentages of (non-) fraudulent transactions as in the original data
b. stratification applied on predictor variables-> resemble the real product transaction distribution 


### VISUAL DATA EXPLORATION

-NO PERIODICITY
-time good indicatyor
-distribution good indicator

fraud transaction can be hidden inside usual transaction 


Visual data exploration is important, gives you an initial insights into the data, you can use plots
Then inspect some basic statistical measurements -> calculate them separately for each of the target classes to see whether there are any interesting patterns present 

### EXPLORATORY STATISTICAL ANALYSIS

#### Basic statistical measurements 
(averages, standard deviations, minimum, maximum, percentiles)
  Calculate these measures separately for each of the target classes to see wheter there are any interesting patterns present 
  
#### Basic descriptive statistics
descriptive statistics provide basic insight for the data, they should be assessed together in support and completion of each other
a.MEAN AND MEDIAN
b.VARIATION/STANDARD VARIATION: provide insight with respect to how much the data is spread around the mean value 
c.PERCENTILE VALUES: complementary information wrt the distribution and the median value 
d.MODE the most frequently occurring value


#### Specific descritive statistics

SYMMETRY OR ASYMMETRY OF A DISTRIBUTION -> harder to interpret: limits their pratical use, sometimes it is easier to assess these aspects by inspecting visual plots of the distribution of the involved variables

### BENFORD'S LAW
-> visual and numerical data explorastion technique
it describes the frequency distibution of the first digit in many real-life data strategies
based on the idea you can have a metric that express the destribution 
Compare the expected distribution following benfords's law with the one provided by the company(with the observed distribution in a data set)
Strong deviation from the expected frequencies may indicate the data to be suspicious and manipulated
It can be used as a screening tool for fraud detection
It is a partially negative rule, if the law is not satisfied, then it is probable that the involved data were manipulated and further investigation or testing is required, 
conversely, if a data set compies, it can be still fraudulent . 
A sufficient amount of data related to an invidudal casa need to be gathered. 


### MISSING VALUES
Some analytical techniques (e.g., decision trees) can deal directly with missing values. Other techniques need some additional preprocessing.

 a. 
 1. Replace the missing values with a known value
 2. Delete observations or variables with lots of missing values: assumes information has no meaningful interpretation 
 3. Keep missing values since they can be meaningful and may have relation with fraud and nees to be considered as a separate category 

b. Statistically test whether missing information is related to the target variable or not.
 1. if yes, then we can adopt the keep strategy and make a special category for it
 2. if not, one can depending on the number of observations available- delete or replace


(fraud 4 - 01/04/22 )
### OUTLIERS
extreme observations that are very dissimilar to the rest of the population, can be valid or invalid , unvariate(one dimension) or multivariate(multiple dimensions)
 
####  Univariate Outlier Detection and Treatment
Minimum and maximum values for each of the data elements 
->graphical tools: 
  1.histogramm 
  2.box plot(you rappresent on a scale quartils, first and third, the media and the maximum and minimun, if they are inside the quarttile range- whatever is over is the outliers),
  3.z-scores ( reducing the outliers to a threshold you are selecting- impose both  LOWER AND UPPER LIMIT ON A VARIABLE AND ANY VALUES BELOW/ABOVE ARE BROUGH BACK Of these limits ). Measures how many standard deviations an observation lies away from the mean 
  compute the distribution, represent it on an istogram 
  if inside the range, plot all the data on this line, you compute statistics on your data, then you plot the rane first/last quartile-> how much of your data is inside this area
  how many stanrdard deviation an observation lies away from the mean-> you check for each single instance how much differs from the media in terms of standard deviation 


####  Multivariate Outlier Detection and Treatment
(now you are considering multiple features at the same time )
  1. fit the features in a multidimensional space -> can be seen as a vector
  -distance between different vectors
  .fitting regression lines and inspecting the observations with large errors
  2.clustering or calculating the Mahalanobis distance




-variouys schemes exist to deal with outliers 
  .for invalid observations one could treat the outlier as a missing value
  .for valid obs impose both a lower and upper limit on a variable and any values below/above are brought back to these limits -> they are information that we don't want to loose
#### Truncation example 


Not all invalid values are outlying and may go unnoticed if not explicitely looked into
Construct a set of rules formulated based on expert knowledge 
find relation you know must be present in your dataset
constraint that apply to the combination of variable values 

take explicit precautions
these  kind of inconsistences can by find by experience

 
 ??? When handling valid outliers in the data set using the treatment techniques, we may impair the ability of descriptive analytics in detecting frauds:
    Be extremely careful in treating valid outliers when applying unsupervised learning techniques to build a fraud detection model.

??? When handling invalid outliers, on the contrary, they can be treated as missing values preferably by including an indicator that the value was missing or even more precisely an invalid outlier.
 
 

extremly careful to treat these values, you have to document by addign a feature that specify because 
it is missing a value, if you start a preprocessing in the wrong way you cannot be more able to detect the anomaly 


### Standardize data

<img width="516" alt="image" src="https://user-images.githubusercontent.com/61761693/174438418-c18fb07a-cf78-468b-a18f-f23443328b74.png">

another problem: represented by this image 
compare two value of your dataset -> the distance ( eucledian, manhattan..)
the problem of this computation is that it is not correct ? 
The scale are differt!!! doesn't make any sense 
u have to standardize your features !!

scaling variables to a similar range
1. mix/man standardize ( max and min of the current distribution and rescale everything based on that)
2. z-score (calculate che z scores, compute min, compute standard deviation, keep the distance )
3. decimal scaling (divide by 10 to put all the features in the same scale)

### Categorization 

Additional information about the domain, sometimes you want to add to the dataset some knowledge that directly derive from of the domain you are analyzing. 

some times you have also continuous variables, and you have to study the slot of the c variables and defining when there is a change  in the slot (increase, dcrease, ioncrease) 
depending on the data you may want to extract different information that can be useful -> but you are adding complexity, adding feeatures to te original one that must be treated.


### Variable selection 

Many analytical modeling exercises start with tons of variables, of which typically only a few actually contribute to the prediction of the target variable
problem automatically solved by random forest alghoritms, they learn the feature important to you, but in another case you don't want to spend complexity and add features to your model 
this is a problem cause sometimes the dataset has a huge amount of features, and in the end only few of them are really helpful-> 10/15 variables


#### FILTERS
Are a very handy variable selection mechanisms
allow a quick screening of which variable should be retained
depending on the type of the variable and the type of target variable  you can select a different statistic test that measure the correlation between the target and the variable

Pearson correlation
additional metodology to analyze the correlation
It measures a linear dependency between two variables and always varies between -1 and +1
Filters allow reduction in the number of dimension of the data set early in the analysis 

There are other type of filters..
Filters allow reduction in the number of dimensions of the data set early in the analysis. 
Is necessary a follow-up input selection step during the modeling phase. 
Drawback: work univariayely and do not consider correlation between the dimensions individually



sometimes you cannot use all the feature 
the motivation may contain personal information 
feature seletion independent from your decision 

#### PCA 
PRINCIPAL COMPONENT ANALYSIS
group of methods to automatically reduce the dimensionality of your dataset and at the same time finds a set of feature not correlated with each other.
you are able to reduce, select feature that you want and the feature are not correlated

reduce dimension by forming new value that are a linear composition of the original ones (main component) 
at maximum the same number of the original ones. 
only a small portion of your variable contains the information you need. 
the info contained in the original data set can be summerixzed by a limited number of components 


find two new features that try to better describe the distribution of the data in the space
 PC1 will describe the set of data in a way that you can continue the analysis
 they are ortogonal-> not correlation between of them 

### Correlation and stability 
 assure that your model will be stable
 when we analyze the stabilty we refer **to correlation between variables**

 it means that when you have to select the feature, the most important one, you have to check that they are not correlated, otherwise 
 the model is not stable -> we achieve bad result 

if you apply PCA-> your model will be stable

should we apply PCA always? 

qith pca you loose the interpretability of the features 
trade-off: PCA if your are not interested in interpretaibility 
the problem is that interpretability is one of the key aspect /parameter to evaluate the effectivness of a fraud detection methods
everything has to be evaluate at the end by an human 
if you need to have a score easy to investigate/interpret, you have to avoid PCA

 #### Segmentation ?? non so se ci si ?? soffermato 
Sometimes the data are segmented before the analytical modeling starts.
It allow to estimate different analytical models each tailored to a specific segment.
However, by segmenting, will increase:
??? the number of analytical models to estimate
??? the production, monitoring, and maintenance costs.
 

## DESCRIPTIVE ANALYTICS FOR FRAUD DETECTION

### unsepervised learning techniques -> descriptive analytics for fraud detection 
unsupervised aims at finding anomalous behavior that deviates from the norm of the dataset
you have to define the norm ( average behiuour of dataset of customer/ or behavior of the average customer)

unsupervised , you can identify from new cyber attack 

you want to identiy an outlier detection
techiques relevant when you have NO labels!
fraudsters is dynamically adapting, organization is at the beginning 
find a way to model an average behavior

**Define your norm, define the AVERAGE behavior of your dataset**

-the norm depends on the domain you are analyzing 
-when you define a norm you are defining the boundering of why is normal and what is not 
-the norm may change over time 
-anomalies do not necessarily represent frauds, since it is unsupervised, what ever you find is knowledgne that canbe related or Not

GRAPHICAL outlier detection procedures
procedure similar for outliers in preprocessing, you can canalyze them in one or multi dimension 
1. One dimension outliers-> histogram or box plot 
2. Two/three dimensional outliers -> scatter plot 

disadvantges: less formal and limited to a few dimensions, require active involvement of the end user, for a large dimensional data set, is cumbersome

knowledge to verify what you have found


## STATISTICAL OUTLIER DETECTION

### Z-score
If the absolute value of the z-score is bigger than 3 can be considered as outliers 
### Fit a distribution, or mixture of distributions
Outliers: observations with small values for the probability density function 
### Break Point Analysis 
intra-account fraud detection method -> break point indicates a sudden change in the behavior
a. define a fixed time window
b. split into an old and new
c. you compare them 

detect if there is a change in the behiavour and study the difference, if it is higher than a threshold you set, you start investigate
(see slide) 
training part and testing part 
studying the difference -> find something that needs to be investigated
### peer-group
INTER-account techiques
group of account that behaves similarly to the target account, elements in your dataset that are close together,  when the behaviour deviates from the peer created, anomaly 
#### a. peer group identification 
#### b. anomaly valuation
Steps: 
1. The peer group of a particular account is identified 
  a. from prior business knowledge 
  b. In a statistical way
2. Number of peers ( if too small, sensitive to noise, if too large, insensitive to important irregularities)
3. The behavior of the target account is contrasted with its peers
  a. statistical test 
  b. distance metric 


### association rule analysis 
detect frequently occurring relationship between items
association  between two different items in the dataset
Key input: transactions database D consisting of a transaction identifier and a set of items I. 
 you define association rule X sub set of items and Y subset of items-> statistical measure of the strengh of the association



 INSURANCE FRAUD EXAMPLE 
 Goal: find frequentelly occurring relationships/associations rules between the various parties involved. 
compute a set of statistics
1. identify frequenty item strategies
The frequency of an item set is measured by means of its support, which is the percentage of total transactions in the database that contains the item set 
support(X) -> percentage of total transactions in the database that containts the item set 
2. derive association rules -confidence- strong enough to be considered
confidence(X->Y): measures the strength of the association and is defined as the conditional probability of the rule consequent, given the rule antecedent. 


> FRAUD DETECTION

> in the previuour lecture we explodred the unsupervised, the main difference with rw supervised 
> you don't have any label related to the custom value you want to predict/classify
> we have to extract the norm
> main challenge of unsupervised-> anomaly DETECTIONyou want to detect something that is outling with > the norm itself
> allows you to extract knowledge
> started from graphic techniques-> something that outlies from the nrm, group of points
> statistical: this time exploiting statistical techniques
> break point: intraaccount , you decide testing window and you test if the new distribution is > similar to the preboous one
> peer-group, seasonality, data that change during time


## CLUSTERING

-> main unsupervised learning technique
summarize advantages and disadvantages of unsupervised
split your data into group such that you want to max similarity intragroup and difference betweek element from different groups

process that requires a good amount of data
group data in different set 
**if you have a lot of feature apply feature selection**

norm: big cluster of data 
anomalies: small cluster that is away from the normal 
this is what you want them to analyze to understand it it is frudolent or Not

this single ^^ anticipates one of the main challenge of clustering, a super good tipycal result is in this example
the interesting fact about clustering it works -> you are gonna obtain cluster in any change
the change is to find a way to understand if the cluster is meaningful or not, if it is relevant

final result of clustering technique-> something that was not relevant

core element of clustering techiques: ***distance matric!!***

Aim of clustering: group observation based on similarity 
distance metric is needed to quantify similarity !

in order to cluster element you have to compute the similarity between two element

-euclidea,/minkowski(depending on the parameter you may obtain a manhattan or euclidean) -> be careful you want to standardize

**Continuous Variables** ok -> euclidian, pearson correlation or cosine measure 

**Categorical variables** -> binary variables, zero or one depending on if this particular features is present or not in your data
  a. Simple matching coefficent -> SMC computes number of identical matches between values of a variable(take a distance and another distance and you compute how many times are different)
  b. jaccard index -> similarity when they are both set to one
  -categorical with more than two values
  first option: 
  -> transform them in dummy 0/1 values 
  -> coarse classification
  second option: 
  -> apply simple matching coefficent 
  -> count the number of identical matches 

You have to do a trial and error approach
Continuous and categorical variables mix -> due opzioni 

<img width="638" alt="image" src="https://user-images.githubusercontent.com/61761693/174471077-96f4170b-d7f5-4f9b-a732-6908ea1faaaa.png">


## Clustering Hierarchical 

Divisive and agglomerative depending on how you perform the clustering
#### Divisive
you start by considering all the elemnts inside your dataset as beyond one single cluster  and then you start analyzing the similarity between the elements to split them until you reach one element
#### Agglomerative
you assign one single cluster to each element, compute similarity and you start group them 

Distance between clusters -> different methods (you can call a library in python)

single: most closest point 
complete: defined by the distance between the two most different
average: all the points
centroid: the mean 

Final result will be something in between the two step, find different result and test them 

main problem of distance: not efficient, you have to visit the entire dataset 

NUMBER OF CLUSTERS-> decide on the optimal number of clusters
-dendogram: keep track of all the possible merge, and put in a diagram the distances 
-screen plot: plot of the distance at which clusters are merged, the elbow point that indicates the optimal clustering

you have comunque to decide if it is correct or not 
using a different technique would result in a different result , why? 
_____ non ho capito so solo che succede se tipo uso complete invece di average


Advantage: number of cluster does not need to be specified, allows to cluster data without knowing a priori the number of cluster to select 
Disadvantage: they do not scale at all, the higher the amount of data, the higher the computation 
the interpretation of the cluster is often subjective -> you have to have an expert that evaluates your result


## Clustering Non Hierarchical 

basic techniques that can be used, the number of features are not so used and i want something that can be interpret by an analyst 
#### K-MEANS: 

1. Select k observations as initial cluster centroids(seeds)
2. Assign each observation to the cluster that has the closest centroid(eg Euclidean distance)-> apply each observations to the closest centroid 
3. When all observations have been assigned, recalculate the positions of the k centroids(mean)-> recompute centroids 
4. Repeat until the cluster centroids no longer change or a fixed number of iterations is reached

continue until k into distributoion or after a limit number of iterations

disadvantages: you have to know the number of clusters ! (or you have to try all the possible combinations )
the final result depend on where you put the position of centroid (on where you put the centroid)


#### SOM (self organizing maps) 
NN that has only two layer ( input and output layer) 
Allows to visualize and cluster high dimensional data on a low-dimensional grid of neurons 
each input is connected to the all possibile outputh with a set of weights 

When a training vector x is presented, the weight vector of each neuron c is compared with x, the neuron that is most similar to x in Euclidian sense is the BMU
BMU most similar vector of the input you have provided on the basis 
we select the BMU 
once we have selected it we are going to update all the weights to match the best matchin until
try to map all the neibg to the distribution of your original dataset 

iterative procedure
1.compute the BMU that is the most similar vector to the input that you have porovided on the basis of the euclidian distance 
2. update all the wights in order to match the BMU -> stretch to fit as much as possible the original distribution 

you will have a stable solution at the end 
a light part  / darker part will rappresent clusters 

Soms are a very handy tool for clustering high-dimensional data sets because of the visualization facilities. Since there is no objective function to minimize, it is harder to compare various SOM solutions against each other. Experimental evaluation and expert interpretation is needed to decide on the optimal size of the SOM. 
Unlike k-means clustering, a SOM does not force the number of clusters to be equal to the number of output neurons. 


## SEMI-SUPERVISED CLUSTERING 

In many domains, the expert have prior knowledgne about existing fraud patterns and anomalous behavior. We can incorporate backgroun knowledge to guide the clustering. 
Bias the clustering with expert knowledge suh that che clusters can be found quicker and with the desider properties. 

put constraints on how you are going to cluster elements inside your data 
put labels or minimun distance between particular pairs of elements-> procedure easier and faster
you are guideing the cluster procedure
this can be done when you have information provided by experts

you are going to label all your istances with already a preformed cluster that you know from a precedent knowledge

We can have different type of constraints
-Observation-level constraints
If the fraud behavior of only a few observations is known, they can then be forced into the same cluster.
-Cluster-level constraints 
-Other 

**One-Class SVM** 
Maximize the distance between a hyperplane and the origin 
try not to cluster your data in different group, then try to distinguish what is the norm to what is a outlier 
they try to do this by trying to rappresent your data in a two dimensional space and find the best hyperplane 



PAINFUL PART NOW !! yay 
it is difficult to understand if final result is good or not, try multiple things to understand 

best solution: statistical measure
compute intersimilarity/intra 
or SSE (iterate between different solutions)

or the other solution is to manually analyze final output and block the characteristic we have obtained. 


final result of cluster technique is a label dataset (final data is a cluster to which each single labelbelong ??)-> use the output of the unsupervised (cluster)and train a supervised on the basis og the label of the cluster technique 
-> interpret the result! 

## PREDICTIVE ANALYTICS FOR FRAUD DETECTION

The aim is to build an analytical model predicting a target measure of interest
(fraud lezione 5 )

unsupervised learning techinque can generate new knowledge, i have to find a way to evaualte the result 
Second main category 

we have labels, called **target variable**

not to model average/norm ma to directly predict the variable you have available, you exploit the target. you train your system by making it learn if the target is a particular variable or another

#### regression

In the case of a continuous target variable( it can change ex amount / timestamp) 
time of amount of the next fraudolent transaction 
varies along a predefined interval 

#### classification

we have a categorical target, can be binary or multiclass(we want do discern the different categories of fraud transactions)

depending on the type of target variable you are predicting
we are gonna focus on the binary

**Target variable definition**

Usually the target variable is hard to obtain 
the quality of the final output depends on the quality of the lable we provide 
main problem of applying supervised learning techniques? 
-we have few samples and in between them there are transations that are interesting ( not really fraudolent), we have noise 

A system cannot be based only on supervised learning
we don't have enough data to model our system, this is why they are used together in an active learning system 
COMPLEX ANALYTICAL MODELING EXERCISE

defining the target and understand which is the best model that fit the target variable we want to predict

### linear regression
one of the most usual solution to understand if we are capable to predit a continuous target variable  
model the target variable as a linear combination of the input of your system, weight the single input
combine the input of your system in order to provide a linear combinatin 
we do this obtimazing a property 
minimize the so called **squared error function**
build your linear regression model, compute/predict the target variable and THEN you select the values of the parameter to minimize the error of the prediction 

how you obtain the weights by minimizing 

graphical: finding a linear relation that minimized the sum of all error squares between the distribution of your point and the line you are modelling 
trying to find the best line that allows you to predict the best value of the distribution you are trying to predict

goal: fin the best fitting line that allows you to predict the next value/amount of a transaction 
find the best fit line that can accurately predict the output for the continuous dependent variable with the help of independent variables.


if you try to apply it on NON continuous variable you can have some problems 
transform your line in a x score or a sigmoid ?? 
ypu want to bound between between 0,1 -> probability! 

We pass the weighted sum of inputs through an activation function that can map values in between 0 and 1.
Such activation function is known as sigmoid function and the curve obtained is called as sigmoid curve or S-curve.
 
bounding function? 
logistic regression ? 

"Logistic regression estimates the probability of an event occurring, such as voted or didn't vote, based on a given dataset of independent variables. Since the outcome is a probability, the dependent variable is bounded between 0 and 1."
best line that separetes class 1 and class 2


Linear and logistic regression can be used for variable selection. 
#### Linear regression 
Predicting the **continuous** dependent variable with independent variables.
Find the best fit line to
 -predict the output for the continuous dependentvariable.
 -finds the linear relationship between dependent variable and independent variable.
Based on Ordinary least squares
**Output** : continuous values

#### Logistic regression 
Predict the **categorical** dependent variable with independent variables.
It estimates a linear decision boundary to separate both classes.
Based on the concept of Maximum Likelihood estimation.
Used for
??? Classification
??? Regression 
??? where the probabilities is required.
**Output**: between the 0 and 1.


what about building a model on the basis of the target variable and exploit the grades that this model is assigning to each single feature 
to undestabnd which are the variable ^^ more to the final variable
this can be done with all the supervised method that are undestandable 

each single parameter is telling you the importante of that variable with the respect to the target 
parameter that weights more -> the one we are going to use 
we can also do a statistical test to undestand  from the distribution of your data if the feature is relevant or Not
you are gonna do a staticial test 

**linear regression -> student's t-distribution**
**logistic regression -> chi squared distribution** 

reject the null hypotesis if the estimate coefficent is high in absolute value  compared to its standard error 

### P-Value
p-value rappresents the probability of a getting a more extreme value than the one observed.
low p-value -> SIGNIFICANT VARIABLE
high p-value -> INSIGNIFICAT VARIABLE
We can compare the p-value against a singificance level 


logistic tries to make this separation, how many times can we do this? 

train your model, extract the data, manually see high value
or you can do statically test -> p value -> select or not this feature **(forward, backward, stepwise)**


In general always remember that when you are performing variable selection statistical significance is not the only metric we have to consider
statical can be help, but sometimes you have to consider 
-**interpretability**
Interesting fact: does not only provides the importante of a feature may help you in interpreting the impact of that feature on th final target variable
depending on the sign we can undestand if it produces a decrease or an increase-> 
-**operational efficiency**
-**legal issues**

In general we almways have to find a trade-off good amount of feature and what to keep 

## DECISION TREE 

more powerful than linear-logistic regression 
algorithms based on a tree-like structure- recursive partioning -> fit the distribution of your target variabile in a structure and each node rappresent a test condition of the value of the specific feature
you start from the top node and then you reach the final nodes = leaf nodes
for each node we establish a condition, and depending on the value you split to one brunch or another, until you reach the leaf node where you take the decision 

you use this to undestand if a new sample  is fraudolent or not based on the value of the single feature you are going to encounter by travelling 

algoritms: depending on how you perform the stepwise
-splitting 
-stopping
-assignment 


### Splitting decision 

we have to define a metric - **impurity or caos**
minimal: all elements are good or Not
maximum: half of one type , half of the other type 
you have to understand if the split is giving you an increase or decrease of impurity -> we want to minimize the impurity 
find a way to measure such impurity: ENTROPY or GINI index (they are 0 or 1- maximum when are half/half 0 all related to the 0 or 1 class)
they are totally equivalent
you have to decide how to split and when by choosing the split in terms of decrease in impurity -> gain 
higher gain is preferred !!!! GAIN = DECREASE IN IMPURITY 

you perform this by following a greedy and recursive strategy: take the feature, compute the gain, take the feature, compute the gain, select the one with the best gain 
since you have tree structure you can parallize it 

### Stopping decision

if the tree continuous to split -> overfitting
stop before your model start fit your own distribution 
to avoid:  devide training and validation 

properties: 
you can rappresent every decision tree as a rule set -> set of rules that every the same rules of a decision tree
decision rules 

a decision rule automatically extract features from your dataset 
(we saw this on clustering. at the end we saw decision tree, it was difficutl to understand if a cluster was correct and what was the motivation of that variable in that cluster)
we can now interpret the result of a cluster solution using them as an input of the decision tree-> they are full interpretable 

regression: 
decision tree can be used also to predic the next continuous variable ( target) 
the final output is not a label but a cont variable ( x example a probability )
we have the same functions and the same challenges 
changes: the metrics 

variables that occur at the top of the  TREE ARE MORE PREDECTIVE -> ti da piu informazioni
in base alla risposta mi da una soluzione piu accurata 

they tend to overfit, this decision tre can bee highly dependent on the sample used to construct siuch table 



## NEURAL NETWORK 

generalization of the statistical models  
basic component of a neural network is a logistic regression
logistic and linear regression is a neural network with one neuron 

generalization of a NN-> combination on neurons organized in different layers (MLP)
input layer
hidden layer-> combine different inputs that are offered to the output
output layer 

combine the result of different logistic model based on the same input but but made differently 
ENSABLE of different logistic model combined together and i want an unique result of all these modesl combined together
feature extraction-> this is what i want, different feature for each different hidden layer 
preprocessing in the hidden layer of the neural network 

tranformation function/activation function -> classification or regression 

In the fraud setting? 
you never use network with more than 1 or 2 hidden layers -> capable of approximating any function to any desided degree of accuracy on a compact interval 


(fraud lesson 6 )


NN are able to model complex pattern-> generalization of logistic regression 
Neuron that implement a logistic or linear regression depending on the function 
the function is called activation function
Basic core unit of a NN as a neuron that receive as input the values of the feature of the dataset ( preprocessed) and then you are gonna wakes them with the same paramenter of the logistic function 

weights of the node 
For each single node of a NN you are combining them with different weights 

We generalize such concept and we analyze what is a MLP, just a combination of neurons organized in layer. 
you have an inpout layer, hidden ( feature extractionb layer), and putput layer 
you are creating feature that are combination of the weights 

we can have different activation function 
and even if neuron differ from activation function, you have the same activation function per layer 

When we think about the general usage, whaty happens is that you have to select the number of hidden layers and hidden neurons in the hiddel layer
in fraud we don't have complex patterns, ONE hidden layer is enough to approximate the majority of the function. 

we have to preprocess the data in the correct form, NN appreciates zeros and ones. 

We have to find a way to find the value of the weights, in the NN the job of finding optimal parameters is complex. 
We have to follow an iterative function that minimizes 

Continout -> MSE (mean squared error)
Binary -> Maximum likelihood

start from random weights and then adjsust them using an optimization algorithm 

problem? the cost function it is usually a non convex function, means that may have not a global minimum, if you start from the wrong weights you can fall to the local mimumum?? e quindi??

preliminary training -> start from different set of weights, start the optimization and continue only with the one that gives best intermediate solution 

The optimization procedure then continues until the error function shows no further progress/the weights stop changing substantially(probably reached a minimum)/after a fixed number of optimization steps (Epochs)

more hidden neurons will be required to model the pattern if it is complex ( it is a linear relation between input/output)
how to tune the number of hidden neurons? 
1. Split the data into a training, validation, and test set.
2. Vary the number of hidden neurons
3. Train a neural network on the training set
4. Measure the performance on the validation set.
5. Choose the number of hidden neurons with optimal validation set performance.
6. Measure the performance on the independent test set.
 
Neural networks can model very complex patterns and decision boundaries in the data -> They can even model the noise in the training data -> Overfitting
1?? Option
??? Training set -> estimate the weights.
??? Validation set -> independent data set used to decide when
to stop training and avoid this overfitting. 
2?? Option
Weight regularization: keep weights small in absolute sense to avoid fitting the noise in the data.
??? Add a weight size term to the objective function of the neural network.
 

you relate input/output in a mathematical copmplez way -> black box
you have to find a way of opening it and interpret the results 

this three can be applied to any ML black box
#### 1. variable selection 
undestand the variable that are activately contributing to the output 
in  linear and logistic you have p-value, in NN no p value 
possible solution: is a GRAPHICAL one ( analyzed by humans)-> HINTON DIAGRAMS -> size and color of the square to understand the diagram 
(Performance-driven) Selection: Backward Variable Selection
It does not offer a clear insight into its internal workings. The relationship between the inputs and the output remains nonlinear and complex.

#### 2. rule extraction 
Extract if-then classification rules, mimicking the behavior of the neural network:
??? Decompositional technique: decompose the network???s internal workings by inspecting weights and/or activation values.
??? Pedagogical technique: consider the neural network as a black box and use the neural network predictions as input to a white-box analytical technique such as decision trees
Can essentially be used with any underlying algorithm
 
 The rule sets must be evaluated in terms of Accuracy, conciseness and fidelity that measures to what extent the extracted rule set succeeds in mimicking the neural network. 


### 3. two stage models
1. Estimate an easy-to-understand model first (e.g., linear regression, logistic regression).
a. This will give us the interpretability part.
2. Use a neural network to predict the errors made by the simple model using the same set of predictors.
a. performance benefit of using a nonlinear model.

# Support vector machine 
tries to separate the two different classes 
you have an unique -- is not convex 
extra objective to find the best hyperplane that maximues the distance between the two classes you are analyzing 

you have a quadratic function that has an unique global min 

once you habve minimize thi syou really find the optimal value 

in real world we have nonserparable case -> dataset that contains non separable
mapping between different hyperspace

how to tune it? same procedure we have already seen: 
1. Partition the data into 40%???30%???30% training, validation and test data.(must be indipendent set- no coomon elemtns )
2. Build a SVM classifier for each parameter combination from the set.
3. Choose the combination with the best validation set performance.
4. Build a SVM classifier with the optimal parameter combination on Combined training + Validation data set.
5. Calculate the performance of the estimated classifier on the test set.
 

still a BB, how to interpret it???
-variable selection (backward)
-decomposition rule extraxtion approaches 


# ensemble methods 
Aim at estimating multiple analytical models instead of using only one.

methods that overfit !we use decision tree 

1. aggregating - subsample your dataset + build a classifier 
2. boosting 
3. random forests of decision tree that are built randomly on a random subset of your dataset 
the more randomness the higher performance we are going to obtain 


we built N models, how to evaluate the performance of such methods? 
DO NOT MIX TRAIN VALIDATION AND TEST 

