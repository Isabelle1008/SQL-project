What issues will you address by cleaning the data?

I removed duplicates in the tables all_sessions and analytics
and i established primary keys in all tables



Queries:
Below, provide the SQL queries you used to clean your data.

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
