-- List the overall top five names in alphabetical order and find out if each name is "Classic" or "Trendy."
SELECT
	first_name
	, SUM(num) AS sum
	, CASE WHEN COUNT(first_name) >= 50 THEN 'Classic'
		   ELSE 'Trendy'
	  END AS popularity_type
FROM baby_names
GROUP BY first_name
ORDER BY first_name
LIMIT 5;


-- What were the top 20 male names overall, and how did the name Paul rank?
SELECT
	DENSE_RANK() OVER(ORDER BY SUM(num) DESC) AS name_rank
	, first_name
	, SUM(num) AS sum
FROM baby_names
WHERE 1=1
	AND sex = 'M'
GROUP BY first_name

ORDER BY sum DESC
LIMIT 20;


-- Which female names appeared in both 1920 and 2020?
SELECT
	first_name
	, COUNT(first_name) AS total_occurrences
FROM baby_names
WHERE 1=1
	AND year IN(1920, 2020)
	AND sex = 'F'
GROUP BY first_name
HAVING COUNT(first_name) > 1
