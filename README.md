# JSON-Data-Wrangling
_Springboard Data Science Career Track - mini project on JSON data wrangling_
*****

Project Objective
-------------
Using data in file `data/world_bank_projects.json` and the techniques demonstrated
1. Find the 10 countries with most projects
2. Find the top 10 major project themes (using column 'mjtheme_namecode')
3. In 2. above you will notice that some entries have only the code and the name is missing. Create a dataframe with the missing names filled in.

_source for data:_
[http://jsonstudio.com/resources/](http://jsonstudio.com/resources/)

Solution
--------
**About the dataset:** The dataset gives information about the projects funded by The World Bank to different countries. The dataset contains 
one row of data for each project funded. It has information 500 projects and for each project there are 50 attributes / columns. More
information on the dataset can be found at [http://data.worldbank.org/data-catalog/projects-portfolio.](http://data.worldbank.org/data-catalog/projects-portfolio) 
The dataset includes basic information such as the project title, task manager, country, project id, sector, themes, commitment amount, product line, and financing. It also provides links to publicly disclosed online documents.

**Solution Summary:** To solve this problem, following is the high level approach that has been followed
1. Read the JSON file using <code>pandas.read_json</code>
2. Use <code>value_counts()</code> function on the `countryname` column to get the 10 countries with most projects
3. The major project themes are contained as a dict in `mjtheme_namecode` column, there are multiple steps to get the top 10 major project themes
  
    - Normalize and load the `mjtheme_namecode` column
    - Find the top 10 major project themes by using the <code>value_counts()</code> function
    - Some of the theme names in the <code>name</code> column are missing, in these missing cells, the value contained is `''` and not a <code>NaN</code>, follow a two step process to clean it up: sort by the code, convert all `''` to  the name values using the <code>replace()</code> function with _forward fill_ method
