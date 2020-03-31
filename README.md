## Module 1 Project
This is the first project where the project consists of Data Analysis on some of the movies that are most trending at the Box Office and their meaningful insights that will not only assist the decision makers of the company to expediate in their progress of achieving the most trending business but also some of the investor to make a clear understanding for their profitable future investments.


## -------------------------------------OUTLINE BEGINS------------------------------------- 


This repository consists of the following list of files
√ A Complete Dataset Analysis on some credible information labelled in "istudent.ipynb" python file.
√ A presentation based on Data Analysis for non-stake holders.
√ A Blog post based on Project that gives an idea to my fellow Data Science friends
√ A complete ReadMe.md file the gives that gives the outline of the project.


## DATASET

For every credible data , we used some credible datasets, below are some of the credible datasets used to complete Data Analysis

√ "rt.movie_info.tsv.gz"

√ "imdb.title.basics.csv.gz"

√ "tn.movie_budgets.csv.gz"


## QUESTIONS CONSIDERED WHILE ANALYSING THE DATA

√. Who are the Top Directors which show good Revenue in return?

√. Which Studios is preferably recommended for production for better Picture Quality?

√. Which Genric Movies are made the most?

√. What is the Average Cost in making movies and Average Profit at National Scale and WorldWide Scale?


## Project Content

** The codes below is type of codes used in every dataset with different variables for Data Analysis **

1st Dataset -- "rt.movie_info.tsv.gz"
**This particular dataset is in .tsv file so had to add another command to open this file **

```"df=pd.read_csv("rt.movie_info.tsv.gz", sep='\t')"```

**Outlook of Data in all Datasets**

```print(df.isnull().sum())```

```print(df.info())```

**Cleaned, Sorted and Rearranged the Data into readable format**

```df=df.dropna().dropna(axis=1)```

```df=df.sort_values("box_office",ascending=False)```

```df['box_office']= df['box_office'].apply(lambda x: x.replace('$', '').replace(',', '')).astype('int64')```

**Dropped Uncessary Columns **

```df.drop(["id","dvd_date","currency"],axis=1,inplace=True)
```
**Rearranged the columns and added titling feature in all the columns title**

```df=df[['director','writer','genre','rating','theater_date','box_office','runtime','studio','synopsis']]```

```df.columns = map(str.title, df.columns)```

**To read the complete synopsis, used a special highlight features that could read the synopsis while making sure reading the specific with the relevant Director**

```df.style.set_properties(**{'background-color': 'linear-gradient(to bottom left, #9999ff 0%, #ff99cc 100%)','color': 'black'}) ```
                           
**2nd Dataset along with 3rd Dataset**
**Creating a new DataFrame to join the tables for later data analysis**

```new_moneybudgets=pd.DataFrame(movie_budgets['movie'])```

```new_moneybudgets['Movie_Budget']= movie_budgets['production_budget']```

```new_moneybudgets['National_Profit']=movie_budgets['domestic_gross']```

```new_moneybudgets['WorldWide_Profit']=movie_budgets['worldwide_gross']```

```new_moneybudgets['Net_Profit']=movie_budgets['worldwide_gross']-movie_budgets['production_budget']```


**Joined/Merged 2 Datasets with the following Command:**

```cc_df= pd.merge(new_moneybudgets,df2,how='inner',on="movie")```
```cc_df=cc_df.rename(columns={"start_year":"Year"})```

**Work on the first 100 dataset**

```cc_df=cc_df.sort_values('Net_Profit',ascending=False).head(100)```

## -------------------------------------PLOTS------------------------------------- 

**1st DATASET PLOTS:**
                           
Based on the cleaned Dataset made the plot for TOP 10 DIRECTORS in respect to Revenue in movies


![image](https://user-images.githubusercontent.com/47164862/77980338-a8da6000-72cc-11ea-9433-b4ea32e3e7df.png)

**Mel Gibson : $368000000                     Peter Jackson : $303001229
Sam Mendes : $299300000                       Jay Roach : $279167575
Chris Columbus : $261835892                   Joel ZWick : $241250669
Steven Spielberg : $234141872                 Peter Berg : $227946274
Bryan Singer : $214813155                     Justin Lin : $209805005  **


Based on the cleaned Dataset made the scatter plot for TOP 20 STUDIOS in respect to Revenue in movies

![image](https://user-images.githubusercontent.com/47164862/77980944-45513200-72ce-11ea-8d14-4d0914650452.png)

**_ Universal Pictures And 20th Century Fox are the recommended Studios for production of Movies _**


**2nd and 3rd DATASET PLOTS:**

Movies that are produced more in specific Genres
![image](https://user-images.githubusercontent.com/47164862/77981812-76cafd00-72d0-11ea-9c85-2fb4819fcf9b.png)

**Horror: 4, 'Mystery': 2,
Family: 12, Action:46, Adventure: 66, 
'Sci-Fi': 26, 'Crime': 4, 
'Thriller': 11, 'Drama': 15, 
'Sport': 2, 'Animation': 18, 
'Comedy': 23, 'Fantasy': 25, 
'Romance': 4, 'Musical': 5, 
'Biography': 2, 'Music': 1, 
'Documentary': 4, 'History': 1 **

Average Cost in Production for the Specific Generic Movies


![image](https://user-images.githubusercontent.com/47164862/77982290-9878b400-72d1-11ea-9fb0-a2fc693ef1ee.png)


Average National Profit for the Specific Genric Movies


![image](https://user-images.githubusercontent.com/47164862/77982353-c52ccb80-72d1-11ea-8e0f-728217364b76.png)


Average WorldWide Profit for Specific Generic Movies


![image](https://user-images.githubusercontent.com/47164862/77982494-150b9280-72d2-11ea-83e5-d8808023a238.png)



## Conclusion
**_ With the analysis above this is clear that every single aspect of details matters to make a great movie. Most importantly the Directors , Writers, Picture Quality and the Genres to have a great Revenue on a movie. With the limited data in the datasets the other factors as Release time, Actors and many other aspects are important to predict the movie Revenue. Overall with all the analysis above I would highly recommended to make a move for Adventure/ Action Movies or Fanstasy/Romantic Movies for producion based on the analysis as they would easily on an average would Net Profit for about 25 to 30 million. _**
