### My Quick Snippets

```python

# Pivot tables and Pivot table plots

class_pivot = train.pivot_table(index="Pclass", values="Survived")
class_pivot.plot.bar()
plt.show()

# Binning

def process_age(df,cut_points,label_names):
    df["Age"] = df["Age"].fillna(-0.5)
    df["Age_categories"] = pd.cut(df["Age"],cut_points,labels=label_names)
    return df

cut_points = [-1,0,5,12,18,35,60,100]
label_names = ["Missing","Infant","Child","Teenager","Young Adult","Adult","Senior"]
train = process_age(train,cut_points,label_names)

age_bin_train = train.pivot_table(index = "Age_categories", values = "Survived")
age_bin_train.plot.bar()

# Cross-validation with k-fold Cross validation

from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression
import numpy as np

all_X = df.columns #alternatively columns = ["col1","col2"],then all_X = df[columns]
lr = LogisticRegression()
scores = cross_val_score(lr,all_X,all_y,cv=10)
accuracy = numpy.mean(scores)

print("the scores are ",scores)
print("the accuracy is ",accuracy)


# Creating submission files

#take the ids from the holdout dataset
holdout_ids = holdout["PassengerId"]

#create a dataframe with exactly two columns IDs and Survived from the predictions
submission_df = {"PassengerId" : holdout_ids,
                 "Survived" : holdout_predictions}

#dataframe it and export to csv
submission = pd.DataFrame(submission_df)
submission.to_csv("submission.csv", index = False)

#Binning and One-Hot Encoding

import pandas as pd

train = pd.read_csv('train.csv')
holdout = pd.read_csv('test.csv')

def process_age(df):
    df["Age"] = df["Age"].fillna(-0.5)
    cut_points = [-1,0,5,12,18,35,60,100]
    label_names = ["Missing","Infant","Child","Teenager","Young Adult","Adult","Senior"]
    df["Age_categories"] = pd.cut(df["Age"],cut_points,labels=label_names)
    return df

def create_dummies(df,column_name):
    dummies = pd.get_dummies(df[column_name],prefix=column_name)
    df = pd.concat([df,dummies],axis=1)
    return df

train = process_age(train)
for column in ["Age_categories","Pclass","Sex"]:
    train = create_dummies(train,column)
    
holdout = process_age(holdout)
for column in ["Age_categories","Pclass","Sex"]:
    holdout = create_dummies(holdout,column)
      
print(train.columns)

# Learning the feature importance by looking at the co-efficients
# best-performing features, we need a way to measure which of our features are relevant to our outcome,logiristic regression comes with a packed,in which a coeffient attribute can be accessed after the the model is fit

columns = ['Age_categories_Missing', 'Age_categories_Infant',
       'Age_categories_Child', 'Age_categories_Teenager',
       'Age_categories_Young Adult', 'Age_categories_Adult',
       'Age_categories_Senior', 'Pclass_1', 'Pclass_2', 'Pclass_3',
       'Sex_female', 'Sex_male', 'Embarked_C', 'Embarked_Q', 'Embarked_S',
       'SibSp_scaled', 'Parch_scaled', 'Fare_scaled']


lr = LogisticRegression()
lr.fit(train[columns],train["Survived"])
coefficients = lr.coef_
feature_importance = pd.Series(coefficients[0],index=train[columns].columns)
feature_importance.plot.barh()

# If the feature importance mean something if they are both +ve and -ve,meaning if the target is categorical..
# say if the likelihood of a survival is opposite of likelihood of death,If it the results are mutually exclusive
# then you want to absolute it,then oder it

orderd_feature_importance = feature_importance.abs().sort_values()
orderd_feature_importance.plot.barh()

Concatenate dummy rows (One hot encoded) in the original df

for col in columns:
    train[col + "_scaled"] = minmax_scale(train[col])
    holdout[col + "_scaled"] = minmax_scale(holdout[col])

```
default python file opening functions
importing as array for numerical data numpy
importing as dataframe for mixed data pandas
