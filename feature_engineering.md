```python
# map,applymap,Series.str.extract,and applying the whole formula to a column
# Regular expressions for Title capturing and mapping to pre-defined titles

titles = {
    "Mr" :         "Mr",
    "Mme":         "Mrs",
    "Ms":          "Mrs",
    "Mrs" :        "Mrs",
    "Master" :     "Master",
    "Mlle":        "Miss",
    "Miss" :       "Miss",
    "Capt":        "Officer",
    "Col":         "Officer",
    "Major":       "Officer",
    "Dr":          "Officer",
    "Rev":         "Officer",
    "Jonkheer":    "Royalty",
    "Don":         "Royalty",
    "Sir" :        "Royalty",
    "Countess":    "Royalty",
    "Dona":        "Royalty",
    "Lady" :       "Royalty"
}

extracted_titles = train["Name"].str.extract(' ([A-Za-z]+)\.',expand=False)
train["Title"] = extracted_titles.map(titles)

extracted_titles = holdout["Name"].str.extract(' ([A-Za-z]+)\. ',expand=False)
holdout["Title"] = extracted_titles.map(titles)

train["Cabin_type"] = train["Cabin"].str[0]
train["Cabin_type"] = train["Cabin_type"].fillna("Unknown")

holdout["Cabin_type"] = holdout["Cabin"].str[0]
holdout["Cabin_type"] = holdout["Cabin_type"].fillna("Unknown")

for column in ["Title","Cabin_type"]:
    train = create_dummies(train,column)
    holdout = create_dummies(holdout,column)
    
    
#collinearity. Collinearity occurs where more than one feature contains data that are similar.
#The effect of collinearity is that your model will overfit - you may get great results on your test data set, but then the model #performs worse on unseen data (like the holdout set).

#As a result, when we created our two dummy columns from the categorical Sex column, 
#we've actually created two columns with identical data in them. This will happen whenever we create dummy columns, 
#and is called the dummy variable trap. The easy solution is to choose one column to drop any time you make dummy columns.
