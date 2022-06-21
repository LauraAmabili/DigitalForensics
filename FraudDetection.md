# Fraud Analysis and Detection 



## Fraud detection 
#### 17/03/2022 Fraud lection 1 

what is a fraud? 
criminal activity-> criminal or wrongful deception intended to result in financial or personal gain. 
main driver of the frods. If we use this definition to understand 

fraud is an uncommon, well-considered, imperceptibly concealed, time-evolving and often carefully organized crime. 
These 5 are the main challenges you have to cope with. 
It is not an isoleted phenomena, it is a social phenomenal, it comes to expenses of the victim. 
Who is the victim? organization, person, society. 

UNCOMMON: only a minority of cases concerns fraud, of which only a limited number will be known to concern fraud. 
Only a minority of the cases in your datased concern fraud, only a small percentage of your dataset is related to the class fraud. 
but, besides that, of this part, only a limited number will be known to concern fraud. Some of them may be not detected, but they are in your dataset. 
You will have to exploit as much as possible these few. 
-detect fraud is difficult: fraudulent cases are covered by the legitimate ones.
-learn from historical cases is difficult: since only few examples are available. 

WELL-CONSIDERED AND IMPERCEPTIBLY CONCEALED: the attacker tries to blend in the legitimate one. 
Fraudsters try to remain unnoticed and covered, blend in frauds, not behave different from non-fraudsters.
Fraudsters hide very well by well-considering and planning how to precisely commit fraud. Frauds are not impulsive and unplanned. 
mimic attacks, the attacker tries to mimic the behave of the user. 
frauds that evade from detection systems. 

TIME-EVOLVING: fraudsters adapt and refine their methods to remain undetected. Fraud detection systems improve and learn by example. 
The adversary is always one step further. Fraudsters techniques evolve in time along with or better ahead of fraud detection mechanisms. 

CAREFULLY ORGANIZED CRIME: every single fraud cases is not an isoleted event. 
Fraudsters: do not operate independently, involve complex and organized structures. To detect fraud the context should be taken into account. 


why do people commit fraud: 
Basic driver: potential monetary gain or benefit. 
-MID or GRiD: difficult financial situation, financial gain.
Fraud triangle: basic conceptual model that presents the factors that explain the drivers for an individual to commit fraud. 
-Rationalisation, opportunity, motivation -> we have to reduce the opportunity driver. 

Fraud categories: 
Banking and credit card: one of the most done, economic motivation. Unauthorized taking of another's credit. 
1. create fake personal information and steal much money possible, steal from a financial istritution
2. obtain data of the bank account of an user and perform fraud

Insurance fraud: 
1. sell fake insurance
2. exploit some condition to earn money

Corruption: 
The misuse of entrusted power for private gain 

Counterfeit: imitate intended to be passed off fraudulently or deceprively as genuine-> concerns valuable objects. 

Product warranty fraud: fraudulently claiming compensation or remuneration based on a product warranty. 

Healthcare fraud: filing of dishonest healthcare claims to make profit.
Telecommunications fraud: phishing, scamming, cloning, superimposition fraud. -> super easy to exploit, no phisical attack. Just the voice. 
Money laundering: criminal activity and make them appeal as legal. 
Click fraud: legal links on a website in order to add the number of clicks. 
Identity theft. 
Tax evasion. 
Plagiarism. 

Frauds impacts -> need to invest up to date defense infrastructures. 

## ANTI-FRAUD STRATEGY 

These mechanisms aim to reduce the losses since the frauds are prevented and dected and fraudsters tend to look for easy target 

Fraud prevention ( recognize or discover fraudulent activities-ex-post) 
Fraudsters adapt and change their behavior
The most effective ways to deal with the problem of fraud is to adopt methods that will decrease motive, restrict opportunity
and limit the ability for potential fraudsters to rationalize their actions.

and fraud detection(avoid or reduce fraud-ex-ante)
A fraud detection strategy should involve use of analytical and other procedures to highlight anomalies, 
and the introduction of reporting mechanisms that provide for communication of suspected fraudulent acts. 

An anti-fraud strategy main components: 
-preventuion
-detection
-deterrence
-response

-Expert-based approach: approach built on the domain knowledgne of the fraud analyst. 
Involves a manual investigation of a suspicious case. 
It may find a mechanisms- requires a detailed investigation to understand and address the new mechanism. 
The comprehension of the fraud mechanisms allows extending the fraud detection and prevention mechanisms. 

