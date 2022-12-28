![Dashboard 1](https://user-images.githubusercontent.com/98208084/209764597-b68f5b9c-b431-4f29-a91c-78b426d64967.png)

## Covid Dashboard - Tableau

Motivation: after completion of my Data Science and Decisions degree at UNSW I feel that my skillset is primarily lacking in the area of Data Visualisation industry practices. One particularly sought-out skill which will be the main focus of this blog is Tableau. Tableau is a powerful data visualization tool that is widely used in various industries to analyze and communicate complex data. COVID-19 was chosen as the focus of this project since the pandemic has been major factor in the lives of many individuals and businesses alike since 2019. The global pandemic has also led to a large abundance of geospatial data which will be used in this project.  

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

### Data Exploration
The data used in this project is relatively clean and thus does not need to undergo any cleaning. 
We can go straight to writing SQL queries to retrieve the data we want from our database. 

 ```tsql
SELECT SUM(new_cases) as total_cases, SUM(CAST(new_deaths as int)) as total_deaths, SUM(CAST(new_deaths as int))/SUM(new_cases)*100 as DeathPercentage
FROM PortfolioProject..CovidDeaths
WHERE continent is not null
ORDER BY 1,2
 ```
This first query gives us information on the aggregate number of cases and deaths as well as death percentage of confirmed cases. 

```tsql
SELECT location, SUM(CAST(total_deaths as int)) as TotalDeathCount
FROM PortfolioProject..CovidDeaths
WHERE continent is null
	and location not in ('World', 'European Union', 'International', 'High income', 'Upper middle income', 'Lower middle income', 'Low income')
GROUP BY Location
ORDER BY TotalDeathCount desc
```
This next query gives us the total number of deaths in each continent.

```tsql
SELECT location, population, MAX(total_cases) as HighestInfectionCount, MAX((total_cases/population)*100) as PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
GROUP BY Location, Population
ORDER BY PercentPopulationInfected desc
```
The third query returns information on the location, population, highest infection count and percent of the population that has been infected.

```tsql
SELECT location, population, date, MAX(total_cases) as HighestInfectionCount, MAX((total_cases/population)*100) as PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
GROUP BY Location, Population, date
ORDER BY PercentPopulationInfected desc
```
Finally, the last query gives us the same information as query 3 but as a time series. 

### Dashboard Building
The final step of this project is to visualise my findings in a Tableau dashboard. 
My key takeaways from this part of the project is 
- the importance of having a clear goal in mind for what I want to achieve from the dashboard
- to keep the dashboard simple in terms of information and design
- testing and iterating the dashboard to imrove its design






