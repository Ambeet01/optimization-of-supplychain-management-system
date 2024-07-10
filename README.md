create database dataanalytics_db;
use dataanalytics_db;
show tables;
select * from mba;
desc mba;
create table education(datasrno int, workex int, gmat int);
desc education;
create table education(datasrno int, workex int, gmat int);
desc education;
Insert into education values(1, 10, 700), (2, 11, 650), (3, 12, 690);
select * from education;

# OPT_LOCAL_INFILE=1   ---> set this parameter in workbench user connection settings (under Advanced)
show variables like 'secure_file_priv';
show variables like '%local%';
# OPT_LOCAL_INFILE=1   ---> set this parameter in workbench user connection settings (under Advanced)
show variables like 'secure_file_priv';
show variables like '%local%';
# OPT_LOCAL_INFILE=1   ---> set this parameter in workbench user connection settings (under Advanced)
LOAD DATA  INFILE'gh repo clone richaaprasad/Covid-19-Database-SQL-And-Power-BI'
INTO TABLE education 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"' 
LINES TERMINATED BY '\n' 
IGNORE 1 ROWS;
select * from education;
SELECT workex AS mode_workex
FROM (
    SELECT workex, COUNT(*) AS frequency
    FROM education
    GROUP BY workex
    ORDER BY frequency DESC
    LIMIT 1
) AS subquery;
SELECT VARIANCE(workex) AS workex_variance
FROM education;
