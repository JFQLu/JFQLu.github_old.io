![Dashboard 1](https://user-images.githubusercontent.com/98208084/209764597-b68f5b9c-b431-4f29-a91c-78b426d64967.png)

## Covid Dashboard - Tableau

Motivation: after completion of my Data Science and Decisions degree at UNSW I feel that my skillset is primarily lacking in the area of Industry practices of Data Visualisation. One particularly sought-out skill which will be the main focus of this blog is Tableau. Tableau is a powerful data visualization tool that is widely used in various industries to analyze and communicate complex data. COVID-19 was chosen as the focus of this project since the pandemic has been major factor in the lives of many individuals and businesses alike since 2019. The global pandemic has also led to a large abundance of geospatial data which will be used in this project.  

Technologies used: 
- Excel
- Microsoft SQL Server Management Studio (SSMS)
- Tableau Public 

---


### Data Collection
The data for this project comes from [Link](https://ourworldindata.org/covid-deaths). 
#### Data includes (non-exclusive): 
- date
- location
- new_cases 
- new_deaths
- population

We can then import this data into a SQL database to be used in querying in SSMS. 

### Data Analysis
The data used in this project is relatively clean and thus does not need to undergo any cleaning. 
We can go straight to writing SQL queries to retrieve the data we want from our database. 


 ```tsql
 SELECT *
 FROM sys.tables
 WHERE [name] = 'SomeTable'
 ```
