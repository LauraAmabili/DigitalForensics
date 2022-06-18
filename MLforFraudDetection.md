Fraud 3

Machine learning for Fraud Detection 
Analyticts techniques with focus on the fraud practitioner's perspective. 

pefrorm detection 

Real data is typically dirty, full of inconsistencies, incompleteness and duplication, from messy data you get messy analytical models
so we have to apply data filtering mechanisms
first step of data anlyting preprocessing part
data preprocessing step -> 80% of your time
lose a lot of time here, data are pain if you have ever worked with a real dataset

Data-filtering mechanisms must be applied to clean up and reduce the data.
Even the slightest mistake can make the data totally unusable and the results invalid.
 
-transactional data: structured and detailed information captyring the key characteristics of a customer transaction
Summarized over longer time horizons by aggregating it -> they are meaningful when interpreted individually and furthermore their interaction is useful for fraud detectio  and anti money laundering

-types of data elements
continuous data: defined on an interval ( limited and unlimited) 
categorial:all the set of data defined on a category  
  -nominal: no meaniningful ordering between a limited set of data
  -ordinal: meaningful ordering
  -binary: two values 

-sampling: take a subset of historical data to build an analytical model 
we not analyze directly the full data set because the key requirement for a good sample is to be representative fot the future entities 
-> timing and representativeness are crucial. 
Sampling timing and bias-> choosing the optimal time window, but it is a trade off between lots of data that gives you a mor robust analytical model and recent data that are more representative
An average period to get as accurate as possibile a picture of the target population 
Sampling bias should be avoided even if not straighforward
 
Take a subset of historical data to build an analytical model.
With the availability of high-performance computing
why not analyze directly the full data set?
 
  sampling procedure: problem of bias, biased on your decision/selection
  taking a sample is biased by our decision
  a good sample should not be biased 
  model and select sample that target the avaerage period and behavior, i want an average picture
  but this is not an easy task 


what can I do ? 
-build separate models for homogenous time frames or different frames-> complex and demanding solution
-sampling observations over a period covering a full business cycle and build a single model
  a. cost of reduced fraud detection power since less tailored to a particular data frames
  b. less complext and costy to operate

Sampling has a direct impact on the fraud detection power 


adventage of sampling: you have a smaller dataset, faster in creating your model and being ready to update it 
Stratified sampling: a sample is taken according to predefined strata-> 
a. stratifying according to the target fraud indicator-> sample will contain exactly the same percentages of (non-) fraudulent transactions as in the original data
b. stratification applied on predictor variables-> resemble the real product transaction distribution 


# visual data exploration 
-NO PERIODICITY
-time good indicatyor
-distribution good indicator

fraud transaction can be hidden inside usual transaction 


Visual data exploration is important, gives you an initial insights into the data, you can use plots
Then inspect some basic statistical measurements -> calculate them separately for each of the target classes to see whether there are any interesting patterns present 

# exploratory statistical analysis
-basic statistical measurements (averages, standard deviations, minimum, maximum, percentiles)
-basic descriptive statistics
descriptive statistics provide basic insight for the data, they should be assessed together in support and completion of each other
a.MEAN AND MEDIAN
b.VARIATION/STANDARD VARIATION 
c.PERCENTILE VALUES
d.MODE
-specific descritive statistics
. SYMMETRY OR ASYMMETRY OF A DISTRIBUTION -> harder to interpret: limits their pratical use, sometimes it is easier to assess these aspects by inspecting visual plots of the distribution of the involved variables

BENFORDS'S LAW -> visual and numerical data explorastion technique
it describes the frequency distibution of the first digit in many real-life data strategies
based on the idea you can have a metric that express the destribution 
Compare the expected distribution followinf benfords's law with the one provided by the company(with the observed distribution in a data set)
Strong deviation fromn the expected frequencies may indicate the data to be suspicious and manipulated
It can be used as a screening tool for fraud detection
It is a partially negative rule, if the law is not satisfied, then it is probable that the involved data were manipulated and further investigation or tsting is required, 
conversely, if a data set compies, it can be still fraudulent . 
A sufficient amount of data related to an invidudal casa need to be gathered. 


