# Customer segmentatioon project

In this project, we work with datasets containing demographic information about the customers of a mail-order company in Germany as well as that of general population of the country. The main aim is to use these information to identify individuals from the population who are more likely to turn into future customers of the company and also predict the corresponding probabilities. The datasets, however, cannot be made public.

## Requirements

The following packages are required to run the code :
- **Python 3.7+**
- **NumPy** (`pip install numpy`)
- **pandas** (`pip install pandas`)
- **SciPy** (`pip install scipy`)
- **scikit-learn** (`pip install scikit-learn`)
- **XGBoost** (`pip install xgboost`)

## List of files

- _**Arvato Project Workbook.ipynb**_ : This is a jupyter notebook with a detail explanation of the analysis.
- _**customer_prediction**_ : A csv file containing predictions for response probabilities of each individual in the test dataset. For each individual there are two entries in the csv file - unique id number of that person and  the corresponding response probability.

Note that, the datasets used in the analysis are not provided in this repository as they cannot be made public.

## Analysis method

The whole analysis can be broken down into four main steps :

- **Exploratory Data Analysis**

In this step, we perform data cleaning wherever required. It mainly involves the following steps :

1. replacement of unknown values in the dataset by NaNs.
2. removal of columns and rows with high percentage of null values (>20%).
3. removel of features with high correlations (>80%).
4. if there are duplicate rows, drop all only keeping the first occurrences.
5. dropping categorical coulmns with high cardinality (>15).
6. encode categorical columns wherever necessary.
7. removal of columns and rows with high percentage of outliers (>10%), if any.
8. imputing null values using the strategies "median" and "most frequent" (depending on the feature).
9. standardize all the features.


- **Dimensionality reduction**

In this step, we reduce the dimension of the preprocessed dataset while preserving as much as information possible. For this, we use principal component analysis technique and by looking at the scree plot, decide to keep 150 principal components that explain more than 85% variance in the data.

- **Clustering**

Next, we group people based on their distances in the feature (or the principal component) space and for this, we use clustering techniques specifically k-means clustering. We choose the final number of clusters to be 12 from the elbow plot.

- **Model building**

Finally, we build a model which, given a set of features associated with an individual, will be able to predict how likely that person is to respond positively to the campaign and use this model to predict response probabilities of individuals in the provided test dataset.


## External link

You can check my article on this project on the **Medium** platform [here](https://medium.com/@nabanita.rimpi/identifying-customers-using-data-7b5cf626a301?sk=2ed96c8502e77a36cf7c568c5b6e019e).
