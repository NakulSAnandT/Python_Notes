Bivariate analysis is an analytical technique used to explore the relationship between two variables in a dataset. It aims to understand how changes in one variable are associated with changes in another variable.

1. Scatter plot: A scatter plot is used to display the relationship between two continuous variables. Each data point is plotted as a point on the graph, with one variable on the x-axis and the other variable on the y-axis. Scatter plots help visualize the pattern and strength of the relationship between the variables.

		 sns.scatterplot(x = 'LoanAmount', y = 'Loan_Amount_Term', data= df)

----------------------------------------------------------------------------------

2. Line plot: A line plot is useful when you want to compare the trends or changes in two continuous variables over time or some other ordered variable. Each variable is plotted on a separate line, and the lines are connected to show the trend.
-----------------------------------------------------------------------------------
3. Bar plot: Bar plots are commonly used for comparing a categorical variable with a numerical variable. The categorical variable is represented on the x-axis, and the height of the bars represents the value of the numerical variable. Bar plots help visualize the differences in values across categories.

		g = pd.crosstab(df['Loan_Status'], df['Education'])
		g.div(g.sum(1).astype(float), axis=0).plot(kind='bar', stacked=True, figsize=(4, 4))
		plt.xlabel('Loan_Status')
		plt.ylabel('Count')
		plt.title('Loan Approval Status by Education')
		plt.legend(title='Gender')

-------------------------------------------------------------------------------------------------------------

4. Box plot: Box plots are effective for comparing the distribution of a numerical variable across different categories of a categorical variable. The box represents the interquartile range (IQR), with the median shown as a line within the box. The whiskers extend to show the range of data, and any outliers are plotted as individual points.

---------------------------------------------------------------------------------------------

5. Heatmap: A heatmap is useful for visualizing the relationship between two categorical variables. It uses color coding to represent the frequency or proportion of each combination of categories. Heatmaps provide a quick overview of the distribution and patterns within the data.

----------------------------------------------------------------------------------------

6. Violin plot: Violin plots combine the features of box plots and kernel density plots. They are useful for comparing the distribution of a numerical variable across different categories of a categorical variable. The width of the violin represents the density of data at different values.