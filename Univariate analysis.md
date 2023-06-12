Numerical Values
------------------------
 
-  **Histograms —** `**sns.histplot()**`

A histogram groups values into ranges (or bins), and the height of a bar shows how many values fall in that range.

![](https://miro.medium.com/v2/resize:fit:501/1*Zahip49tUxXmg_28Zyw5qw.png)

From a histogram, we will get the following:

- Range of the data. The minimum and maximum values are on opposite edges of the histogram. Highly concentrated regions are also apparent. Tall bars are where most data points fall whereas sparsely represented ranges appear as gaps or short bars.
- Shape or skewness of the feature. A feature can be right-skewed (tail is towards right), left-skewed (left-tailed), normally distributed (one center), or randomly distributed (no apparent pattern, multiple peaks).
- Presence of outliers. These appear as isolated bars on the far left or right.

The code below creates a seaborn histogram for our target variable `selling price`.

sns.histplot(x='selling_price', data=cars);

----------------------------------------------------------------------------------------------
- **KDE plot —** `**sns.kdeplot()**`

The [‘kernel density estimate’ plot](https://seaborn.pydata.org/generated/seaborn.kdeplot.html) creates a smooth version of a histogram by normalizing all points to appear under one curve.

![](https://miro.medium.com/v2/resize:fit:540/1*qhLeKXr4EfizT49mLf80DQ.png)


It is best used when comparing a variable’s distribution between groups of another variable, a concept known as [segmented univariate distribution](https://www.linkedin.com/pulse/segmented-univariate-analysis-junaid-alam/).

The code below compares how `engine sizes` are distributed among the `fuel types`. We pass `hue=’fuel’` to split the data by the fuel types.

sns.kdeplot(x='engine_cc', data=cars, hue='fuel')

----------------------------------------------------------------------------------------------
- **KDE with Histogram plot —** `**sns.histplot(kde=True)**`

----------------------------------------------------------------------------------------------
- **Rug plot —** `**sns.rugplot()**`

A [rug plot](https://en.wikipedia.org/wiki/Rug_plot) draws ticks on the x-axis that show the location of individual data points.

![](https://miro.medium.com/v2/resize:fit:575/1*3LSJYKYHkUghlBrA01EwJw.png)


The dense areas are places where most observations fall under while the heights of the ticks are inconsequential.

Rug plots complement histograms when it comes to outliers because we can see where the outlier data points fall. The code below creates [a rugplot](https://seaborn.pydata.org/generated/seaborn.rugplot.html) and histogram for the `kilometers driven` feature. Note the outlier positions.

----------------------------------------------------------------------------------------------

- **Box plots —** `**sns.boxplot()**`

A [boxplot](https://www.simplypsychology.org/boxplots.html) shows the distribution, center and skewness of a numeric feature. It divides the data into sections that contain 25% of the data approximately.

![](https://miro.medium.com/v2/resize:fit:614/1*0PutKiHOWnclkxey28JjOw.png)

Boxplot illustration created by author

[Outliers](https://en.wikipedia.org/wiki/Outlier), if present, appear as dots on either end. The whiskers that extend from the box represent the minimum and maximum values. The box depicts the [Interquartile range](https://en.wikipedia.org/wiki/Interquartile_range) and holds 50% of the data.

Boxplots take up less space than histograms as they are less detailed. They also define quartile locations and are good for quick comparisons between different features or segments.

The code below creates a boxplot of the `mileage` feature.

sns.boxplot(x=cars['mileage_kmpl'])

![](https://miro.medium.com/v2/resize:fit:436/1*pNRaCqVEhVH0BIUJmjp-Yw.png)

Boxplot by author

Suppose you want to compare the distribution of two columns that are related; perhaps they have the same measuring unit. We can create a box plot and pass the two columns in the `data` as below.

sns.boxplot(data=cars.loc[:, ['engine_cc', 'max_power_bhp']])

![](https://miro.medium.com/v2/resize:fit:481/1*_GVPGwFsn29E7nnMxXCgdw.png)

-----------------------------------------------------------------------------
- **Violin plot —** `**sns.violinplot()**`

The [violin plot](https://towardsdatascience.com/violin-plots-explained-fb1d115e023d) features a combination of a box plot and a kernel density plot. This means that in addition to showing the quartiles, it also lays out the underlying distribution such as presence and location of different peaks.

![](https://miro.medium.com/v2/resize:fit:436/1*8zzFPbzfffXDVn2xKLFtXg.png)

--------------------------------------------------------------------------
- **Strip plot —** `**sns.stripplot()**`

A [strip plot](https://seaborn.pydata.org/generated/seaborn.stripplot.html) implements a scatter plot to show the spread of individual observations for a feature.

Dense locations indicate areas with many overlapping points, and you can quickly spot outliers. It’s however hard to establish the relative center unlike a box plot, and it’s [best](https://datavizproject.com/data-type/strip-plot/) for smaller datasets.

The code below creates a strip plot of `selling price`.

sns.stripplot(x=cars["selling_price"]);

![](https://miro.medium.com/v2/resize:fit:436/1*ETTy2aTWozmMyXsFclRbdw.png)

-------------------------------------------------------------------------
------------------------------------------------------------------------

Categorical values
---------------------------------

- **Count plot —** `**sns.countplot()**`

A [count plot](https://seaborn.pydata.org/generated/seaborn.countplot.html) compares different classes of a categorical feature and how often they occur. Think of a bar chart with the bar height showing number of times each class occurs in the data.

![](https://miro.medium.com/v2/resize:fit:374/1*tWIp5Y9ZK5R2nGw6YuYz1g.png)


---------------------------------------------------------------------
- **Pie chart —** `**plt.pie()**`

A [pie chart](https://byjus.com/maths/pie-chart/) displays the percentage distribution of a categorical variable in a circular graph.

![](https://miro.medium.com/v2/resize:fit:330/1*6rAyGAT8-jnCCslDpWBg6Q.png)


Pie charts are not very popular with the visualization community. For one, the graph appears cluttered when the groups exceed four. Two, sometimes the widths for the slices are not intuitively clear.

df = cars['transmission'].value_counts()###df  
Manual       7078  
Automatic    1050  
Name: transmission, dtype: int64

Next, we create the pie chart using `plt.pie()` and pass it the values for each group, the labels for each slice (optional), and how to display the values inside the slices (optional).

plt.pie(df, labels=df.index, autopct="%.0f%%");
