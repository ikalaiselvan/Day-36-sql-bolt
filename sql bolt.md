Lesson 1:

	1. select title from movies
	2. select director from movies
	3. select title, director from movies
	4. select title, year from movies
	5. select * from movies
	
Lesson 2: 

	1. select * from movies where id = 6;
	2. select * from movies where year between 2000 and 2010;
	3. select * from movies where year not between 2000 and 2010;
	4. select title, year from movies limit 5; (Only movie name and year)
		a. 	select * from movies where id limit 5; (All details of movie)
			select * from movies where id between 1 and 5; (All details of movie, If id is series)

Lesson 3: 

	1. SELECT title from movies
	where title like "toy story%";
		a. SELECT * from movies where director like "John Lasseter"; (All details)
		
	2. SELECT * from movies 
	where director = "John Lasseter"; (case sensitive)
		a. SELECT * from movies 
		where director like "john lasseter"; (case insensitive)
		
	3. SELECT * from movies
	where director != "John Lasseter"; (case sensitive)
		a. SELECT * from movies
		where director not like "john lasseter"; (case insensitive)
		
	4. SELECT * from movies where title like "wall-_";
		a. SELECT * from movies where title like "wall-%";

Lesson 4:

	1. select distinct director from movies 
	order by director; (distinct key to remove duplicates columns from multiple table with same title)
	
	2. select title from movies 
	order by year desc
	limit 4;
	
	3. select title from movies
	order by title
	limit 5;
	
	4. select title from movies
	order by title
	limit 5 offset 5;

Lesson 5:

	1. select city, population from north_american_cities
	where country = "Canada";

	2. select city from north_american_cities
	where country = "United States"
	order by latitude desc;

	3. select city, longitude from north_american_cities
	where Longitude < -87.629798
	order by longitude;
	
	4. select * from north_american_cities
	where country like "mexico"
	order by population desc
	limit 2;
	
	5. select * from north_american_cities
	where country like "united states"
	order by population desc
	limit 2
	offset 2;
	
Lesson 6:

	1. SELECT title, domestic_sales, international_sales FROM movies
	inner join boxoffice
	on movies.id = boxoffice.movie_id;
		A. SELECT title, domestic_sales, international_sales FROM movies
		inner join boxoffice
		on id = movie_id;
		
		B. SELECT kalai.title, director, year,
		       selvi.domestic_sales,
		       selvi.international_sales,
		       selvi.rating
		FROM   boxoffice selvi
		       INNER JOIN movies kalai
		               ON selvi.movie_id = kalai.id;
		
	2. SELECT * FROM movies
	inner join boxoffice
	on id = movie_id
	where international_sales > domestic_sales;
	
	3. select title, rating from movies
	join boxoffice
	on id = movie_id
	order by rating desc;
	

Lesson 7:

	1. select building from employees
	group by building
	
		A. select distinct building_name from buildings
		left join employees
		on building = building_name
		where years_employed not null;
	
	2. select * from buildings;
	
	3. select distinct building_name, role from buildings
	left join employees
	on building_name = building;
	
Lesson 8:

	1. select name, role from employees
	where building is null;
	2. select building_name from buildings
	left join employees
	on building = building_name
	where building is null;
	
Lesson 9:

	1. select title, (domestic_sales + international_sales)/ 1000000 as Total_salesin_MU from movies
	left join boxoffice
	on id = movie_id;
	2. select title, rating * 10 as Percentage
	from movies
	left join boxoffice
	on id = movie_id;
	3. select title, year from movies
	where year % 2 = 0;
	
Lesson 10:

	1. select name, max(years_employed) from employees;
	
	2. select role, avg(Years_employed) as average_years from employees
	group by role;
	
	3. select building, sum(years_employed) as years_vice_sum from employees
	group by building;
	
Lesson 11:

	1. select role, count(years_employed) as Artists from employees
	where role like "artist";
		A. select role, count(years_employed) as Artists from employees
		where role = "Artist"; (case sensitive)
		
	2. select role, count(years_employed) as Artists from employees
	group by role;

	3. select role, sum(years_employed) as sum_of_engineer from employees
	where role like "engineer";
	
Lesson 12:

	1. select director, count(title) as Movie_count from movies
	group by director;

	2. select director, sum(domestic_sales+international_sales) as total_sale  from movies
	left join boxoffice
	on id = movie_id
	group by director;
	
	
Lesson 13:

	1. insert into movies
	values (15, "toy story 4", "john lasseter", 2000, 114);
	
	2. insert into boxoffice
	values (15, 8.7, 340*1000000, 270*1000000);
	
	
Lesson 14:

	1. update movies
	set director = "John Lasseter"
	where id = 2;
		A. update movies
		set director = "John Lasseter"
		where title = "A Bug's Life";
		
	2. update movies
	set year = 1999
	where title = "Toy Story 2";
	
	3. update movies
	set title = "Toy Story 3", director = "Lee Unkrich"
	where id = 11;
	
Lesson 15:

	1. delete from movies
	where year < 2005;

	2. delete from movies
	where director = "Andrew Stanton";
	
Lesson 16:
	
	1. create table database(
	name text,
	version text,
	download_count integer
	);
	
	
Lesson 17:

	1. alter table Movies
	add Aspect_ratio float
	
	2. alter table Movies
	add language text
	default English;
	
Lesson 18:

	1. drop table if exists movies;
	2. drop table if exists boxoffice;
