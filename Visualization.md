Seaborn : 
--------------------------------------------------------------------------------------------
- **Line chart** : sns.lineplot(data = df)

plt.figure(figsize = (20,20))
sns.lineplot(data = df(Column name)) # use squared bracket when mentioning a column
sns.lineplot(data = df(column name 2))
plt.xlabel('')
plt.ylabel('')
plt.title('')

----------------------------------------------------------------------

- **Bar chart**: sns.barplot(x = df(column1), y = df(column2) )
----------------------------------------------------------------------
- **Heat Map**: sns.heatmap(data = df, annot =True) # annot keeps the values in middle of the heatmap
----------------------------------------------------------------------
- **Scatter plot**  : sns.scatterplot(x = df(column1), y = (col2), data = df)
	sns.scatterplot(x=candy_data('pricepercent'), y=candy_data(winpercent), hue=candy_data('chocolate ')) # use chocolate to color code

----------------------------------------------------------------------
- **Regression plot** : sns.regplot(x = df(column1), y = (col2), data = df)
----------------------------------------------------------------------
- **Implot** : sns.lmplot(x="pricepercent", y="winpercent", hue="chocolate", 
-----------------------------------------------------------------------
- data=candy_data) # to build multiple regression line
-----------------------------------------------------------------------
- **Swarmplot:** sns.swarmplot(x=candy_data()'chocolate) y=candy_data(winpercent))
-----------------------------------------------------------------------
- **KDE Plot**: sns.kdeplot(data=iris_data('Petal Length (cm)'], shade=True)
-----------------------------------------------------------------------
- **2d kde plot**: sns.jointplot(x=iris_data()'Petal Length (cm)'], y=iris_data('Sepal Width (cm)'], kind="kde")
----------------------------------------------------------------------
