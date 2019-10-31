# Importing data to 

```python

# Open a file: 
file
file = open('moby_dick.txt', mode='r')

# Print it
print(file.read())

# Check whether file is closed
print(file.closed)

# Close fil2
file.close()

# Check whether file is closed
print(file.closed)

#Pivot tables and Pivot table plots

class_pivot = train.pivot_table(index="Pclass", values="Survived")
class_pivot.plot.bar()
plt.show()

#Binning


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

submission.to_csv(index = False)
```
default python file opening functions
importing as array for numerical data numpy
importing as dataframe for mixed data pandas