-missing values
Some analytical techniques (e.g., decision trees) can deal directly with missing values. Other techniques need some additional preprocessing.
 a. 
 1. Replace the missing values with a known value
 2. Delete observations or variables with lots of missing values: assumes information has no meaningful interpretation 
 3. Keep missing values since they can be meaningful and may have relation with fraud and nees to be considered as a separate category 
b. Statistically test whether missing information is related to the target variable or not.
1. if yes, then we can adopt the keep strategy and make a special category for it
2. if not, one can depending on the number of observations available- delete or replace


(fraud 4 - 01/04/22 )
-outliers 
extreme observations that are very dissimilar to the rest of the population, can be valid or invalid , unvariate(one dimension) or multivariate(multiple dimensions)
  UNIVARIATE OUTLIER DETECTION AND TREATMENS
  .minimum and maximum values for each of the data elements 
  .graphical tools: 
  histograms, 
  box plot(you rappresent on a scale quartils, first and third, the media and the maximum and minimun, if they are inside the quarttile range- whatever is over is the outliers),
  z-scores ( reducing the outliers to a threshold you are selecting- impose both  LOWER AND UPPER LIMIT ON A VARIABLE AND ANY VALUES BELOW/ABOVE ARE BROUGH BACK Of these limits )
  compute the distribution, represent it on an istogram 
  if inside the range, plot all the data on this line, you compute statistics on your data, then you plot the rane first/last quartile-> how much of your data is inside this area
  ho wmany stanrdard deviation an observation lies away from the mean-> you check for each single instance how much differs from the media in terms of standard deviation 

  MULTIVARIATE OUTLIER DETECTION AND TREATMENS (now you are considering multiple features at the same time )
  fit the features in a multidimensional space -> can be seen as a vector
  -distance between different vectors
  .fitting regression lines and inspecting the observations with large errors
  .clustering or calculating the Mahalanobis distance




-variouys schemes exist to deal with outliers 
  .for invalid observations one could treat the putlier as a missing value
  .for valid obs impose both a lower and upper limit on a variable and any values below/above are brought back to these limits -> they are information that we don't want to loose
   Truncation example 


Not all invalid values are outlying and may go unnoticed if not explicitely looked into
Construct a set of rules formulated based on expert knowledge 
find relation you know must be present in your dataset
constraint that apply to the combination

take explicit precautions

theser kind of inconsistences can by find by experience

# PREPROCESSING 

extremly careful to treat these values, you have to ducment by addign a feature that specify because 
it is missing a valueif you start a preprocessing in the wrong way you cannot be more able to detect the anomaly 


another problem: represented by this image : INSERT image
compare two value of your dataset -> the distance ( eucledian, manhattan..)
the problem of this computation is that it is not correct ? 
The scale are differt!!! doesn't make any sense 
u have to standardize your features !!


## standardize data-> 
scaling variables to a similar range
-mix/man standardize ( max and min of the current distribution and rescale everything based on that)
-z-score (calculate che z scores, compute min, compute standard deviation, keep the distance )
-decimal scaling (divide by 10 to put all the features in the same scale)

## Categorization 
Additional information about the domain, sometimes you want to add to the dataset some knoldegne that directly derive from of the domain you are analyzing 
some times you have also continuous variables, and uoi have to study the slot of the c variables and defining when there is a change  in the slot (increase, dcrease, ioncrease) 
depending on the data you may want to extract different informatio that can be useful -> but you are adding complexity, adding feeatures to te original one that must be treated

## Variable selection 
problem automatically solved by random forest alghoritms, they learn the feature important to you, but in another case you don't want to spend complexity and add features to your model 
this is a problem cause sometimes the dataset has a huge amount of features, and in the end only few of them are really helpful-> 10/15 variables


## filters
are a very handy variable selection mechanisms
allow a quick screening of which variable should be retained
depending on the type of the variable and the type of target variable  you can select a different statistic test that measure the correlation between the target and the variable
PEARSON correlation
additional metodology to analyze the correlation
Filters allow reduction in the number of dimension of the data set early in the analysis 

Drawback: work univariayely and do not consider correlation between the dimensions individually


sometimes you cannot use all the feature 
the motivation may contain personal information 
feature seletion independent from your decision 

## PCA 
PRINCIPAL COMPONENT ANALYSIS
group of methods to automatically reduce the dimensionality of your dataset and at the same time finds a set of feature not correlated with each other
you are able to reduce, select feature that you want and the feature are not correlated

