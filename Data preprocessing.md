

##### **Missing Files Handling**

	#Fills mean value
	df['LoanAmount'].fillna(df['LoanAmount'].mean(), inplace = True) #
	#fills mode
	df['Loan_Amount_Term'].fillna(df['Loan_Amount_Term'].mode().iloc[0], inplace =True)
	#fills
	df['Gender'].fillna('unkmown', inplace =True)
	#drops
	df.dropna(inplace = True)

----------------------------------------------------------------------------------------

##### **Converting categorical columns into numerical can be done using one-hot encoding or label encoding**

- Label encoding :

		from sklearn.preprocessing import LabelEncoder

		cat_Cols = df.drop(['ApplicantIncome', 'CoapplicantIncome', 'LoanAmount','Loan_Amount_Term', 'Credit_History'], axis = 1)
		# Create a new dataframe to store the encoded values
		encoded_df = df.copy()
		# Initialize LabelEncoder
		encoder = LabelEncoder()
		for col in cat_Cols:
		encoded_df[col] = encoder.fit_transform(  encoded_df[col])
		# Print the new DataFrame with label encoded features
		encoded_df



- One Hot Encoding(Dummies):


			cat_cols = df.drop(['ApplicantIncome', 'CoapplicantIncome', 'LoanAmount', 'Loan_Amount_Term', 'Credit_History'], axis=1) 
			# Perform one-hot encoding using get_dummies() encoded_df=pd.get_dummies(df, columns=cat_cols) 
			# Print the new DataFrame with one-hot encoded features 
			encoded_df

---------------------------------------------------------------------------------

##### **Skewedness Handling** 

- To find skewed columns ( Numerical)

	for i in df_c.columns:
	sk = skew(encoded_df[i])
	if sk > 0:
	 print("Positive skewness column:", i)
	else:
	print("Negative skewness column:", i)

- Handling Skewedness ( Apply logarithmic transformation)

		encoded_df['CoapplicantIncome'] = np.log(encoded_df['CoapplicantIncome'])
		sns.histplot(encoded_df['CoapplicantIncome'], kde = True)
		plt.figure()
		pp = stats.probplot(encoded_df['CoapplicantIncome'], plot = plt)

-------------------------------------------------------------------------------------------