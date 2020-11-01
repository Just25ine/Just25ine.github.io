# Reading in and Cleaning Data:

Below is an example of cleaning and manipulating flanker experiment data to ready it for analysis. To begin the data is read in. In this exampleue to unexpected delays, block 5 of the experiment had to be completed on a second day, apart from all of the other blocks. After all the trials were completed, we came to the conclusion that the delay to another day may have an effect on the data collected, an effect which we do not want to measure and do not want to alter the results. Say, for the sake of the example, we do find that an effect has occurred due to the delay. We decide to remove the trials from block 5. We may also want to remove any outliers, though this is not always the case, but I will do it in this example to show how it would be done. Finally, data that is irrelevant to the data analysis is removed.


```python
import pandas as pd
```


```python
#Reading in the data:
df = pd.read_csv('s15.csv')

#Changing the reaction time data into milliseconds
df.rt = df.rt * 1000

#Removing block 5 of the data:
df = df[df.block != 5]

#Removing Outliers
df.rt = df.rt[df.rt > (df.rt.mean() - (3*df.rt.std()))]
df.rt = df.rt[df.rt < (df.rt.mean() + (3*df.rt.std()))]

#Cleaning up the table:
df.index += 1 
df.index.name = 'Overall_Trial_Num'
df = df.drop(['Unnamed: 0'], axis=1)

#Table Index:
print('Table: Cleaned Data')
df
```

    Table: Cleaned Data





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
      <th>block</th>
      <th>trialNum</th>
      <th>flankers</th>
      <th>rt</th>
      <th>error</th>
    </tr>
    <tr>
      <th>Overall_Trial_Num</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>congruent</td>
      <td>353.112741</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>2</td>
      <td>congruent</td>
      <td>289.481512</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>3</td>
      <td>incongruent</td>
      <td>288.795258</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>4</td>
      <td>congruent</td>
      <td>287.419173</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>5</td>
      <td>congruent</td>
      <td>256.959232</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>187</th>
      <td>4</td>
      <td>44</td>
      <td>congruent</td>
      <td>547.400581</td>
      <td>False</td>
    </tr>
    <tr>
      <th>188</th>
      <td>4</td>
      <td>45</td>
      <td>incongruent</td>
      <td>390.344515</td>
      <td>False</td>
    </tr>
    <tr>
      <th>189</th>
      <td>4</td>
      <td>46</td>
      <td>congruent</td>
      <td>298.489134</td>
      <td>False</td>
    </tr>
    <tr>
      <th>190</th>
      <td>4</td>
      <td>47</td>
      <td>congruent</td>
      <td>283.786265</td>
      <td>False</td>
    </tr>
    <tr>
      <th>191</th>
      <td>4</td>
      <td>48</td>
      <td>incongruent</td>
      <td>271.029110</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>191 rows × 5 columns</p>
</div>