-->rule-based engine
Rules describing previously detected fraud patterns that are applied to future transactions and trigger an alert when a fraud may be committed. 
You have to keep the rule base lean and effective. Rule based engine must continuously monitored, improved and updated to remain effective. 
disadvantages -> expensive to build, require manual input, difficul to maintain and manage 
fraudsters can learn the rules and circumvent them, new fraud patterns are not automatically updated


Expert-based relies on human expert input, evaluation and monitoring

-Automated fraud detection systems: however expert based remain important to build an effective system
Requires less human involvement, could lead to a more efficient and effective system 
first expert based -> then automated 

### FRAUD MANAGEMENT: 
all the activities that must take place after a fraudolent activity has been detected and confirmed 

-corrective measure: resolve and correct the consequencies. 
Actions to retrospectively detect and subsequently address similar fraud cases. 
Retrospective screening
  -asses the impact of the newly dected type of fraud
  -resolve, by means of corrective measures, fraud cases. 
The sooner corrective measures are taken and fraud is detected, the more effective such measures are and the more losses can be avoided. 
-preventive: to prevent
Actions that aim at preventing future frauds, making the organization more robust and less vulnerable
Typical process: 
1. investigate the fraud case to understand the underlying mechanisms. 
2. Extend the available expert knowledge with the discovered mechanisms. 
3. Adjust the detection and prevention system. 


step futher-> automatated base -> frauds becomes easier to detect the more time has passed. 
the more time passed, the more a fraud mechanisms is used, if a fraud is done and it is not detected, it will be done again. 
the more data you have the more you can build systems 

the more a fraud schema is used , the more easier to detect it is if time has passed
fraud paterns becomes more apparent, statistically easier to detect


### DATA DRIVEN FRAUD DETECTION

like any other security mechanisms, there is a cost of operating 
if a label is correct and you are reducing the loss, if the label is not correct: you have labeled as fraud a legit transaction
for every false positive you have a cost same for every false negative
but we cannot really investigate every transaction
in general we have a limited invastigation capacity

Organizations have a limited investigation capacity, so a shift is taking place toward data-driven or statistically based fraud-detection systems
a. precision 
    Increased detection power wrt classic approaches, produces massime volumes of information to uncover frauds that are not apparent to the human eye. 
    The goal is to make optimal use of the limited investigation capacity and maximize the fraction of fraudulent cases among the inspected ones + the detected amount of frauds 
b. operational efficiency 
c. cost efficiency 
    Automated data-driven approaches are complaint with stringent operational requiremens 
d. growing amount of interest 
    This increasing awareness and attention for fraud is likely due to negative social and financial impact.
    Leads to growing investments and research, both from academia, industry, and government.
 

## FRAUD-DETECTION TECHNIQUES
Approcahes are adopting powerful statistically-based methodologies and analyzing massive amounts of data
fraud remains hard to detect because is a dynamic phenomenon. 

Why it is challenging to detect fraud? 
fraudsters adapt theirs approaches to commit fraud without being exposed, probe fraud detection and prevention systsmes to understand their functioning to discover their weaknesses
Fraudsters develop advances strategies to cover/blend in their tracks to avoid being detected 
There is the need for new techniques that are able to detect and address stealthy patterns. 


#### 18/03/2022 Fraud lection 2 


unsupervised learning techniques-> 
They do not require labeled observations, Find behavior that deviates from normal one

learn from historical observation, allow detecting novel fraud patterns 
detect the difference between the norm and the fraudulentcases


supervised learning techniques-> 
Learn from historical observations to retrieve patterns!! that allow differentiating normal and fraudulent behavior



limitation of supervised: impossible to see the future, supervised is a train of historical previous cases
higher number of false negatives 
They need historical examples to learn from ( labeled data!)

supervised look inside the huge amount of data 
unserivised: how they behave. 
extract features from data 
such kind of systems are not enough , complement the system with supervised.

chain and combination between the system ->active learning systme: combination of supand unserivised fed with the feedback of an analyst of a group who is continously improving your system

un vs sup .> you want to apply unservised every time you have a data set but not labeled
supervaside data with label legitimed and unlegitimed -> predict, detect and estimate some features
limitation of supervised learning techiques: is it not enough 
start knownladge from the domain 
antifraud detection system I have to consider the information I have available
start with unsupervised learning that extract novel patterns, once you have the investigation of the anaylist you start with data from the past, find pattern and then supervised 