reduce dim by forming new value that are a linear composition of the original ones (main component) 
at maximum the same number of the original ones 
only a small portion of your variable contains the information you need 

the info contained in the original data set can be summerixzed by a limited number of components 


find two new features that try to better describe the distribution of the data in the space
 PC1 will describe the set of data in a way that you can continue the analysis
 they are ortogonal-> not correlation between of them 

 ## correlation and stability 
 assure that your model will be stable
 when we analyze the stabiltu we refer to correlation between variables

 it means that when you have to select the feature, the most important one, you have to check that they are not correlated, otherwise 
 the model is not stable -> we achieve bad result 


if you apply PCA-> your model will be stable

should we apply PCA always? 

qith pca you loose the interpretability of the features 
trade-off: PCA if your are not interested in interpretaibility 
the problem is that interpretability is one of the key aspect /parameter to evaluate the effectivness of a fraud detection methods
everything has to be evaluate at the end by an human 
if you need to have a score easy to investigate/interpret, you have to avoid PCA


# DESCRIPTIVE ANALYTICS FOR FRAUD DETECTION
## unservised learning techniques -> descriptive anaytocs for fraud detection 
unsupervides aims at finding anomalos behavior that deviates from the norm of the dataset
you have to define the norm ( average behiuour of dataset of customer/ or behavior of the average customer)

unsupervised , you can identify from know cyber attack 

you want to identiy an outlier detection

techiques relevant when you have NO labels!
fraudsters is dynamically adapting, organization is at the beginning 



define your norm, define the AVERAGE behavior of your dataset 
find a way to model an average behavior

the norml depends on the domain you are analazing 
when you define a norm you are defining the boundering of whay is normal and what is not 


since it is unsupervised, what ever you find is knowledgne that canbe related or Not


procedure similar for outliers in preprocessing, you can canalyze them in one or multi dimension 
disadvantges: less formal and limited to a few dimensions, require active involvement of the end user, for a sarge dimensional data set, is cumbersome



knowledge to verify what you have found

1. statistical outlier detection 
-> z-score
-fit a distribution 
these two are the same saw before
-> break point analysis

intra-account fraud detection method -> break point indicates a sudden change in the behavior
a. define a fixed time window
b. split into an old and new
c. you compare them 
detect if there is a change in the behiavour and study the difference, if it is higher than a threshold you set, you start investigate
(see slide) 
training part and testing part 
studying the difference -> find something that needs to be investigated
->peer-group
INTER-account techiques
group of account that behaves similarly, elements in your dataset that are close together,  when the behaviour deviates from the peer created, anomaly 
a. peer group identification
  -distance 
  -ask experts
  -select number of peers is a problem (tto many all the dataset, depends on the locality of the model you want to build)
b. anomaly valuation
-> association rule analysis 
detect frequently occurring relationship between items
association  between two different items in the dataset
 you define association rule X sub set of items and Y subset of items-> statoistical measure of the strengh 


 INSURANCE FRAUD EXAMPLE 
 Goal: find frequentelly occurring relationships/associations rules between the various parties involved. 
compute a set of statistics
1. identify frequenty item strategies
suppert(X) -> percentage of total transactions in the database that containts the item set 
2. derive association rules -confidence- strong enough to be considered
confidence(X->Y)







FRAUD DETECTION

in the previuour lecture we explodred the unsupervised, the main difference with rw supervised 
you don't have any label related to the custom value you want to predict/classify
we have to extract the norm
main challenge of unsupervised-> anomaly DETECTIONyou want to detect something that is outling with the norm itself
allows you to extract knowledge
started from graphic techniques-> something that outlies from the nrm, group of points
statistical: this time exploiting statistical techniques
-break point: intraaccount , you decide testing window and you test if the new distribution is similar to the preboous one
-peer-group, seasonality, data that change during time 
-


# CLUSTERING
-> main unsupervised learning technique
summarize adv and dis of unservised 
split your data into group such that you want to max similraty intragroup and difference betweek element from different groups


process that requiresa a good amount of data
group data in different set 
if you have a lot of fetures apply feature selection 
norm: big cluster of data 
anomalies: small cluster that is away from the normal 
this is what you want them to analyze to understand it it is frudolent or Not

