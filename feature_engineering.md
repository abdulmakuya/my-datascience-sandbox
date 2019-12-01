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

#Another way apart from using the coefficients from logreg,to select the most important features,
#we can also use a method called Recursive Feature Selection Cross Validation (RFSCV) which he RFECV class starts by training a model #using all of your features and scores it using cross validation. It then uses the logit coefficients to eliminate the least important #feature, and trains and scores a new model. At the end, the class looks at all the scores, and selects the set of features which #scored highest.


from sklearn.feature_selection import RFECV

columns = ['Age_categories_Missing', 'Age_categories_Infant',
       'Age_categories_Child', 'Age_categories_Young Adult',
       'Age_categories_Adult', 'Age_categories_Senior', 'Pclass_1', 'Pclass_3',
       'Embarked_C', 'Embarked_Q', 'Embarked_S', 'SibSp_scaled',
       'Parch_scaled', 'Fare_categories_0-12', 'Fare_categories_50-100',
       'Fare_categories_100+', 'Title_Miss', 'Title_Mr', 'Title_Mrs',
       'Title_Officer', 'Title_Royalty', 'Cabin_type_B', 'Cabin_type_C',
       'Cabin_type_D', 'Cabin_type_E', 'Cabin_type_F', 'Cabin_type_G',
       'Cabin_type_T', 'Cabin_type_Unknown']

all_X = train[columns]
all_y = train["Survived"]
lr = LogisticRegression()
selector = RFECV(lr,cv=10)
selector.fit(all_X,all_y)

optimized_columns = all_X.columns[selector.support_]

optimized_columnsIndex (<class 'pandas.core.indexes.base.Index'>)
Index(['SibSp_scaled', 'Title_Mr', 'Title_Officer', 'Cabin_type_Unknown'], dtype='object')

#So the RFECV suggests that those are the most important features in the dataset

