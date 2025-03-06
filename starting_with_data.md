Question 1: Find the total number of unique visitors (`fullVisitorid`)


SQL Queries: SELECT COUNT(DISTINCT fullvisitorid) AS unique_visitors
            FROM all_sessions;



Answer: 



Question 2: removing duplicates

SQL Queries: WITH cte AS (
             SELECT ctid, ROW_NUMBER() OVER (PARTITION BY fullvisitorid ORDER BY ctid) AS row_num
             FROM all_sessions
             )
            DELETE FROM all_sessions
            WHERE ctid IN (
            SELECT ctid
            FROM cte
            WHERE row_num > 1
            );
    
            WITH cte AS (
            SELECT ctid, ROW_NUMBER() OVER (PARTITION BY fullvisitorid ORDER BY ctid) AS row_num
            FROM analytics
            )
            DELETE FROM analytics
            WHERE ctid IN (
            SELECT ctid
            FROM cte
            WHERE row_num > 1
            );





Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
