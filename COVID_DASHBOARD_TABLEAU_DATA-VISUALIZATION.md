Step into a world of data-driven understanding with my crafted Tableau dashboard focused on COVID-19. 
This dashboard transforms raw statistics into visual stories, offering a comprehensive snapshot of the pandemic's impact.
LINK FOR THE COVID_DASHBOARD IN TABLEAU

-------------------------------------------------------------------------------------------------------------------------------

https://public.tableau.com/app/profile/shabeen.abdul.varis/viz/COVID_DASHBOARD_16916884847960/Dashboard1

---------------------------------------------------------------------------------------------------------------------------------

 \* Sql Queries Used For Tableau Dashboard *\

-- 1

-- select covid data of india

SELECT Location, date, total_cases, new_cases, total_deaths, population
FROM covid_death
WHERE continent IS NOT NULL AND location='india' 
ORDER BY 1,2;

--2


-- Countries with Highest Infection Rate compared to Population

SELECT Location, Population, MAX(total_cases) AS HighestInfectionCount,  Max((total_cases/population))*100 AS PercentPopulationInfected
FROM covid_death
WHERE continent<>''
GROUP BY Location, Population
ORDER BY PercentPopulationInfected DESC;

--3

-- Countries with Highest Death Count per Population

SELECT location ,max( cast(total_deaths as unsigned)) as TotalDeathCount
FROM covid_death
WHERE continent <>''
GROUP BY Location
ORDER BY TotalDeathCount DESC;

--4

-- BREAKING THINGS DOWN BY CONTINENT
-- Showing contintents with the highest death count per population

SELECT continent, MAX(cast(Total_deaths as unsigned)) as TotalDeathCount
FROM covid_death
WHERE continent<>''
GROUP BY continent
ORDER BY TotalDeathCount DESC;

--5


-- Total Cases vs Population
-- Shows what percentage of population infected with Covid

SELECT Location, date, Population, total_cases,  (total_cases/population)*100 AS PercentPopulationInfected
FROM covid_death
WHERE location = 'india'
ORDER BY 1,2;