this single ^^ anticipates one of the main challenge of clustering, a super good tipycal result is in this example
the interesting fact about clustering it works -> you are gonna pobtain cluster in any change
the change is to find a way to understand if the cluster is meaningful or not, if it is relevant


final result of clustering technique-> something that was not relevant 


Clustering techniques can be devided in Hierarchical and nonhierarchical
Hierarchical you have: agglomerative/divisive 
NON Hierarchical: 


core element of clustering techiques: distance matric!!

Aim of clustering: group observation based on similarity 
distance metric is needed to wuantify similarity !
in order to cluster element you have to compute the similarity between two elemnt 
-euclidea,/minkowski(depending on the parameter you may obtain a manhattan or euclidean) -> be careful you want to standardize


for continuois variables ok -> euclidian, pearson correlation or cosine measure 
categorical variables -> binary variables, zero or one depending on if this particular features is present or not in your data
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


## Clustering Hierarchical 
Divisive and agglomerative depending on how you perform the clustering
Divisive: you start by considering all the elemnts inside your dataset as beyond one single còluster  and then you start analyzing the similarity between the elements to split them until you reach one element
Agglomerative: you assign one single cluster to each element, compute similarity and you start group them 

Distance between clusters -< different methods (you can call a library in python)

single: most closest point 
complete: defined by the distance between the two most different
average: all the points
centroid: the mean 

Final result will be something in between the two step, find different result and test them 

main problem of distance: not efficient, you have to visit the entire dataset 

NUMBER OF CLUSTERS 
-dendogram: keep track of all the possible merge, and put in a diagram the distances 
-screen plot: 

if have comunque to decide if it is correct or not 
using a different technique would result in a different result , why? 
_____ non ho capito so solo che succede se tipo uso complete invece di average


hierarchical -> advantage: number of cluster does not need tobe specified, allows to cluster data without knowing a priori the number of cluster to select 
Disadvantage: they do not scale at all, the higher the amount of data, the higher the computation 
the interpretation of the cluster is often subjective -> you have to have an expert that evaluates your result


## Clustering Non Hierarchical 
basic techniques that can be used, the nmber of features are not so used and i want something that can be interpret by an analyst 
K-MEANS: 
aopply each observations to the closest centroid 
step 2: recompute centroids 
reassign observation 


continue until k into distributoion or after a limit number of iterations

disadvantages: you have to know the number of clusters ! (or you have to try all the possible combinations )
the final result depend on where you put the position of centroid (on where you put the centroid)


SOM (self organizing maps) 
NN that has only two layer ( input and output layer) 
Allows to visualize and cluster high dimensional data on a low-dimensional grid of neurons 
each inpout is connected to the all possibile outputh with a set of weights 
BMU most similar vector of the input you have provided on the basis 
we select the BMU 
once we have selected it we are going to update all the weights to match the best matchin until
try to map all the neibg to the distribution of your original dataset 


iterative procedure
1.compute the BMU that is the most similar vector to the input that you have porovided on the basis of the euclidian distance 
2. update all the wights in order to match the BMU -> stretch to fit as much as possible the original distribution 

you will have a stable solution at the end 
a lighet part  / darker part will rappresent clusters 


## semi-supervised clustering 

put constraints on how you are going to cluster elemtns inside your data 
put labels or minimun distance between particular pairs of elements-> procedure easier and faster
you are guding the cluster procedure
this can be done when you have information provided bu experts

you are going to label all your istrances with already a preformed cluster that you know from a precedent knowledge


One-Class SVM 

try not to cluster your data in different group, theu try to distinguish what is the norm to what is a outlier 
they try to do this by trying to rappresent your data in a two dimensional space and find the best hyperplane 


PAINFUL PART NOW !! yay 
it is difficult to understand if final result is good or not, try multiple things to understand 

best solution: statistical measure
compute intersimilarity/intra 
or SSE (iterate between different solutions)

or the other solution is to manually analyze final output and block the characteristic we have obtained. 


final result of cluster technique is a label dataset (final data is a cluster to which each single labelbelong ??)-> use the output of the unsupervised (cluster)and train a supervised on the basis og the label of the cluster technique 
-> interpret the result! 

# Predective analytics for fraud detection 

(fraud lezione 5 )

unsupervised learning techinque can generate new knowledge, i have to find a way to evaualte the result 
Second main category 
we have labels, called target variable
not to model average/norm ma to directly predict the variable you have available, you exploit the target. you train your system by making it learn if the target is a particular variable or another 
-regression

