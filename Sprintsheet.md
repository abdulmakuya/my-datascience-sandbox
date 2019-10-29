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

```
default python file opening functions
importing as array for numerical data numpy
importing as dataframe for mixed data pandas
