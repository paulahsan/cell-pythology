---
layout: post
title: Heatmap with theme RdYlBu
date: 2022-08-02 15:05:00 +0900
description: Tutorial for plotting heatmap. # Add post description (optional)
img: output_10_0.png
fig-caption: sample heatmap
tags: [data plotting, wide form data, heatmap, data viz]
---

# Make a heatmap
Here we will learn to make a heatmap by taking RdYlBu as colormap or theme

## Import library


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 
```

## Generate Data


```python
df = pd.DataFrame(np.random.rand(4,3),columns=["A","B","C"] )
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
      <td>0.996340</td>
      <td>0.214264</td>
      <td>0.556522</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.081258</td>
      <td>0.576770</td>
      <td>0.893816</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.159397</td>
      <td>0.189863</td>
      <td>0.378016</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.995932</td>
      <td>0.263881</td>
      <td>0.128237</td>
    </tr>
  </tbody>
</table>
</div>



### Plot Heatmap


```python
sns.heatmap(df,
            cmap="RdYlBu"
           )
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/output_7_0.png)
    


### Plot cluster map


```python
sns.clustermap(df,
            cmap="RdYlBu"
           )
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/output_9_0.png)
    



```python
sns.boxplot(data=df)
plt.show()
```


    
![png]({{site.baseurl}}/assets/img/output_10_0.png)
    



```python

```
