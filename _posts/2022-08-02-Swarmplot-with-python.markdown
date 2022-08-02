---
layout: post
title: Swarmplot with python
date: 2022-08-02 18:05:00 +0900
description: Tutorial for plotting swarmplot. # Add post description (optional)
description: Tutorial for plotting heatmap. # Add post description (optional)
img: Swarmplot-with-python_output_7_0.png
fig-caption: sample swarmplot source:author

tags: [data plotting, swarmplot, data viz]
---

# Make a swarmplot
Here we will learn to make a swarmplot

## Import library


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 
```

## Generate Data


```python
df = pd.DataFrame(np.random.rand(400,3),columns=["A","B","C"] )
df.head()
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.606046</td>
      <td>0.660908</td>
      <td>0.406183</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.166003</td>
      <td>0.914510</td>
      <td>0.182683</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.368522</td>
      <td>0.963965</td>
      <td>0.473712</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.242509</td>
      <td>0.552537</td>
      <td>0.049429</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.140715</td>
      <td>0.073817</td>
      <td>0.222349</td>
    </tr>
  </tbody>
</table>
</div>



### Plot Swarmplot


```python
sns.swarmplot(data=df,
              palette="prism"
             )
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/Swarmplot-with-python_output_7_0.png)
    


### Plot violin


```python
sns.violinplot(data=df,
               palette="Pastel1"
              )
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/Swarmplot-with-python_output_9_0.png)
    


### Plot Boxen


```python
sns.boxenplot(data=df,
               palette="viridis"
              )
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/Swarmplot-with-python_output_11_0.png)
    

