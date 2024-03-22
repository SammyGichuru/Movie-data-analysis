# Movie Data Analysis for Microsoft
This repository contains data analysis and insights derived from analyzing movie data. The goal of this analysis is to provide actionable insights for Microsoft's new venture into the film industry.

# PROJECT OVERVIEW
As Microsoft ventures into the movie industry by establishing its own movie studio, it's crucial to understand the current landscape of the film industry. This repository explores various aspects of movie data, including box office performance, genre trends, and factors influencing movie success.

# CONTENTS
Data: 6 data sets were provided for analysis 
Notebooks: Jupyter notebooks containing data analysis and visualization scripts.
Presentations: PowerPoint presentations summarizing key findings and recommendations

### DATA
The data sets provided were i.e bom. movie gross, tn movie budgets ,imdb,rt.reviews,rt_movie info and tmbd movies.

in this repository we only focused on 3 of them  bom. movie gross, tn movie budgets and imdb.

### JUPYTER Notebook
Jupyter notebooks containing data analysis and visualization scripts
detailed analytical breakdown of analayzed data 

### Presentations
 PowerPoint presentations summarizing key findings and recommendations.

# Analysis Objectives
1.Identify Top-Performing Genres:

Analyze box office gross 
Investigate trends in genre popularity over time.

2.Evaluate Budget vs. Revenue Relationship:

Analyze the correlation between film budget and box office revenue within different genres.

3.Develop Actionable Recommendations:

Develop Actionable Recommendations:

Based on the analysis of genre trends, performance factors, and audience preferences,
formulate clear recommendations for Microsoft Studios on:
The most promising genres and subgenres to focus on for film production.
Considerations for budget allocation and target audience demographics within chosen genres.
The potential of exploring hybrid genre films to expand audience reach.


# DATA ANALYSIS 
 ## 1.DATA CLEANING 
 Imported all data setsbom. movie gross, tn movie budgets and imdb.
 
 the imbd we used an sql query 

 import sqlite3
conn = sqlite3.connect('im.db')
import sqlite3

#### Connect to your SQLite database
conn = sqlite3.connect('im.db')

#### Create a cursor object
cursor = conn.cursor()

##### Retrieve a list of all tables in the database
cursor.execute("SELECT name FROM sqlite_master WHERE type='table';")
tables = cursor.fetchall()

#### Iterate over the tables and display their schema
for table in tables:
    table_name = table[0]
    print(f"Table Name: {table_name}")
    cursor.execute(f"PRAGMA table_info({table_name})")
    columns = cursor.fetchall()
    print("Columns:")
    for column in columns:
        print(column)
    print()

#### Close the cursor and database connection
cursor.close()
conn.close()

 
once all data sets were cleaned and dropped all null 
we focused on the persons,directors and movies table for the Im.db 
for the bom.movies we focused on all columns ,where as for  tn movie budgets we focused on the porduction, foreign gross and worldwide gross mainly 

## merged data code

#### Selecting specific columns from movies_df
movies_df_selected = movies_df[['movie', 'studio', 'domestic_gross_x', 'foreign_gross', 'year', 'production_budget', 'domestic_gross_y', 'worldwide_gross']]

#### Selecting specific columns from movies_df2
movies_df2_selected = movies_df2[['movie', 'genres', 'primary_name','runtime_minutes']]

#### Merging the two DataFrames on the common column 'movie'
movies_select = pd.merge(movies_df_selected, movies_df2_selected, on='movie', how='inner')

#### Displaying the merged DataFrame
movies_select

# DATA VISUALIZATION 
we mainly created visualization  for 
Bar graphs showing the genre that was allocated the highest production budget 
 
 Bar graphs showing the genre that gained the highest gross both domestic and worldwide


 Correlation  graphs showing how production cost influences gross profit for both  foreign and domestic 



 # CONCLUSION
 The analysis scripts will generate reports and visualizations located in the Powerpoint slide . The powerpoint slide will summarize the key findings and insights derived from the data analysis.