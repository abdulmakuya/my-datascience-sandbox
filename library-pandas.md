# USECASE 01 : Select and persist only agents (i.e rows with v2 starting with with 0,1,2,3


```python
#** make a query selecting agents (v2 starts with 0,1,2,3)
query = (df.v2.str.startswith('1') | (df.v2.str.startswith('2')) | (df.v2.str.startswith('3')) | (df.v2.str.startswith('0')) )
#convert the selection into a dataframe
df[query]
#persist the dataset
only_agents_dataset = df[query]
only_agents_dataset.to_csv("ONLY_AGENTS_DATASET_1stWeel.csv", index=False)

#Select/filters rows with certain words in a column.
nbc = ['NBCCASHIN', 'NBCCASHINC','NBCCASHOUT','NBCGEPG',]
query_nbc_raw = df.v6.isin(nbc)
nbc_txn = df[query_nbc_raw]

#Find the unique values in a column
syntax = df.column.unique()
df.v6.unique()
CASHIN, CASHOUT

#Get a colum from a dataset, and change it to an array
nbc_v8 = np.array(nbc_txn.v8)
total = np.sum(nbc_v8)

#Drop columns
df.drop(columns = ['v11','v12'], inplace = True)


#Pick a sample space randomly
from random import sample
from random import shuffle

all_agents = ["","",""]

samp_agents = sample(all_agents,100)


#Change column type
df.v2.astype(str)
df.v2.astype(int)

df.dtypes

```

