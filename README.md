## Module 1 Project
This is the first project where the project consists of Data Analysis on some of the movies that are most trending at the Box Office and their meaningful insights that will not only assist the decision makers of the company to expediate in their progress of achieving the most trending business but also some of the investor to make a clear understanding for their profitable future investments.

### -------------------------------------OUTLINE BEGINS------------------------------------- 
This repository consists of the following list of files
√ A Complete Dataset Analysis on some credible information labelled in "istudent.ipynb" python file.
√ A presentation based on Data Analysis for non-stake holders.
√ A Blog post based on Project that gives an idea to my fellow Data Science friends
√ A complete ReadMe.md file the gives that gives the outline of the project.

### DATASET
For every credible data , we used some credible datasets, below are some of the credible datasets used to complete Data Analysis
√ "rt.movie_info.tsv.gz"
√ "imdb.title.basics.csv.gz"
√ "tn.movie_budgets.csv.gz"

## Project Content
1st Dataset -- "rt.movie_info.tsv.gz"
This particular dataset is in .tsv file so had to add another command to open this file 
"df=pd.read_csv("rt.movie_info.tsv.gz", sep='\t')"

Outlook of Data
print(df.isnull().sum())
print(df.info())

Cleaned, Sorted and Rearranged the Data into readable format
df=df.dropna().dropna(axis=1)
df=df.sort_values("box_office",ascending=False)
df['box_office']= df['box_office'].apply(lambda x: x.replace('$', '').replace(',', '')).astype('int64')

Dropped Uncessary Columns
df.drop(["id","dvd_date","currency"],axis=1,inplace=True)

Rearranged the columns and added titling feature in all the columns title
df=df[['director','writer','genre','rating','theater_date','box_office','runtime','studio','synopsis']]
df.columns = map(str.title, df.columns)


## Recommended Section
## Conclusion

