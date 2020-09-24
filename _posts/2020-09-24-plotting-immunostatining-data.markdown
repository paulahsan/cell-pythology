---
layout: post
title: Plotting Immunostaining Data
date: 2020-09-24 16:05:00 +0900
description: Tutorial for plotting immunostaining data. # Add post description (optional)
img: banner-wide-violinplot.png
fig-caption: wide form violinplot source:https://seaborn.pydata.org/examples/wide_form_violinplot.html 
tags: [data plotting, wide form data, immunostaining, data viz]
---
In this tutorial we will gernerate a demo immunostaining data and show how to plot it into different types of plots.

## Import important libraries


```python
# numerical python
import numpy as np
# dataframe implementation in python
import pandas as pd
# vizualization library in python
import matplotlib.pyplot as plt
# vizualization librariy based on matplotlib
import seaborn as sns
```

## Make a random dataset

### Generate a random array

fix a seed value so that resut become reproducible


```python
np.random.seed(8)
```

generate an array of random integers with 50 rows and 4 columns
the lowest and highest number in the array would be 3 and 10 respectively


```python
data=np.random.randint(low=3,high=10,size=(50,4))
```

this can also be written as simple as 
data=np.random.randint(3,10,(50,4))

as the data have 4 columns, lets assume they stand for
experiemntal conditions and represent column names


```python
header=["WT_IR_0","WT_IR_30","MU_IR_0","MU_IR_30"]
```

### Convert array into a dataframe
make a dataframe by combining the data with header


```python
df=pd.DataFrame(data, columns=header)
```

Print the first five lines of the data.

This is called wide form of data


```python
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
      <th>WT_IR_0</th>
      <th>WT_IR_30</th>
      <th>MU_IR_0</th>
      <th>MU_IR_30</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>7</td>
      <td>4</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8</td>
      <td>5</td>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7</td>
      <td>4</td>
      <td>6</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>7</td>
      <td>8</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



## Plotting the data

### Make a boxplot out of the data
Using the boxplot function of seaborn module generate a boxplot



```python
sns.boxplot(data=df);
```


![boxplot]({{site.baseurl}}/assets/img/simple_boxplot_wide_form.png)


Reader may try the following

`sns.boxplot(data=df)`ommitting the colon`";"`, or just writing 

`sns.boxplot(df)` and see the differences among outputs

### Make a violinplot out of  the data


```python
sns.violinplot(data=df, inner="point", palette='RdBu')
plt.title("Violin plot", size=22)
plt.xlabel("Cell line and condition", size=20)
plt.ylabel("Number of foci", size=20)
plt.xticks(size=16)
plt.show()
```


![violinplot]({{site.baseurl}}/assets/img/violinplot_wide_form.png)


### Try other different form of plots systematically


```python
custom_pallette=['salmon','cyan','lavender','palegreen']
plot_type= [sns.violinplot,sns.boxplot, sns.boxenplot, sns.swarmplot] 

fig,ax = plt.subplots(nrows=2,ncols=2, 
                      figsize=(10,10),
                      gridspec_kw={'hspace': 0.3})

for idx, plot in enumerate(plot_type):
    axis=ax.flatten()[idx]
    plot(data=df, ax=axis,palette=custom_pallette)
    axis.set_title(plot.__name__, size=20)
    axis.set_xlabel("Cell line", size=16)
    axis.set_ylabel("# Foci", size=16)
    
```


![all_plot]({{site.baseurl}}/assets/img/seaborn_all_plots_wide_form.png)


Now breakdown the above code for beginners. 
`custom_pallette=['salmon','cyan','lavender','palegreen']` this is a custom color palette defined by user.

Then we make a list containing different function from seaborn module in the follwoing line `plot_type= [sns.violinplot,sns.boxplot, sns.boxenplot, sns.swarmplot] `

we make a figure `fig` and axes object `ax` by calling `plt.subplots()`.

`nrows=2, ncols=2,` defines how many row and columns do I need, `figsize=(10,10)` set the size of the figure.

grid spec key word arguments `gridspec_kw={'hspace': 0.3}` tells the function the horizontal spaces `'hspace'` will be `0.3` and it determines the space between two rows.

Finally, we call `enumerate` function on `plot_type` list and draw the plots.

Because different plots will be on different axes, we declare beforehand it by `axis=ax.flatten()[idx]`

`axis.set_title(plot.__name__, size=20)` set the title of each of the sub-plots and sizes of the titles and then the x-axis and y-axis label is defined in the following line

This toturial should help plotting immunopstatining data into meaningful nice plot.
