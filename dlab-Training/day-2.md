# Explatory Data Analysis Checklist
1. What are the questions we are trying to answer
2. What kind of data do we have
3.
4.
5.


what I did,
1.Install anaconda which comes with jupiter notebook,virtual env,
```python
    import pandas as pd
    df = pandas.read_csv("filename.csv" , sep=";")
    
    df.head() # top 5 by default
    df.shape() # row * columns
    df.info()
    df.describe
    df.iloc # takes you to one specific record,takes in the record number as the variable
    
    df.quality.unique # gives unique value of categorical data [3,5,7,8]
    df.quality.value_counts() # number of frequency for each categorical value
    df.[["ph","residual sugar","quality"]] # return the dataset as seen with only these fields
    
    # Correlation can be done with a correlation matrix,and or correlation plot using a heatmap
    # what are the things that correlate the best
    # what are the things that correlate most with the target
    df.corr() # seeing how fields interact with one another
    
    # Plots and Visualizations 
    # we might need to visualize the data in order to to perfom more explatories
    # correlation plot
    # box whiskers
    # density chart
    # scatter graph
```
Able to ask these questions
1. matplotlib correlation plot
Styling. 
```python
corr = df.corr()
corr.style.background_gradient(cmap='coolwarm')
```
2. matplotlib box whisker plot