All these systems must be used in a complementary way. 

Besides that, since frauds are not an isoleted fenomena, we want to exploit the domain, for exampole we want to consider social network analysis, 
trying to buiold graphs on the entity evolving payment to undestand if there are patters. 
If there is a opatern used or exploited by fraudsters. 

Developing a fraud detection system:
a. expert based rule engine
b. unsupervised learning systems
c. syopervised learning systems 

## FRAUD MANAGEMENT CYCLE

Fraud detection -> detect it 
Fraud Investigation: every thing flagged as fraud must be investigate by humane EVERY TIME, in order to check if it is a really fraud or not, it's important, allows to understand the knowledgne to use for automated systems
Fraud Confirmation: not, ok this is not fraudolent, change the label, retrain your system, unless put and conferm the label and go on 
Fraud Prevention : now we have to prevent these transaction

feedback loop-> you have to automatize all these process and we will automatize this process-> you have to update all your models and systems (the supervised and unsupervised to mathc the new pattern) 
the preprocessing step is the step that occupies the 80% of your time 

Regular update of the model->. 
regulare update of the model is recommendable given the dynamic nature of fraud. 
The frequency of retraining or updating the detection model depends on several factors:
○ The volatility of the fraud behavior.
○ The detection power of the current model.
○ The amount of (similar) confirmed cases already available in the database.
○ The rate at which new cases are being confirmed.
○ The required effort to retrain the model.
Reinforcement learning = continuously updates the detection model by learning from the newest observations

Example -> outliers at the data time level, allow detecting abnormal or anomalous behavior and/or characteristics in data set which may occur at the data item level or the data set level. 
With a label that indicates wheter a transaction was fraudulent -> predictive analystics that classify an instance as being fraudulent or not-> but it is important to generalize
not fitting only in a model. 


## FRAUD ANALYTICAL PROCESS

iterative, if you encounter a problem you have to go back to another 
1.identify data sources: depends in which domain you are going to work 
2.select the data, store in a consistend way 
3.clean the data -> issue
4.transform the data-> ML model wants the data in a particular form ( numerical and categorical into something that can be treated)
5.analyze -> interpret and evaluate 


Analyzing output 
The analytical model is estimated on the preprocessed and transformed data. The actual fraud-detection model is built. 
what is the minimal requirement of your system? 
in the end you may want to detect something that was not initial in the dataset 

Possible analysis output
-trivial fraudulent patterns
-unknown patterns 

Once the analytical model has been appropriately validated and approved, it can be put into production.
 

successful fraud analytics model ->
### statistical accuracy-> 
detection power and corrrectness of the statistical model in flagging suspicious cases 
we need to make sure the model generalized well and is not overfitted to the historical date set 
### interpretability-> 
since the output must be investigated, you want to have an outout that is understandable by the human- WB/BB interpretability depends on the technique used 
### operational efficiency->  cases are evaluated in real time. Operational efficiency is crucia
fraud managment -> RISK 
( statistical and economical evaluation of the exposure to damage because of the presente of vulnerabilities and threats) 

security vs cost balance
Direct costs
● Management
● Operational
● Equipment
Indirect costs (more relevant)
● Less usability
● Slower performance
● Less privacy (due to security controls) 
● Reduced productivity (users are slower)
### economical cost-> 
developing and implementing a fraud detection model involves a significant cost to an organization -> cost-benefit analysis
### regulatory compliance: 
there are soe data that you cannot analyze due to the legislations and normatives. You lose the correspondence between user-transaction. 


Challenges of developing fraud-detection models 
The challenges are not only for the ML tasks, but also in the domain you are analyzing. 

-Dynamic nature of fraud, frauds are dynamic in nature, they continue to evolve
-Accuracy you will have to achieve a high detection rate, but it is a direct cost of the bank 
be careful about the costs 
-SKEWNESS of the data: frauds are uncommon, you have to find techniques that balance your dataset 
-The system must be scalable, able to analyze huge amount of data

In the end, a fraud detection prevention system has the final goal of extraxcting novel knowledge -> red flags of fraud
The knowledgne that you extract that allows you to understand and interpret fraudolent pattersn. 


