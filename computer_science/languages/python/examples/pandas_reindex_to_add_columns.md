---
aliases: [Pandas Reindex to Add Columns, Add Columns with Pandas Reindex]
tags: [python, code, example, HOW-TO, machine_learning, ai, pandas, data_science, computer_science]
status: ongoing
edited: 2021-11-11
---

# Pandas Reindex to Add Columns
This is a [[python|Python]] code example of using a function from Pandas #todo library.

The way to use `df.reindex()` isn't so complex that it requires an example, but its usage is important enough.

## Example
code:
```python
import pandas as pd

data = [{'a': 1, 'd': 2, 'g':3, 'j':4}]
df = pd.DataFrame(data)
columns = ['a','b','c','d','e','f','g']
new_df = df.reindex(columns=columns)
```

output:
```python
>>> df
   a  d  g  i
0  1  2  3  4

>>> new_df
   a   b   c  d   e   f  g
0  1 NaN NaN  2 NaN NaN  3
```

explanation:
1. a `data` with columns `a,d,g,j` has values `1,2,3,4`, respectively
2. data is converted to Pandas DataFrame, `df`
3. columns `b,c,e,f` are added to `df` with null values (a new DataFrame is returned, instead of modifying the `df` in place)

things to note:
1. the order of new columns overwrite the order of the existing columns
2. the existing columns that are not part of the new columns gets removed

why it's important:
1. there may be a time when the order of the columns _matter_. Using `append` will add new columns _after_ the existing columns, thereby throwing off the intended order.

## Scenario
#machine_learning 
A data in [[machine_learning|Machine Learning]] must always be in order, as far as columns go. The order of the columns must be preserved when training an ML model, and then be present with the test data when making prediction with the ML model. Put simply, the order of the columns of the training data and the test data must match.

Take User Based Collaborative Filtering model - in short, UBCF.

The structure of the input data for the model is user : products.

Training Data:

|    | p1 | p2 | p3 | p4 |
|----|----|----|----|----|
| u1 | 1  | 0  | 0  | 1  |
| u2 | 0  | 0  | 1  | 1  |
| u3 | 0  | 1  | 0  | 0  |

Once trained, the model only accepts input data with shape `(, 4)`.

Now, let's say the UBCF model is put to use.
A new user `u4` buys an item and now requesting a recommendation.

The initial form of the new data would be like this:

|    | p1 |
|----|----|
| u4 | 1  |

which would not work with the model, as is.
Thus, columns from the training data (with order preserved) must be called to `reindex` the new data.

|    | p1 | p2 | p3 | p4 |
|----|----|----|----|----|
| u4 | 1  | 0  | 0  | 0  |

Voila, now the UBCF model takes the data and spits out recommendations.