In the case of a continuour target variable( it can change ex amount / timestamp) 
time of amount of the next fraudolent transaction 


-classification

we have a categorical target, can be binary or multiclass(we want do discern the different categories of fraud transactions)

depending on the type of target variable you are predicting


we are gonna focus on the binary
Usually the target variable is hard to obtain 
the quality of the final output depends on the quality of the lable we provide 
main problem of applying supervised learning techniques? 
-we have few samples and in between them there are trans that are interesting ( nit really fraudolent), we have noise 

A system cannot be based only on supervised learning
we don't have enough data to model our system, this is why they are used together in an active learning system 
deploung: COMPLEX ANALYTICAL MODELING EXERCISE

defining the target and understand which is the best model that fit the target variable we want to predict

one of the most usual solution to undestand if we are capable to predit a continuous target variable -> linear regression 
model the target variable as a linear combination of the input of your system, weight the single input
combine the input of your system in order to provide a linear combinatin 
we do this obtimazing a property 
minimize the so called squared error function
build your linear regression model, compute/predict the target variable and THEN you select the values of the parameter to minimize the error of the prediction 

how you obtain the weights by minimizing 

graophical: finding a linear relation that minimized the sum of all error squares between the duistribution of your point and the line you are modelling 
trying to find the best line that allows you to predict the best value of the distribution you are trying to predict

goal: fin the best fitting line that allows you to predict the next value/amount of a transaction 

if you try to apply it on NON continuous variable you can have some problems 
transform your line in a x score or a sigmoid ?? 
ypu want to bound between between 0,1 -> probability! 
bounding function? 
logistic regression ? 
"Logistic regression estimates the probability of an event occurring, such as voted or didn't vote, based on a given dataset of independent variables. Since the outcome is a probability, the dependent variable is bounded between 0 and 1."
best line that separetes class 1 and class 2


Linear and logistic regression can be used for variable selection. 
what about building a model on the basis of the target variable and exploit the grades that this model is assigning to each single feature 
to undestabnd which are the variable ^^ more to the final variable
this can be done with all the supervised method that are undestandable 

each single parameter is telling you the importante of that variable with the respect to the target 
parameter that weights more -> the one we are going to use 
we can also do a statistical test to undestand  from the distribution of your data if the feature is relevant or Not
you are gonna do a staticial test 

linear regression -> student's t-distribution 
logistic regression -> chi squared distribution 

reject the null hypotesis if the estimate coefficent is high in absolute value  compared to its standard error 

p-value rappresents the probability of getting the same value ??? no 

logistic tries to make this separation, how many times can we do this? 

train your model, extract the data, manually see high value
or you can do statically test -> p value -> select or not this feature (forward, backward, stepwise)


In general always rremember that when you are performing variable selection statistical significance is not the only metric we have to consider
statical can be help, but sometimes you have to consider 
-interpretability 
Interesting fact: does not only provides the importante of a feature may help you in interpreting the impact of that feature on th final target variable
depending on the sign we can undestand if it produces a decrease or an increase-> 
-operational efficiency 
-legal issues 

In general we almways have to find a trade-off good amount of feature and what to keep 

# DECISION TREE 

more powerful than linear-logistic regression 
algorithms based on a tree-like structure- recursive partioning -> fit the distribution of yoru target bariabile in a structure in each node rappresent a test condition of the valueof the specific feature
you start from the top node and then you reach the final nodes = leaf nodes
for each node we establish a condition, and depending on thevalue you split to one brunch or another, until you reach the leaf node where you take the decision 

you use this to undestand if a new sample  is fraudolent or not based on the value of the single feature you are going to encounter by travelling 

algoritms: depending on how you perform the stepwise
-splitting 
-stopping
-assignment 


SPLITTING DECISION 
me have to define a metric - impurity or caos 
minimal: all elemnts are good or Not
maximum: half of one type , half of the other type 
you have to undestand if the split is giving you an increase or decrease of impurity -> we want to minimize the impurity 
find a way to measure such impurity: ENTROPY or GINI index (they are 0 or 1- maximum when are half/half 0 all related to the 0 or 1 class)
they are totally equivalent
you ahve to decide how to split and when by choosing the split in terms of decrease in impurity -> gain 
higher gain is preferred !!!! GAIN = DECREASE IN IMPURITY 

