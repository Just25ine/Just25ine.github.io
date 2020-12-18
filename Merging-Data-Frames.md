# Merging Two Participants' Data:

Often, merging two data sets or dataframes is between two different types of data; however, I will merge two data sets from two different participants from the same flanker experiment by concatenating across rows. I will create a multilevel index indicating the data for each participant. By doing this, we have both of the participants' data in one dataframe under the same columns instead of two separate dataframes. The multilevel index allows us to differentiate between the two sets of data and facilitates easy filtering and slicing, as is shown below. 


```python
import pandas as pd
```


```python
#Reading in data:
df_1 = pd.read_csv('s14.csv')
df_2 = pd.read_csv('s15.csv')

#Concatenating the two data sets using a dictionary:
df_dict = {'subject_14': df_1, 'subject_15': df_2}
df_full = pd.concat(df_dict, axis=0)

#Displaying the full dataframe:
print('Table 1: Flanker Experiment Data for Participants 14 and 15:')
df_full

```

    Table 1: Flanker Experiment Data for Participants 14 and 15:





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
      <th></th>
      <th>Unnamed: 0</th>
      <th>block</th>
      <th>trialNum</th>
      <th>flankers</th>
      <th>rt</th>
      <th>error</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">subject_14</th>
      <th>0</th>
      <td>144</td>
      <td>1</td>
      <td>1</td>
      <td>incongruent</td>
      <td>0.495394</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>147</td>
      <td>1</td>
      <td>2</td>
      <td>congruent</td>
      <td>0.394956</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>150</td>
      <td>1</td>
      <td>3</td>
      <td>congruent</td>
      <td>0.407109</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>153</td>
      <td>1</td>
      <td>4</td>
      <td>incongruent</td>
      <td>0.508727</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>156</td>
      <td>1</td>
      <td>5</td>
      <td>incongruent</td>
      <td>0.334156</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="5" valign="top">subject_15</th>
      <th>224</th>
      <td>819</td>
      <td>5</td>
      <td>34</td>
      <td>congruent</td>
      <td>0.301171</td>
      <td>False</td>
    </tr>
    <tr>
      <th>225</th>
      <td>822</td>
      <td>5</td>
      <td>35</td>
      <td>incongruent</td>
      <td>0.524165</td>
      <td>False</td>
    </tr>
    <tr>
      <th>226</th>
      <td>825</td>
      <td>5</td>
      <td>36</td>
      <td>congruent</td>
      <td>0.399177</td>
      <td>False</td>
    </tr>
    <tr>
      <th>227</th>
      <td>828</td>
      <td>5</td>
      <td>37</td>
      <td>congruent</td>
      <td>0.363240</td>
      <td>False</td>
    </tr>
    <tr>
      <th>228</th>
      <td>831</td>
      <td>5</td>
      <td>38</td>
      <td>congruent</td>
      <td>0.416024</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>469 rows × 6 columns</p>
</div>



As an example of how the multilevel index makes data selection easy, it allows us to take each subject's data from the full dataset and display it as shown below. So, instead of having two different data sets, we have one data set with all the data, which can be sectioned to indivdiual data.


```python
#Using loc accessor to display data from subject 14:
print('Table 2: Flanker Experiment Data for Subject 14 Only:')
df_full.loc['subject_14']
```

    Table 2: Flanker Experiment Data for Subject 14 Only:





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
      <th>Unnamed: 0</th>
      <th>block</th>
      <th>trialNum</th>
      <th>flankers</th>
      <th>rt</th>
      <th>error</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>144</td>
      <td>1</td>
      <td>1</td>
      <td>incongruent</td>
      <td>0.495394</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>147</td>
      <td>1</td>
      <td>2</td>
      <td>congruent</td>
      <td>0.394956</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>150</td>
      <td>1</td>
      <td>3</td>
      <td>congruent</td>
      <td>0.407109</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>153</td>
      <td>1</td>
      <td>4</td>
      <td>incongruent</td>
      <td>0.508727</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>156</td>
      <td>1</td>
      <td>5</td>
      <td>incongruent</td>
      <td>0.334156</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>235</th>
      <td>849</td>
      <td>5</td>
      <td>44</td>
      <td>incongruent</td>
      <td>0.523022</td>
      <td>False</td>
    </tr>
    <tr>
      <th>236</th>
      <td>852</td>
      <td>5</td>
      <td>45</td>
      <td>congruent</td>
      <td>0.647998</td>
      <td>False</td>
    </tr>
    <tr>
      <th>237</th>
      <td>855</td>
      <td>5</td>
      <td>46</td>
      <td>incongruent</td>
      <td>0.475372</td>
      <td>False</td>
    </tr>
    <tr>
      <th>238</th>
      <td>858</td>
      <td>5</td>
      <td>47</td>
      <td>congruent</td>
      <td>0.475072</td>
      <td>False</td>
    </tr>
    <tr>
      <th>239</th>
      <td>861</td>
      <td>5</td>
      <td>48</td>
      <td>incongruent</td>
      <td>0.472104</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>240 rows × 6 columns</p>
</div>


