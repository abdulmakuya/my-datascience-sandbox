### -If you have experience with machine learning? What is your favorite Machine Learning Algorithm? And why?    
Here I would start with the "No free Lunch theorem of Optimization", In which in plain english suggests that No one algorithms fits all/any circumstance.So it depends on the dataset, the question we are trying to answer,the level of accuracy vs. explainability.

But generally speaking I would normally start with regression algorithm (Logistic/linear) and documenting the results I get,I keep doing feature engineering/reduction (by reducing multicolliniarity of the dataset, or choosing most important),Principal Component Analysis and see what is the best result I could with algorithm from these processes.
  
Then I try with decision tree regressor/classifier (depending on the question on table) and see what results I get.I would then step ahead to further advanced algorithm like Random forest,Support Vector Machine or neural networks.
  
 If the results (accuracy score by using train and test data ) dont significantly improve with the increase of algorithm's complexity,then I would finally choose the less complex one.in favour of explainability and the Ocam's Razor rule
  
  Then I try with decision tree regressor/classifier (depending on the question on table) and see what results I get.I would then step 
  ahead to further advanced algo like Random forest,Support Vector Machine or neural networks.
  
  If the results (accuracy score by using train and test data ) dont significantly improve with the increase of algorithm's complexity,then 
  I would finally choose the less complex one.in favour of explainability and the Ocam's Razor rule
  
### Given a problem, how comfortable are you in your ability to analyze the data and build a machine learning solution for problem? 
  I am confident enough,let me elaborate the steps I would pass through
  - Data Cleaning/wrangling
    Check for duplicates,null values,
  - Exploratory Data Analysis (EDA)
    Play around with the data,see the distribution,outliers,
  - Feature engineering/Dimensionality reduction
  - Model Creation
    Import,initialize and fit
    
  - Fine tuning,iterating to improve accuracy score
  
### What are the possible applications of Machine learning and related fields in the real world? *
  Understanding user needs,clusters and behaviour in various scenarios and industries in businesses

### What do you think is the difference between Machine Learning, Artificial Intelligence, and Deep Learning? *
   Artificial Intelligence is any kind of intelligence mimicking natural intelligence but exhibited by a machine,Machine learning is the    process of teaching this machine before it becomes intelligent.

### What are the ethical implications of using machine learning? *
  I think is the proper use and being careful that unintended catastrophic scenarios don't occur. Foristance the scandal on identifying a black person as a gorilla.Also by making data and AI capabilities open so that its not monopolized by a certain entity.
  
### What is the difference between Regression and Classification? *
  Regression refers to problems that output continuous data,foristance we can have a model that predicts someone's height by looking at their gender,race,weight etc.,WHILE regression are the problems that output classes/classify datapoints into groups foristance say whether a fruit is an apple or orange based on the weight and color score
  
### What are the likely challenges of introducing machine learning solutions to real world problems? *
  Overfitting/underfitting and therefore make serious errors,secondly is that we cant always understand or comprehend what has a model do to get the results which it gets,and this explainability is crucial in business decision or life related matters
  
### In the real world, we often have datasets that have missing or corrupted values, how would you deal with that? *
  We start with a process called Data wrangling,in which we try to clean as much as possible.from looking at duplicates,null values in which we might decide to use the central tendencies such as (Mean, Mode and Standard deviation )etc.
  
### What is Exploratory Data Analysis (EDA)? *
  Refers to the process where we play around with the data in hopes of finding some comprehension or insight before hand,say distributions,central tendencies,errors,trends etc.
  
### What do you think are the necessary skills to becoming a successful machine learning engineer? *
  Being curious,and keen to detail.Ability to understand or briefly explain fundamental algebra, calculus, statistics and probability.
Technologically is the basics of  Data structures and algorithms and profiency with any programming language (preferebly python for this case)

### What open source tools in the python ecosystem are crucial to the development of machine learning projects? *
  First and foremost is a proper environment,there fore the anaconda,jupyter lab/notebook and 
  ML libraries like 
- scikitlearn, 
- pandas
- matplotlib
- pip
Dont forget a cup of milk coffee and a favourite smoothie instead of heavy meal..Hahhahh

### Why would a machine learning engineer need to visualize his datasets? *
  Python Data visualization libraries
  like Matplotlib,Bokeh and for high end needs a good Graphics card.
  For live dashboard application they might use somethings like 
  chart.js,d3.js

### What are the advantages and disadvantages of Neural Networks? *
  Neural networks are perfect performing for very huge datasets and ones that keep growing,but the disadvantage comes that it is very complex for a human to explain or comprehend 
  
### Given any standard machine learning problem, walk through the steps you would take to successfully approach it.
- I would start exploring the data,parallel to asking general questions regarding the industry domain.
- Start doing some wrangling,(check for duplicates,null values,outliers)
- Perform feature engineering/Dimensionality reduction/Reduce linear collinearility
- Also I would continue preparing the data by doing feature scaling, standardization, one-hot encoding etc
- Start importing,initializing and fitting ML algorithms starting with simplest to complex (In favor of Occam's Razor )
- Checking for the accuracy score and continue with optimization process.
