# Computing the Mean and Accuracy of Reaction Time Data:

In this example, reaction time data from a flanker experiment is converted to milliseconds and the mean is found for each different block of trials and displayed in a pandas dataframe. The accuracy rate of each block was calculated from the error data and displayed in a seperate pandas dataframe. The rational was to determine if individuals got better with successive trials of the flanker task. 


With the EDA that this returns, it appears that individuals do not get better at the task in this experiment after successive trials. It actually appears to indicate fatigue; the individuals appeared to respond slower as the trials went on. No clear correlation was found for accuracy rates.


```python
import pandas as pd
import numpy as np
import matplotlib as plt
```


```python
df = pd.read_csv('s15.csv')
```


```python
df.rt = df.rt * 1000
```


```python
df.groupby('block')[['rt']].mean().rename(columns={'rt': 'mean_rt'})
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mean_rt</th>
    </tr>
    <tr>
      <th>block</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>307.275372</td>
    </tr>
    <tr>
      <th>2</th>
      <td>345.714050</td>
    </tr>
    <tr>
      <th>3</th>
      <td>374.704452</td>
    </tr>
    <tr>
      <th>4</th>
      <td>411.236369</td>
    </tr>
    <tr>
      <th>5</th>
      <td>396.632954</td>
    </tr>
  </tbody>
</table>
</div>




```python
((df.groupby('block')[['error']].count() - df.groupby('block')[['error']].sum())/df.groupby('block')[['error']].count()).rename(columns={'error': 'accuracy_rate'})
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>accuracy_rate</th>
    </tr>
    <tr>
      <th>block</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0.812500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.750000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.791667</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.914894</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.894737</td>
    </tr>
  </tbody>
</table>
</div>