you perform this by following a greedy and recursive strategy: take the feature, compute the gain, take the feature, compute the gain, select the one with the best gain 
since you have tree structure you can parallize it 

STOPPING DECISION 
if the tree continuous to split -> overfitting
stop before your model start fit your own distribution 
to avoid devide training and validation 

properties: 
you can rappresent every decision tree as a rule set -> set of rules that every the same rules of a decision tree
decision rules 

a decision rule automatically extract features from your dataset 
(we saw this on clustering. at the end we saw decision tree, it was difficutl to understand if a cluster was correct and what was the motivation of that variable in that cluster)
we can now interpret the result of a cluster solution using them as an input of the decision tree-> they are full interpretable 

regression: 
decision tree can be used also to predic the next coninous variable ( target) 
the final output is not a label but a cont variable ( x example a probability )
we have the same functions and the same challenges 
changes: the metrics 

variables that occur at the top of the  TREE ARE MORE PREDECTIVE -> ti da piu informazioni
in base alla risposta mi da una soluzione piu accurata 

they tend to overfit, this decision tre can bee highly dependent on the sample used to construct siuch table 



# NEURAL NETWORK 
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
the function is called act func 
Basic core unit of a NN as a neuron that receive as input thevalues of the feature of the dataset ( preprocessed) and then 
you are gonna wakes them with the same paramenter of the logistic function 

weights of the node 
For each single node of a NN you are combining them with different weights 

We generalize such concept and we alyze what is a MLP, just a combination of neurons organized in layer. 
you have an inpout layer, hidden ( feature extractionb layer), and putput layer 
you are creating feature that are combination of the weights 

we can have different activation function 
and even if neuron differ from activation function, you have the same activation function per layer 

When we think about the general usage, whaty happens is that you have to select the number of hidden layers and hidden neurons in the hiddel layer
in fraud we don't have complex patterns, ONE hidden layer is enough to approximate the majority of the function. 

we have to preprocess the data in the correct form, NN appreciates zeros and ones. 

We have to find a way to find the value of the weights, in the NN the job of finding optimal parameters is complex. 
We have to follow an iterative function that minimizes 

Continout -> MSE
Binary -> Maximum likelihood

start from random weights and then adjsust them 

problem? the cost function it is usually a non convex function, menas that may have not a global minimum, if you start from the wrong weights you can fall to the local mimumum?? e quindi??

preliminary training -> start from different set of weights, start the optimization and continui only with the one that gives best intermediate solution 

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
1° Option
● Training set -> estimate the weights.
● Validation set -> independent data set used to decide when
to stop training and avoid this overfitting. 2° Option
Weight regularization: keep weights small in absolute sense to avoid fitting the noise in the data.
● Add a weight size term to the objective function of the neural network.
 

you relate input/output in a mathematical copmplez way -> black box
you have to find a way of opening it and interpret the results 


this three can be applied to any ML black box
1. variable selection 

undestand the variable that are activately contributing to the output 
in  linear and logistic you have p-value, in NN no p value 
possible solution: is a GRAPHICAL one ( analyzed by humans)-> HINTON DIAGRAMS -> size and color of the square to understand the diagram 
(Performance-driven) Selection: Backward Variable Selection
It does not offer a clear insight into its internal workings. The relationship between the inputs and the output remains nonlinear and complex.

2. rule extraction 
Extract if-then classification rules, mimicking the behavior of the neural network:
● Decompositional technique: decompose the network’s internal workings by inspecting weights and/or activation values.
● Pedagogical technique: consider the neural network as a black box and use the neural network predictions as input to a white-box analytical technique such as decision trees
○ Can essentially be used with any underlying algorithm
 


3. two stage models


# Support vector machine 
tries to separate the two different classes 
you have an unique -- is not convex 
extra objective to find the best hyperplane that maximues the distance between the two classes you are analyzing 

you have a quadratic function that has an unique global min 

once you habve minimize thi syou really find the optimal value 

in real world we have nonserparable case -> dataset that contains non separable
mapping between different hyperspace

how to tune it? same procedure we have already seen: 
1. Partition the data into 40%⁄30%⁄30% training, validation and test data.(must be indipendent set- no coomon elemtns )
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
