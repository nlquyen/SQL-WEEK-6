# SQL-WEEK-6
#IBM Data Analytics SQL with R Final Project

#Problem 5
#How many hectares of Rye were harvested in Canada in 1968?
dbGetQuery(conn, "SELECT SUM(HARVESTED_AREA) 
                    FROM CROP_DATA 
                    WHERE YEAR = 1968 AND
                    GEO = 'CANADA' AND 
                    CROP_TYPE = 'Rye'")

#Problem 10
#Rank the crop types harvested in Saskatchewan in the year 2000 by their average yield. Which crop performed best?
dbGetQuery(conn,"SELECT CROP_TYPE AS CROP_RANK,  
            AVG_YIELD AS AVG_YIELD_2000 
    FROM CROP_DATA
    WHERE YEAR = 2000 AND
    GEO = 'Saskatchewan'
    ORDER BY AVG_YIELD_2000 DESC LIMIT 10")    

 #Problem 12: Use a subquery to determine how much wheat was harvested in Canada in the most recent year of the data.
 dbGetQuery(conn, "SELECT SUM(HARVESTED_AREA) AS TOTAL_WHEAT
        FROM CROP_DATA
        WHERE YEAR = (SELECT MAX(YEAR) FROM CROP_DATA
        WHERE GEO = 'CANADA' AND CROP_TYPE = 'Wheat')"
)
